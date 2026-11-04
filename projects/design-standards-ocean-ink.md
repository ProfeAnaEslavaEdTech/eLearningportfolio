# Ocean Ink — Design & Accessibility Standards (repo backup)

Backup of the standing design rules for Ana Eslava-Graterol's work. The
authoritative copy lives in the **Ocean Ink Design System** skill
(claude.ai → Settings → Skills). This file is a git-persisted backup so the
rules survive even if the synced skill copy is overwritten.

---

## Accessibility rules (WCAG 2.1 AA)

- **New tab/window = visible cue (WCAG 3.2.5).** Any link or button that opens
  in a new tab or window carries a **visible** label saying so — e.g.
  `Go to Lesson 7 (opens in a new tab) →` /
  `Ir a la Lección 7 (abre en pestaña nueva) →`. The cue may be smaller/lighter
  but must be visible, not just `title`/`aria`. Pair with `target="_blank"` and
  `rel="noopener"`. Applies to e-learning buttons, document/PDF links and all
  external links. **Never open a new tab silently.**
- Body text ≥ 4.5:1 contrast; large text and UI ≥ 3:1.
- Focus ring: 3px outline, 2px offset, on every interactive element.
- Every state colour paired with a glyph + label (never colour-only).
- Charts/progress: never colour-only encoding; add labels, patterns or position.
- Dark theme built from the dark token column, never by inverting.
- Captions + audio scripts on all narrated media.

## Brand quick reference

- **Palette:** indigo `#3B5BD6` (primary), deep `#2A43A8`, gold `#E8A33D`
  (one accent per screen; `#9A5B00` for gold text on light), rose = progress only.
- **Type:** Fraunces (headings) + Inter (body) — both on Google Fonts.
- **Dark/light:** always ship both themes, each from its own token column.
- **Gradient:** hero bands only, one per page.

## Reusable "open in new tab" button (Ocean Ink)

```html
<a href="FULL_DESTINATION_URL" target="_blank" rel="noopener"
   style="display:inline-block;font-family:Inter,Arial,sans-serif;
          background:#3B5BD6;color:#fff;text-decoration:none;
          font-weight:600;font-size:16px;padding:14px 28px;
          border-radius:10px;box-shadow:0 3px 8px rgba(34,48,124,.25);">
  BUTTON LABEL <span style="font-weight:400;font-size:13px;opacity:.85">(opens in a new tab)</span> →
</a>
```

---

_Transparency (EU AI Act, Art. 50): compiled with the assistance of generative AI;
reviewed and approved under the editorial responsibility of Ana Eslava-Graterol._
