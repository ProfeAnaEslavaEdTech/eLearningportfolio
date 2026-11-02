# Chemical Spill Response — Course Build Kit

A complete, paste-ready production kit for building the *Chemical Spill Response SOP*
course in **Articulate Storyline 360** and **Rise 360**, with an AI-avatar intro,
a based-on-a-real-incident dramatization, and the full bilingual (EN/ES) slide scripts.

- **Tool:** Storyline 360 (zero-error engine) + Rise 360 (narrative shell)
- **Export:** SCORM 2004 (+ xAPI / cmi5 where supported)
- **Evaluation:** Kirkpatrick L1–L4; zero-error (100 %) mastery gate on critical steps
- **Languages:** EN / ES
- **Status:** illustrative, employer-neutral scenario — swap in a real SOP when ready

> **Portfolio angle — one module, two tools.** This kit builds the *same* course content
> (same incident, same 7 SOP steps, same scripts, same objectives) in **both** Storyline 360
> and Rise 360, so a reviewer can see the same learning designed two ways and judge when to
> reach for each tool. The content in Parts 3–5 is tool-agnostic — paste it into either build.

## Same content, two tools — at a glance

| Element | In **Storyline 360** | In **Rise 360** |
|---|---|---|
| AI-avatar intro | Video on an intro slide + CC | Video block + text disclosure |
| The Incident (reenactment) | Audio on timeline + CC + Continue trigger | Audio/Video block + transcript |
| Debrief | Slides with layers / click-to-reveal | Statement + Process + Accordion |
| Key terms glossary | Lightbox slide / slide master button | Accordion or Flashcard-grid block |
| **The 7-step zero-error scenario** | **Native: slides, layers, variables, triggers** | **Embedded as a Storyline block** (Rise can't do the logic) |
| Knowledge checks | Freeform / quiz slides | Knowledge Check blocks |
| Assessment & pass rule | Results slide + variable conditions | Quiz lesson (pass %) + the Storyline gate |
| Reaction survey (L1) | Survey quiz slides | Ungraded Knowledge Check |
| Responsiveness | Modern player (manual tuning) | Automatic, by design |
| Best at | Decisions, consequences, simulation, full control | Narrative flow, speed, responsive reading |

**Rule of thumb:** decision & consequence → Storyline; narrative & reference → Rise. The
honest showcase is to build the scenario natively in Storyline **and** wrap the same content
in Rise with that scenario embedded — demonstrating you choose the tool to fit the learning.

---

## Language strategy — selectable, not dual-on-screen

**"Bilingual" here means language-*responsive*: the learner picks English or Spanish at launch
and sees ONE language on screen at a time.** Never put EN and ES together on the same screen.
The EN/ES pairs in Parts 3–5 are **source text** — you implement each as its own language
version, not side by side.

- **Storyline:** a "Choose your language / Elige tu idioma" start slide sets a text variable
  `lang` (`en`/`es`) and jumps to a **monolingual EN scene** or **ES scene**. Add a small
  "change language" button if needed. (Alternative for small courses: one slide set where each
  text object has EN/ES states driven by `lang` — more work to maintain; prefer parallel scenes.)
- **Rise / Articulate 360 AI:** Rise can't live-switch content language per learner, so produce
  **two separate course versions** (one EN, one ES) and let the LMS or a launch page offer the
  choice. Generate each with the AI prompts **run once per language** (English, then Spanish).
- **WCAG:** each version declares its own page language (3.1.1). Because no screen mixes
  languages, you don't need 3.1.2 language-of-parts tagging.

---

## PART 1 · Storyline 360 build guide

### 0 · Project setup
1. New Project → **Design › Story Size › 1920×1080**.
2. Save as `Spill-Response_v0.1.story` (version the filename — controlled record).
3. Set theme fonts/colors to the Ocean Ink palette (Fraunces/Inter, indigo + gold).

### 1 · Structure (Story View → New Scene)
| Scene | Slides | Purpose |
|---|---|---|
| 0 · Language | 0.1 Choose your language / Elige tu idioma | Sets `lang`; jumps to EN or ES scene |
| 1 · Intro | 1.1 Welcome/avatar · 1.2 Objectives · 1.3 How it works | Hook + relevance |
| 2 · Incident | 2.0 Reenactment (audio drama) | Emotional hook (L1) |
| 3 · Scenario | 3.1 → 3.7 (one per SOP step) | Zero-error decision engine |
| 4 · Results | 4.1 Results slide | Pass/fail + score to LMS |
| 5 · Wrap | 5.1 Reaction survey · 5.2 Job aid | L1 + support |

### 2 · Variables (Triggers panel › Manage project variables)
| Name | Type | Default | Purpose |
|---|---|---|---|
| `lang` | Text | en | learner's chosen language (`en`/`es`) — set on slide 0.1 |
| `errorCount` | Number | 0 | total critical errors |
| `critStep1_ok` … `critStep6_ok` | True/False | False | each critical step cleared |
| `firstTryFail` | True/False | False | missed any step on first try (L2 signal) |

> **Language select (slide 0.1):** two buttons — *English* / *Español*. English button →
> set `lang = en` → jump to the EN intro; Español → set `lang = es` → jump to the ES intro.
> Build the EN and ES paths as parallel monolingual scenes (one language on screen at a time).

### 3 · The zero-error decision slide (template — reuse for all 7)
**Base layer:** scenario image + prompt + answer buttons. Set the **Next button initial
state = Disabled**.
**Two layers:** `Correct` (✓ + why + Continue) and `Consequence` (plain-language outcome,
in gold not red, + Try again).

Triggers on the **correct** button:
- Show layer `Correct`
- Adjust `critStepN_ok = True`

Triggers on **each wrong** button:
- Show layer `Consequence`
- Adjust `errorCount` + Add 1
- Adjust `firstTryFail = True`

Layer triggers:
- `Consequence` › **Try again** → Hide layer (returns to decision; Next stays disabled)
- `Correct` › **Continue** → change Next state to Normal (or Jump to next slide)

Reuse by **copy/paste** of slide 3.1; change image, prompt, options and the `critStepN_ok`
variable each time. Vary interaction types (hotspot, multiple-response, drag-and-drop).

### 4 · Results slide (4.1)
Insert › Quizzing › **Results Slide**. Mark **passed** only if `critStep1_ok`…`critStep6_ok`
are all True **AND** `errorCount = 0`. Report **first-attempt** performance (`firstTryFail`).

### 5 · Accessibility
Alt text on every image; logical **tab order** per slide; **closed captions** on all audio;
no colour-only meaning; set slide language (EN/ES). Target WCAG 2.1 AA / Section 508.

### 6 · Publish
Publish › LMS › **SCORM 2004 (4th ed.)** › track by Results slide › report completion **and**
success › Resume on. Test pass/fail/resume in **SCORM Cloud** before release.

### 7 · Version-lock
SOP vX → `.story` vX → package vX, recorded together. Re-issue when the SOP changes.

> **The one thing people get wrong:** the Next button must start **Disabled** on every
> critical decision; only the correct path enables it. Otherwise the zero-error gate leaks.

---

## PART 2 · Rise 360 build guide

**Principle:** Rise can't do true zero-error branching (no variables/triggers). Build the
narrative, glossary and knowledge checks in Rise → **embed the zero-error engine as a
Storyline block.** Decision & consequence = Storyline; everything else = Rise.

**Language:** build **two separate Rise courses** — one English, one Spanish (Rise can't
live-switch content language per learner). Offer the choice on a launch page or via the LMS;
each learner sees a single-language course.

### Lessons
| # | Lesson | Blocks |
|---|---|---|
| 1 | Welcome (AI avatar) | Video + Text (disclosure) |
| 2 | The Incident (reenactment) | Audio/Video + transcript + content note |
| 3 | Debrief: what went wrong | Statement + Process + Image&text |
| 4 | Before you start — Key terms | Accordion / Flashcard grid (bilingual glossary) |
| 5 | The 7 SOP steps | Process + Labeled graphic |
| 6 | Practice: Spill scenario | **Storyline block** (zero-error engine) |
| 7 | Check your knowledge | Knowledge Check blocks (ungraded) |
| 8 | Assessment | **Quiz** lesson (graded, pass %) |
| 9 | Reaction survey (L1) | Ungraded Knowledge Check / form |
| 10 | Job aid & close | Button/File (download) + Statement |

### Publish
Publish › LMS › **SCORM 2004** (or **cmi5** with an LRS). Completion = *Quiz passed*
(or all lessons viewed + quiz passed). Test in SCORM Cloud.

### Version-lock
SOP vX → Rise course vX → embedded `.story` vX → package vX.

---

## PART 3 · AI avatar — course intro script

**Disclosure:** generic AI presenter → recommended; **clone of a real person → legally
required + consent** (EU AI Act Art. 50(4)+50(5)). Disclosure is built into the opening.

**[On-screen caption 0–4 s + spoken]**
EN: *This course is presented by an AI-generated avatar. Content authored and verified by
Ana Eslava-Graterol (EU AI Act, Art. 50).*
ES: *Este curso es presentado por un avatar generado por IA. Contenido creado y verificado
por Ana Eslava-Graterol (Ley de IA de la UE, art. 50).*

**EN (spoken):** "Hi, and welcome. I'm an AI-generated presenter, and I'll guide you through
this short course on responding to a chemical spill in the lab. When a spill happens, the
first few seconds decide everything. Here you'll practise the real procedure in a
simulation, where a mistake costs nothing but teaches everything. You'll work through the
seven steps of the spill SOP and, to pass, get the critical steps right — with zero errors.
Miss one, and you'll see what would happen, then try again. Let's begin."

**ES (hablado):** "Hola y bienvenido. Soy un presentador generado por inteligencia
artificial y te guiaré en este breve curso sobre cómo responder a un derrame químico en el
laboratorio. Cuando ocurre un derrame, los primeros segundos lo deciden todo. Aquí
practicarás el procedimiento real en una simulación, donde un error no cuesta nada pero lo
enseña todo. Recorrerás los siete pasos del procedimiento y, para aprobar, deberás acertar
los pasos críticos — con cero errores. Si fallas en uno, verás qué pasaría y podrás
intentarlo de nuevo. Comencemos."

---

## PART 3b · Avatar packages — EN & ES (Articulate Interactive Video: ① script → ② voiceover → ③ video options)

**Persona (both):** a lab safety officer in full PPE (white lab coat, safety goggles, nitrile
gloves) in a working chemistry lab — fume hood, labelled reagent shelves, spill-kit station
behind. Calm, credible. The disclosure is spoken (first line) **and** on screen (first 4 s).

### English course
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
background; 16:9; captions ON (EN); on-screen text 0–4 s: "AI-generated avatar · Content
verified by Ana Eslava-Graterol · EU AI Act Art. 50."

### Spanish course
**① Script / content:**
> Este curso es presentado por un avatar generado por inteligencia artificial. Contenido
> creado y verificado por Ana Eslava-Graterol, conforme a la Ley de IA de la Unión Europea,
> artículo 50.
>
> Bienvenido. Soy tu guía de seguridad con inteligencia artificial, y voy vestido como
> deberías estar tú antes de acercarte a un derrame: bata, gafas y guantes. En los próximos
> minutos responderás a un derrame químico tal como ocurre de verdad en este laboratorio:
> decisiones rápidas, consecuencias reales. Seguirás los siete pasos del procedimiento y, para
> aprobar, deberás acertar los pasos críticos — con cero errores. Si te equivocas, verás
> exactamente qué provocaría, y podrás intentarlo de nuevo. Mantente alerta, protégete y
> protege a quienes te rodean. Comencemos.

**② Create voiceover:** Spanish (es-ES or neutral es-419), clear professional; keep punctuation;
pronunciations FDS, EPI, reactivo, reactivo al agua.
**③ Set video options:** same presenter + lab scene as the EN version; 16:9; captions ON (ES);
on-screen text 0–4 s: "Avatar generado por IA · Contenido verificado por Ana Eslava-Graterol ·
Ley de IA de la UE, art. 50."

> Keep both videos visually identical; only the voice, captions and on-screen text change by
> language. Directions to Articulate stay in English; only the spoken script differs.

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
EN: *Dramatization based on a real laboratory incident. Names and details have been changed.
Voices are AI-generated.*
ES: *Dramatización basada en un incidente real de laboratorio. Se han cambiado nombres y
detalles. Las voces son generadas por IA.*
**Content note:** *This lesson depicts a workplace chemical injury. / Esta lección representa
una lesión química laboral.*

### Script — 3 voices: NARRATOR, MARA (technician), LUIS (colleague)

**EN**
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
> NARRATOR: Mara spent three weeks in recovery. The spill was a water-reactive reagent.
> Every step that could have protected her was in the SOP she skipped. Today, you'll walk
> those steps — before it's ever real.

**ES**
> NARRADOR: Eran las 4:50 de un viernes. Quedaba una sola tarea antes del fin de semana.
> MARA: *(con prisa)* Ya casi… solo muevo este frasco—
> *(SFX: tintineo, golpe, salpicadura)*
> MARA: *(ahogo)* No, no, no—
> LUIS: ¿Qué fue eso? …Mara, ¿qué se derramó?
> MARA: No… no sé, lo limpio y ya—
> NARRADOR: Y ese fue el primer error. No miró la etiqueta. Tomó un papel — con las manos
> desnudas.
> *(SFX: siseo agudo; Mara grita)*
> MARA: *(dolor)* ¡Mi mano… me quema!
> LUIS: ¡No lo toques! ¡Ve al lavaojos — yo doy el aviso!
> NARRADOR: Mara pasó tres semanas en recuperación. Era un reactivo reactivo al agua. Cada
> paso que podía haberla protegido estaba en el procedimiento que se saltó. Hoy, tú
> recorrerás esos pasos — antes de que sea real.

---

## PART 4b · "Chemical Spill Incident: Lessons Learned" — intro + debrief accordion

The text-based opener (distinct from the dramatized reenactment): an incident narrative + a
4-section expandable debrief. Build EN and ES as separate single-language versions.

**On-screen disclosure (0–4 s):** EN *Dramatization based on a real incident. Names and
details changed.* · ES *Dramatización basada en un incidente real. Se han cambiado nombres y
detalles.*

### Incident narrative
EN:
> **Chemical Spill Incident: Lessons Learned.** A technician accidentally knocked over a bottle
> of corrosive acid. Without checking the label or putting on gloves, they grabbed paper towels
> to clean it up. The acid soaked through, causing a chemical burn. As the spill spread, fumes
> triggered the fire alarm. Skipping standard operating procedure (SOP) steps led to injury,
> panic, and an expensive cleanup.
ES:
> **Incidente de derrame químico: lecciones aprendidas.** Un técnico volcó accidentalmente un
> frasco de ácido corrosivo. Sin revisar la etiqueta ni ponerse guantes, tomó papel para
> limpiarlo. El ácido traspasó el papel y le causó una quemadura química. Al extenderse el
> derrame, los vapores activaron la alarma de incendios. Saltarse los pasos del procedimiento
> (PNT) provocó una lesión, pánico y una limpieza costosa.

**Incident Debrief: What Went Wrong? / Análisis del incidente: ¿qué salió mal?**
*Expand each section. / Expande cada sección.* Each section: what happened → consequence →
what the SOP requires.

### Section 1 — Not Checking the Label / No revisar la etiqueta
EN: The technician acted on an unknown chemical. **Consequence:** they misjudged the hazard and
chose the wrong response. **SOP (Step 1 – Assess):** always consult the label and the SDS first;
never identify a chemical by sight, smell or touch.
ES: El técnico actuó sobre un producto desconocido. **Consecuencia:** calculó mal el peligro y
eligió la respuesta equivocada. **PNT (Paso 1 – Evaluar):** consulta siempre la etiqueta y la
FDS primero; nunca identifiques un producto por la vista, el olor o el tacto.

### Section 2 — No PPE Worn / Sin EPI
EN: They cleaned the spill without gloves or goggles. **Consequence:** a chemical burn to the
skin. **SOP (Step 3 – PPE):** put on chemical-resistant gloves, goggles and an apron *before*
approaching the spill.
ES: Limpió el derrame sin guantes ni gafas. **Consecuencia:** una quemadura química en la piel.
**PNT (Paso 3 – EPI):** ponte guantes resistentes a químicos, gafas y bata *antes* de acercarte
al derrame.

### Section 3 — Improper Cleanup / Limpieza inadecuada
EN: Using paper towels spread the acid and raised exposure. **Consequence:** wider
contamination and more risk. **SOP (Steps 4–5 – Contain & correct kit):** ring the spill with
absorbent, away from drains, and use the correct spill kit for the chemical — never paper towels.
ES: Usar papel extendió el ácido y aumentó la exposición. **Consecuencia:** más contaminación y
riesgo. **PNT (Pasos 4–5 – Contener y kit correcto):** rodea el derrame con absorbente, lejos de
los desagües, y usa el kit adecuado para el producto — nunca papel.

### Section 4 — No Alarm or Report / Sin alarma ni reporte
EN: They did not alert others or report the spill. **Consequence:** delayed emergency response
and greater danger. **SOP (Steps 2 & 7 – Alert/evacuate & Document):** alert people and evacuate
immediately, then complete the incident log and notify your supervisor.
ES: No avisó a nadie ni reportó el derrame. **Consecuencia:** respuesta de emergencia tardía y
mayor peligro. **PNT (Pasos 2 y 7 – Avisar/evacuar y Documentar):** avisa y evacúa de inmediato,
luego completa el registro del incidente y avisa a tu supervisor.

> **Bridge to practice:** "Four skipped steps caused this. Now you'll take the controls — and
> get all seven right, with zero errors." / "Cuatro pasos omitidos causaron esto. Ahora tomas
> tú el control — y acertarás los siete, con cero errores."

---

## PART 5 · The 7 scenario slides (paste-ready, EN/ES)

For each slide: **On-screen** (learner-facing prompt + options), **VO**, **Correct**
feedback, **Consequence** feedback, and **Dev notes** (variable + interaction + triggers).
Correct option marked ✓. Feedback colours: Correct = rose/✓; Consequence = gold/! (never red).

### Slide 3.1 — Step 1 · Assess the spill
**On-screen (EN):** *A liquid has spilled near the bench. What is your FIRST action?*
- A) Smell it to identify what it is.
- ✓ B) Consult the SDS to identify the chemical and its hazards.
- C) Start wiping it up right away.
- D) Ignore it — it's probably water.

**On-screen (ES):** *Se ha derramado un líquido cerca del banco. ¿Cuál es tu PRIMERA acción?*
- A) Olerlo para identificar qué es.
- ✓ B) Consultar la FDS para identificar el producto y sus peligros.
- C) Empezar a limpiarlo de inmediato.
- D) Ignorarlo — probablemente es agua.

**VO (EN):** "Something's spilled. Before you touch anything — how do you find out what it is?"
**VO (ES):** "Algo se ha derramado. Antes de tocar nada — ¿cómo averiguas qué es?"
**Correct:** EN "Right. The SDS tells you what it is and how to handle it. Never identify a
chemical by sight, smell or touch." · ES "Correcto. La FDS te dice qué es y cómo manejarlo.
Nunca identifiques un producto por la vista, el olor o el tacto."
**Consequence:** EN "You leaned in to smell it — the vapour was toxic. Never identify a spill
by smell. Try again." · ES "Te acercaste a olerlo — el vapor era tóxico. Nunca identifiques
un derrame por el olor. Inténtalo de nuevo."
**Dev notes:** `critStep1_ok`. Multiple choice (or hotspot on the SDS binder). Correct →
show `Correct`, set `critStep1_ok=True`. Wrong → show `Consequence`, `errorCount+1`,
`firstTryFail=True`.

### Slide 3.2 — Step 2 · Alert & evacuate
**On-screen (EN):** *The SDS shows a hazardous, volatile reagent. What now?*
- ✓ A) Alert the people nearby and clear the area.
- B) Quietly clean it before anyone notices.
- C) Keep working on your task.
- D) Open a window and carry on.

**On-screen (ES):** *La FDS indica un reactivo peligroso y volátil. ¿Y ahora?*
- ✓ A) Avisar a las personas cercanas y despejar la zona.
- B) Limpiarlo en silencio antes de que alguien lo note.
- C) Seguir con tu tarea.
- D) Abrir una ventana y continuar.

**VO (EN):** "It's hazardous and gives off vapour. What protects the people around you?"
**VO (ES):** "Es peligroso y desprende vapor. ¿Qué protege a las personas a tu alrededor?"
**Correct:** EN "Yes — people first. Alert and evacuate before you do anything else." ·
ES "Sí — primero las personas. Avisa y evacúa antes de hacer nada más."
**Consequence:** EN "You stayed quiet. The vapour spread and a colleague was exposed. Alert
and evacuate first. Try again." · ES "Te quedaste en silencio. El vapor se extendió y un
compañero quedó expuesto. Primero avisa y evacúa. Inténtalo de nuevo."
**Dev notes:** `critStep2_ok`. Branching decision.

### Slide 3.3 — Step 3 · Don the correct PPE
**On-screen (EN):** *You're ready to act. What do you put on BEFORE approaching the spill?
(Select all that apply.)*
- ✓ Chemical-resistant gloves · ✓ Safety goggles · ✓ Lab apron
- Approach with bare hands · Just a dust mask

**On-screen (ES):** *Estás listo para actuar. ¿Qué te pones ANTES de acercarte? (Selecciona
todas las que correspondan.)*
- ✓ Guantes resistentes a químicos · ✓ Gafas de seguridad · ✓ Bata de laboratorio
- Acercarte con las manos desnudas · Solo una mascarilla de polvo

**VO (EN):** "Protect yourself before you get close. Choose your PPE."
**VO (ES):** "Protégete antes de acercarte. Elige tu EPI."
**Correct:** EN "Full PPE on — now you're protected." · ES "EPI completo — ahora estás
protegido."
**Consequence:** EN "You reached in bare-handed and the reagent burned your skin. Don full
PPE first. Try again." · ES "Te acercaste con las manos desnudas y el reactivo te quemó la
piel. Primero ponte el EPI completo. Inténtalo de nuevo."
**Dev notes:** `critStep3_ok`. Multiple-response; correct only when all three PPE selected
and no wrong item.

### Slide 3.4 — Step 4 · Contain the spill
**On-screen (EN):** *PPE on. How do you stop the spill spreading?*
- ✓ A) Ring the spill with absorbent, working from the outside in.
- B) Wipe it toward the floor drain.
- C) Pour water on it to dilute it.
- D) Leave it and get a mop.

**On-screen (ES):** *Con el EPI puesto. ¿Cómo evitas que el derrame se extienda?*
- ✓ A) Rodear el derrame con absorbente, de afuera hacia adentro.
- B) Arrastrarlo hacia el desagüe del suelo.
- C) Echarle agua para diluirlo.
- D) Dejarlo e ir por un trapeador.

**VO (EN):** "Stop it spreading — and keep it away from drains."
**VO (ES):** "Evita que se extienda — y mantenlo lejos de los desagües."
**Correct:** EN "Contained. Ringing it from the outside in keeps it controlled." ·
ES "Contenido. Rodearlo de afuera hacia adentro lo mantiene bajo control."
**Consequence:** EN "You wiped toward the drain — the reagent entered the water system, a
reportable release. Contain it, away from drains. Try again." · ES "Lo arrastraste hacia el
desagüe — el reactivo entró en el sistema de agua, un vertido notificable. Conténlo, lejos
de los desagües. Inténtalo de nuevo."
**Dev notes:** `critStep4_ok`. Branching decision.

### Slide 3.5 — Step 5 · Use the correct spill kit
**On-screen (EN):** *The SDS says the reagent is water-reactive. Which kit do you use?*
- ✓ A) The dry / neutralizing kit for water-reactive chemicals.
- B) The universal water-based kit.
- C) Dilute it with plenty of water.
- D) Whichever kit is closest.

**On-screen (ES):** *La FDS indica que el reactivo es reactivo al agua. ¿Qué kit usas?*
- ✓ A) El kit seco / neutralizante para productos reactivos al agua.
- B) El kit universal a base de agua.
- C) Diluirlo con bastante agua.
- D) El kit que tengas más cerca.

**VO (EN):** "This one reacts with water. Choose the kit that's safe for it."
**VO (ES):** "Este reacciona con el agua. Elige el kit seguro para él."
**Correct:** EN "Exactly — the right kit for the reagent class. Safely absorbed." ·
ES "Exacto — el kit correcto para este tipo de reactivo. Absorbido con seguridad."
**Consequence:** EN "Water triggered a violent reaction; the spill spread and released fumes.
Match the kit to the reagent class. Try again." · ES "El agua provocó una reacción violenta;
el derrame se extendió y liberó vapores. Ajusta el kit al tipo de reactivo. Inténtalo de
nuevo."
**Dev notes:** `critStep5_ok`. Decision + strong consequence layer (this is the highest-risk
step).

### Slide 3.6 — Step 6 · Dispose of the waste
**On-screen (EN):** *The spill is absorbed. Where does the waste go?*
- ✓ A) The labelled hazardous-waste container.
- B) The general waste bin.
- C) The sink.
- D) Back on the shelf for now.

**On-screen (ES):** *El derrame está absorbido. ¿Dónde va el residuo?*
- ✓ A) El contenedor etiquetado de residuos peligrosos.
- B) La basura común.
- C) El fregadero.
- D) De vuelta al estante por ahora.

**VO (EN):** "The residue is still hazardous. Where does it belong?"
**VO (ES):** "El residuo sigue siendo peligroso. ¿Dónde debe ir?"
**Correct:** EN "Correct — labelled hazardous-waste container, every time." ·
ES "Correcto — contenedor etiquetado de residuos peligrosos, siempre."
**Consequence:** EN "General waste can't take hazardous residue — that's a reportable
violation. Use the hazardous-waste container. Try again." · ES "La basura común no admite
residuos peligrosos — es una infracción notificable. Usa el contenedor de residuos
peligrosos. Inténtalo de nuevo."
**Dev notes:** `critStep6_ok`. Drag-and-drop (drag the waste bag to the correct bin).

### Slide 3.7 — Step 7 · Document & report *(important, not a hard-fail)*
**On-screen (EN):** *The area is safe. What is the final step?*
- ✓ A) Complete the incident log and notify your supervisor.
- B) Skip the paperwork — it's handled.
- C) Tell a colleague verbally and move on.

**On-screen (ES):** *La zona es segura. ¿Cuál es el paso final?*
- ✓ A) Completar el registro del incidente y avisar a tu supervisor.
- B) Saltarte el papeleo — ya está resuelto.
- C) Comentárselo a un compañero de palabra y seguir.

**VO (EN):** "One step left — and it's the one people forget."
**VO (ES):** "Queda un paso — y es el que la gente olvida."
**Correct:** EN "Done properly. The incident log closes the loop and improves the SOP." ·
ES "Bien hecho. El registro cierra el ciclo y mejora el procedimiento."
**Feedback (wrong):** EN "Without the report, the organisation can't learn or comply. Always
document." · ES "Sin el informe, la organización no puede aprender ni cumplir. Documenta
siempre."
**Dev notes:** scored question, **not** part of the zero-error gate (no `errorCount`). Normal
feedback, not a consequence loop.

---

## PART 6 · Avatar generation prompts

### A · Synthesia (standalone video, then embed)
1. **New video › blank 16:9.**
2. **Avatar:** choose a professional stock presenter (neutral, business-casual). Do **not**
   use a custom clone of a real person unless you have their written consent.
3. **Voice:** EN = a clear professional English voice; ES = a `es-ES` or `es-419` voice.
   Produce **two videos** (one per language) or a dual-language pair.
4. **Script:** paste the Part 3 spoken text for the chosen language. Add pauses with commas /
   full stops; use the pause control between sentences for pacing.
5. **Pronunciation:** add custom pronunciations — "SDS" (ess-dee-ess), "FDS" (efe-de-ese),
   "reagent", "PPE/EPI", "water-reactive".
6. **On-screen disclosure:** add a **text element** with the Part 3 caption, timed **0–4 s**,
   high-contrast lower third ("AI-generated presenter").
7. **Background:** clean lab or neutral studio; add a name strip "AI Presenter".
8. **Captions:** enable subtitles → download **.vtt** (and .srt).
9. **Export:** 1080p `.mp4`. Keep the project so you can re-generate if the script changes.

### B · Articulate avatars (AI Assistant, powered by Synthesia) — inside Rise/Storyline
> Articulate 360's AI Assistant now generates avatar videos (Synthesia-powered) directly in
> the authoring tool. Exact labels evolve — [VERIFY current UI in your 360 subscription].
1. **Rise:** open the lesson › insert a **block** › choose the **AI/Video** option › select
   **Generate avatar video** (AI Assistant).
   **Storyline:** slide › **AI Assistant** › avatar/video generation.
2. **Choose avatar + language** (EN or ES voice) from the built-in set.
3. **Paste the Part 3 script** for that language. Generate, preview, and insert the block.
4. **Captions** are generated automatically — keep them on.
5. Below the video add a **Text block** repeating the written disclosure (first-exposure
   transparency), and put the transparency note in the course credits too.
6. Advantages: stays inside your course, auto-captioned, no separate upload. Limitation:
   fewer avatars/controls than full Synthesia, and availability depends on your plan.

> Whichever tool you use, the **Art. 50 disclosure stays the same** and must appear at first
> exposure. A clone of a real person additionally requires that person's consent.

---

## PART 7 · Articulate 360 AI generator prompts (fast path)

**Why this exists:** Articulate 360 AI ("Welcome back" dashboard → *Course / Guide /
Interactive Video / Scenario / Training Deck*) generates a Rise course from a goal prompt in
minutes — far faster than hand-building in Storyline. Use it to produce the **shell + first
draft fast**, then refine. Keep **Storyline** only for the strict *variable-based zero-error
gate*, which the AI flow can't enforce.

> **Tip:** click the **paperclip / link** on the dashboard and attach this file (or the SOP)
> as source content, then paste the matching prompt below into *"What's the goal for this
> course?"*. Use **Apply brand** to pull in your Ocean Ink colours/fonts.

### Prompt A — "Course" type (full module)
> Create a workplace health-and-safety compliance course titled **"Chemical Spill Response
> SOP"** for adult laboratory technicians (new hires and refresher), experienced on the
> bench, bilingual English/Spanish, taken on desktop and tablet, ~15 minutes, mandatory with
> annual recertification.
>
> Goal / terminal objective: given a simulated lab chemical spill and the available kits, the
> technician performs all seven SOP steps in the correct order with zero critical errors.
>
> Structure the course as: (1) a short AI-presenter welcome; (2) a "based on a real incident"
> hook that makes the stakes real; (3) a debrief of what went wrong; (4) a bilingual key-terms
> glossary (SDS/FDS, PPE/EPI, hazardous waste, containment); (5) a practice scenario covering
> the seven steps — Assess (consult the SDS, never touch/smell), Alert & evacuate, Don PPE,
> Contain away from drains, Use the correct kit for the reagent class, Dispose in the
> hazardous-waste container, Document & report; (6) ungraded knowledge checks; (7) a graded
> quiz where the critical steps must be answered correctly; (8) a 3-item reaction survey; (9) a
> downloadable job aid.
>
> Tone: clear, professional, plain-language adult workplace learning — not marketing. Write to
> WCAG 2.1 AA (alt text, captions, no colour-only meaning). Emphasise that a wrong critical
> choice shows its real-world consequence, then lets the learner try again.
>
> LANGUAGE: Generate this as a SINGLE-LANGUAGE **English** course. I will create the Spanish
> version separately (same prompt in Spanish). Do NOT put two languages on the same screen —
> the learner selects one language and sees only that language.

### Prompt B — "Scenario" type (the branching decision engine)
> Build a branching decision scenario for lab technicians responding to a chemical spill. The
> learner plays a technician who discovers a spill and must follow the SOP exactly. Create one
> decision point per step: (1) identify the spill — correct = consult the SDS; wrong = smell or
> touch it; (2) correct = alert and evacuate; wrong = clean it quietly; (3) correct = don full
> PPE first; wrong = approach bare-handed; (4) correct = contain with absorbent away from
> drains; wrong = wipe toward the drain; (5) the reagent is water-reactive — correct = the dry
> neutralizing kit; wrong = the water-based kit; (6) correct = hazardous-waste container; wrong
> = general bin; (7) correct = complete the incident log and notify the supervisor.
>
> For every wrong choice, show a realistic consequence (a colleague exposed, a chemical burn, a
> violent reaction, a reportable release) and route the learner back to retry that decision —
> the scenario is passed only when all critical steps are correct with zero errors. Keep
> feedback supportive, never punitive. LANGUAGE: generate a SINGLE-LANGUAGE English scenario;
> I will create the Spanish version separately. Never show two languages on the same screen.

### Prompt C — "Interactive Video" type (the reenactment / avatar intro)
> Create a short interactive-video intro for the spill-response course. Open with a 45–60s
> AI-presenter welcome, then a dramatized "based on a real incident" scene (anonymized) that
> shows a technician skipping the SOP and getting hurt. Add 1–2 reflective pause-points ("What
> should she have done first?"). Display an on-screen disclosure for the first 4 seconds: "AI-
> generated avatar / voices. Dramatization — names and details changed." LANGUAGE: single-
> language English; create the Spanish version separately — one language on screen at a time.

### What the AI flow can and can't do
- ✅ Fast full-course shell, lessons, knowledge checks, a branching **Scenario**, auto-captions,
  brand styling, EN/ES drafting.
- ⚠️ It does **not** enforce a true variable-based 100 % mastery gate (`errorCount = 0` across
  steps). The Scenario's branching gives consequence-and-retry, which is close; for a strict,
  auditable zero-error record, build that one piece in **Storyline** and embed it.
- Always review and edit AI output (content accuracy, bias, SOP fidelity) — your editorial
  responsibility, and the basis of the Art. 50 note below.

---

## PART 8 · Final quiz — directions (paste into Articulate 360 AI "Quiz instructions")

**Kirkpatrick note:** a quiz measures **Level 2 (Learning)**. You cannot *measure* L3
(behaviour) or L4 (results) inside a quiz — so this builds a strong L2 **zero-error** quiz,
adds one **L1 reaction** item, and frames questions at the **L3 "what would you do on the
job"** level so results point toward transfer. The true 100 %-on-critical gate stays in
Storyline; the AI quiz just sets a high pass mark.

> Create a final assessment for the Chemical Spill Response SOP course.
>
> **Purpose (Kirkpatrick):** measures Learning (L2) — can the technician apply the SOP.
> Write at the application level (what they would DO on the job), not recall, so results point
> toward behaviour (L3). Include ONE unscored reaction item at the end (L1): "How confident
> are you that you could respond to a real spill correctly?"
>
> **Content — one scenario question per critical step (7):** 1 Assess → consult the SDS
> (distractors: smell/touch, wipe); 2 Alert & evacuate (distractors: clean quietly, keep
> working); 3 Don PPE first (distractor: bare-handed); 4 Contain away from drains (distractor:
> wipe to drain); 5 water-reactive → dry/neutralizing kit (distractor: water-based/water);
> 6 hazardous-waste container (distractor: general bin/sink); 7 Document & report. Use
> realistic distractors from common real mistakes.
>
> **Difficulty & zero-error:** steps 1–6 are critical — zero-error (100 % mastery); passing
> score = 100 %. For each critical question, feedback shows the real-world consequence of the
> wrong answer, then restates the correct action. Mix MC, multiple-response (PPE), matching.
> Plain professional adult tone.
>
> **Language:** generate the quiz in English only; create the Spanish quiz separately. One
> language per version — never both on the same screen.
> **Accessibility:** no colour-only cues; screen-reader-friendly; alt text for any image.

- The AI quiz is percentage-based → "100 % to pass" = the zero-error rule at course level.
- For an auditable per-step gate (`errorCount = 0`), keep it in the Storyline scenario.
- If possible: passing score = 100 %, allow retries with feedback (learn from the consequence).

---

## PART 9 · Remaining course content (makes both courses content-complete)

Source text (EN/ES). Build each as its own single-language version. Every piece reinforces the
portfolio goal: the learner *follows the SOP*, and the design *proves it*.

### 9.1 Language launch page (in front of the two versions)
EN: **Choose your language** — [English] [Español]
ES: **Elige tu idioma** — [English] [Español]

### 9.2 Debrief lesson (after the reenactment, before practice)
Bridges the story to the procedure by mapping each mistake to the SOP step that would have
prevented it — this is the "why the SOP exists" moment.

EN:
> **What went wrong — and what the SOP says.** The injury wasn't bad luck; it was five skipped
> steps.
> • She never checked the SDS → Step 1: Assess before you act.
> • She didn't alert or evacuate → Step 2: People first.
> • She reached in bare-handed → Step 3: PPE before approach.
> • She wiped toward the spread → Step 4: Contain, away from drains.
> • Water on a water-reactive reagent → Step 5: The right kit for the chemical.
> The SOP is the difference between a near-miss and three weeks of recovery. Now you'll walk
> every step.

ES:
> **Qué salió mal — y qué dice el procedimiento.** La lesión no fue mala suerte; fueron cinco
> pasos omitidos.
> • Nunca consultó la FDS → Paso 1: Evalúa antes de actuar.
> • No avisó ni evacuó → Paso 2: Primero las personas.
> • Se acercó con las manos desnudas → Paso 3: EPI antes de acercarte.
> • Arrastró el derrame → Paso 4: Contén, lejos de los desagües.
> • Agua sobre un reactivo reactivo al agua → Paso 5: El kit correcto para el producto.
> El procedimiento es la diferencia entre un casi-accidente y tres semanas de recuperación.
> Ahora recorrerás cada paso.

### 9.3 Results / feedback messages
PASS — EN:
> **Certified: zero critical errors.** You followed the SOP exactly — the way it protects you
> and everyone in the lab. Your first-attempt result has been recorded. Keep the job aid at
> your bench.
PASS — ES:
> **Certificado: cero errores críticos.** Seguiste el procedimiento al pie de la letra — como
> debe ser para protegerte a ti y a todo el laboratorio. Se ha registrado tu resultado del
> primer intento. Mantén la guía rápida en tu puesto.

NOT YET — EN:
> **Not yet — and that's how we keep it safe here.** A critical step was missed. Review the
> consequence, then repeat the scenario until every critical step is correct with zero errors.
> On the job there are no retries — that's why we practise until it's automatic.
NOT YET — ES:
> **Todavía no — y así mantenemos la seguridad aquí.** Se omitió un paso crítico. Revisa la
> consecuencia y repite el escenario hasta acertar cada paso crítico con cero errores. En el
> trabajo real no hay segundos intentos — por eso practicamos hasta que sea automático.

### 9.4 Job aid — bench quick-reference (one page, downloadable, non-gated)
EN — **Chemical Spill Response — 7 steps**
> 1. ASSESS — consult the SDS; never touch or smell. 2. ALERT & EVACUATE — people first.
> 3. PPE — gloves, goggles, apron before you approach. 4. CONTAIN — ring with absorbent, away
> from drains. 5. CORRECT KIT — match the kit to the chemical (water-reactive = dry kit).
> 6. DISPOSE — labelled hazardous-waste container only. 7. DOCUMENT — incident log + supervisor.
> *If unsure what it is, STOP and check the SDS.*
ES — **Respuesta a derrames químicos — 7 pasos**
> 1. EVALÚA — consulta la FDS; nunca toques ni huelas. 2. AVISA Y EVACÚA — primero las personas.
> 3. EPI — guantes, gafas, bata antes de acercarte. 4. CONTÉN — rodea con absorbente, lejos de
> los desagües. 5. KIT CORRECTO — ajusta el kit al producto (reactivo al agua = kit seco).
> 6. DESECHA — solo contenedor etiquetado de residuos peligrosos. 7. DOCUMENTA — registro +
> supervisor. *Si no sabes qué es, DETENTE y consulta la FDS.*

### 9.5 Summary / close
EN:
> **You followed the SOP — now make it a habit.** Seven steps, in order, every time. The one
> that saves you: when in doubt, check the SDS and never identify a spill by sight, smell or
> touch. Download your job aid and keep it visible.
ES:
> **Seguiste el procedimiento — ahora conviértelo en hábito.** Siete pasos, en orden, siempre.
> El que te salva: ante la duda, consulta la FDS y nunca identifiques un derrame por la vista,
> el olor o el tacto. Descarga tu guía rápida y mantenla a la vista.

---

## Portfolio framing — how this proves candidate suitability
This course is evidence for the Senior Instructional Designer role. Direct mapping:

| Job responsibility | Evidence in this build |
|---|---|
| Conduct job/task/performance analysis → objectives | DIF task analysis → Mager/Bloom objectives (Design) |
| Design complex technical instruction across media | Storyline sim + Rise course + AI avatar + reenactment |
| Develop criteria to evaluate effectiveness | Zero-error gate + Kirkpatrick L1–L4 + metrics |
| Partner/consult; agree outcomes & success metrics | Training strategy + agreed success metrics |
| Use evaluation to improve; share lessons | Closing-the-loop (L2↔L3 diagnosis) |
| Oversee vendors / translate programs | Bilingual EN/ES, language-selectable; storyboard precise enough to brief a vendor |
| EHS adherence | The SOP content itself + accessibility (WCAG AA) |

**The thesis for the hiring manager:** *"I don't just make courses — I design training that
provably changes on-the-job behaviour, measured against a zero-error compliance standard, in
two languages, to WCAG AA."*

---

© 2026 Ana Eslava-Graterol · profeanaeslava · All rights reserved.

_Transparency note: developed with the assistance of generative AI; reviewed, edited and
approved under the editorial responsibility of Ana Eslava-Graterol, instructional designer
registered as a self-employed professional in Spain (in the spirit of the EU AI Act, Art. 50
— Regulation (EU) 2024/1689)._
