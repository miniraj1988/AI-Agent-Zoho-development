# AI Agent Zoho Development

This repository is the shared source of truth for the Zoho development project and its AI-assisted delivery workflow.

## AI delivery model

- **Claude** — Architect, planner, task decomposer, reviewer, and QA authority.
- **Cursor Agent** — Implementation agent. Reads bounded tasks, changes the project, runs verification, and reports evidence.
- **GitHub** — Persistent shared state, plans, tasks, results, and implementation history.
- **Human developer** — Product/business decision maker and escalation point; should not be required for routine implementation handoffs.

## Repository map

| Path | Purpose |
|---|---|
| `docs/` | Stable project requirements, architecture, business processes, data model, and integration knowledge |
| `plans/` | Claude-created implementation plans and phases |
| `tasks/` | Bounded implementation tasks for Cursor |
| `results/` | Cursor execution reports and verification results |
| `evidence/` | Screenshots and other task evidence |
| `zoho/` | Zoho CRM configuration knowledge: modules, fields, workflows, blueprints, permissions, layouts |
| `deluge/` | Deluge functions/scripts and related notes |
| `tests/` | Test scenarios, acceptance tests, regression cases |
| `ai/` | Machine-readable agent state and communication protocol |

## Core workflow

1. Claude updates the project plan.
2. Claude creates a bounded `TASK-###.md` with scope, acceptance criteria, constraints, and verification requirements.
3. Cursor reads the task and project context.
4. Cursor implements only the requested scope.
5. Cursor runs the required verification.
6. Cursor stores a result report and evidence.
7. Claude reviews the result and either:
   - approves the task,
   - creates a follow-up/fix task, or
   - returns the task for correction.
8. Git history and the task/result files provide the audit trail.

## Agent communication contract

See:

- `ai/project-state.json`
- `ai/AGENT-PROTOCOL.md`
- `tasks/TASK-TEMPLATE.md`
- `results/RESULT-TEMPLATE.md`

## Important rule

Tasks must be **small, explicit, and independently verifiable**. Cursor should never infer a large amount of hidden scope from a short task.

## Zoho integration strategy

Prefer deterministic APIs/MCP where available. Use browser automation only where the required Zoho operation cannot be reliably performed through an API/tool. Browser-based changes must include screenshots or equivalent evidence when requested by the task.
