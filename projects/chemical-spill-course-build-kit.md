# Chemical Spill Response — Course Build Kit (English master)

A complete, paste-ready production kit for building the *Chemical Spill Response SOP*
course in **Articulate Storyline 360** and **Rise 360**, with an AI-avatar intro,
a based-on-a-real-incident dramatization, and the full scenario scripts.

- **Tool:** Storyline 360 (zero-error engine) + Rise 360 (narrative shell)
- **Export:** SCORM 2004 (+ xAPI / cmi5 where supported)
- **Evaluation:** Kirkpatrick L1–L4; zero-error (100 %) mastery gate on critical steps
- **Language:** **English master.** The Spanish version is a *translated copy* (build EN,
  duplicate, translate) — learner-selectable, one language on screen at a time.
- **Status:** illustrative, employer-neutral scenario — swap in a real SOP when ready

> **Portfolio angle — one module, two tools.** This kit builds the *same* course content in
> **both** Storyline 360 and Rise 360, so a reviewer sees the same learning designed two ways
> and judges when to reach for each tool. The goal is not merely a finished course but
> **evidence that the designer can produce SOP-compliance training that makes people follow
> the SOP** — the core of a senior instructional-design role.

## Same content, two tools — at a glance

| Element | In **Storyline 360** | In **Rise 360** |
|---|---|---|
| AI-avatar intro | Video on an intro slide + CC | Video block + text disclosure |
| The Incident (reenactment) | Audio on timeline + CC + Continue trigger | Audio/Video block + transcript |
| Debrief | Slides with layers / click-to-reveal | Statement + Process + Accordion |
| Key terms glossary | Lightbox slide / slide master button | Accordion or Flashcard-grid block |
| **The 7-step zero-error scenario** | **Native: slides, layers, variables, triggers** | **Embedded as a Storyline block** |
| Knowledge checks | Freeform / quiz slides | Knowledge Check blocks |
| Assessment & pass rule | Results slide + variable conditions | Quiz lesson (pass %) + the Storyline gate |
| Reaction survey (L1) | Survey quiz slides | Ungraded Knowledge Check |
| Responsiveness | Modern player (manual tuning) | Automatic, by design |
| Best at | Decisions, consequences, simulation, full control | Narrative flow, speed, responsive reading |

**Rule of thumb:** decision & consequence → Storyline; narrative & reference → Rise.

## Language strategy — English master, then translated copies

Build everything in **English first** (this kit). To localize: **copy the finished course and
translate the copy into Spanish** — learner picks one language at launch and sees only that
language (never both on screen).

- **Storyline:** a "Choose your language" start slide sets a text variable `lang` (`en`/`es`)
  and jumps to a monolingual EN or ES scene. Build EN first; duplicate the scenes and translate.
- **Rise / Articulate 360 AI:** build the English course, then **duplicate it and translate**
  to produce the Spanish course. Offer the choice on a launch page or via the LMS.
- **WCAG:** each version declares its own page language (3.1.1). No screen mixes languages.

---

## PART 1 · Storyline 360 build guide

### 0 · Project setup
1. New Project → **Design › Story Size › 1920×1080**.
2. Save as `Spill-Response_v0.1.story` (version the filename — controlled record).
3. Set theme fonts/colors to the Ocean Ink palette (Fraunces/Inter, indigo + gold).

### 1 · Structure (Story View → New Scene)
| Scene | Slides | Purpose |
|---|---|---|
| 0 · Language | 0.1 Choose your language | Sets `lang`; jumps to EN scene (ES added when localized) |
| 1 · Intro | 1.1 Welcome/avatar · 1.2 Objectives · 1.3 How it works | Hook + relevance |
| 2 · Incident | 2.0 Reenactment (audio drama) | Emotional hook (L1) |
| 3 · Scenario | 3.1 → 3.7 (one per SOP step) | Zero-error decision engine |
| 4 · Results | 4.1 Results slide | Pass/fail + score to LMS |
| 5 · Wrap | 5.1 Reaction survey · 5.2 Job aid | L1 + support |

### 2 · Variables (Triggers panel › Manage project variables)
| Name | Type | Default | Purpose |
|---|---|---|---|
| `lang` | Text | en | learner's chosen language — set on slide 0.1 |
| `errorCount` | Number | 0 | total critical errors |
| `critStep1_ok` … `critStep6_ok` | True/False | False | each critical step cleared |
| `firstTryFail` | True/False | False | missed any step on first try (L2 signal) |

### 3 · The zero-error decision slide (template — reuse for all 7)
**Base layer:** scenario image + prompt + answer buttons. Set the **Next button initial
state = Disabled**.
**Two layers:** `Correct` (✓ + why + Continue) and `Consequence` (plain-language outcome,
in gold not red, + Try again).

Triggers on the **correct** button: Show layer `Correct`; Adjust `critStepN_ok = True`.
Triggers on **each wrong** button: Show layer `Consequence`; Adjust `errorCount` + Add 1;
Adjust `firstTryFail = True`.
Layer triggers: `Consequence` › **Try again** → Hide layer (Next stays disabled);
`Correct` › **Continue** → change Next state to Normal (or Jump to next slide).

Reuse by copy/paste of slide 3.1; change image, prompt, options and the `critStepN_ok`
variable. Vary interactions (hotspot, multiple-response, drag-and-drop). Step 7 is scored,
not a hard-fail.

### 4 · Results slide (4.1)
Insert › Quizzing › **Results Slide**. Mark **passed** only if `critStep1_ok`…`critStep6_ok`
are all True **AND** `errorCount = 0`. Report **first-attempt** performance.

### 5 · Accessibility
Alt text on every image; logical **tab order** per slide; **closed captions** on all audio;
no colour-only meaning; set slide language. Target WCAG 2.1 AA / Section 508.

### 6 · Publish
Publish › LMS › **SCORM 2004 (4th ed.)** › track by Results slide › report completion **and**
success › Resume on. Test pass/fail/resume in **SCORM Cloud** before release.

### 7 · Version-lock
SOP vX → `.story` vX → package vX, recorded together.

> **The one thing people get wrong:** the Next button must start **Disabled** on every
> critical decision; only the correct path enables it. Otherwise the zero-error gate leaks.

---

## PART 2 · Rise 360 build guide

**Principle:** Rise can't do true zero-error branching (no variables/triggers). Build the
narrative, glossary and knowledge checks in Rise → **embed the zero-error engine as a
Storyline block.** Decision & consequence = Storyline; everything else = Rise.

**Language:** build the **English** course; to localize, **duplicate it and translate** to
produce the Spanish course. Offer the choice on a launch page or via the LMS.

### Lessons
| # | Lesson | Blocks |
|---|---|---|
| 1 | Welcome (AI avatar) | Video + Text (disclosure) |
| 2 | The Incident (reenactment) | Audio/Video + transcript + content note |
| 3 | Debrief: what went wrong | Statement + Process + Image&text |
| 4 | Before you start — Key terms | Accordion / Flashcard grid (glossary) |
| 5 | The 7 SOP steps | Process + Labeled graphic |
| 6 | Practice: Spill scenario | **Storyline block** (zero-error engine) |
| 7 | Check your knowledge | Knowledge Check blocks (ungraded) |
| 8 | Assessment | **Quiz** lesson (graded, pass %) |
| 9 | Reaction survey (L1) | Ungraded Knowledge Check / form |
| 10 | Job aid & close | Button/File (download) + Statement |

### Publish
Publish › LMS › **SCORM 2004** (or **cmi5** with an LRS). Completion = *Quiz passed*
(or all lessons viewed + quiz passed). Test in SCORM Cloud. Version-lock SOP vX → course vX →
embedded `.story` vX → package vX.

---

## PART 3 · AI avatar — course intro script

**Disclosure:** generic AI presenter → recommended; **clone of a real person → legally
required + consent** (EU AI Act Art. 50(4)+50(5)). Disclosure is built into the opening.

**[On-screen caption 0–4 s + spoken]**
> This course is presented by an AI-generated avatar. Content authored and verified by Ana
> Eslava-Graterol (EU AI Act, Art. 50).

**[Avatar speaks]**
> "Hi, and welcome. I'm an AI-generated presenter, and I'll guide you through this short course
> on responding to a chemical spill in the lab. When a spill happens, the first few seconds
> decide everything. Here you'll practise the real procedure in a simulation, where a mistake
> costs nothing but teaches everything. You'll work through the seven steps of the spill SOP
> and, to pass, get the critical steps right — with zero errors. Miss one, and you'll see what
> would happen, then try again. Let's begin."

---

## PART 3b · Avatar package (Articulate Interactive Video: ① script → ② voiceover → ③ options)

**Persona:** a lab safety officer in full PPE (white lab coat, safety goggles, nitrile gloves)
in a working chemistry lab — fume hood, labelled reagent shelves, spill-kit station behind.
Calm, credible. Disclosure spoken (first line) **and** on screen (first 4 s).

**① Script / content:**
> This course is presented by an AI-generated avatar. Content authored and verified by Ana
> Eslava-Graterol, under the EU AI Act, Article 50.
>
> Welcome. I'm your AI safety guide, and I'm dressed the way you should be before you ever go
> near a spill — lab coat, goggles, gloves. In the next few minutes you'll respond to a
> chemical spill the way it really happens in this lab: fast decisions, real consequences.
> You'll follow the seven steps of the spill procedure, and to pass you'll need the critical
> steps right — with zero errors. Make a wrong call and you'll see exactly what it would
> cause, then try again. Stay sharp, protect yourself and the people around you. Let's begin.

**② Create voiceover:** English, clear professional voice; keep punctuation for pauses;
pronunciations SDS = "ess-dee-ess", PPE, reagent, water-reactive.
**③ Set video options:** presenter in lab coat/PPE if available (else neutral) + chemistry-lab
background; 16:9; captions ON; on-screen text 0–4 s: "AI-generated avatar · Content verified
by Ana Eslava-Graterol · EU AI Act Art. 50."

> To localize: duplicate the video, switch the voice to Spanish, translate the script and
> on-screen text — keep the avatar and background identical.

---

## PART 4 · "Based on a real incident" reenactment

### Guardrails (do first)
1. **Anonymize** — change names, dates, location; label on screen "Dramatization based on a
   real incident. Names and details changed."
2. **No real victim's voice/footage without written consent.**
3. **Never clone a real person's voice** without consent (deepfake under Art. 50).
4. **Trauma-informed** — content note at start; purposeful, not gratuitous; allow replay/skip.
5. **Disclose synthetic voices** (Art. 50).

**[On-screen 0–4 s + spoken]**
> Dramatization based on a real laboratory incident. Names and details have been changed.
> Voices are AI-generated.
**Content note:** This lesson depicts a workplace chemical injury.

### Script — 3 voices: NARRATOR, MARA (technician), LUIS (colleague)
> NARRATOR: It was 4:50 on a Friday. One task left before the weekend.
> MARA: *(moving fast)* Almost done… just need to move this bottle—
> *(SFX: glass clinks, smash, splash)*
> MARA: *(gasp)* No, no, no—
> LUIS: What was that? …Mara, what spilled?
> MARA: I— I don't know, I'll just wipe it—
> NARRATOR: And that was the first mistake. She didn't check the label. She reached for a
> paper towel — bare-handed.
> *(SFX: sharp hiss; Mara cries out)*
> MARA: *(pain)* My hand— it's burning—
> LUIS: Don't touch it! Get to the eyewash — I'm calling it in!
> NARRATOR: Mara spent three weeks in recovery. The spill was a water-reactive reagent. Every
> step that could have protected her was in the SOP she skipped. Today, you'll walk those
> steps — before it's ever real.

---

## PART 4b · "Chemical Spill Incident: Lessons Learned" — intro + debrief accordion

A text-based opener (distinct from the dramatized reenactment): an incident narrative + a
4-section expandable debrief.

**On-screen disclosure (0–4 s):** Dramatization based on a real incident. Names and details
changed.

### Incident narrative
> **Chemical Spill Incident: Lessons Learned.** A technician accidentally knocked over a bottle
> of corrosive acid. Without checking the label or putting on gloves, they grabbed paper towels
> to clean it up. The acid soaked through, causing a chemical burn. As the spill spread, fumes
> triggered the fire alarm. Skipping standard operating procedure (SOP) steps led to injury,
> panic, and an expensive cleanup.

**Incident Debrief: What Went Wrong?** *Expand each section.* Each: what happened → consequence
→ what the SOP requires.

- **Not Checking the Label.** Acted on an unknown chemical. **Consequence:** misjudged the
  hazard and chose the wrong response. **SOP (Step 1 – Assess):** consult the label and the SDS
  first; never identify a chemical by sight, smell or touch.
- **No PPE Worn.** Cleaned the spill without gloves or goggles. **Consequence:** a chemical burn
  to the skin. **SOP (Step 3 – PPE):** gloves, goggles and apron *before* approaching.
- **Improper Cleanup.** Paper towels spread the acid and raised exposure. **Consequence:** wider
  contamination and more risk. **SOP (Steps 4–5 – Contain & correct kit):** ring the spill with
  absorbent away from drains and use the correct spill kit — never paper towels.
- **No Alarm or Report.** Did not alert others or report. **Consequence:** delayed emergency
  response and greater danger. **SOP (Steps 2 & 7 – Alert/evacuate & Document):** alert and
  evacuate immediately, then complete the incident log and notify your supervisor.

> **Bridge to practice:** "Four skipped steps caused this. Now you'll take the controls — and
> get all seven right, with zero errors."

---

## PART 5 · The 7 scenario slides (paste-ready)

Each slide: **On-screen** (prompt + options), **VO**, **Correct** feedback, **Consequence**
feedback, **Dev notes**. ✓ = correct. Feedback colours: Correct = rose/✓; Consequence = gold/!
(never red).

### Slide 3.1 — Step 1 · Assess the spill
**On-screen:** *A liquid has spilled near the bench. What is your FIRST action?*
- A) Smell it to identify what it is.
- ✓ B) Consult the SDS to identify the chemical and its hazards.
- C) Start wiping it up right away.
- D) Ignore it — it's probably water.

**VO:** "Something's spilled. Before you touch anything — how do you find out what it is?"
**Correct:** "Right. The SDS tells you what it is and how to handle it. Never identify a
chemical by sight, smell or touch."
**Consequence:** "You leaned in to smell it — the vapour was toxic. Never identify a spill by
smell. Try again."
**Dev notes:** `critStep1_ok`. Multiple choice (or hotspot on the SDS binder).

### Slide 3.2 — Step 2 · Alert & evacuate
**On-screen:** *The SDS shows a hazardous, volatile reagent. What now?*
- ✓ A) Alert the people nearby and clear the area.
- B) Quietly clean it before anyone notices.
- C) Keep working on your task.
- D) Open a window and carry on.

**VO:** "It's hazardous and gives off vapour. What protects the people around you?"
**Correct:** "Yes — people first. Alert and evacuate before you do anything else."
**Consequence:** "You stayed quiet. The vapour spread and a colleague was exposed. Alert and
evacuate first. Try again."
**Dev notes:** `critStep2_ok`. Branching decision.

### Slide 3.3 — Step 3 · Don the correct PPE
**On-screen:** *You're ready to act. What do you put on BEFORE approaching the spill? (Select
all that apply.)*
- ✓ Chemical-resistant gloves · ✓ Safety goggles · ✓ Lab apron
- Approach with bare hands · Just a dust mask

**VO:** "Protect yourself before you get close. Choose your PPE."
**Correct:** "Full PPE on — now you're protected."
**Consequence:** "You reached in bare-handed and the reagent burned your skin. Don full PPE
first. Try again."
**Dev notes:** `critStep3_ok`. Multiple-response; correct only when all three PPE selected and
no wrong item.

### Slide 3.4 — Step 4 · Contain the spill
**On-screen:** *PPE on. How do you stop the spill spreading?*
- ✓ A) Ring the spill with absorbent, working from the outside in.
- B) Wipe it toward the floor drain.
- C) Pour water on it to dilute it.
- D) Leave it and get a mop.

**VO:** "Stop it spreading — and keep it away from drains."
**Correct:** "Contained. Ringing it from the outside in keeps it controlled."
**Consequence:** "You wiped toward the drain — the reagent entered the water system, a
reportable release. Contain it, away from drains. Try again."
**Dev notes:** `critStep4_ok`. Branching decision.

### Slide 3.5 — Step 5 · Use the correct spill kit
**On-screen:** *The SDS says the reagent is water-reactive. Which kit do you use?*
- ✓ A) The dry / neutralizing kit for water-reactive chemicals.
- B) The universal water-based kit.
- C) Dilute it with plenty of water.
- D) Whichever kit is closest.

**VO:** "This one reacts with water. Choose the kit that's safe for it."
**Correct:** "Exactly — the right kit for the reagent class. Safely absorbed."
**Consequence:** "Water triggered a violent reaction; the spill spread and released fumes.
Match the kit to the reagent class. Try again."
**Dev notes:** `critStep5_ok`. Decision + strong consequence layer (highest-risk step).

### Slide 3.6 — Step 6 · Dispose of the waste
**On-screen:** *The spill is absorbed. Where does the waste go?*
- ✓ A) The labelled hazardous-waste container.
- B) The general waste bin.
- C) The sink.
- D) Back on the shelf for now.

**VO:** "The residue is still hazardous. Where does it belong?"
**Correct:** "Correct — labelled hazardous-waste container, every time."
**Consequence:** "General waste can't take hazardous residue — that's a reportable violation.
Use the hazardous-waste container. Try again."
**Dev notes:** `critStep6_ok`. Drag-and-drop (drag the waste bag to the correct bin).

### Slide 3.7 — Step 7 · Document & report *(important, not a hard-fail)*
**On-screen:** *The area is safe. What is the final step?*
- ✓ A) Complete the incident log and notify your supervisor.
- B) Skip the paperwork — it's handled.
- C) Tell a colleague verbally and move on.

**VO:** "One step left — and it's the one people forget."
**Correct:** "Done properly. The incident log closes the loop and improves the SOP."
**Feedback (wrong):** "Without the report, the organisation can't learn or comply. Always
document."
**Dev notes:** scored question, **not** part of the zero-error gate (no `errorCount`).

---

## PART 6 · Avatar generation prompts

### A · Synthesia (standalone video, then embed)
1. New video › blank 16:9.
2. Avatar: a professional stock presenter (neutral, business-casual). No custom clone of a real
   person without written consent.
3. Voice: a clear professional English voice.
4. Script: paste the Part 3 spoken text. Add pauses with punctuation; use the pause control.
5. Pronunciation: SDS (ess-dee-ess), reagent, PPE, water-reactive.
6. On-screen disclosure: text element with the Part 3 caption, timed 0–4 s, high-contrast.
7. Background: clean lab or neutral studio; name strip "AI Presenter".
8. Captions: enable subtitles → download .vtt / .srt.
9. Export 1080p `.mp4`. Keep the project to re-generate if the script changes.

### B · Articulate avatars (AI Assistant, powered by Synthesia) — inside Rise/Storyline
> Labels evolve — [VERIFY current UI in your 360 subscription].
1. Rise: lesson › insert block › AI/Video › Generate avatar video. Storyline: AI Assistant.
2. Choose avatar + English voice.
3. Paste the Part 3 script. Generate, preview, insert.
4. Captions auto-generated — keep them on.
5. Below the video add a text block repeating the disclosure; also put it in the course credits.

> Whichever tool, the Art. 50 disclosure must appear at first exposure. A clone of a real
> person additionally requires that person's consent.

---

## PART 7 · Articulate 360 AI generator prompts (fast path)

Use Articulate 360 AI to generate the English shell/draft fast, then refine. Keep the strict
variable-based zero-error gate in Storyline. Attach this file (or the SOP) as source and use
**Apply brand** for Ocean Ink.

### Prompt A — "Course" type
> Create a workplace health-and-safety compliance course titled "Chemical Spill Response SOP"
> for adult laboratory technicians (new hires and refresher), experienced on the bench, taken
> on desktop and tablet, about 15 minutes, mandatory with annual recertification.
>
> Goal / terminal objective: given a simulated lab chemical spill and the available kits, the
> technician performs all seven SOP steps in the correct order with zero critical errors.
>
> Structure: (1) a short AI-presenter welcome; (2) a "based on a real incident" hook; (3) a
> debrief of what went wrong; (4) a key-terms glossary (SDS, PPE, hazardous waste, containment);
> (5) a practice scenario covering the seven steps — Assess (consult the SDS, never touch or
> smell), Alert and evacuate, Don PPE, Contain away from drains, Use the correct kit for the
> reagent class, Dispose in the hazardous-waste container, Document and report; (6) ungraded
> knowledge checks; (7) a graded quiz where the critical steps must be answered correctly; (8) a
> 3-item reaction survey; (9) a downloadable job aid.
>
> Tone: clear, professional, plain-language adult workplace learning — not marketing. Write to
> WCAG 2.1 AA. Emphasise that a wrong critical choice shows its real-world consequence, then
> lets the learner try again.
>
> LANGUAGE: Generate this as an ENGLISH course. (The Spanish version will be a translated copy.)

### Prompt B — "Scenario" type
> Build a branching decision scenario for lab technicians responding to a chemical spill. One
> decision point per step: (1) identify the spill — correct = consult the SDS; wrong = smell or
> touch it; (2) correct = alert and evacuate; wrong = clean it quietly; (3) correct = don full
> PPE first; wrong = bare-handed; (4) correct = contain with absorbent away from drains; wrong =
> wipe toward the drain; (5) the reagent is water-reactive — correct = the dry neutralizing kit;
> wrong = the water-based kit; (6) correct = hazardous-waste container; wrong = general bin; (7)
> correct = complete the incident log and notify the supervisor.
>
> For every wrong choice, show a realistic consequence (a colleague exposed, a chemical burn, a
> violent reaction, a reportable release) and route the learner back to retry that decision —
> passed only when all critical steps are correct with zero errors. Feedback supportive, never
> punitive. LANGUAGE: English (Spanish is a translated copy).

### Prompt C — "Interactive Video" type
> Create a short interactive-video intro. Open with a 45–60s AI-presenter welcome, then a
> dramatized "based on a real incident" scene (anonymized) showing a technician skipping the SOP
> and getting hurt. Add 1–2 reflective pause-points. Display an on-screen disclosure for the
> first 4 seconds: "AI-generated avatar and voices. Dramatization — names and details changed."
> LANGUAGE: English (Spanish is a translated copy).

### What the AI flow can and can't do
- ✅ Fast English course shell, lessons, knowledge checks, a branching Scenario, auto-captions,
  brand styling.
- ⚠️ It does not enforce a true variable-based 100 % mastery gate (`errorCount = 0`). For a
  strict, auditable zero-error record, build that one piece in Storyline and embed it.
- Always review and edit AI output (accuracy, bias, SOP fidelity) — your editorial responsibility.

---

## PART 8 · Final quiz — directions (paste into Articulate 360 AI "Quiz instructions")

**Kirkpatrick note:** a quiz measures **Level 2 (Learning)**. It cannot measure L3 (behaviour)
or L4 (results) — so this builds a strong L2 zero-error quiz, adds one L1 reaction item, and
frames questions at the L3 "what would you do on the job" level. The true 100 %-on-critical gate
stays in Storyline.

> Create a final assessment for the Chemical Spill Response SOP course.
>
> **Purpose (Kirkpatrick):** measures Learning (L2) — can the technician apply the SOP. Write at
> the application level (what they would DO on the job), not recall, so results point toward
> behaviour (L3). Include ONE unscored reaction item at the end (L1): "How confident are you that
> you could respond to a real spill correctly?"
>
> **Content — one scenario question per critical step (7):** 1 Assess → consult the SDS
> (distractors: smell/touch, wipe); 2 Alert & evacuate (distractors: clean quietly, keep
> working); 3 Don PPE first (distractor: bare-handed); 4 Contain away from drains (distractor:
> wipe to drain); 5 water-reactive → dry/neutralizing kit (distractor: water-based/water); 6
> hazardous-waste container (distractor: general bin/sink); 7 Document & report. Use realistic
> distractors from common real mistakes.
>
> **Difficulty & zero-error:** steps 1–6 are critical — zero-error (100 % mastery); passing
> score = 100 %. For each critical question, feedback shows the real-world consequence of the
> wrong answer, then restates the correct action. Mix MC, multiple-response (PPE), matching.
> Plain professional adult tone.
>
> **Accessibility:** no colour-only cues; screen-reader-friendly; alt text for any image.
> **LANGUAGE:** English (the Spanish quiz is a translated copy).

- The AI quiz is percentage-based → "100 % to pass" = the zero-error rule at course level.
- For an auditable per-step gate (`errorCount = 0`), keep it in the Storyline scenario.
- If possible: passing score = 100 %, allow retries with feedback (learn from the consequence).

---

## PART 9 · Remaining course content (makes the course content-complete)

### 9.1 Language launch page
**Choose your language** — [English] [Español] *(the Spanish course is the translated copy)*

### 9.2 Debrief lesson (after the reenactment, before practice)
> **What went wrong — and what the SOP says.** The injury wasn't bad luck; it was five skipped
> steps.
> • She never checked the SDS → Step 1: Assess before you act.
> • She didn't alert or evacuate → Step 2: People first.
> • She reached in bare-handed → Step 3: PPE before approach.
> • She wiped toward the spread → Step 4: Contain, away from drains.
> • Water on a water-reactive reagent → Step 5: The right kit for the chemical.
> The SOP is the difference between a near-miss and three weeks of recovery. Now you'll walk
> every step.

### 9.3 Results / feedback messages
**PASS:**
> **Certified: zero critical errors.** You followed the SOP exactly — the way it protects you
> and everyone in the lab. Your first-attempt result has been recorded. Keep the job aid at
> your bench.

**NOT YET:**
> **Not yet — and that's how we keep it safe here.** A critical step was missed. Review the
> consequence, then repeat the scenario until every critical step is correct with zero errors.
> On the job there are no retries — that's why we practise until it's automatic.

### 9.4 Job aid — bench quick-reference (one page, downloadable, non-gated)
> **Chemical Spill Response — 7 steps**
> 1. ASSESS — consult the SDS; never touch or smell. 2. ALERT & EVACUATE — people first.
> 3. PPE — gloves, goggles, apron before you approach. 4. CONTAIN — ring with absorbent, away
> from drains. 5. CORRECT KIT — match the kit to the chemical (water-reactive = dry kit).
> 6. DISPOSE — labelled hazardous-waste container only. 7. DOCUMENT — incident log + supervisor.
> *If unsure what it is, STOP and check the SDS.*

### 9.5 Summary / close
> **You followed the SOP — now make it a habit.** Seven steps, in order, every time. The one
> that saves you: when in doubt, check the SDS and never identify a spill by sight, smell or
> touch. Download your job aid and keep it visible.

---

## Portfolio framing — how this proves candidate suitability
This course is evidence for the Senior Instructional Designer role.

| Job responsibility | Evidence in this build |
|---|---|
| Conduct job/task/performance analysis → objectives | DIF task analysis → Mager/Bloom objectives |
| Design complex technical instruction across media | Storyline sim + Rise course + AI avatar + reenactment |
| Develop criteria to evaluate effectiveness | Zero-error gate + Kirkpatrick L1–L4 + metrics |
| Partner/consult; agree outcomes & success metrics | Training strategy + agreed success metrics |
| Use evaluation to improve; share lessons | Closing-the-loop (L2↔L3 diagnosis) |
| Oversee vendors / translate programs | English master + Spanish translated copy; vendor-ready storyboard |
| EHS adherence | The SOP content itself + accessibility (WCAG AA) |

**The thesis for the hiring manager:** *"I don't just make courses — I design training that
provably changes on-the-job behaviour, measured against a zero-error compliance standard, built
as an English master and localized to Spanish, to WCAG AA."*

---

© 2026 Ana Eslava-Graterol · profeanaeslava · All rights reserved.

_Transparency note: developed with the assistance of generative AI; reviewed, edited and
approved under the editorial responsibility of Ana Eslava-Graterol, instructional designer
registered as a self-employed professional in Spain (in the spirit of the EU AI Act, Art. 50
— Regulation (EU) 2024/1689)._
