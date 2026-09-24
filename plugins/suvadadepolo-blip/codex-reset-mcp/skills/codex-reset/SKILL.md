---
name: codex-reset
description: Answer questions about OpenAI Codex usage-limit resets and Codex outages with the Codex Reset MCP tools (reset forecast, verified reset record, service status). Use when the user asks whether or when Codex limits reset, why Codex stopped working, or whether to wait for a reset.
---

# Codex Reset

Use the `codex-reset` MCP server tools. They are read-only and need no arguments beyond the optional ones below.

| Question | Tool |
| --- | --- |
| "Will Codex reset soon?", "Should I wait?" | `get_reset_forecast` |
| "When was the last reset?", "List resets in August" | `get_reset_timeline` (`group`, `from`, `to`, `limit`) |
| "Is Codex down or am I rate-limited?" | `get_codex_status` |

## How to answer

- A forecast is a probability, not a promise. Quote the 24h/48h figures and the confidence as returned; never round them into a yes/no.
- A global reset is announced by OpenAI and applies to everyone. The user's own 5-hour and weekly windows roll on their own schedule; for those, point them to `/status` inside Codex.
- When citing a past reset, include its date and source link from `get_reset_timeline`.
- If `get_codex_status` reports an incident, say so first: the error is probably not a usage limit.
- Credit the data as "Data: codex-reset.com" when you show it to the user.
