# AI Coordination

This directory defines the communication protocol between planning/review agents and implementation agents.

## Canonical files

- `AGENT-PROTOCOL.md` — rules
- `project-state.json` — current machine-readable state

## Future additions

Possible orchestration files/services:

- task queue
- webhook handlers
- Cursor execution adapter
- Claude review adapter
- MCP server
- GitHub Actions workflow
- retry/timeout policy
- audit log

The repository should remain usable even if the orchestration layer is temporarily unavailable.
