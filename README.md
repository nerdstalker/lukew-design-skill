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

## Using it outside Claude Code

The skill is plain markdown with no runtime dependencies, so any AI harness that accepts context files can use it. The pattern is always the same: get `SKILL.md` into context and make sure the assistant can reach the `references/` files (inline them, upload them, or let the agent read them from disk).

**Codex CLI** — clone the repo anywhere, then point to it from your `AGENTS.md`:

```markdown
## Design reviews
For any UI/UX review or design advice, first read
~/lukew-design-skill/SKILL.md and follow it, including reading the
references/ files it says apply to the domain under review.
```

Or make it an on-demand slash prompt: copy `SKILL.md` to `~/.codex/prompts/lukew.md` (and keep the repo cloned so the reference paths resolve), then invoke `/lukew` when you want a review.

**ChatGPT** — create a Project (or a custom GPT) and upload the five `.md` files. Set the project instructions to: "For design reviews, follow SKILL.md exactly, consulting the uploaded reference files it names for the relevant domain." Since ChatGPT can't read files off your disk mid-chat, uploading all five up front replaces the on-demand loading.

**Cursor** — save `SKILL.md` as a rule at `.cursor/rules/lukew-design.mdc` with `description`-based (agent-requested) triggering, and keep the repo in your workspace so the agent can open the references.

**GitHub Copilot** — add the same pointer paragraph as the Codex example to `.github/copilot-instructions.md`, with the repo cloned inside the workspace.

**Any other agent** — worst case, concatenate everything into one file and paste it as a system prompt:

```bash
cat SKILL.md references/*.md > lukew-design-full.md
```

That's ~700 lines of markdown — well within any modern model's context window.

## Sources

- *Mobile First* (A Book Apart, 2011)
- *Web Form Design: Filling in the Blanks* (Rosenfeld Media, 2008)
- "Sign Up Forms Must Die" (A List Apart, 2008) and the inline-validation study with Etre (A List Apart, 2009)
- Talks: "Obvious Always Wins" (2017), "Mind the Gap" (2019), "How AI Ate My Website" (2024–2025), Conversions@Google mobile workshops
- [lukew.com](https://www.lukew.com) writings, including the 2023–2026 AI product design series
- [Ask LukeW](https://www.lukew.com/ask/) — his own AI interface over his full archive; the skill consults it for questions the bundled references don't cover

## License

MIT — see [LICENSE](LICENSE). The distilled principles remain the intellectual work of Luke Wroblewski; go read [lukew.com](https://www.lukew.com) and buy his books.
