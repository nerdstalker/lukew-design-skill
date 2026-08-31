# Form Design Principles

From *Web Form Design: Filling in the Blanks* (Rosenfeld Media, 2008), organized by the book's own structure, supplemented by his "Best Practices for Form Design" deck (static.lukew.com/webforms_lukew.pdf), "Sign Up Forms Must Die" (A List Apart, 2008), and the 2009 inline-validation study with Etre (A List Apart). Where a guideline comes from secondary summaries rather than his own materials, it's flagged.

Foundational stance: **"Forms suck."** Nobody wants to fill in a form — they want what's on the other side: commerce (checkout), access (registration), or engagement (data input). Form friction is directly monetizable — he cites a two-field eBay fix worth ~$300K/month.

## The four governing principles (Ch. 1)

1. **Minimize the pain** — smart defaults, inline validation, forgiving inputs.
2. **Illuminate a clear path to completion.**
3. **Consider the context** — familiar vs. unfamiliar data; a one-time checkout and an expert's daily data-entry screen deserve different designs. Guidelines are "if your goals are X, try Y," not absolutes.
4. **Ensure consistent communication** — help, errors, and success messages speak with one voice despite many stakeholders.

Ground disputes in data: usability/field testing, support incidents, completion and drop-off tracking, eye tracking.

## Form organization (Ch. 2)

- Start from the user's goals and the natural **conversation**, never from mirroring the database schema. Order questions the way a competent human would ask them.
- For every field apply Caroline Jarrett's question protocol (cited in the book): **Keep, Cut, Postpone, or Explain**.
- **One page vs. multiple:** short or closely related content → one page. Distinct topics/stages (shipping → billing → review) → one topic per page with a progress indicator. Never split a coherent topic across pages just to look shorter — "avoid solutions that simply distribute a sign-up form's fields across multiple pages."
- **Minimum visual noise:** use the fewest visual elements needed to show relationships. Whitespace alone usually groups; boxes, rules, and bands each add fixations and impair scanning.
- **Security/privacy reassurance at the point of anxiety:** "We don't spam. Period." beside the email field; lock/security messaging beside card fields — not badges dumped in a footer.

## Path to completion (Ch. 3)

- **Name the form** so it matches the link that brought the user there.
- **Start pages:** when a form needs info people must look up (VIN, policy number), warn upfront and list what they'll need — before the form, not inside it.
- **Clear scan line:** a single left-aligned vertical line of label/field pairs; ~50–75% of an input's height as spacing between questions. Nothing should cross the scan line — two-column field layouts break it *and* break tabbing order.
- **Minimal distractions:** strip navigation, banners, and cross-sells from form pages; every distraction is an exit.
- **Progress indicators** on multi-page forms must accurately reflect the steps (no appearing/disappearing steps). For long forms, show progress **and allow saving**.
- **Tabbing:** many users tab between fields; ensure markup order follows the visual path.

## Labels (Ch. 4)

Based on Penzo's 2006 eye-tracking study, which he cites:

- **Top-aligned** — familiar data, fastest completion (label + field in one fixation); best for localization and mobile. Cost: vertical space.
- **Right-aligned** — when vertical space is constrained; nearly halves fixations vs. left-aligned. Cost: ragged edge makes label-column scanning hard.
- **Left-aligned** — unfamiliar/advanced data where you *want* people to slow down and scan the questions. Cost: weakest label-field association.
- **Placeholder-as-label:** acceptable only for one-or-two-field micro-forms (search, login). It vanishes on focus — never on longer forms. One of the most common failures in modern UIs; always flag it.
- Put required/optional indicators **with the label**, not floating at the field edge.

## Input fields (Ch. 5)

- **Required vs. optional:** mark whichever is rarer. If everything's required, say so once at the top. Text ("optional") beats symbols; the asterisk is acceptable for required. Better: **avoid optional fields altogether** — they're Cut/Postpone candidates.
- **Field length is an affordance** — match it to the expected answer (ZIP short, address long). When length can't carry meaning, keep lengths consistent.
- **Selection controls:** radios for a single visible choice among few (~≤6) options worth comparing; checkboxes for zero-or-more or a single binary; dropdowns for many familiar options (states, months) where space matters — poor when options need comparing (his later mobile-era hardening: "dropdowns should be the UI of last resort"); list boxes almost never.
- **Flexible/forgiving inputs:** accept `(555) 123-4444`, `555.123.4444`, `5551234444` in one field and normalize server-side — don't force a format or fragment into three boxes. If a constraint is unavoidable, put a format example adjacent to the field.

## Actions (Ch. 6)

- Primary actions (Submit, Continue, Save) vs. secondary (Cancel, Back, Reset). **Avoid secondary actions if at all possible**; if unavoidable, make the visual distinction unmistakable (prominent button vs. subdued link).
- **Never ship a Reset/Clear button** — used almost only by accident, and it destroys data.
- **Placement (his Etre eye-tracking test):** align the primary action with the input column's scan line. Worst tested layout: Cancel left, Submit far right — slower, scattered fixations, users felt less in control. Equal-weight adjacent buttons invite wrong-button errors.
- **Button labels describe what happens:** "Create Account & Continue," "Review Order" — not bare "Submit."
- **In-progress + double-submit:** long-running submissions show progress, and **the submit button disables after click** to prevent duplicates.
- **Agree and submit:** fold terms acceptance into the primary action ("By clicking Register you agree…") where legally possible, rather than an extra checkbox; if a checkbox is required, colocate it with the button.

## Help text (Ch. 7)

- Help is warranted only when data is unfamiliar, users may question *why* it's requested, there's a recommended format, or a request is optional.
- **Minimize the help needed** — a form requiring lots of help is itself broken.
- Visible help **directly adjacent** to the field beats everything. For heavier needs, escalate: automatic inline exposure on focus → user-activated "?" expansion → section-level help panel/dialog (reference-grade content only).

## Errors and success (Ch. 8)

- Errors: announce at the **top of the page** with strong contrast, **link each error to its field**, repeat the message at the field, and make remedies **actionable** (how to fix, not just "invalid").
- **Double the visual language** at error fields — at least two cues (color + icon/bold/text) so color alone never carries meaning (accessibility).
- **Never wipe or silently change entered data** through an error round-trip.
- Success: confirm **in context of the submitted data** (the updated record with a dismissable "saved" bar, or a transient highlight à la 37signals' yellow fade) — not an orphaned generic page.
- **No dead ends:** a success page offers the logical next steps (view what you created, continue shopping).

## Inline validation (Ch. 9 + the 2009 Etre study)

- Three jobs: **validate** answers, **suggest** valid input (autocomplete/disambiguation), and **communicate limits** (character countdown, password-strength meter).
- **Reserve confirmation validation for high-error-rate or unpredictable fields** (username availability, password rules). Green checkmarks on trivial fields go unnoticed and confuse.
- **Timing:** never flag a field before or while the user is still typing an open-ended answer — validate **on blur**. For strict-requirement fields, validating during typing works if delayed enough not to fire prematurely.
- Keep messages **persistent** (no fading) and **to the right of the field**.
- Measured results of doing it right: **+22% success, −22% errors, +31% satisfaction, 42% faster, −47% eye fixations.** (Note: study published 2009, after the book — it validates the chapter.)

## Unnecessary inputs (Ch. 10)

- **"The number one thing you can do to increase completion rates is to get rid of fields."** Challenge each field's business rationale; derive what you can (city/state from ZIP), postpone what can wait, capture implicitly what you already know.
- **Smart defaults:** pre-select the most common choice; **personalized defaults** for signed-in users (saved addresses, locale) — a returning user should never retype known data. Never default consequential opt-ins (marketing consent, paid add-ons).
- CAPTCHAs are friction from the user's perspective — prefer invisible/back-end abuse prevention; if unavoidable, make it forgiving. (Inferred from his examples, not a verbatim book rule.)

## Additional inputs & progressive disclosure (Ch. 11–12)

- Offer optional extras via **progressive disclosure**: inline additions ("Attach files…" links that expand in place), overlays for coherent optional subtasks. Most effective when **user-initiated**; keep one consistent disclosure idiom per form.
- **Selection-dependent inputs:** keep the mutually exclusive top-level choices visibly one set; **clearly associate dependent fields with their trigger** (indent/enclose under the selected option); **avoid layout "jumping"** that pushes the original options apart when a selection expands. Exposing every option's sub-fields at once scatters attention and inflates perceived length.

## Gradual engagement (Ch. 13) — "Sign Up Forms Must Die"

Sign-up forms demand commitment before demonstrating value. Instead let people **use the product first** and collect account data when it's actually needed — first use should teach the service by doing (edit the movie, then register to publish it). Rules: it's *not* just spreading sign-up fields across pages; auto-created accounts need clear recovery paths; it fits where experiential value can precede authentication. Expect fewer but more qualified sign-ups. **When reviewing any flow that opens with a registration wall, this is the first finding.**

## Markup & accessibility (cross-cutting)

`<label>` elements bound to inputs (screen readers + bigger tap targets); deliberate tab order; `<fieldset>`/`<legend>` for related groups; error states never conveyed by color alone.

## Quick checklist

1. Keep/Cut/Postpone/Explain every field; derive or prefill what you can
2. Conversation order; one topic per page; honest progress indicator
3. Single column, one clear scan line; no crossing elements; sane tab order
4. Top-aligned labels for familiar data; no placeholder-as-label
5. Mark the rarer of required/optional, with the label
6. Flexible input formats; right mobile keyboards; field length as affordance
7. Right selection control for the option count; dropdowns as last resort
8. Smart defaults — never for consequential opt-ins
9. Inline validation on high-error fields, on blur; persistent messages
10. Errors: top + field, actionable, doubled cues, data preserved
11. One distinct primary action on the scan line; kill Reset; descriptive label; disable after click
12. Success in context, no dead ends
13. Reassure at the point of anxiety (spam, card security)
14. Gradual engagement instead of a registration wall
