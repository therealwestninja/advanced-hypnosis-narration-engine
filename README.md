# · Advanced Hypnosis Narration Engine ·

**A free, AI-driven, fully browser-native hypnosis experience generator.**

Generate personalized induction scripts with AI, hear them narrated by the browser's text-to-speech engine, and experience guided sessions with procedural soundscapes, hypnotic visual effects, and real-time customization — all running locally in your browser.

Live here:
[https://perchance.org/advanced-hypnosis-narration-engine](https://perchance.org/advanced-hypnosis-narration-engine)
No account required. No downloads.

---

## What's New

* **Phase-locked entrainment** — binaural beats and isochronic tones now ramp their frequency per session phase across the α/θ/δ brain-wave map (settling alpha, induction theta, deepener theta-delta, work theta, wake alpha, reintroduction beta), with smooth 6-second crossfades at each phase boundary
* **40 Hz gamma flicker visualizer** — alpha-grade entrainment surface with conservative implementation (5–15% alpha modulation, narrow centered pulse, blue palette, voice-coupled) and OS-aware reduced-motion fallback
* **Drag-and-drop phase reordering** — grab the ≡ handle on any phase row to drag it anywhere, with live drop indicators
* **Per-phase duration estimate + timeline view** — every phase shows its estimated duration inline; a proportional timeline above the list visualizes the full session shape, click any block to jump to that phase
* **2D Director calibration pad** — combined intensity × pace control on a drag-snap grid alongside the existing sliders
* **A/B experiment mode** — pick two presets, run a blinded session with one of them randomly chosen, rate it 1–5 after the session, see per-preset rolling averages
* **Conversational free-text check-in** — type how you feel ("tired but mind is racing") instead of moving sliders; lexicon-based parser maps to mood / tension / energy values
* **Phase audition** — 🔊 button on every phase row plays it aloud using current voice settings before you commit to a full session
* **Annual review screen** — opens after 30+ days of practice; sessions, minutes, completion %, longest streak, mood arc, top guides / methods / contexts. Pure local aggregation, no AI
* **API key call counter** — visible per-session count in Options for engaged users who bring their own Anthropic/OpenAI key, plus a one-click "clear & revert to Perchance" button
* **Persona portrait grid hydration** — generated portraits appear as soft thumbnails on every persona card
* **Audio/viz safety relaxation gate** — set your profile age range and the overcautious gates step back: gamma flicker confirmation modal skips, prefers-reduced-motion auto-degrade skips, speech rate caps widen, soundscape volume caps lift, soundscape labels soften. Casual users keep all original safeguards
* **Shareable links** — post a persona or a full session config as a real URL, with tailored link previews in Discord / Slack / iMessage
* **Streaming script generation** — watch each phase appear live as the AI writes it, instead of staring at a spinner
* **Semantic memory** — the AI recalls past sessions that are *relevant* to your current intention, not just the most recent ones
* **Regeneration diffs** — retry a single phase and pick between the original and the new version side-by-side
* **Community persona packs** — third-party persona collections load on demand without bloating the app
* **Token-aware prompt assembly** — long profiles, memory, and affirmations never silently exceed the context window
* **Multi-provider AI** — use the free built-in Perchance model, or bring your own Anthropic / OpenAI key

---

## What It Does

### 6-Step Guided Workflow

1. **Choose a Guide**
   25 built-in personas across four temperaments, each with distinct tone and delivery. Create unlimited custom personas. Import personas others have shared.

2. **Choose a Method**
   37 induction techniques across therapeutic, somatic, demonstration, rapid, and advanced categories.

3. **Set an Intention**
   Define what you want to achieve. The AI converts this into structured hypnotic suggestions.

4. **Affirmations**
   Add your own affirmations.
   These are no longer static — the AI:

   * weaves them into sessions
   * structures them across phases
   * adapts delivery style (woven / pulses / light touch)

5. **Configure & Review**

   * session length
   * narrator voice
   * soundscape + visuals
   * edit and rearrange generated script
   * adjust phase structure

6. **Generate & Begin**
   Run a fully narrated session with real-time controls.

---

## Session Model

Sessions are no longer fixed to 5 phases.

They now include:

* settling
* induction
* deepener
* **multiple work blocks (up to 5 for deep sessions)**
* affirmation phases (dynamic)
* **lightener**
* **reintroduction**

This creates a full arc:
**descent → work → recovery → return**

---

## AI Generation

* **Streaming per-phase generation** — each phase renders live as it's written, with an inline preview you can read as it builds
* **Semantic memory retrieval** — the generator embeds your past session digests and pulls in the most relevant ones when writing a new script (not just the most recent)
* **Token-aware prompt assembly** — profile, adaptive context, and memory are prioritized and trimmed as needed so long-term users don't silently blow past the context limit
* **Adaptive intelligence** — learns what works for you (personas, methods, lengths, depth preferences) and shifts recommendations over time
* **3-tier hierarchical memory** — per-session digests, rolling patterns (every 5 sessions), long-term profile (every 15)
* **Per-phase regeneration with diff** — unhappy with one phase? Retry just that one and compare old vs. new side-by-side
* **Multi-provider routing** — default free Perchance AI, or plug in your own Anthropic / OpenAI key (be aware your key lives in the browser)

---

## Script Editing (Step 5)

You can:

* drag-and-drop phases via the ≡ grab handle (or ↑/↓ buttons)
* see a proportional **timeline visualization** above the list — click any block to jump to that phase
* see **estimated duration** (⏱ Xm Ys) on every phase row, plus session total
* **audition** any phase aloud (🔊 button) before committing to a full session
* remove or add phases (induction, deepener, level, work, affirmation, lightener, wake, reintroduction, sounding, custom)
* edit full script text
* regenerate individual phases and compare outputs side-by-side
* author custom blocks, then ✨ Reimagine them in your guide's voice
* control session flow directly

This is a core feature, not just a preview step.

---

## Audio

* Procedural soundscapes (no audio files shipped — everything synthesized)
* phase-locked binaural beats and isochronic tones — entrainment frequency ramps per session phase across the α/θ/δ map
* narration ducking during speech
* voice selection with quality sorting
* live adjustment during session (volume, pitch, rate, tempo)
* mobile lock-screen media controls

---

## Visuals

* multiple animated focus effects (spiral, tunnel, vortex, pendulum, mandala, candle, flow-field, aurora, and more)
* 40 Hz gamma flicker (alpha-grade, conservative implementation, voice-coupled)
* real-time tuning (speed, intensity, complexity)
* phase-reactive pacing
* reduced-motion support
* background image generation (AI, static URL, or YouTube)

---

## Session Player

* dynamic phase playback (not fixed count)
* progress tracking + transcript view
* live settings panel
* emergency exit + grounding system
* fullscreen + wake lock
* optional ambient audio recording

---

## UI / UX

* mobile-first layout (portrait optimized)
* no horizontal overflow
* responsive grid-based UI
* improved readability (contrast + font sizing)
* clear navigation (back buttons, step clarity)
* onboarding tour for new users
* toast notifications (non-blocking, non-interrupting)

---

## Data & Systems

### History

Stores per session:

* full script
* phase structure
* affirmations + mode
* profile snapshot
* session metrics (depth, mood delta, completion state)

### Profiles

User profile is injected into AI generation:

* goals
* preferences
* traits
* appearance (for personalized imagery)

### Adaptive System

Tracks and updates automatically:

* completion rates
* mood-delta variance
* method/persona preferences by reward signal
* novelty-seeking vs. repetition patterns
* depth tolerance
* recovery mode when sessions trend poorly

### Tracking

Expanded analytics:

* session outcomes
* usage patterns
* feature interaction
* structural preferences

---

## Stats & Charts

* usage breakdowns (guides, methods, intentions)
* time-of-day patterns
* mood change tracking
* completion rates
* feature usage maps
* activity heatmap (GitHub-style)
* pre/post improvement sparkline

---

## Backup & Sharing

### Local

* full backup / restore (gzipped JSON)
* script export to .txt
* compatibility with older formats (automatic migration)

### Shareable Links

* **session configs** — share the persona, method, length, soundscape, affirmations, and optionally the generated script as a single URL
* **custom personas** — share a persona you've built; recipients can add it to their own library with one click
* **rich link previews** — shared URLs produce tailored titles and descriptions when pasted in chat apps
* **community persona packs** — opt-in third-party collections load lazily when selected

### Privacy-aware share flow

* recipients see an age-gate prompt before importing personas with potentially sensitive content
* URL is cleaned after import so a reload doesn't re-trigger the flow

---

## Privacy

* runs locally in browser
* no default data collection
* no telemetry

### Optional (Opt-in Only)

Users may enable:

> **Remote backup + processing**

* requires explicit consent
* disabled by default
* clearly disclosed before activation

---

## Safety

* contraindication screening
* session limits + cooldowns
* grounding system
* emergency exit
* alertness check
* crisis resources
* reduced-motion defaults for seizure-risk visuals

---

## Accessibility

* keyboard controls
* reduced motion support
* improved contrast + readability
* larger tap targets
* focus indicators
* ARIA labels on navigation

---

## Technical Stack

* Perchance (single-file app)
* `ai-text-plugin` for streaming generation
* `text-to-image-plugin` for backgrounds
* `upload-plugin` for shareable content
* `dynamic-import-plugin` for community packs
* Web Audio API (procedural synthesis)
* Canvas 2D rendering
* IndexedDB storage (persisted)
* Web Speech API (TTS)
* Wake Lock, Media Session, Vibration, Clipboard APIs

---

## Browser Support

* Chrome / Edge: full support
* Safari: full support
* Firefox: partial (speech-synthesis differences)
* Mobile: fully supported (lock-screen controls on iOS 16+ / Android 10+)

Features that gracefully degrade when unavailable:

* semantic memory falls back to recency-based retrieval
* streaming falls back to full-phase render
* share links fall back to hash-URL encoding if upload service is unreachable
* haptics silently skip on desktop

---

## Installation

No installation required.
Runs entirely in browser.

---

## License

MIT

---

## Credits

Created by therealwestninja
Perchance platform: perchance.org
