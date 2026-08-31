# lukew-design

A [Claude Code](https://claude.com/claude-code) skill that reviews and improves UI/UX design work through the lens of **Luke Wroblewski's** published principles — mobile-first design, web form design, obvious-over-clever interactions, data-informed design, and AI product interface patterns.

> **Unofficial.** This skill is based on Luke Wroblewski's public writing, books, and talks ([lukew.com](https://www.lukew.com), *Mobile First*, *Web Form Design*). It is not affiliated with, created by, or endorsed by Luke Wroblewski. All principles are attributed to their published sources.

## What it does

Once installed, Claude uses this skill whenever you ask for a design review, UX critique, or design advice. It works in three modes:

1. **Advise** — opinionated guidance while you're designing, grounded in published principles rather than taste.
2. **Critique** — a structured review of a screen, form, flow, or codebase, with findings ordered by user impact, each tied to the principle it violates and its source.
3. **Apply** — with your approval, it implements the agreed fixes in your code.

Example prompts:

- "Review this sign-up form" (with a screenshot or the component code)
- "Critique the mobile layout of my landing page"
- "What would LukeW say about this checkout flow?"
- "Review the chat UI of my AI app"

## What's inside

```
lukew-design/
├── SKILL.md                     # workflow, core philosophy, output format
└── references/
    ├── forms.md                 # Web Form Design: labels, validation, errors, gradual engagement
    ├── mobile.md                # Mobile First: thumb zones, touch targets, content-first
    ├── data-informed.md         # Mind the Gap: metrics, the three gaps, find-the-bandaid
    └── ai-interfaces.md         # 2023–2026 AI product patterns: citations, agent UIs, steering
```

The reference files load on demand, so the skill stays lightweight in context until a review touches that domain.

## Install

**Claude Code (personal, all projects):**

```bash
git clone https://github.com/nerdstalker/lukew-design-skill.git ~/.claude/skills/lukew-design
```

**Claude Code (single project):** clone into `.claude/skills/lukew-design` inside the project instead.

Then just ask for a design review — the skill triggers automatically.

## Sources

- *Mobile First* (A Book Apart, 2011)
- *Web Form Design: Filling in the Blanks* (Rosenfeld Media, 2008)
- "Sign Up Forms Must Die" (A List Apart, 2008) and the inline-validation study with Etre (A List Apart, 2009)
- Talks: "Obvious Always Wins" (2017), "Mind the Gap" (2019), "How AI Ate My Website" (2024–2025), Conversions@Google mobile workshops
- [lukew.com](https://www.lukew.com) writings, including the 2023–2026 AI product design series

## License

MIT — see [LICENSE](LICENSE). The distilled principles remain the intellectual work of Luke Wroblewski; go read [lukew.com](https://www.lukew.com) and buy his books.
