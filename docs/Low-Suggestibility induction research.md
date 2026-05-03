# HNE Low-Suggestibility Inventory: A Working Document
*Comprehensive shotgun-style research dossier for the Hypnosis Narration Engine, scoped for users scoring 1–3/10 on Stanford HIP / HGSHS / SHSS:C.*

## TL;DR
- **For a self-rated 1/10 responder, the highest-leverage HNE features are NOT better suggestion scripts; they are (a) a CSTP-style skill-training onboarding flow, (b) physiology-first sensory engineering (paced breathing at ~6 bpm, audio-visual entrainment, vibroacoustic-feeling low-end mixes, ASMR/3D audio, ganzfeld-like visualizers), and (c) explicit expectancy/framing rituals — because the published evidence shows these produce real effects via mechanisms that bypass the trait of hypnotizability rather than depending on it.**
- **Hypnotizability is highly stable (~0.7 test-retest over 25 years) but is NOT immutable: the Carleton Skills Training Program (CSTP) reliably moves ~50% of "lows" into the high range on retest; tDCS and TMS to left DLPFC give ~6–15% transient boosts that disproportionately help low responders; LSD, oxytocin, and nitrous have measurable suggestibility-enhancing effects in RCTs but are out-of-scope for browser software. The "phenomenological control" reframe (Dienes/Lush) suggests that what HNE should actually train is goal-directed alteration of experience, decoupled from hypnosis branding.**
- **Build HNE as a stack: a Tier-1 "anything works in a browser" layer (audio engineering, visualizers, breath pacing, expectancy framing, CSTP-style modeling), a Tier-2 "BYO hardware" layer (Muse/Sens.ai/Mindplace/HRV sensors via WebBluetooth/WebHID/WebUSB), and a Tier-3 "off-platform protocol guidance" layer (float tanks, supplements, brain stimulation devices). Treat each as opt-in modules with explicit evidence labels.**

---

## Key Findings

1. **Trait stability is real but porous.** SHSS:C test-retest ≈ 0.71 over 25 years (Piccione 1989). But targeted interventions move the needle: CSTP (Gorassini & Spanos) converts 50–80% of initially-low subjects to high-scoring on post-test in repeated trials; rTMS/cTBS to left DLPFC (Stanford SHIFT 2024) raised HIP scores ~1 point for ~1 hour; cathodal tDCS over left DLPFC gave ~15% gains, with the largest gains in the lowest-baseline group (Perri et al.).
2. **Low responders benefit *more* than highs from neuromodulation and physiological methods**, because highs are at ceiling. This is a recurring finding across tDCS (Perri 2023), binaural-beat theta studies (Brady & Stevens 2000), and breath/relaxation interventions.
3. **"Phenomenological control" (Dienes/Lush) is the most useful theoretical frame for HNE.** It says response to imaginative suggestion is a metacognitive skill — generating intentional experiences without awareness of the intention — which can be cued by *any* context that primes the goal. This means a script doesn't need a "hypnotic induction" wrapper to work; it needs goal-clarity, expectancy, and practice with phenomenological-control tasks.
4. **Expectancy & framing alone produce hypnosis-like depth.** A balanced-placebo EEG study (2025) found that *labeling* a procedure as "hypnosis" was the dominant determinant of subjective depth, and a "white noise hypnosis" placebo induction matched conventional inductions. This is gold for HNE: ritual, framing, and consistent cues are first-class features, not garnish.
5. **The strongest audio bypass is paced slow-exhalation breathing.** Resonance-frequency breathing at ~5.5–6 bpm (4.5–7 individual range) reliably increases HRV, vagal tone, and parasympathetic dominance — physiological correlates of trance-adjacent states — independent of suggestion. This is trivially implementable in JS.
6. **Audio-Visual Entrainment (AVE) has mixed but non-zero evidence.** A 2025 narrative review (PMC12564294) finds heterogeneous results but real effects on EEG and subjective state. Isochronic tones produce stronger EEG entrainment than binaural beats; binaural beats need headphones; both work better when low/medium hypnotizable subjects are tested (Brady & Stevens). Brain.fm's neural-phase-locking via amplitude modulation has independent EEG/fMRI validation.
7. **Sensory deprivation/REST robustly raises hypnotizability.** Multiple studies (Barabasz, Suedfeld) show chamber REST and dry flotation REST significantly increase SHSS:C scores, with effects persisting at follow-up. Lighted REST > unlighted in a 2014 trial. HNE can simulate a partial-REST condition through ganzfeld visualizers + masking pink/brown noise + headphones.
8. **Hypnagogia is the alternative trance entry point that doesn't require suggestibility.** It's a physiological state everyone enters at sleep onset; Lacaux et al. (2021) found it triples creative-insight rates. The Edison/Dalí "key drop" method is the canonical induction. HNE can target hypnagogic delivery for users who report low trance — they get the experience by physiology, not by suggestion.
9. **Ritual technologies (drumming, chanting, dance, fasting) work via attention capture + autonomic arousal, not suggestion.** EEG studies of shamanic drumming show modest entrainment but trance reports correlate with hypnotizability — meaning rhythm helps everyone get partway, but highs go further.
10. **Pharmacological enhancers exist but are mostly out-of-scope for software:** intranasal oxytocin (24 IU) reliably increases hypnotic compliance in lows (Bryant et al.); LSD (40–80 µg) raises Creative Imagination Scale scores significantly (Carhart-Harris 2015); psilocybin and nitrous oxide also have signal. Modafinil shows mixed results. None are deliverable through a browser, but HNE could include opt-in protocols/disclaimers.

---

## Details — Inventory by Category

### 1. Suggestibility Training Programs (the highest-evidence trainable approach)

**Carleton Skills Training Program (CSTP) — Gorassini & Spanos**
- **What it is:** A multi-component training (originally ~75 min in-person, also exists as videotape, audiotape, and self-administered booklet versions, all roughly equivalent in efficacy per Kirkeby 1991).
- **Components (the actual protocol):**
  1. **Information**: explicit teaching that hypnotic responses are achievable by everyone, that they are *not* a sign of weak will, that imagination + active enactment is the mechanism, and that subjects retain control.
  2. **Attitude/expectancy modification**: directly addresses common myths ("I'm not the type", "I'll lose control") and replaces with positive expectancy.
  3. **Modeling**: subjects watch a videotaped model successfully responding to suggestions, demonstrating *how* to think about and physically enact each item. (This component is significant — removing it reduces gains.)
  4. **Goal-directed fantasy / imaginal strategies**: instructs subjects to imagine concrete scenarios that make the response feel natural (e.g., "imagine a helium balloon tied to your wrist" for arm levitation).
  5. **Active enactment**: subjects are explicitly told to physically *do* the suggested behavior, using imagination to make it feel involuntary, rather than passively waiting. The 1995 Schoenberger study showed a fantasy-only variant (no enactment) works equally well and avoids "compliance" framing.
  6. **Practice + feedback**: subjects practice with sample suggestions and receive corrective coaching.
- **Evidence:** RCT-backed across 15+ studies. ~50–80% of initially low-hypnotizable subjects score high on retest; gains are partially maintained at 4 months. Effects exceed simple "practice the same induction repeatedly" controls. Some replication failures (Bates 1988) suggest demand characteristics inflate scores; the 1996 simulator-control experiments by Spanos show genuine non-compliance gains remain.
- **Why it helps lows specifically:** It's *designed* for them — it directly addresses the cognitive-attitudinal barriers (passivity, disbelief, mystified expectations) that distinguish lows from highs.
- **HNE port:** ⭐ HIGHEST PRIORITY. Build a 2–4 session interactive onboarding: written/animated "what hypnosis really is" explainer; video-modeled demonstrations of each suggestion type (arm heaviness, hand magnets, taste hallucination); GDF strategy library; practice items with self-rated phenomenology; explicit cueing of active enactment. The booklet/audio version is already known to work — porting to browser is a perfect fit.
- **Verdict:** "Would this work for HNE?" Absolutely yes; this is the single most evidence-supported intervention you can fully implement in pure JS.

**Sachs & Anderson program (1967)** — earlier predecessor; comparable efficacy to CSTP per Cangas-Pérez et al. Less documented; CSTP supersedes it.

**Repeated practice / familiarization** — Vickers (1980) and Diamond's reviews show simply repeating inductions modestly increases susceptibility (~0.5–1 point). Less powerful than CSTP but free. **HNE port:** automatic; just usage tracking and progressive scripts.

---

### 2. Cognitive / Imaginative-Absorption Training

**Tellegen Absorption Scale (TAS) and MODTAS**
- **What it is:** 34-item self-report measure; nine content clusters (synesthesia, ASC, aesthetic involvement, imaginative involvement, ESP, etc.). Modified version (Jamieson) is preferred. Correlates 0.3–0.5 with hypnotizability, consistently the strongest single trait predictor.
- **Mechanism:** Absorption = "disposition for situations in which one's total attention fully engages perceptual, enactive, imaginative, and ideational resources" (Tellegen & Atkinson 1974).
- **Trainability:** Less direct evidence than CSTP, but plausibly trainable via:
  - Daily *imagery vividness exercises* (visualize an apple in detail; close eyes and trace a familiar room from memory; recall a favorite piece of music)
  - *Aesthetic immersion practice* (slow art-viewing, slow music-listening)
  - *Synesthesia-priming* (cross-modal pairing exercises: "what color is this sound?")
  - *Flow-state cultivation* — anything that produces deep task engagement
- **HNE port:** ⭐ HIGH PRIORITY. Build an "absorption gym": short daily imaginative-immersion exercises with self-rated vividness scoring. Track MODTAS subscale-aligned progress. Use as warm-up before each hypnosis session.
- **Verdict:** Trainable absorption is plausible and cheap; absorption gym pairs naturally with CSTP onboarding.

**Phenomenological Control framework (Dienes, Lush)**
- **What it is:** A reframing — what is measured by hypnotizability scales is the metacognitive skill of producing intentional experiences without awareness of the intention. The Phenomenological Control Scale (PCS) measures this without "hypnosis" framing.
- **Implication for HNE:** You can drop the "hypnosis" framing entirely if the user resists it, and instead train phenomenological control directly via tasks like the rubber-hand illusion, mirror-touch synesthesia priming, and imagined-perception exercises. Dienes' position: "let's stop hypnotising and start instructing people to use their capacity for phenomenological control."
- **HNE port:** Build a "Phenomenological Control" mode label as an alternative to "Hypnosis" mode for skeptical users; same underlying scripts, different framing. Include rubber-hand-illusion-style cross-modal exercises as training items.

---

### 3. Brain Stimulation Approaches (real signal, mostly not portable)

**rTMS / cTBS to left DLPFC — Stanford SHIFT (Faerman et al., Nature Mental Health 2024)**
- 92 seconds of continuous theta-burst stimulation (two 46-second bursts, 800 pulses) over individually-fMRI-targeted left DLPFC.
- Increased HIP by ~1 point for ~1 hour in 80 fibromyalgia patients (initially low-medium hypnotizable).
- Mechanism: strengthens functional connectivity between left DLPFC and dorsal anterior cingulate cortex (dACC) — the trait neural signature of high hypnotizability per Hoeft et al. 2012.
- **HNE port:** None directly. Worth flagging as "if your clinic offers TMS, schedule HNE sessions in the post-stim hour."

**tDCS over left DLPFC (cathodal/inhibitory) — Perri et al. 2023**
- 1.5–2 mA over left DLPFC for 15–20 min produced ~15% increase in PCI hypnoidal-state scores.
- **Lower-baseline subjects benefited most** (the most relevant finding for HNE's audience).
- Devices like Halo Sport, Foc.us, Soterix at-home tDCS exist but are off-label and risky.
- **HNE port:** Document in protocol guide as "experimental adjunct"; include 30-min waiting-window timer feature for users who do tDCS before sessions.

**Transcranial focused ultrasound (tFUS), TUS** — early research; can target deeper structures (thalamus, ACC) than TMS/tDCS. No published hypnosis trials yet. Speculative.

**Photobiomodulation (tPBM)** — 1064 nm to right PFC improved working memory and visual attention (Wang 2022, Science Advances). Sens.ai integrates near-infrared LEDs in headset. Mechanism: cytochrome c oxidase upregulation, increased ATP, cerebral blood flow. Indirectly relevant to cognitive substrates of hypnosis. **HNE port:** Hardware-dependent; mention as adjunct.

**PEMF / Schumann resonance entrainment (7.83 Hz)** — Devices like EarthPulse, BioMat. Evidence is mostly for sleep and pain; brain entrainment claims are weakly supported (correlational HRV studies from HeartMath). **Speculative-to-pseudoscience tier;** include for completeness with appropriate evidence labels.

**Scalar fields / "energy" devices** — No mainstream evidence. Pseudoscience tier; out-of-scope but include in inventory per user request as opt-out-by-default category.

---

### 4. Pharmacological / Nutraceutical Adjuncts (out-of-scope to deliver, in-scope to inform)

| Agent | Evidence | Effect | HNE relevance |
|---|---|---|---|
| **Intranasal oxytocin (24 IU, 4 puffs/nostril)** | RCT, Bryant et al. 2012/2013 | Increased hypnotic responding in low subjects via trust/rapport pathway | Document protocol in guide; mention parasocial narrator design as a software analog |
| **LSD (40–80 µg IV)** | RCT, Carhart-Harris 2015 | Significantly raises Creative Imagination Scale; trait conscientiousness predicts response | Out-of-scope; flag in psychedelic-music section |
| **Psilocybin** | Multiple RCTs for depression; Hartogsohn review on suggestibility | Increases suggestibility, ego dissolution, music absorption | Out-of-scope; informs music-design choices (Kaelen) |
| **MDMA** | MAPS PTSD trials | Increases trust, openness, reduces fear | Out-of-scope |
| **Nitrous oxide** | Whalley & Brooks 2009 | Modest suggestibility increase | Out-of-scope; some dental clinics combine N2O + hypnosis |
| **Ketamine (sub-anesthetic)** | Anecdotal; theoretical via NMDA-driven dissociation | Dissociative state, possibly trance-adjacent | Out-of-scope |
| **Cannabis (low-dose THC, CBD)** | Anecdotal; mixed | Variable; can increase absorption or anxiety | Out-of-scope; user-dependent |
| **Kava** | OTC; reduces anxiety via GABA-A | May lower defenses; reduces inhibition | Mention as legal pre-session anxiolytic |
| **Kratom** | Variable legality; opioid-like | Sedation in some contexts | Don't recommend; safety concerns |
| **L-theanine + caffeine** | OTC; raises alpha EEG | Calm focus | Reasonable pre-session pairing |
| **Magnesium glycinate, glycine, apigenin** | OTC sleep aids | Parasympathetic shift | Reasonable for evening sessions |
| **Modafinil** | Mixed (Aldwinckle 2014) | Possibly increases suggestibility via attentional gain | Off-label; out-of-scope |
| **Diazepam** | One small study; ambiguous | Probably reduces voluntary control more than enhances response | Not recommended |

---

### 5. Audio-Engineering Techniques (the densest HNE-portable category)

**Binaural beats**
- Two carrier tones (200–500 Hz typical), e.g., 200 Hz left + 204 Hz right → perceived 4 Hz beat → frontal theta entrainment.
- For hypnosis induction: theta range (4–7 Hz, often 6 Hz on 250 Hz carrier per Karino 2006) and alpha (8–12 Hz, often 10 Hz).
- Brady & Stevens 2000: 3 sessions × 20 min of binaural-beat theta stimulation increased SHSS:C in low and medium subjects, no change in highs.
- Requires headphones; weaker than isochronic on EEG measures; some null replications exist.
- **HNE port:** Easy with Web Audio API (two oscillators, panned hard L/R). Default 6 Hz on 200 Hz carrier for trance induction; offer alpha for relaxation, delta for deep work.

**Isochronic tones**
- Single tone amplitude-modulated at target frequency. Works without headphones. Manns 1981 showed stronger entrainment than binaural beats.
- Subjectively more aggressive; better for energetic states than deep trance.
- **HNE port:** Trivial in Web Audio (gain node + LFO).

**Monaural beats**
- Two tones mixed *before* delivery, played in both ears. Stronger than binaural; works without headphones. Less researched.
- **HNE port:** Trivial.

**Brain.fm-style neural phase locking**
- Amplitude modulation of *musical* content (not pure tones) at target frequencies, often combined with spectral shaping.
- Independent EEG/fMRI evidence of stronger phase-locking in frontal regions vs. control music; activates executive, default-mode, and salience networks.
- **HNE port:** Implementable but requires generating or modulating music programmatically. Tone.js + a granular sampler over Creative-Commons ambient stems can approximate this.

**Pink noise / brown noise / white noise**
- Pink noise reduces sleep latency and increases slow-wave activity (multiple studies); brown noise (1/f²) is the deepest masker.
- **HNE port:** Trivial; offer per-session selection. Phase-time pink-noise pulses synchronized to slow-wave EEG (Muse S Athena does this) is hardware-dependent.

**ASMR triggers and binaural recording**
- Tingles + relaxation in ~50% of population; non-responders still report relaxation. Cyclic acoustic patterns predict ASMR response (Fang et al.).
- Production tricks: close-mic'd whispered voice (Neumann KU100 or 3Dio Free Space-style binaural mic), tactile sounds (paper, brush, tapping), slow gentle hand movements, personal-attention roleplay, spatial L/R alternation.
- **HNE port:** ⭐ HIGH PRIORITY. Record narrator with binaural intent; produce parallel "ASMR mix" of every script. Layer subtle ambient triggers (rain, fire crackle, fabric, breath) panned 3D.

**3D audio / ambisonics / HRTF spatialization**
- Web Audio's PannerNode and Resonance Audio (Google) library support full HRTF spatialization in browser.
- Bath University study: imaginative suggestibility predicts VR "presence"; spatial audio likely operates similarly — bypassing the imagination requirement by *providing* the spatial scene.
- **HNE port:** ⭐ HIGH PRIORITY. Spatialize narrator voice in moving trajectory around the listener; place ambient elements at distinct 3D positions; use Doppler shifts for moving elements (helicopter, breath, ocean waves).

**Hemispheric panning / Hemi-Sync (Monroe Institute)**
- Patented multiplexed binaural-beat + music + pink-sound mixes for "hemispheric synchronization." Evidence is largely Monroe-internal; mainstream EEG literature treats binaural-beat hemisphere claims skeptically. Still, listener reports of altered states are robust (likely via expectancy + masking + binaural). CIA's Project Stargate evaluated it for remote viewing.
- **HNE port:** Reproduce the *stack* (binaural carrier + masked pink noise + ambient music + spoken guidance) as a preset. Avoid using "Hemi-Sync" trademark.

**Suggestopedia / Lozanov music protocol**
- Uses Baroque largo movements (~60 BPM, e.g., Albinoni Adagio, Pachelbel Canon, Bach Air on G String) for "passive concert" review phase. Claim: heart rate entrains to 60 BPM, induces relaxed-alert state, accelerates memory.
- Empirical replication mixed; mainstream view treats specific 60-BPM claim as overstated, but slow-tempo classical does reduce arousal.
- **HNE port:** Offer 60-BPM ambient playlist mode. Use as a "review phase" after suggestions to consolidate.

**Mendel Kaelen / Imperial College psychedelic playlists**
- Designed for psilocybin therapy: ambient + neoclassical, with arc-shaped intensity curve (calm → peak → resolution). Wavepaths is the adaptive successor.
- Kaelen's research (PhD): music quality predicted depression-treatment outcome *more* than drug intensity.
- Key finding: *resonance* (music matches user's internal state) matters more than universal "good" music.
- **HNE port:** ⭐ MEDIUM PRIORITY. Implement an arc-shaped intensity envelope across each session; allow user to flag tracks as "carrying me" vs "feels manipulative" and adapt. Integrate Spotify/SoundCloud playlist embedding for licensed Kaelen content; ship CC-licensed alternatives by default.

**Vibroacoustic therapy (VAT) — Skille/Lehikoinen**
- Low-frequency sine waves 30–120 Hz delivered through transducers in chair/bed. 40 Hz most-studied for pain. Increases HRV, parasympathetic activity (RCT in Czech students).
- **HNE port:** Mix in a sub-bass 40 Hz sine layer underneath the soundscape — most consumer subwoofers will reproduce it tactilely if the user has one. Offer "haptic mode" via WebHID rumble for game controllers as a tactile substitute. Recommend tactile transducer (Buttkicker, Subpac) as BYO hardware.

---

### 6. Visual-Engineering Techniques

**Audio-Visual Entrainment (AVE) / Mind Machines**
- Stroboscopic glasses + entrainment audio. **MindPlace Procyon** (color LEDs, ganzfeld goggles, 50 preset programs, SpectraStrobe music encoding), **MindPlace Kasina**, **Roxiva rX1**, **Laxman**, **Lucia N°03** (the high-end stroboscopic light, ~$10K, eyes-closed, hypnagogic light experience marketed by Winkler/Proeckl).
- Evidence: A 2025 narrative review (PMC12564294) finds heterogeneous evidence — real EEG photic-driving effects, mixed clinical results. Lucia N°03 has small studies (Sussex University in progress, Munich applied sciences) suggesting psilocybin-comparable openness shifts; not independently replicated.
- **HNE port:** ⭐ Implement a screen-based flicker visualizer as a Lucia/Procyon analog. CSS/Canvas/WebGL flicker at user-chosen frequency (delta 2 Hz, theta 6 Hz, alpha 10 Hz, gamma 40 Hz). **CRITICAL: photosensitive-epilepsy warning + frequency lockouts in the seizure-risk band (15–25 Hz). Eyes-closed mode through eyelids attenuates risk; keep brightness modest.** Add on-screen mandala/kaleidoscope generator that pulses at the entrainment frequency.

**Ganzfeld**
- Homogenized visual field (halved ping-pong balls + red light originally; modern: VR with uniform red field). Induces hypnagogic-like ASC reliably; Schmidt & Prein 2019 documented decreased thalamocortical coupling.
- Highs report stronger ASC under ganzfeld than lows (Cardeña 2020) — but lows still get *some* effect, which is the relevant finding.
- **HNE port:** Full-screen uniform red/orange field with subtle gradient noise, plus matched pink-noise audio. Procyon's "Ganframes" do this physically; software version is fullscreen + brightness. ⭐ HIGH PRIORITY.

**Dreamachine / Brion Gysin stroboscope**
- Rotating cylinder with cutouts at ~7–13 Hz alpha range, eyes closed, induces patterns and visions. Modern implementation: any controlled flicker source.
- **HNE port:** Software dreamachine — full-screen flicker at adjustable Hz with optional color cycling. Combine with spoken narration. Shares photosensitivity caveats with AVE.

**Pulfrich effect**
- Depth illusion when one eye sees darker filter; brain's slower processing creates 3D from 2D motion.
- **HNE port:** Niche; offer optional "pulfrich glasses" mode (one-lens-tinted glasses are cheap) with side-scrolling visualizer. Speculative for trance use; novel and immersive.

**Optokinetic / motion induction / vection**
- Large-field moving patterns produce self-motion illusion; well-known to reduce frontal-executive activation transiently.
- **HNE port:** Endless tunnel/starfield/cloud-flythrough WebGL visualizer; combine with descending count.

**Biofeedback-driven visuals**
- Visualization parameters driven by user's HRV, breath, or EEG. Muse SDK, Sens.ai, polar HR straps via Web Bluetooth, pulse-oximeter via WebUSB, breath via microphone amplitude analysis.
- **HNE port:** Mic-based breath detection is free and works on any device — modulate the visualizer "breathing" with the user's actual breath. Use Web Bluetooth for HRV-coherence rings (à la HeartMath) when available.

---

### 7. Bodywork / Somatic Adjuncts

**Resonance-frequency / paced breathing**
- 5–6 bpm with extended exhale (inhale 4s, exhale 6s; or 4-7-8); HRV biofeedback meta-analyses show robust effects on anxiety, mood, vagal tone. Each person has individual RF (4.5–7 bpm).
- **HNE port:** ⭐⭐ ESSENTIAL. Visual breath pacer (expanding circle, ascending/descending tone, or breathing soundscape sync). Default 5.5 bpm; user-selectable. Optional RF-finder protocol that walks through 4.5/5/5.5/6/6.5 bpm with self-report.

**Cold-face / mammalian dive reflex**
- Splash cold water on face or apply cold pack to forehead/eyes for 30s; triggers vagal bradycardia.
- **HNE port:** Pre-session protocol prompt; not deliverable in software but worth recommending.

**Wim Hof breathing**
- 30 cycles of hyperventilation + retention; produces alkalosis, transient altered state, often emotional release.
- **HNE port:** Implementable as a guided protocol but requires safety warnings (no driving, no water, never standing). Some evidence it serves as a distinct on-ramp to altered states for low-suggestibility users.

**Hum / chant / vocal toning (om, vagal vocal)**
- Vibrates vagus nerve through laryngeal/pharyngeal route; modest HRV effects.
- **HNE port:** Optional vocal-along feature; mic-detect user's hum and reward via visualizer.

**Weighted blanket / deep pressure**
- Reduces autonomic arousal; pairs well with seated/supine sessions.
- **HNE port:** External recommendation only.

**Polyvagal-informed safety cueing**
- Stephen Porges: prosodic warm voice, slow eye-contact pace, predictable rhythm cue ventral vagal "safety" state. Deb Dana's protocols.
- **HNE port:** ⭐ Narrator voice direction guide: warm prosody, slow tempo, downward cadence at sentence ends, predictable rhythm. Make this an explicit narrator-design principle.

---

### 8. Pre-induction Preparation & Expectancy Management

**Kirsch's three expectancy targets** (Kirsch 1985, "Response Expectancy"):
1. Belief that the *setting* is appropriate for hypnosis.
2. Belief that *responses* are appropriate to the patient role.
3. Belief that *one is hypnotizable*.

**Practical interventions:**
- Display prior session "depth ratings" trending upward (real or framing).
- "Bogus pipeline" — show physiological readings (real HRV, breath rate) and label them as "depth indicators." Honest about what you're measuring; honest framing of meaning.
- Pre-session questionnaire that *itself* acts as priming ("rate your openness today, rate your imagination today").
- Ritual cues: same opening sound, same lighting prompt ("dim your lights"), same breath count.
- Consistent narrator persona = parasocial trust building.
- Honest framing that doesn't oversell: "this works by *training* your brain to enter focused-imagination states; depth grows over sessions."

**The 2025 balanced-placebo EEG study** is the killer datum: labeling determines subjective depth. ⭐ HNE should treat the framing/onboarding screen as a *first-class clinical intervention*, not as marketing copy.

---

### 9. Hypnagogic / Hypnopompic Entry Points

**Why this matters for lows:** Hypnagogia is a physiological transition state that everyone reliably enters at sleep onset, regardless of suggestibility. Lacaux et al. (Sci Adv 2021) showed it triples creative-insight rates in problem-solving. Phenomenologically it overlaps heavily with "deep trance": loss of voluntary control, vivid imagery, fluid logic.

**Induction methods:**
- **Edison/Dalí "key drop"**: hold a heavy object so you wake when it falls, capturing the borderland state.
- **WILD (Wake-Induced Lucid Dreaming)**: lie still, let body fall asleep while attention stays.
- **WBTB (Wake-Back-To-Bed)**: wake at 5 hrs sleep, stay up briefly, return — high hypnagogia density.
- **Lucia N°03-style flicker** with closed eyes induces hypnagogic light experiences.
- **Audio "anchor"** (a soft repeated prompt every 3–5 min) keeps you on the edge.

**HNE port:** ⭐ "Hypnagogic mode" — a session designed to be done lying down at bedtime or during a deliberate nap. Audio gradually softens/lengthens; periodic gentle voice anchors with reflective prompts ("what just appeared?"); record session for hypnopompic review. Phone-tilt or held-finger motion sensor as software "key drop." Pair with "dream incubation" prompt ("what question do you want your mind to explore?").

---

### 10. Sensory Deprivation / REST

**Float tanks (Lilly/Suedfeld/Barabasz)** robustly increase SHSS:C scores; chamber REST stronger than flotation in some studies (Kaplan & Barabasz 1990, but Barabasz 2014 with dry-flotation lighted REST was strongest).

**HNE port:** Software cannot replicate true REST, but can simulate:
- Eye mask + headphones + dark quiet room as user-side ritual.
- Software ganzfeld (uniform red visualizer or "eyes closed" guidance) + masked pink noise to simulate auditory homogenization.
- Recommend BYO float-tank session with HNE audio piped in (waterproof bone-conduction speakers exist).

---

### 11. VR / AR-based Hypnosis

- VR-hypnosis (Patterson et al.; Terzulli 2023) shows pain reduction and altered autonomics, particularly in *low* hypnotizable subjects who lack imaginative ability — VR provides the imagery for them.
- Bath University: imaginative suggestibility predicts "presence" in VR; therefore VR-hypnosis may benefit those with low TAS by providing the absorption substrate exogenously.
- **HNE port:** ⭐ HIGH PRIORITY. WebXR support — render scenes (forest, beach, infinite hallway, cathedral) in VR for users with Quest/Vision Pro. Same scripts; spatial audio + visual replaces user's failed imagination. Even mobile cardboard VR or fullscreen smartphone "VR" provides 50% of the benefit.

---

### 12. Neurofeedback / Biofeedback Hardware Integration

**Consumer EEG headbands accessible via Web Bluetooth/WebHID:**
- **Muse 2 / Muse S Athena** — 4-7 EEG channels, PPG, fNIRS (Athena), pink-noise sleep cueing. SDKs: muse-js, MuseLSL. ⭐ Most popular and best-supported.
- **Sens.ai** — 3 EEG + heart coherence + tPBM (NIR LEDs in headset). $2K+. Pricey but most feature-rich.
- **Neurosity Crown** — 8 EEG channels, dev-friendly, JS SDK.
- **OpenBCI Cyton/Ganglion** — research-grade, 4–16 channels, BLE.
- **EMOTIV Insight/EPOC X** — 5–14 channels, JS Cortex API.
- **Flow Neuroscience headset** — tDCS + app, depression-focused.

**Closed-loop neurofeedback for trance/meditation states:**
- Frontal-midline theta (FMθ, 3.5–6.5 Hz at Fz) is the meditation/focused-attention biomarker; Brandmeyer & Delorme 2020 trained novices to amplify it.
- Sensorimotor rhythm (SMR, 12–15 Hz at Cz) = body-quiet state.
- **HNE port:** Optional "Muse mode": session adapts based on real-time theta/alpha — reward (deepen narration, dim lights) when target frequencies are present, gentle re-engagement when mind wanders.

**HRV biofeedback:**
- Polar H10, Garmin HRM-Pro, Apple Watch (via HealthKit-bridged web), Whoop, Oura accessible via web bluetooth or companion apps.
- Resonance-frequency assessment protocol described above.
- **HNE port:** ⭐ HIGH PRIORITY. HRV coherence is the cheapest hardware-augmented depth metric.

**Pulse oximeters via Web Bluetooth** (Wellue, ChoiceMMed) give SpO2 + HR for breath-coherence visualization at very low cost.

---

### 13. Ritual / Cultural Approaches

**Drumming** (200–220 BPM "shamanic tempo")
- EEG studies (Konopacki & Madison 2018) show modest theta increases. Trance reports correlate with hypnotizability — so drumming helps everyone partway, highs further. Vaitl et al. 2005 review: rhythmic drone induces ASC.
- **HNE port:** Drumming preset audio track; loopable; tempo-adjustable. Combine with vection visualizer for stronger effect.

**Chanting / mantra repetition**
- Reduces default-mode-network activity (Kalyani 2011 "Om" study); rhythmic vocalization stimulates vagus.
- **HNE port:** Optional vocal-along; mantra display synced to breath.

**Dance / movement** — Gabrielle Roth 5Rhythms, ecstatic dance, Sufi whirling. Out-of-scope for narration but worth mentioning as off-platform pre-session protocol.

**Fasting / post-prandial state** — Mild fasting increases ketones, may sharpen attention; heavy meals dull alertness. Practical guidance: light meal 2 hours pre-session.

**Ceremony/setting design** — Lighting (warm low), scent (sage, lavender, palo santo), seated/lying posture preference, no-phone-rule: low-cost, high-impact. **HNE port:** Pre-session checklist screen.

---

### 14. Cross-modal Sensory Enhancement

**Synesthesia priming**
- Bouba/Kiki paradigm; ask user to assign colors to sounds, textures to emotions. Increases cross-modal associations linked to MODTAS synesthesia subscale.
- **HNE port:** Quick warm-up exercises before session.

**Multi-sensory congruence**
- When narrator describes "warm golden light," visualizer shows golden gradient + audio shifts to brighter timbre. Boosts immersion via predictive coherence.
- **HNE port:** ⭐ Tag scripts with sensory-element metadata; auto-sync visuals/audio to text.

**Doppler / motion cues** in 3D audio for narrative scenes (rushing river, passing wind) trigger automatic spatial-attention engagement.

---

### 15. Narrative / Literary Techniques

**Bibliotherapy** — long-form reading puts capable readers into transportation/absorption states comparable to trance (Green & Brock 2000). Highly engaged narrative = absorption training.

**Parasocial bonding** with consistent narrator persona — reuse same voice, name, micro-mannerisms. Trust = increased oxytocin (the same mechanism oxytocin nasal spray exploits).

**Ericksonian indirect suggestion / metaphor** — embeds suggestions inside stories; bypasses critical analysis. Pairs *especially* well with low responders who resist direct command.

**HNE port:** ⭐ HIGH PRIORITY. Build a stable of named narrator personas with consistent voice direction and mini-bios. Lean heavily on metaphor/story-scaffolded scripts over command-style.

---

### 16. Conditioning / Anchoring

**Classical conditioning of trance triggers** — pair a unique sound (a specific bell, gong, breath cue) with peak-trance state across many sessions; sound becomes a CR for trance entry.

**Anchoring (NLP)** — touch a specific finger together at peak relaxation; later use as access cue. Self-applicable.

**HNE port:** ⭐ Persistent "trance anchor" sound that plays at depth peak each session and is offered as a downloadable ringtone/widget for use during the day. Track-the-anchor-usage feature.

---

### 17. Bypass Techniques (Confusion / Overload / Fatigue)

**Elman induction** — rapid eye-fixation + relaxation + fractionation (open/close eyes, deeper each time) + arm-drop test. ~4 minutes to deep trance.

**Confusion induction (Erickson)** — overload working memory with paradoxical instructions ("the more you try to focus, the less you can remember to try not to focus"). Forces relinquishment of conscious analysis.

**Sensory overload induction** — bombard with multiple simultaneous suggestions, paradoxes, conflicting sensations.

**Sleep-deprivation states** — naturally lower critical-faculty thresholds; higher absorption.

**HNE port:** ⭐ Implement Elman as a fast-track induction option; confusion induction as an "Ericksonian" mode for resistant users; overload induction as an experimental "strong" mode with clear warnings about disorientation.

---

### 18. Somatic / Therapy-Adjacent Techniques That Bypass Cognitive Resistance

- **Somatic Experiencing (Levine)** — body-tracking pendulation between activation and settling. Bypasses verbal/cognitive defenses.
- **IFS (Internal Family Systems)** — "parts" dialog frame; allows skeptical user's "skeptic part" to be addressed rather than fought.
- **EMDR-adjacent bilateral stimulation** — alternating L/R audio tones or visual cues (1-2 Hz). Some users report dissociation/absorption similar to light trance.
- **Focusing (Gendlin)** — felt-sense attention.

**HNE port:** ⭐ "IFS-aware" script library that explicitly speaks to the part of the user that doesn't believe this works ("and that part of you that's skeptical can stay alert; only the part that's curious needs to come along"). Bilateral audio panning at 1–2 Hz as ambient option. Felt-sense check-ins between suggestions.

---

### 19. Modern Light/Sound Devices — Realistic Assessment

| Device | Real signal | What it does well | HNE relevance |
|---|---|---|---|
| **Lucia N°03** | Anecdotal + early small studies; psilocybin-comparable openness shifts in pilot data | Eyes-closed flicker hypnagogia; impressive subjective experience | Inspirational target for software flicker mode |
| **Mindplace Procyon/Kasina** | AVE literature (heterogeneous, real EEG effects) | Strong audio-visual entrainment, ganzfeld goggles, customizable | Reproduce via screen + headphones in HNE |
| **Roxiva rX1** | Same AVE category | High-end stroboscope with audio | Same |
| **NeuroVizr** | Marketing-heavy, modest evidence | 11-min sessions, 40 Hz emphasis (gamma + Alzheimer's research narrative) | Reproduce stack philosophy |
| **Muse / Sens.ai** | Real EEG validation; meditation-training studies show modest improvements | Real biofeedback | Direct integration via Web Bluetooth |
| **Brain.fm** | Independent EEG + fMRI peer-reviewed | Neural phase locking via amplitude modulation | Inspiration for HNE music engine |
| **Hemi-Sync (Monroe)** | 50 yrs reports; weak independent EEG; declassified CIA review | Robust subjective effects | Replicate stack architecture |
| **Wavepaths (Kaelen)** | Adaptive music for psychedelic therapy; design-validated | Personalized, arc-shaped music | Inspiration for adaptive-music engine |

---

### 20. Speculative / Pseudoscience Tier (Included Per User Request)

- **Biofield/energy work / Reiki / Healing Touch** — no convergent mainstream mechanism; small RCTs show relaxation effects largely attributable to attention/expectancy. Not delivered via software.
- **Scalar wave / "torsion field" devices** — no mainstream physics support.
- **Pyramidal geometry / orgone** — no evidence.
- **Crystals / sound bowls (Tibetan/crystal)** — singing bowls produce real low-frequency vibration with vibroacoustic-like effects; "crystal energy" claims unsupported.
- **Schumann resonance ambient generators (7.83 Hz tone)** — reproducible as audio file; no convincing entrainment evidence at audio-only intensities; does no harm.
- **Holosync / Centerpointe** — proprietary binaural-beat program with strong marketing; no independent replication of unique claims.

**HNE port:** Include these as optional toggles labeled clearly with evidence level (e.g., "Exploratory / Unproven"). Many users find these meaningful via expectancy alone — and that's a legitimate, ethical path to subjective benefit, *as long as honestly labeled*.

---

## Recommendations (Concrete, Staged Build Plan)

### Phase 1 — Browser-only essentials (high-evidence, zero hardware)
1. **CSTP-style onboarding flow** (4 short modules: information, expectancy, modeling video, practice items with self-rating).
2. **MODTAS + Phenomenological Control Scale assessment** at intake; show users their profile and tailor scripts (e.g., for low-imagery users: VR-style scene scripts; for high-aesthetic users: Kaelen-style music sessions).
3. **Resonance-frequency breath pacer** (visual + audio) with RF-finding protocol — default 5.5 bpm.
4. **Web Audio engine with**: binaural + isochronic + monaural tone generators; pink/brown noise; 3D HRTF spatialization (Resonance Audio); 40 Hz sub-bass haptic layer; arc-shaped intensity envelope.
5. **WebGL visualizer suite**: software ganzfeld, software dreamachine flicker (with seizure-risk lockouts and warnings), tunnel/vection, mandala-pulse, breath-synced expanding orb.
6. **Expectancy/ritual scaffolding**: pre-session checklist, consistent opening/closing rituals, named narrator personas, depth tracking with honest interpretation, "trance anchor" classical-conditioning feature.
7. **Hypnagogic mode** — designed for bedtime/nap use with sparse anchor prompts.
8. **IFS-aware skeptic-friendly script variants** — first-class alternative to "hypnosis" framing.
9. **Elman + confusion-induction script options** as fast/strong alternatives to progressive relaxation.

### Phase 2 — Bring-your-own-hardware integration
10. **Web Bluetooth/HID/USB integrations**: Muse (EEG), Polar H10 (HRV), generic pulse-ox, generic HRM. Visualizer drives off live signal.
11. **Closed-loop adaptation**: deepen narration when frontal theta or HRV coherence is up; gentle re-engage when mind-wandering signature appears.
12. **WebXR/VR mode** (Quest, Vision Pro, mobile cardboard) — same scripts, immersive scenes for low-imagery users.
13. **Mic-based breath/hum detection** (free; no hardware) drives visualizer breathing and rewards humming.

### Phase 3 — Off-platform protocol library
14. **Curated guides** for: float-tank pairing, tDCS/TMS pairing, supplement pairing (legal OTC), fasting/circadian timing, AVE-device pairing (Procyon/Kasina/Roxiva/Lucia/NeuroVizr — consume HNE audio while wearing them).
15. **Wavepaths-style adaptive music engine** (longer-term R&D): generative ambient stems mixed in real time with arc envelope; user-flagged "this carries me / this feels off" feedback loop.

### Decision benchmarks (when to advance to next phase)
- Phase 1 → 2 once 25%+ of users report "deepest experience yet" within 4 sessions, *and* MODTAS/PCS measures show stable upward trend across cohort.
- Phase 2 → 3 once Muse-mode adoption exceeds 10% of paying users (signal that hardware-augmented depth is valued enough to invest in adaptive music).
- Halt/redesign if low-suggestibility cohort shows no improvement across 8 sessions: most likely deficit is in CSTP onboarding or in expectancy framing, not in audio engineering.

---

## Caveats

- **Effect sizes for trait modification are modest.** CSTP gains are real but often partially attributable to demand characteristics; even after correction, genuine gains are 0.5–1.5 SHSS:C points for low subjects, not "full conversion."
- **Many interventions in this inventory have weak or contested evidence.** Binaural beats, AVE, Hemi-Sync, Schumann resonance entrainment, photobiomodulation for hypnosis, vibroacoustic for trance — all have signal but also null replications. Treat the inventory as breadth, not endorsement.
- **The "feel like it's working" mechanism IS partly placebo/expectancy/demand.** This is not pejorative — it's how the brain produces subjective change. Honest framing ("this works partly through expectancy and ritual, and that's a legitimate mechanism") is ethically required and, per the Kirsch/balanced-placebo literature, *enhances* rather than reduces effect.
- **Safety:** Photic flicker can trigger seizures (~1 in 4000 prevalence; higher in undiagnosed). Wim Hof breathing has caused syncope-related drowning deaths. Hypnagogic-state work near sleep can cause sleep paralysis. Brain stimulation devices have rare adverse events. HNE should default-off any stimulation above conservative thresholds and require informed-consent flow for advanced features.
- **Pharmacology is out of HNE's lane.** Mention as protocol-pairing options with safety disclaimers; do not recommend dosing.
- **The biggest unknown for a 1/10 user:** whether the trait is genuinely fixed at the neural level (DLPFC-dACC connectivity per Hoeft/Spiegel) or whether the 1/10 score reflects skill/attitudinal deficits that CSTP can address. Pragmatically, the answer is: *try CSTP-style training first; if no gain after 8 sessions, lean into the bypass-the-trait stack* (physiology, AVE, hypnagogia, VR, ritual). Most low scorers will move *somewhat* with CSTP. Some won't, and for them the value of HNE comes from physiological/sensory effects that don't require trait suggestibility at all — and those effects are real, measurable, and worth building for.
- **The user is a 1/10 self-reporter, not someone formally tested by Stanford.** Worth running a self-administered Elkins Hypnotizability Scale or HGSHS:A at baseline before assuming the floor; scores often rise with proper administration and expectancy framing alone.