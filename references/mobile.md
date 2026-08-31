# Mobile & Touch Design Principles

From *Mobile First* (A Book Apart, 2011), his Conversions@Google workshops ("Mobile Design Essentials"), and lukew.com writing.

## Why mobile first (the tripod)

1. **Growth** — design for where usage is, and where it's going.
2. **Constraint forces focus** — the small screen strips a product to the essence of what makes it work. A feature that can't justify its place on mobile is suspect everywhere.
3. **Capabilities enable innovation** — location, camera, touch, and sensors allow things desktop can't do. Ask what the design does with them.

## The one-thumb, one-eyeball test

Design for **one-handed use and partial attention**. If the core flow can't be completed with one thumb while the user is distracted, it fails. Apply this test to any mobile flow under review.

## Touch targets and thumb zones

- Minimum touch target ~**44×44 px** (finger-pad size); primary actions larger. Space targets to prevent mis-taps.
- Place primary, frequent actions in the natural **thumb arc** — the bottom of the screen. Put destructive actions out of easy reach.
- As screens grew, thumb-zone logic justified **bottom navigation** even against platform guidelines — the Google+ case ("Obvious Always Wins") showed visible bottom tabs multiplied feature usage versus a hamburger menu. Data can license breaking convention.

## No hover dependence

Touch has no hover. Any interaction gated on mouseover — revealed buttons, tooltips carrying essential info, hover menus — is broken on touch. Design tap-first; enhance with hover.

## Content first

- Open with content, not chrome. Minimize persistent navigation; surface it on demand.
- **One primary action per screen**; secondary actions visually subordinate.

## Input on mobile

- Right keyboard for the field: `type="tel"`, `type="email"`, `inputmode="numeric"`, autocomplete attributes.
- Top-aligned labels (narrow screens make side labels impossible).
- Prefer tapping over typing: steppers, segmented controls, and toggles over dropdowns and free text where the option set is small. Dropdowns are expensive on mobile (two taps + a scroll wheel).

## Performance is a design feature

Mobile networks are slow and unreliable. Payload size, image weight, and load order are UX decisions, not just engineering ones. Load content first; treat speed as part of the design review.

## Progressive enhancement

Start from the universally capable baseline; layer touch, sensors, and larger screens on top — rather than designing the ideal-conditions version and degrading.

## Quick checklist

1. Core flow passes one-thumb/one-eyeball
2. Touch targets ≥ 44px, spaced
3. Primary actions in the thumb zone; destructive actions out of it
4. Core navigation visible (no hamburger hiding primary features)
5. No hover-gated interactions
6. Content before chrome; one primary action per screen
7. Correct input types/keyboards; taps over typing
8. Performance budgeted; content loads first
