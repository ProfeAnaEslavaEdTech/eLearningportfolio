# Chemical Spill Response SOP — Storyline Activity Design

## Project brief
- **Tool:** Articulate Storyline 360, exported as SCORM 2004 (+ xAPI hook)
- **Domain:** Health & Safety compliance — SOP for a Chemical Lab (not language learning)
- **Evaluation model:** Kirkpatrick, with a "zero-error" (100%-mastery) gate
- **Purpose:** portfolio showpiece
- **Languages:** EN / ES (bilingual)
- **Status:** illustrative scenario — swap in real SOP when ready

---

## ADDIE course design — *Chemical Spill Response SOP*

### A — ANALYSIS

**Performance analysis:** Incidents trace to technicians not executing the spill
SOP correctly under pressure — a genuine skill + knowledge gap, so training is
justified. Non-training complements: laminated job aid at each bench + quarterly drill.

**Audience:** New & refresher lab technicians; experienced, mixed EN/ES, desktop +
tablet, mandatory annual recertification.

**Job/Task Analysis + DIF (D = Difficulty, I = Importance, F = Frequency; H/M/L):**

| # | SOP step | D | I | F | Critical? | Common error | Treatment |
|---|---|---|---|---|---|---|---|
| 1 | Assess spill (SDS, volume, hazard) | M | H | L | ✅ | Smell/touch to identify | Course + job aid |
| 2 | Alert & evacuate area | L | H | L | ✅ | Clean quietly, no alert | Course + drill |
| 3 | Don correct PPE | L | H | M | ✅ | Bare-handed kit grab | Course + job aid |
| 4 | Contain (ring the spill) | M | H | L | ✅ | Wipe toward drain | Course + practice |
| 5 | Neutralize/absorb — correct kit | H | H | L | ✅ | Water on water-reactive | Course + mastery |
| 6 | Dispose in hazardous-waste container | L | H | M | ✅ | General waste bin | Course + job aid |
| 7 | Document & report | L | M | M | ⚠️ | Skip paperwork | Job aid + reminder |

Steps 1–6 form the zero-error gate; step 7 is important but not a hard-fail.

### D — DESIGN

**Terminal objective:** Given a simulated lab chemical spill and the available kits,
the technician performs all seven SOP steps in correct order with **zero critical errors**.

**Objectives → assessment map:**

| Enabling objective (Mager) | Bloom | Step | Assessment item | Pass rule |
|---|---|---|---|---|
| Identify hazard via SDS without contact | Apply | 1 | Hotspot: "consult SDS" | pass/fail |
| Alert + evacuate as first physical action | Apply | 2 | Branching decision | pass/fail |
| Select correct PPE before approaching | Apply | 3 | Multi-response | pass/fail |
| Contain before cleanup, away from drains | Apply | 4 | Decision | pass/fail |
| Choose correct kit for the reagent class | Apply | 5 | Decision + consequence | pass/fail |
| Route waste to hazardous-waste container | Apply | 6 | Drag-to-bin | pass/fail |
| Complete incident log | Apply | 7 | Form check | scored (non-gate) |

**Zero-error logic (Pattern A, remediation loop):** wrong critical choice →
Consequence layer → "Try again" returns to that decision; `+1 errorCount`, flag
`firstTryFail`. Success = all 6 critical steps ok AND errorCount = 0. First-attempt
accuracy recorded separately as the true L2 signal.

**Kirkpatrick plan:**

| Level | What | How |
|---|---|---|
| L1 Reaction | ≥85% rate "relevant to my job" | 3-item in-course survey |
| L2 Learning | ≥95% reach zero-error mastery; report first-attempt accuracy | Results slide → LMS |
| L3 Behaviour | SOP adherence in ≥95% of bench audits within 90 days | xAPI + supervisor checklist |
| L4 Results | Reportable spill incidents ↓, faster time-to-competency | Ops metric (owner + baseline + quarterly) |

### D — DEVELOPMENT (Storyline build spec)

- **Scene map:** Welcome/Why → Pre-check → Scenario (slides 1–7, branching) → Results → Reaction survey → Job-aid download
- **Variables:** `errorCount` (Number, 0); `critStep1_ok…critStep6_ok` (T/F); `firstTryFail_sN` (T/F per step)
- **Per-decision triggers:** correct → `Correct` layer, set `critStepN_ok=True`, enable Next; wrong → `Consequence` layer, `errorCount+1`, `firstTryFail_sN=True`, "Try again" (Next stays locked)
- **Next button disabled** until required interaction fires
- **Accessibility:** captions on all VO, alt text on hazard images, logical tab order, no colour-only meaning, WCAG 2.1 AA contrast
- **SCORM 2004:** track by Results slide; report completion + success; passing = zero-error rule; resume/suspend on; test in SCORM Cloud

### I — IMPLEMENTATION

Pilot with 5–8 technicians → capture L1 + first-attempt L2 → fix weak steps →
publish to LMS, assign with annual recert, version-lock (SOP vX → .story vX →
package vX). Deploy bench job aid. Brief supervisors on observation checklist (L3).

### E — EVALUATION (closing the loop)

- Low first-attempt accuracy on a step → teaching/practice weak → fix the course
- High L2 but poor L3 audits → transfer/environment issue → job aids, drills, coaching
- Share lessons learned back to SOP owners each quarter

---

## 📖 Before you start — Key terms / Antes de empezar — Términos clave

*Optional reference, always accessible while taking the course (Storyline lightbox/
master-slide button, or Rise sidebar lesson / accordion). Not gated; kept off the
required-visited path and out of completion/Results tracking.*

| Acronym / Sigla | English | Español |
|---|---|---|
| **SDS** / **FDS** | **Safety Data Sheet** — the document listing a chemical's hazards and emergency measures. Always consult it to identify a spill *without touching or smelling it*. | **Ficha de Datos de Seguridad** — documento que indica los peligros de un producto químico y las medidas de emergencia. Consúltala siempre para identificar un derrame *sin tocarlo ni olerlo*. |
| **SOP** / **PNT** | **Standard Operating Procedure** — the official step-by-step procedure you must follow. | **Procedimiento Normalizado de Trabajo** — el procedimiento oficial paso a paso que debes seguir. |
| **PPE** / **EPI** | **Personal Protective Equipment** — gloves, goggles, apron. Put it on *before* approaching the spill. | **Equipo de Protección Individual** — guantes, gafas, bata. Póntelo *antes* de acercarte al derrame. |
| **Hazardous waste** / **Residuo peligroso** | Chemical waste that must go in a labelled hazardous-waste container, never the general bin. | Residuo químico que debe ir en un contenedor etiquetado de residuos peligrosos, nunca en la basura común. |
| **Containment** / **Contención** | Ringing the spill with absorbent to stop it spreading — done *before* cleanup. | Rodear el derrame con absorbente para evitar que se extienda — se hace *antes* de la limpieza. |
| **Incident report** / **Informe de incidente** | The log you complete after the spill is handled. | El registro que completas después de controlar el derrame. |

> 💡 **Tip / Consejo:** If you're ever unsure what a chemical is, the **SDS/FDS** is your first stop — never identify a spill by sight, smell, or touch.
> Si alguna vez dudas de qué es un producto químico, la **FDS** es tu primer recurso — nunca identifiques un derrame por la vista, el olor o el tacto.

### Designer-only acronyms (keep out of the learner-facing glossary)
ADDIE · SAM (Successive Approximation Model) · DIF (Difficulty, Importance, Frequency) ·
SCORM · xAPI · cmi5 · LRS (Learning Record Store) · LMS · VO (voice-over) ·
WCAG / AA · GMP / GxP · Kirkpatrick L1–L4

---

## Design decisions locked
- Zero-error logic: hard fail + remediation loop (Pattern A)
- Kirkpatrick: L1 + L2 in-module; xAPI hooks + plan for L3–L4
- Source: illustrative Chemical Spill Response scenario (swap in real SOP later)
- Glossary: optional reference, always accessible, non-gated, excluded from completion tracking

---

## Companion skill created
`compliance-training-architect` — an Instructional Design agent for technical/
compliance training in Articulate (Storyline/Rise), bilingual EN/ES, covering
ADDIE/SAM, job-task analysis, Kirkpatrick, zero-error assessment, SCORM/cmi5.
(Delivered as an installable .skill file; employer-neutral — no company name.)
