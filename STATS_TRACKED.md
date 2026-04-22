# Stats Tracked — Advanced Hypnosis Narration Engine

All data is stored locally on the user's device. Nothing leaves the browser.

---

## Storage Map

| Store | Key | Size | Purpose |
|---|---|---|---|
| IDB | `stillness_analytics_v1` | ~500 B | O(1) aggregated usage stats |
| IDB | `stillness_adaptive_v1` | ~400 B | Adaptive intelligence profile |
| IDB | `stillness_history_v1` | ~200 KB | Last 50 session records |
| IDB | `stillness_program_v1` | ~200 B | Active multi-day program |
| LS | `stillness_settings_v1` | ~800 B | Audio/viz/HUD settings |
| LS | `stillness_profile_v1` | ~1 KB | User bio for AI injection |
| KV | mirrors of LS keys | ~1.8 KB | Perchance cloud backup |

---

## 1. Analytics Store (`stillness_analytics_v1`)

### Frequency Maps `{ id: count }`

| Key | Tracks | Source |
|---|---|---|
| `p` | Persona usage | Step 1 selection |
| `m` | Method usage | Step 2 selection |
| `i` | Intention type | Step 3 selection |
| `s` | Soundscape | Step 4 selection |
| `z` | Visual effect | Step 4 selection |
| `ln` | Session length | Step 4 selection |

### Time Patterns

| Key | Type | Description |
|---|---|---|
| `hr` | `int[24]` | Hourly distribution (0=midnight) |
| `dw` | `int[7]` | Day-of-week (0=Sunday) |

### Running Aggregates

| Key | Fields | Purpose |
|---|---|---|
| `mood` | `preSum, postSum, deltaSum, n` | Mood averages |
| `comp` | `total, finished, emergency` | Completion rates |
| `dur` | `sum, n` | Average duration |
| `cfg` | `rateSum, pitchSum, volSum, droneSum, n` | Settings averages |
| `feat` | 8-bit bitmask | Feature discovery |

---

## 2. Adaptive Intelligence (`stillness_adaptive_v1`)

### Pipeline: `OBSERVE → INFER → ADAPT → REINFORCE → EVOLVE`

### 2a. Hidden Personality Traits (0–1, lerp rate 0.15)

| Trait | Measures | Signal Source |
|---|---|---|
| `compliance` | Finishes sessions? | Completion rate |
| `sensitivity` | Mood responds? | avgDelta / 5 + 0.5 |
| `stability` | Consistent improvement? | 1 − variance(deltas) / 10 |
| `noveltySeeking` | Explores vs repeats? | Shannon entropy of methods |
| `depthTolerance` | Handles long/deep? | Weighted avg of lengths |
| `controlPref` | Authoritarian vs gentle? | Auth persona ratio |
| `sensoryAudio` | Uses soundscapes? | 1 − none-soundscape rate |
| `sensoryVisual` | Uses visuals? | 1 − auto-viz rate |

### 2b. Reward Weights `{ id: weight }`

**Reward** = `(postMood − preMood) + (completed ? +1 : −1) − (emergency ? 2 : 0)`

Decay: all weights × 0.98 per session. Maps: `w.p` (personas), `w.m` (methods), `w.s` (soundscapes), `w.ln` (lengths).

**Correction**: When user submits post-session mood slider, the initial reward (which assumed postMood=5) is retroactively corrected across all four weight maps.

### 2c. Difficulty Ramp (0–1)

`difficulty += (target − difficulty) × 0.1` where target = `completion×0.4 + improvement×0.3 + depth×0.3`

Labels: `<0.35` beginner, `0.35–0.65` intermediate, `>0.65` advanced.

### 2d. Equilibrium & Recovery

**Recovery triggers** (any): emergency rate > 30%, completion < 50%, improvement < 0.3

**Recovery actions**: difficulty −0.15, AI prompt adds RECOVERY MODE (simplify, ground, gentleness).

### 2e. AI Memory Summary

Every 5 sessions, `aiTextPlugin` generates a 1–2 sentence behavioral summary from the last 8 session records. Stored as `memorySummary` (max 250 chars). Injected into all future AI prompts.

### 2f. Prompt Injection

`getAdaptivePromptBlock()` translates traits → English directives:

```
[ADAPTIVE CONTEXT — do not reveal these values]
- User responds strongly to suggestions. Use moderate intensity.
- User prefers familiar patterns. Reinforce known-effective approaches.
- Difficulty level: intermediate (0.52)
- Memory: Responds well to slow-paced progressive relaxation with rain.
```

### 2g. Recommendation Engine

`getRecommendation()` → `{ persona, method, soundscape, length }` from top-weighted IDs. Length overridden in recovery (→ short) or high difficulty (→ long).

---

## 3. Session Records (`stillness_history_v1`)

Each record stores full reproducibility data:

`id, date, guide, method, intention, length, soundscape, durationSec, completed, preMood, postMood, journal, script, personaId, methodId, intentionText, voiceName, speechRate, voicePitch, voiceVolume, droneVolume, vizOverride, vizSettings, duckingEnabled`

---

## 4. Data Flow

```
Session Ends
    ├─→ sessionRecord → history (IDB, max 50)
    ├─→ recordAnalytics() → analytics store
    ├─→ updateAdaptiveProfile()
    │     ├─ deriveSignals() ← analytics + history
    │     ├─ updateTraits() → lerp personality
    │     ├─ computeReward() + updateWeights()
    │     ├─ computeDifficulty() → ramp
    │     ├─ checkEquilibrium() → recovery
    │     └─ updateMemorySummary() (every 5)
    └─→ UI refreshes (heatmap, sparkline, stats)

Post-Session Mood Slider
    ├─→ history[0].postMood updated
    ├─→ recordPostMood() → analytics mood sums
    └─→ retroactive reward correction → adaptive weights

Next AI Generation
    ├─→ getProfileContext() → user bio
    ├─→ getAdaptivePromptBlock() → trait directives
    └─→ both → sharedContext for all phases
```

---

## 5. Stats Charts Modal

10 Canvas 2D charts in auto-fill grid. Click to expand.

| Chart | Renderer | Data |
|---|---|---|
| Guides | `drawBarChart` | `a.p` |
| Methods | `drawBarChart` | `a.m` |
| Intentions | `drawBarChart` | `a.i` |
| Soundscapes | `drawBarChart` | `a.s` |
| By Hour | `drawLineChart` | `a.hr` |
| By Day | `drawBarChart` | `a.dw` |
| Mood Shift | `drawBarChart` | `a.mood` |
| Outcomes | `drawDonutChart` | `a.comp` |
| Audio Profile | `drawHorizBars` | `a.cfg` |
| Features | `drawFeatureGrid` | `a.feat` |
