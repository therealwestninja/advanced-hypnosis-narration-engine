# · Advanced Hypnosis Narration Engine ·

**A free, AI-driven, fully browser-native hypnosis experience generator.**

Generate personalized induction scripts with AI, hear them narrated by the browser's text-to-speech engine, and experience guided sessions with procedural soundscapes, 16 hypnotic visual effects, and real-time customization — all running locally in your browser with zero server dependencies.

Live here: [Perchance.org/advanced-hypnosis-narration-engine](https://perchance.org/advanced-hypnosis-narration-engine). No account required. No downloads. No data leaves your device.

---

## What It Does

1. **Choose a Guide** — 25 built-in personas across four temperaments (contemplative, showman, somatic, authoritarian), each with a distinct voice, vocabulary, and therapeutic style. Create unlimited custom personas.

2. **Choose a Method** — 37 induction techniques across five categories: therapeutic, somatic, demonstration, rapid, and advanced. Methods unlock progressively — rapid at 3 completed sessions, advanced at 7 — so beginners build foundational experience first.

3. **Set an Intention** — 20 intention types from emotional state shifts and post-hypnotic triggers through pain management, sleep induction, and behavioural conditioning. The AI crafts a technically-precise hypnotic suggestion from a rough description. Add your own personal affirmations — the AI weaves them verbatim into deepening and work phases.

4. **Configure** — Session length (2–30 minutes), voice selection with quality scoring, 19 procedural soundscapes, 16 visual effects with live tuning (speed, intensity, complexity, trail), pitch/volume/speed controls, ducking toggle, and per-element HUD toggles. All settings auto-save between sessions.

5. **Generate & Begin** — Per-phase AI generation produces each section individually for higher quality, with live neon progress indicators (dark → amber streaming → green complete → red/yellow error with click-to-retry). Edit the script, then begin a fully narrated, visually guided session with real-time controls.

**Or** — click "I already have a script" on Step 1 to skip configuration entirely, paste your own script, and begin immediately.

The system learns from every session. An invisible adaptive intelligence layer observes user behavior, builds a hidden personality model, and progressively shapes future AI generation to match what works best for each individual.

---

## Features

### Audio
- **19 procedural soundscapes** — engine drone, rain (Poisson-scheduled droplets), ocean waves, crackling fire, singing bowls (additive synthesis), heartbeat, binaural beats (theta 6Hz via ChannelMerger), pink/brown/white noise, forest (birds and breeze), stream (flowing water), wind (gusting), distant thunder, wind chimes, cave (sparse drips with echo), night crickets (chirping insects), temple (deep bell and tonal drones), and spaceship (low engine hum with sci-fi bleeps). All synthesised in real-time with the Web Audio API — no audio files, never loops audibly.
- **Narration ducking** — soundscape volume automatically dips to 20% during speech, ramps back between sentences. Toggleable in Configure.
- **Voice quality scoring** — voices sorted by neural/natural/enhanced quality with tier badges.
- **Ambience recording** — record the procedural soundscape to a downloadable `.webm` file via MediaRecorder.
- **Media Session API** — lock-screen play/pause/stop controls on mobile.

### Visuals
- **16 Canvas 2D renderers** — spiral, breathing circle (4-7-8 pacer with haptic feedback), tunnel, starfield warp, candle focal, moiré interference, vortex, mandala, pendulum harmonograph, lissajous, colour wash, flow-field particles, plasma, canvas pulse, and two kaleidoscope meta-effects wrapping flow field and plasma.
- **Live visual tuning** — speed (0.1×–2.0×), intensity, complexity, and trail/fade sliders update the active effect in real-time.
- **Phase-reactive speed** — visuals slow during settling (0.5×) and deepener (0.7×), composited with user speed setting.
- **Live switching** — change the visual mid-session without interruption.
- **Warm sleep overlay** — blue-light-reducing CSS filter auto-activates for sleep intention sessions.
- **Reduced motion** — `prefers-reduced-motion` disables all animations; manual Off/Gentle/Full override.

### Session Player
- **Five-phase playback** with progress bar, phase dots, elapsed time, and current-sentence text display.
- **Keyboard controls** — Space pauses/resumes (including soundscape audio via AudioContext suspend/resume), Escape emergency-ends.
- **Back to script** — return to the script editor mid-session to edit and restart.
- **Fullscreen mode** with auto-hiding controls.
- **Screen Wake Lock** prevents display timeout during sessions, re-acquires on tab visibility.
- **Live settings panel** — slide-out panel for adjusting visual, audio, and HUD elements mid-session.
- **Script transcript** — toggle a full-text view of the script during playback.
- **Double induction** — the Double Induction method automatically picks a contrasting second voice and speaks both simultaneously.
- **Persona-matched emergency re-alerts** — 25 unique re-alert scripts, one per persona, each in that persona's voice.
- **Grounding exercise** — 5-4-3-2-1 senses exercise auto-displayed after emergency end or low alertness.

### AI Generation
- **Per-phase generation** — each script phase (settling, induction, deepener, work, emergence) is generated by an individual AI call for higher quality. Each call receives a running summary of prior phases so the AI continues seamlessly without repetition.
- **Dynamic phase count** — longer sessions get multiple work phases (medium: 2, long: 3) with affirmation interludes between them.
- **Affirmation weaving** — user-authored affirmations are delivered as poetic interludes between work phases, using the user's exact words in the persona's voice.
- **Live progress indicators** — neon-styled phase dots with five states: dark (pending), pulsing amber (streaming), green (complete), red (failed), yellow (unhandled error). Click any red or yellow indicator to retry just that phase.
- **Adaptive ETA** — live countdown estimate that calibrates from actual phase completion times.
- **Suggestion crafter** — converts rough intentions into technically-precise hypnotic suggestions.
- **20 intention types** with specific AI guidance for each (trigger-response links, pain-dial metaphors, conditioning protocols, amnesia framing, etc.).

### Pipeline

```
OBSERVE → INFER → ADAPT → REINFORCE → EVOLVE
```

### How It Works

| Phase | Function | What It Does |
|---|---|---|
| 1. Signals | `deriveSignals()` | Computes 9 normalized behavioral signals from analytics + history |
| 2. Traits | `updateTraits()` | Lerps 8 hidden personality traits toward signals (rate: 0.15) |
| 3. Reward | `computeReward()` | Scores each session: mood delta + completion − emergency |
| 4. Weights | `updateWeights()` | Reward-weighted preference maps for personas, methods, sounds, lengths (0.98 decay) |
| 5. Memory | `updateMemorySummary()` | AI-generated 1–2 sentence behavioral summary every 5 sessions |
| 6. Difficulty | `computeDifficulty()` | 0–1 ramp (beginner → intermediate → advanced) at 0.1 rate |
| 7. Equilibrium | `checkEquilibrium()` | Detects overload → triggers recovery mode (simplify, ground, reduce intensity) |
| 8. Prediction | `getRecommendation()` | Returns top-weighted session configuration |
| 9. Integration | `getAdaptivePromptBlock()` | Translates traits into plain-English AI directives injected into generation |

### Hidden Personality Traits

| Trait | Measures |
|---|---|
| Compliance | Does the user finish sessions? |
| Sensitivity | Does mood respond to sessions? |
| Stability | Is improvement consistent? |
| Novelty-seeking | Does user explore or repeat? |
| Depth tolerance | Handles long/deep sessions? |
| Control preference | Authoritative vs gentle? |
| Sensory audio | Uses soundscapes? |
| Sensory visual | Uses visual effects? |

### Storage

Single IDB key (`stillness_adaptive_v1`), ~400 bytes, fixed-size. Included in backup export/import.

---

## Analytics & Stats

### Data Collection

O(1) aggregated store (`stillness_analytics_v1`, ~500 bytes). Frequency maps for personas, methods, intentions, soundscapes, visuals, lengths. 24-bucket hourly + 7-bucket weekly time patterns. Running mood sums, completion counts, duration totals, settings averages, 8-bit feature discovery bitmask.

### Stats Charts Modal

10 Canvas 2D charts in a responsive auto-fill grid. Click any tile to expand full-width.

- **Guides / Methods / Intentions / Soundscapes** — ranked bar charts
- **By Hour** — area + line chart with peak annotation
- **By Day** — bar chart (Sun–Sat)
- **Mood Shift** — pre vs post comparison bars
- **Outcomes** — donut chart (finished / emergency / incomplete)
- **Audio Profile** — horizontal bars (rate, pitch, volume, drone)
- **Features Tried** — checklist grid from bitmask

### Sidebar Stats

Compact KPI display: sessions, minutes, streak (compassionate, allows 2 one-day gaps), completion rate. Plus analytics insights after 2+ sessions (avg improvement, peak time, favorite guide, favorite sound). Activity heatmap (16-week GitHub-style). Rising-score sparkline (last 20 sessions).


### Clinical Features (Research-Backed)
- **First-run contraindication checklist** — 6 clinical conditions (psychosis, DID, epilepsy, suicidality, under-18 unaccompanied, intoxication) with explicit attestation. Re-displays monthly.
- **0-10 state scale** — pre-session and post-session wellbeing measurement matching clinical VAS/NRS scales.
- **Howard Alertness Scale** — post-session 0-10 alertness check. Auto-triggers the grounding exercise if alertness falls below 5.
- **Rising-score sparkline** — Canvas chart showing pre vs post improvement across the last 20 scored sessions. Users see their own therapeutic progress.
- **Post-session journal** — reflection textarea saved to session history for pattern tracking.
- **Session daily cap** — maximum 3 sessions per day with kind messaging to prevent compulsive use.
- **Crisis resources** — always-visible footer link with direct numbers: 988 (US), Samaritans (UK/IE), Lifeline (AU), Talk Suicide (CA), findahelpline.com.
- **Practice-unlock gating** — rapid methods unlock at 3 completed sessions, advanced at 7. Locked tabs show a tooltip with current progress.

### Structured Programs
- **5 multi-day programs** with IDB-stored day progression, prior-anchor tracking, and AI context injection:
  - 🌙 7-Day Sleep — body scan → staircase → safe place → anchor → dream rehearsal → integration
  - 🍃 14-Day Calm — breath → worry containment → trigger desensitization → resilience → future pacing
  - 🦁 10-Day Confidence — inner critic → posture anchor → voice of authority → identity integration
  - 💊 6-Week Pain — structured pain management following the clinical gut-directed model
  - 🎯 7-Day Focus — attention narrowing → flow state → sustained immersion → autonomous flow

### Quick-Start Presets
- **12 clinical-vertical presets** — Sleep, Quick Calm, Deep Focus, Demo Night, Pain Relief, Micro Reset, Anxiety Relief, Confidence, Peak Flow, Habit Change, Creative Flow, Energy Boost. One click sets guide, method, intention, soundscape, and length.

### Data & Tracking
- **IndexedDB storage** with automatic localStorage migration. `navigator.storage.persist()` prevents browser clearing.
- **Session history** — last 50 sessions tracked with date, guide, method, duration, completion status, pre/post state scores, and journal entries.
- **Compassionate streak** — consecutive-day tracking with up to 2 auto-freeze days per streak (missing a single day doesn't break the streak, per habit-formation research).
- **Activity heatmap** — GitHub-style 16-week calendar visualisation.
- **Script library** — save, name, load, and delete generated scripts.
- **Full backup/restore** — export all personas, scripts, history, and active program state as a single JSON file. Import merges without overwriting.
- **Settings persistence** — all Configure tab settings (audio levels, voice selection, visual effect, viz tuning sliders, HUD toggles, ducking preference, soundscape) auto-save to localStorage with debounced batch writes. Slider saves fire only on release, text inputs debounce at 1500ms.

## Data Persistence

### Dual-Write Settings

Primary: `root.kv` (Perchance cloud). Fallback: `localStorage`. 1500ms debounce for text inputs, immediate for sliders/checkboxes.

### Backup System

`.gz` export/import with gzip compression and JSON fallback. Includes: custom personas, session history, program state, user profile, analytics store, adaptive intelligence profile.

### Session History

Last 50 sessions stored with full reproducibility: complete script text, all settings, mood scores, journal entries. Play/Edit/Delete buttons on each history card.

---

## User Profile

7-field bio in sidebar: Display Name, Pronouns, Age Range, Experience Level, About, Appearance, Goals. Injected into AI generation prompts as `SUBJECT PROFILE:` context block. Persisted via KV + localStorage.

---


### Sharing & Export
- **Script export** — download any generated script as a `.txt` file with metadata header.
- **Config sharing** — compress session config to a URL fragment via `CompressionStream('gzip')`, share via Web Share API or clipboard.
- **Ambience recording** — download procedural soundscapes as `.webm` audio.

### Accessibility
- `aria-live` region announcing step changes.
- Focus management moving to step headings on navigation.
- `@media (prefers-reduced-motion)` with real alternatives (not just `animation: none`).
- Keyboard-first session controls (Space pause, Escape end).
- Content warnings before advanced/authoritarian sessions.
- Grounding exercise routing after emergency end or low alertness.
- Voice quality badges in the dropdown.
- Category colours paired with labels (never colour alone).
- Vibration haptics on Android for breathing phases and session markers.
- iOS Safari viewport fix.

### Assessment
- **Hypnotic Induction Profile quiz** — 3-question self-assessment inspired by the Spiegel Eye-Roll Sign and absorption scales. Maps to three suggestibility tiers with specific method and guide recommendations.

---

## Content Inventory

### 25 Guide Personas

| Category | Personas |
|---|---|
| **Contemplative** | The Driver, The Old Master, The Therapist, The Inner Voice, The Scientist, The Mystic, The Librarian, The Astronomer |
| **Showman** | The Showman, The Mentalist, The Bartender, The Carnival Barker, The Magician, The Late Night DJ |
| **Somatic** | The Bodyworker, The Yoga Teacher, The Dancer, The Martial Artist, The Midwife |
| **Authoritarian** | The Commander, The Headmistress, The Interrogator, The Drill Instructor, The Dominatrix, The Surgeon |

### 37 Induction Methods

| Category | Methods |
|---|---|
| **Therapeutic** | Highway, Spiral Fixation, Betty Erickson 3-2-1, Staircase Descent, Hand Heaviness, Confusion Method, Fractionation, Eye-Roll (Spiegel), 4-7-8 Breath, Progressive Relaxation, Ericksonian Conversational |
| **Somatic** | Body Awareness Scan, Floating Body, Glove Anesthesia, Heartbeat Synchronisation, Automatic Writing, Pain Dial |
| **Demonstration** | Magnetic Hands, Arm Catalepsy, Chevreul's Pendulum, Tipsy Without Drinking, Laughter Trigger, Number Amnesia, Hot Hand / Cold Hand, Stuck to Your Seat |
| **Rapid** | Handshake Interrupt, Arm Drop, Magnetic Gaze, Dave Elman Induction, Shock Induction |
| **Advanced** | Time Distortion, Age Regression, Positive Hallucination, Negative Hallucination, Eyes-Open Somnambulism, Double Induction, Full-Body Anesthesia |

### 19 Soundscapes

| Category | Soundscapes |
|---|---|
| **Natural** | Rain, Ocean Waves, Crackling Fire, Forest, Stream, Wind, Distant Thunder |
| **Tonal** | Engine Drone, Singing Bowls, Heartbeat, Binaural Beats (θ 6Hz), Wind Chimes |
| **Noise** | Pink Noise, Brown Noise, White Noise |
| **Ambient** | Cave, Night Crickets, Temple, Spaceship |

### 20 Intention Types

**Foundation:** Emotional state shift · Post-hypnotic trigger · Behaviour change · Release / let go · Perception shift · Install an anchor · Just experience trance

**Performance:** Peak performance / flow · Deep focus / concentration · Creative flow / unblock

**Body:** Pain management / comfort · Sleep induction · Energy / vitality boost

**Demonstration:** Convincer demonstration · Novelty effect / party trick

**Advanced:** Time distortion · Suggested amnesia · Persona / identity play · Surrender / ego dissolution · Behavioural conditioning

---

## Technical Stack

- **Platform:** [Perchance.org](https://perchance.org) HTML panel — single-file, no build step, 5,280 lines.
- **AI:** Perchance `ai-text-plugin` for suggestion crafting and per-phase script generation with running context summaries.
- **Audio:** Web Audio API — `OscillatorNode`, `AudioBufferSourceNode`, `BiquadFilterNode`, `ChannelMergerNode`, `DynamicsCompressorNode`, `MediaRecorder`. `AudioContext.suspend()/resume()` for true pause.
- **Visuals:** Canvas 2D with `requestAnimationFrame`, `ResizeObserver`, `OffscreenCanvas` for plasma, object pools for particles. User-tuneable speed/intensity/complexity/trail multipliers.
- **Storage:** IndexedDB via a lightweight async key-value wrapper. `navigator.storage.persist()`. localStorage for settings with debounced batch writes (1500ms for text, `change` event for sliders).
- **TTS:** Web Speech API `SpeechSynthesis` with Chrome 15-second watchdog, sentence-level chunking, and `onboundary` word highlighting.
- **Platform APIs:** Screen Wake Lock, Media Session API, Vibration API (Android), Web Share, Clipboard, CompressionStream/DecompressionStream, Fullscreen, Page Visibility.
- **Design:** Cinzel + Nunito typography. Tavern-dark wood backgrounds with neon cyan/amber/magenta/purple LED accents. SVG fractal-noise wood grain texture. Multi-layer glow effects via CSS box-shadow.

---

## Browser Support

| Browser | Status | Notes |
|---|---|---|
| Chrome/Edge 90+ | ✅ Full | Best voice quality (Microsoft Neural voices on Edge). 15-second TTS bug mitigated by watchdog. Media Session for lock-screen controls. |
| Safari 16.4+ | ✅ Full | Wake Lock, reduced-motion, fullscreen all supported. iOS may hide premium voices. |
| Firefox 124+ | ⚠️ Partial | `onboundary` word highlighting may not fire. Wake Lock supported. Needs `speech-dispatcher` on Linux. |
| Mobile Chrome/Safari | ✅ Full | Particle counts auto-reduced. Wake Lock re-acquires on tab visibility. Vibration haptics on Android. |

---

## Installation

This is a Perchance generator — no installation required.

1. Visit the generator page at [Perchance.org/advanced-hypnosis-narration-engine](https://perchance.org/advanced-hypnosis-narration-engine)
2. The tool runs entirely in your browser
3. All data is stored locally in IndexedDB
4. Settings persist automatically between visits

---

## Privacy

- **Zero network requests** during sessions. All audio and visuals are synthesised locally.
- **No analytics, no tracking, no telemetry.**
- **AI calls** go through Perchance's `ai-text-plugin` — the same infrastructure as all Perchance generators.
- **All data** (personas, scripts, session history, state scores, program progress, settings) stays in your browser's IndexedDB and localStorage. Nothing is transmitted.
- **Backup files** are plain JSON on your local filesystem.
- **Shared config URLs** contain only the session configuration (persona ID, method ID, length, soundscape, intention text) — no personal data.

---

## Safety

- **First-run contraindication checklist** — 6 clinical conditions screened with explicit attestation. Re-checks monthly.
- **Session daily cap** — maximum 3 per day with kind messaging to prevent compulsive use.
- **Practice-unlock gating** — rapid methods at 3 sessions, advanced at 7.
- **Content warnings** shown before advanced/authoritarian sessions with confirmation required.
- **Emergency end** always available (button + Escape key) with persona-matched re-alert scripts.
- **Howard Alertness Scale** — post-session alertness check with auto-grounding below 5.
- **Grounding exercise** (5-4-3-2-1 senses) automatically displayed after emergency end or low alertness.
- **30-second cooldown** after emergency end before a new session can start.
- **Crisis resources** — always-visible footer link with international helpline numbers.
- **Reduced motion** support via CSS media query and manual override.
- **Flicker cap** — all visual effects stay below 2Hz oscillation per WCAG 2.3.1.
- **Sleep intention** suppresses the emergence phase — no unexpected re-alerting.
- **Warm overlay** — blue-light-reducing filter for sleep sessions.
- **AI disclosure** — "Content is generated by AI and is not reviewed by a human therapist" on the contraindication screen.

---

## License

MIT — see [LICENSE](LICENSE).

---

## Credits

**Created by** [therealwestninja](https://github.com/therealwestninja) · [DeviantArt](https://www.deviantart.com/west-ninja)

**Soundscape engine and visual renderers** adapted from [Adaptive Session Studio](https://github.com/therealwestninja) (MIT).

**Perchance platform** by [perchance.org](https://perchance.org).

**Design:** Wooden forest fantasy RPG tavern aesthetic with neon LED accents.
