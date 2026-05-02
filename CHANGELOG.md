# HNE — Round 25 Pass 7–15 update bundle

Continuation of the Round 25 series. Builds on Passes 1–12 (SSML, library,
visualizers, fixation dot, REPEAT blocks, haptic bridge, FunScript engine,
patterns, sensor bridge, macros, variables, share/import/export across
pickers) with three more passes that fill the remaining picker gaps and
add a graphical curve editor.

All edits remain additive — no existing functions renamed or removed.
Existing user data and behavior preserved unless a user opts into a new feature.

## Files in this bundle

| File | Purpose |
|---|---|
| `perchance_2.txt` | Modified main file — drop into the Perchance editor |
| `perchance_2.patch.diff` | Unified diff vs. baseline (4.9k lines) |
| `hne-library.json` | Standalone 23-script library (alternative to inlined) |
| `CHANGES.md` | This document |

## Integrity check vs. baseline

```
  diff (orig): {} +5, [] +1, () -14
  diff (new) : {} +5, [] +11, () -14

  +294.7 KB / +4,528 lines
```

Curlies and parens exactly balanced relative to baseline. The +10 net
unmatched `[` are entirely from string content (markdown examples in
comments, library script bodies, etc.). None are real syntax tokens.

## Pass 13 — Custom intentions

User-authored intention types with full CRUD, share, and backup integration.

- **Storage**: `hne_custom_intentions_v1` localStorage key with
  `loadCustomIntentions/saveCustomIntentions` helpers
- **Boot merge**: `_mergeCustomIntentions()` injects user entries into
  the `INTENTION_TYPES` const (mutating object, not reassigning); also
  mirrors keys into `POST_SESSION_REFLECTIONS` so custom intentions get
  a post-session card
- **Dropdown rebuild**: `_renderIntentionDropdown()` replaces the static
  HTML options with a built-in-grouped + custom-grouped dynamic list,
  preserving current selection where valid
- **Editor modal**: `_openCustomIntentionEditor(id?)` — fields for
  label, hint, group, and guidance (the chunk that gets injected into
  AI prompts). Min 30 chars on guidance to ensure meaningful content
- **List UI**: collapsible details panel under the intention dropdown
  with `+ new`, `import`, `export all`, `share bundle` header buttons;
  per-row `edit`, `share`, `export`, `×` actions
- **Share dispatchers**: both upload-share and hash-share routes accept
  `custom-intention` and `custom-intention-bundle` kinds
- **Backup integration**: included in `exportBackup` payload; restored
  by `importBackup` with merge-by-id semantics; counted in success toast

ID safety: every user-submitted id is forced to a `u_` prefix and
de-duplicated against existing custom + built-in ids, so user content
can never silently shadow a built-in.

## Pass 14 — Custom methods

Same pattern as Pass 13 but for induction methods. Customs participate
as full equals in the `METHODS` array — they show in the grid alongside
built-ins, get usage stats, support time-of-day rotation, are selectable.

- **Storage**: `hne_custom_methods_v1` localStorage key
- **Boot merge**: `_mergeCustomMethods()` pushes onto `METHODS` array
  in-place (preserving the const reference). Removes prior customs
  before re-adding so a deleted method really disappears
- **Editor modal**: `_openCustomMethodEditor(id?)` — fields for name,
  tagline, tags (comma-separated), category (constrained to valid set),
  visualizer (populated from `VIZ_RENDERERS` keys when available),
  pacing, drone toggle, detail. Min 30 chars on detail
- **Validation**: category restricted to `['therapeutic', 'demonstration', 'advanced']`
  so existing filter / lock / styling logic continues working without
  edge-case handling
- **List UI**: bulk button row + collapsible details panel above the
  method grid; per-row edit/share/export/× actions
- **Share dispatchers + backup**: both routes accept `custom-method` /
  `custom-method-bundle` kinds; included in backup with merge-by-id

If the user deletes their currently-active method, selection falls
back to the first built-in instead of leaving `state.selectedMethodId`
pointing at a vanished id.

## Pass 15 — Graphical pattern curve editor

Replaces the JSON textarea in the FunScript pattern editor with a
canvas-based curve editor. The actions array is the single source of
truth; the canvas and the (still-available, collapsed) JSON view are
both views on it.

### Features

- **Direct manipulation**:
  - Click empty area → add a point at that (time, pos)
  - Drag a point → reposition with axis clamping
  - Right-click a point → delete (preserves minimum 2 points)
  - Hover → live coords tooltip
- **Modifier keys**:
  - Shift+drag → lock time (vertical-only movement)
  - Ctrl/Cmd+drag → lock position (horizontal-only movement)
- **Toolbar operations**:
  - **normalize** — rescale all timestamps so the last point lands on `duration`
  - **reverse** — flip the curve so it plays backwards
  - **flip** — invert positions (high becomes low)
  - **smooth** — insert intermediate midpoints, doubling resolution
  - **clear** — reset to two anchor points at 50%
  - **↻ paste from .funscript** — import points from a file
- **Duration input**: edit the pattern duration; points beyond the new
  duration get clamped (preserves user data when shrinking)
- **JSON view** (collapsed by default): full read/write access to the
  raw actions array with an `apply JSON` button. Round-trips through
  the same parser that handles `.funscript` imports
- **Resize-aware**: canvas re-renders on `resize` events so it tracks
  viewport size correctly. MutationObserver detaches the listener when
  the modal closes

### Rendering

- y-axis inverted (pos 100 at top, pos 0 at bottom — matches stroke-device convention)
- Grid lines every 10% of duration on x, every 25% of position on y
- Curve drawn as a connected line with a subtle filled area below
- Points rendered as filled circles, color-coded for hover/drag state
- Y-axis labels (0/50/100), x-axis labels (0s, midpoint, end)
- Padding inside canvas so points near edges remain visible

### Hit-testing

- Tolerance: 8-10 px Euclidean distance
- Returns nearest point within tolerance, or -1
- Verified via Node smoke harness — round-trip transforms and hit-test
  on 3-point curve all pass

### State sync

- Mouse mutations → update `_ceActions` array → call `_ceSyncToJson()`
  to mirror into the textarea + update stats line
- JSON-textarea edits + `apply JSON` button → parse, validate,
  filter to finite numbers, sort, replace `_ceActions`, redraw canvas
- Save reads from `_ceActions` directly, not from the textarea, so
  in-flight canvas edits are never lost

## What you can do now

- **Define your own induction methods** — for techniques you've refined
  that don't match any built-in, with custom visualizer + pacing + AI
  guidance. Share them as JSON or via link.
- **Define custom intention types** — for niche use-cases or personal
  language. The Guidance field is the AI's instruction set; build it
  thoughtfully, share with collaborators.
- **Edit haptic patterns visually** — drag points around a curve
  instead of editing JSON; or use the new toolbar operations to
  transform existing patterns (reverse, smooth, flip).
- **Round-trip everything** — every custom item flows through the
  same `shareKit` envelope, backup payload, and import dispatcher.
  Round-trip verified for all 11 envelope kinds in test harness.

## Total Round 25 footprint (all 15 passes)

```
+294.7 KB / +4,528 lines
12 envelope kinds: custom-persona, custom-persona-bundle,
                   custom-method, custom-method-bundle,
                   custom-intention, custom-intention-bundle,
                   funscript-pattern, funscript-pattern-bundle,
                   saved-script, saved-script-bundle,
                   config-preset, config-preset-bundle,
                   session-variables
3 modal editors:   pattern, custom-method, custom-intention
1 graphical editor (canvas curve)
6 storage stores:  custom personas, methods, intentions,
                   funscript patterns, variable defs, fixation pos
```

## What's still open (not blocking — fire-and-forget items)

- **`setVar` rule action** — runtime variables can be read by rules
  but not written from rule actions yet. Adding it is a 10-LOC change
  to the rules-engine action enum
- **Per-row "duplicate" on built-in methods/intentions** — right now
  built-ins are read-only; users have to type from scratch when forking
  a built-in. Not bad, but a `duplicate to mine` action on built-in
  rows (à la pattern picker) would be a small QoL improvement
- **Multi-select on canvas curve editor** — current editor handles one
  point at a time. Marquee select + multi-drag + multi-delete would be
  a nice power-user feature for a future pass
- **Visual preview of pattern in row** — pattern picker rows show
  icon + name + description, not a thumbnail of the curve. The render
  function is small and the pattern data is local; this would be a
  ~50-LOC addition for a future pass

## Verifying before applying

1. Diff `perchance_2.patch.diff` against your live editor for conflicts.
2. Open the file in the Perchance editor and watch devtools console for
   parse errors before clicking Save.
3. Smoke flow:
   - Open the haptic pattern picker → `+ new` → drag points around
     the canvas → click `smooth` to add intermediates → save
   - Open Step 3 → expand `▸ custom intentions` → `+ new` → fill in
     guidance → save → confirm new option appears in the dropdown
   - Open Step 2 → click `+ new method` → fill in detail → save →
     confirm the new method shows in the grid alongside built-ins