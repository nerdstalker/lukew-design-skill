# Form Design Principles

From *Web Form Design: Filling in the Blanks* (Rosenfeld Media, 2008), his form-design talks and slide decks (slideshare.net/lukew), and the 2009 inline-validation study with Etre (A List Apart).

Foundational stance: **"Forms suck."** Nobody wants to fill in a form — they want what's on the other side of it. The design goals are to minimize the pain, illuminate a clear path to completion, and communicate consistently.

## Before anything else: remove questions

Every input is a cost paid by the user. Audit each field: can it be **removed** (do we really need it?), **deferred** (collect later, once the user is invested?), or **inferred** (geo-detect country, derive city from postal code)? Only then optimize what remains. A shorter form beats a better-designed long one.

## Labels

- **Top-aligned labels** for familiar data (name, email, address): eye-tracking (Penzo, 2006) shows users capture label + input in one fixation — fastest completion. Also best for localization (label length varies) and mobile (narrow screens).
- **Right-aligned labels** when vertical space is genuinely constrained: still fast, but harder to scan the label column.
- **Left-aligned labels** only when data is unfamiliar and you *want* users to slow down and scan.
- **Never use placeholder text as the only label.** It vanishes on focus, forcing users to remember what the field asked. This is one of the most common failures in modern UIs — always flag it.

## Path to completion

- Single-column layout; one clear path down the page. Multi-column field layouts cause skipped fields and zig-zag scanning.
- On multi-step forms, show progress and what's ahead.
- Align the primary action with the input column so the path ends where the eye already is.

## Actions

- Visually distinguish the **primary action** (Submit, Continue) from secondary actions (Cancel, Back).
- Avoid secondary actions where possible. **Reset/Clear is almost always harmful** — it destroys user work and is clicked mostly by accident.

## Required vs. optional

If most fields are required, mark the **optional** ones instead of scattering asterisks everywhere. The rare case should carry the annotation.

## Inputs

- Field length should afford the expected answer (a ZIP field shouldn't be as wide as an address field).
- **Flexible inputs**: accept multiple formats (phone with or without dashes, spaces in card numbers) and normalize server-side. Rejecting a valid answer over formatting is a self-inflicted error.
- Group related fields with clear content groupings and headings.
- Use **selection-dependent inputs** (progressive disclosure): reveal follow-on fields only after the triggering choice; keep the exposed option set scannable.
- **Smart defaults**: pre-select or pre-fill the most likely answer (detected country, remembered data) — but never for consequential opt-ins (marketing consent, paid add-ons).

## Validation and errors

- **Inline validation** for confirmable answers (username availability, email format): his 2009 study with Etre measured **+22% success rate, −22% errors, 42% faster completion**. Validate on blur, not on every keystroke — don't flag a field the user is still typing in.
- Error states: announce at the top *and* at the field; explain **how to fix it**, not just that it's wrong; use color + icon + text (never color alone); **never wipe entered data**.
- Pair errors with equally clear success confirmation.

## Help text

Minimal, adjacent to the field it explains. Dynamic/on-demand help for occasional needs; persistent help text only for genuinely unfamiliar questions (why do you need my SSN?).

## Gradual engagement — "Sign Up Forms Must Die" (A List Apart, 2008)

Let people experience the product's value **before** demanding registration. Let them interact immediately; ask for the account once they have something worth saving. Expect fewer sign-ups but more qualified ones. When reviewing any flow that opens with a registration wall, this is the first finding.

## Quick checklist

1. Remove/defer/infer unnecessary questions
2. Top-aligned labels; no placeholder-as-label
3. Single column, visible path to completion
4. Mark optional, not required
5. Flexible input formats; right mobile keyboards
6. Smart defaults (never for consequential opt-ins)
7. Inline validation on confirmable fields, on blur
8. Errors: actionable, data-preserving, not color-only
9. One distinct primary action; kill Reset
10. Gradual engagement instead of a registration wall
