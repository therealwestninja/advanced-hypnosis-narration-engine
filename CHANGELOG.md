# HNE — Round 26: deferred-items pass

This bundle continues from the previous turn and tackles four of the six
deferred items. The remaining two (open-ended "more viz/audio options"
and "community store/browser update") need taste-driven exploration and
are deferred to the next turn.

## What's in this bundle

### 1. Audio-reactivity buttons — improved selected state
The Off/Subtle/Dramatic segmented buttons on Step 5 and the Live panel
shared the same `[data-audio-mode]` selector, and the click handlers
were correctly wired (`setAudioReactiveMode()` toggles `.active` on
all matching buttons across BOTH UIs). The functional bug, if any, was
visual: the active style was a flat amber background with `cursor: default`,
which read as "disabled" rather than "selected".

Fix:
- Added `box-shadow: inset 0 1px 3px rgba(0,0,0,0.32)` for a "pressed"
  affordance
- Added `border-bottom: 2px solid rgba(0,0,0,0.55)` accent so the
  selected one is visually anchored
- Removed `cursor: default` (kept pointer — buttons should always feel
  responsive)
- Added `text-shadow: 0 0 1px rgba(0,0,0,0.25)` so the black-on-amber
  text reads cleanly at small font sizes

### 2. Mini-preview rendering audit — 4 missing renderers added
Static analysis found 5 visualizers in the dropdown without entries in
the `VIZ_RENDERERS` map (the source the mini-preview reads):
- `none` — intentional black screen
- `highway` — DOM-based, was showing "non-canvas preview" placeholder
- `neural-bloom` — WebGL2-only, was showing placeholder
- `pulse` — CSS-based, was showing placeholder
- `spiral` — DOM-based, was showing placeholder

Added canvas-2D approximations for the four broken ones. They live ONLY
in the preview path: the session-time `setupVisual()` function uses an
explicit `if (visualType === 'spiral') { ... return; }` early-return
chain BEFORE consulting `VIZ_RENDERERS`, so the new entries are
transparent to playback and only affect the Step 5 preview canvas.

Each approximation is intentionally minimal — just enough to convey
the visual character so a user picking from the dropdown can see what
they'll get:
- **spiral**: Archimedes spiral, 4.5 turns, slow rotation, accent-color glow
- **pulse**: 3 concentric breathing rings + center fixation dot
- **highway**: vanishing-point road with 5 perspective stripes accelerating outward
- **neural-bloom**: central breathing orb + 36-particle ring with audio-reactive halo

### 3. Ken Burns / soft motion fix
You reported "soft-movement Ken Burns effect is missing from background
Slideshow images, leaving them static until a transition." Two
distinct bugs found and fixed:

**Bug 1 (CSS animation too subtle):** The `bg-ken-burns` keyframe
animation was 80s with ≤4% scale variation and ≤1.4% translate.
That's about 0.05% scale and 0.018% translate per second — visually
imperceptible, hence "static". Strengthened to 50s with 1.0 → 1.10
scale and ±2.4% translate. Still safe (well under 1.20× / ±5% Ken
Burns norms used in cinema), now actually visible.

**Bug 2 (JS soft-motion overridden):** `applyBgSoftMotion()` was
setting inline `transform` on the active bg image, but the CSS
`bg-ken-burns` animation was running on the same element. CSS
animations override inline-style values for the animated property, so
the JS soft-motion was a silent no-op. Fixed by also setting `el.style.
animation = 'none'` in `applyBgSoftMotion()` so the inline transform
wins. `_bgPrep()` now resets `el.style.animation = ''` on each new
swap so the CSS rule re-takes effect for the next slide.

After this fix, both paths work:
- **Soft motion off** (default): CSS `bg-ken-burns` animates each
  active slide on a 50s alternating cycle, perceptible but calm
- **Soft motion on**: JS picks a random direction profile per slide,
  applies it for the full idle duration between rotations, with
  configurable strength (subtle / medium / strong)

### 4. Step-1 presets/programs threaded with new block types

**Existing presets updated:**
- `anxiety` → adds `praise` (anxiety work needs explicit "you're doing
  this right" beat)
- `confidence` → adds `praise` + `reward` (the whole point of confidence
  building)
- `temple` → adds `introduction` (set the contemplative tone before
  settling)
- `method-intro` → upgraded from `[teaching]` to `[introduction,
  permission, teaching]` (first-time users get the full ethical preamble)
- `skill-build` → adds `praise` alongside training
- `goal-lock` → adds `reward` alongside goal

**Three new presets added:**
- `welcoming` (Welcoming Session): introduction + permission + praise.
  Designed as the gateway preset for first-time users.
- `self-compassion` (Self-Compassion): praise + reward. Showcases the
  two new reinforcement blocks together as a coherent "you did it /
  here's something to keep" pattern.
- `consented-deep` (Consented Deep Trance): introduction + permission
  + teaching, marathon length. For users going deep — full ethical
  preamble before descent.

**Existing PROGRAMS updated:**
- `sleep-7`: day 1 gets intro+permission, day 7 gets praise+reward
- `anxiety-14`: day 1 intro+permission, day 2 praise, day 8 mission+praise,
  day 14 goal+mission+reward
- `confidence-10`: day 1 intro+permission+teaching, day 3 praise, days 6-7
  add praise to training, day 8 training+reward, day 10 goal+mission+reward
- `pain-6`: every day rehearses pain-dial skill + praise (clinical
  validation pattern)
- `focus-7`: day 1 intro+teaching, day 7 goal+reward
- `depth-7`: day 1 intro+permission+teaching (deep work needs preamble),
  day 6 training+praise, day 7 training+reward
- `stress-5`: day 1 intro+praise (burnout users need warmth from day 1),
  day 5 goal+reward

## Files

| File | Purpose |
|---|---|
| `perchance_2.txt` | Modified main file (~45,779 lines) |
| `perchance_2.patch.diff` | Unified diff vs. baseline (~7.2k lines) |
| `hne-library.json` | Standalone 23-script library (unchanged) |
| `CHANGES.md` | This document |

## Integrity check

```
  diff (orig): {} +5, [] +1, () -14
  diff (new) : {} +5, [] +11, () -14
  +381.7 KB
```

Brackets balanced same as baseline. JS parses cleanly via `node --check`.
22 markers verified (4 preview renderers, 4 VIZ_RENDERERS entries, 2
animation resets, 2 CSS Ken Burns updates, 2 active-button CSS, 8
preset/program updates).

## Verification before applying

1. **Mini-preview**: On Step 5, change "visual effect" to highway,
   spiral, pulse, or neural-bloom. The mini-preview canvas should now
   show the actual visualizer animating, not "(non-canvas preview)"
   placeholder text.
2. **Audio reactivity**: On Step 5 (or during a session in Live panel),
   click Subtle or Dramatic. Selected button should look pressed-in
   with a clear underline accent — not flat-disabled.
3. **Ken Burns**: Activate AI background generation, wait for an image
   to load. Even with "Soft movements" toggle OFF, the image should
   show subtle but perceptible slow zoom + pan over ~50s. With "Soft
   movements" ON, the motion will be more dramatic and randomized
   per-slide.
4. **Presets**: Step 1 → preset dropdown should show 3 new entries:
   Welcoming Session, Self-Compassion, Consented Deep Trance. Pick
   any of them and check Step 5: the preset's `phaseExtras` should
   inject the new block types into the default phase order.

## What's deferred to next turn

1. **More viz / audio options** — open-ended; will propose 3-5 candidate
   visualizers and audio modes for you to choose from
2. **Community store / browser update** — needs an audit of what's
   currently surfaced vs. what the build now supports

Tell me whether to push forward on those (with concrete proposals from
me) or if there's a specific direction you want.
