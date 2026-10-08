# Agent Protocol

## Roles

### Claude

Claude owns:
- architecture decisions
- requirements interpretation
- implementation planning
- task decomposition
- acceptance criteria
- review of Cursor results
- deciding whether a task is complete

Claude should create bounded tasks rather than giving Cursor an unstructured project-wide instruction.

### Cursor Agent

Cursor owns:
- reading the assigned task and relevant project context
- implementation
- local/API/browser verification
- documenting exactly what changed
- capturing requested screenshots/evidence
- reporting blockers and deviations
- committing implementation changes

Cursor must not silently expand scope.

## Task lifecycle

`planned -> ready -> in_progress -> verification -> completed`

Alternative terminal states:

`blocked`
`needs_revision`
`cancelled`

The canonical status is stored in the task file and summarized in `ai/project-state.json`.

## Handoff contract

A task must contain:

- task ID
- objective
- background/context
- exact scope
- explicit non-goals
- files/components or Zoho areas expected to change
- acceptance criteria
- verification steps
- evidence requirements
- dependencies
- completion definition

## Cursor completion report

Every completed task should produce:

- task ID
- status
- summary
- implementation details
- files/configuration changed
- verification performed
- test results
- screenshots/evidence paths
- known issues
- deviations from plan
- commit SHA
- recommended next action

## Claude review

Claude reviews the result against the acceptance criteria.

A task is not complete merely because Cursor reports success. Completion requires the documented acceptance criteria and verification evidence to be satisfied.

## Communication without developer intervention

The intended future automation is:

Claude creates/updates task -> orchestrator detects ready task -> Cursor executes -> Cursor writes result -> Claude reviews -> next task/fix task is created.

GitHub is the durable communication layer. MCP/API integrations can be added as the orchestration layer.

## Zoho changes

For Zoho configuration:
1. Prefer API/MCP operations when reliable.
2. Use browser automation for UI-only configuration.
3. Capture screenshots when the task requires visual verification.
4. Record Zoho module/layout/function names in the result.
5. Never store secrets, OAuth tokens, passwords, or private credentials in this repository.
