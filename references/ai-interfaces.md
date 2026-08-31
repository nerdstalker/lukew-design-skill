# AI Product & Agent Interface Design

From lukew.com's AI writing, 2023–2026 (index: lukew.com/ff?tag=ai), and the "How AI Ate My Website" talks. This is his most current body of work; cite the specific post when flagging a finding.

## Where the product sits: the evolution of AI products

("The Evolution of AI Products," lukew.com/ff/entry.asp?2096) Seven stages: ML behind the scenes → chat interfaces → retrieval-augmented products → tool use & foreground agents → background agents → agent-to-agent → beyond. Identify which stage the product under review occupies; the interface obligations differ:

- **Foreground agents** need *steering* controls — ways to redirect mid-task.
- **Background agents** need *monitoring* and exception-based notification — and as trust grows, the monitoring UI should recede.

## Durable patterns (lukew.com/ff/entry.asp?2145, Mar 2026)

Check AI product UIs for these; their absence is a finding:

1. **Citations** — sourced answers build trust and give users somewhere to go deeper.
2. **Suggested follow-up questions** — teach users what the system can do; kill the blank-prompt problem.
3. **Multimedia responses** — fix the "walls of text" failure; answer with images, video, structured layouts when the content calls for it.
4. **Collapsed tool actions** — agent tool use shown as a single line, expandable for detail.
5. **Separated process vs. results panes** — don't interleave the agent's work log with its deliverable.
6. **Visual task builders** for composing multi-step instructions.
7. **AI-driven onboarding** — show the product working on the user's own case instead of a tutorial.
8. **Spatial context awareness** — let users highlight/drag/point to direct the model at things.

## Chat interface usability (lukew.com/ff/entry.asp?2093)

People get lost in long chat streams. Remedies: collapse prior Q&A pairs; put tool outputs in separate panels; make outputs editable in place; offer timeline condensing; give sessions a home page listing outputs and files. A chat product that is one undifferentiated scroll is failing this.

## Showing agent work (lukew.com/ff/entry.asp?2142)

Users split between wanting results-only and wanting to see the work. Resolve with **progressive disclosure**: single-line progress summaries by default, expandable detail on demand. Aim for "progress indication over forced observation" — never make the user watch the work to get the result.

## Managing many agents (lukew.com/ff/entry.asp?2106)

The core job is letting people **start, steer, and stop** agents at scale. Familiar metaphors each break: inboxes don't scale, kanban column-moves are semantically unclear for agents, calendars fail for variable-duration or event-triggered agents, dashboards observe but don't control. Evaluate an agent-management UI against start/steer/stop coverage rather than metaphor familiarity. (He cites Scott Jenson: "Copy, extend, and finally, discovery of a new form.")

## Context and steering (lukew.com/ff/entry.asp?2155)

"Better context, better results." Brand, design, and domain guidelines belong in a versioned steering layer between AI tools and the output — maintainable by non-coders (designers, PMs), not buried in prompts individual users must repeat.

## Software for agents as users (lukew.com/ff/entry.asp?2111)

When the product will be consumed by agents, treat them as first-class users: fuller results and summaries than human-scannable snippets, frictionless resource creation, portable data (e.g., MCP).

## Quick checklist

1. Citations on generated answers
2. Suggested follow-ups present
3. Tool/agent work collapsed to one line, expandable
4. Process separated from results
5. Progressive disclosure of agent work; no forced observation
6. Foreground agents steerable; background agents exception-notify
7. Long chats: collapsing, output panels, session home
8. Shared context in a steering layer, not per-user prompt rituals
