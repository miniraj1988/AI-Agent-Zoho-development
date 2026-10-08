# Architecture

## Agent-assisted delivery architecture

```
                    ┌─────────────────────┐
                    │       Claude        │
                    │ Plan / Decompose    │
                    │ Review / QA          │
                    └──────────┬──────────┘
                               │
                        Task files / plans
                               │
                               ▼
                    ┌─────────────────────┐
                    │       GitHub        │
                    │ Source of truth     │
                    │ Tasks + Results     │
                    └──────────┬──────────┘
                               │
                         Ready task
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Cursor Agent      │
                    │ Implement / Test    │
                    │ Browser / API work  │
                    └──────────┬──────────┘
                               │
                       Result + evidence
                               │
                               ▼
                    ┌─────────────────────┐
                    │       Claude        │
                    │ Review / Accept     │
                    │ or create fix task  │
                    └─────────────────────┘
```

## Future autonomous orchestration

The long-term target is:

```
Claude
  ↓
create TASK-###
  ↓
GitHub event / orchestrator / MCP
  ↓
Cursor Agent
  ↓
implementation + verification
  ↓
RESULT-###
  ↓
GitHub event / orchestrator / MCP
  ↓
Claude review
  ↓
approve OR create TASK-###-FIX
```

The human developer should primarily handle business decisions, credentials/permissions, ambiguous requirements, and exceptional failures.

## Source-of-truth rules

1. Business requirements belong in `docs/`.
2. Architecture decisions belong in `docs/`.
3. Implementation plans belong in `plans/`.
4. Actionable work belongs in `tasks/`.
5. Execution reports belong in `results/`.
6. Visual/test evidence belongs in `evidence/`.
7. Secrets never belong in GitHub.
