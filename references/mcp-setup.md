# MCP setup and troubleshooting

Read this when archive tools are missing, a search fails, or the user asks to install or diagnose the connection. The skill folder and the MCP connection are separate dependencies. Installation commands live in [README.md](../README.md#install).

## Diagnose before declaring the archive unavailable

1. Discover available tools by their search capability, not just the literal `mcp__lukew__` prefix. Use the registered client's tools when available.
2. If missing, inspect only the relevant connection status through the host UI or CLI when permitted. For Codex, `codex mcp get lukew` checks that named registration; Claude Code offers `/mcp`. A differently named registration or plugin may expose the same endpoint, so one missing name is not proof that no connection exists. Do not dump unrelated configuration or credentials.
3. Report what the evidence establishes:

| Observation | Report and next action |
| --- | --- |
| No registration for this endpoint in the inspected client | **Not configured in this client.** Offer the matching setup command; obtain authorization before running it. |
| Registration exists but tools are absent | **Not loaded or not exposed in this session.** Inspect enabled state and startup errors when available; suggest reconnecting/restarting, without promising that restart alone will fix it. |
| Configuration cannot be inspected | **Tools are not exposed here; configuration status is unknown.** Ask for the relevant connection status if needed. |
| Search request returns an error | **Request failed**, with the sanitized error type (authentication, permission, timeout, transport, or server error). Do not infer a service-wide outage. |
| Search succeeds with zero results | **Connected; no matching sources.** Broaden the query before judging source coverage. |
| Search succeeds with results | **Live archive search verified.** Cite returned source URLs relevant to the task. |

After a configuration or session repair, retry the real search once. If it still fails, report the new evidence rather than looping or rewriting configuration repeatedly. Respect authentication prompts, network policy, and tool approvals; never disable restrictions to make the check pass.

## Protocol checks are not webpage checks

`https://www.lukew.com/mcp` is a Streamable HTTP MCP endpoint, not a normal article. A browser fetch or HTTP HEAD returning `405 Method Not Allowed` does not prove the server is down. An MCP client must initialize, discover the tools, and call a search according to the negotiated protocol.

If the host permits a direct MCP client, it can help separate endpoint connectivity from native tool registration. Use the discovered input schema and a generic, non-sensitive query such as `mobile form design` (limit 5). State that this was direct-client access; it does not prove the current agent's native tools are configured. Do not use another client to bypass denied access. No authentication material should be requested or printed for troubleshooting.

## Fallback and privacy

Send abstract design questions to the external archive, not the user's full draft, legal agreement, customer data, or private code. A successful search is retrieval evidence, not proof that its sources support every proposed design change.

If live retrieval cannot be completed, state **Reference-only review**, the observed limitation, and the setup/retry option before using bundled references. When the user explicitly requires live sources, ask before substituting fallback. Never call missing native tools an archive outage without evidence.

## Maintainer acceptance checks

Use isolated test profiles or disposable client configuration for fresh-install tests; do not remove a real user's connection to simulate failure. Record client/version, scenario, search outcome, and any untested cases. This checklist is a test plan, not a claim that all clients were exercised.

| Scenario | Expected behavior |
| --- | --- |
| Fresh Claude Code install | Complete folder is discovered, references resolve, HTTP server is registered, and a real search returns a title and URL. |
| Fresh Codex install | Skill discovery and MCP registration both succeed; a new/reconnected session runs a real search and returns a title and URL. |
| Skill present, no connection | Agent diagnoses missing configuration, offers setup without running it unapproved, and does not claim the server is down. |
| Configured connection, stale or disabled session | Agent distinguishes registration from tool availability and reports the relevant startup/enabled-state evidence. |
| Different host prefix or server alias | Agent finds tools by capability instead of rejecting a healthy connection based on its name. |
| Auth/permission failure or blocked network | Agent reports the actual failure, does not bypass controls, and offers bounded recovery or clearly labeled fallback. |
| Successful empty search | Agent reports no matches and broadens the query, not a connection failure. |
| User requires live review; retrieval fails | Agent reports the blocker and asks before substituting reference-only coverage. |
