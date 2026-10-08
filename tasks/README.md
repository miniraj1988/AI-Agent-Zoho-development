# Tasks

Tasks are the executable contract between Claude and Cursor.

## Naming

`TASK-001.md`, `TASK-002.md`, etc.

Fix/rework tasks should use:

`TASK-001-FIX-01.md`

## Status

- `planned` — defined but not ready
- `ready` — Cursor can execute
- `in_progress`
- `verification`
- `completed`
- `needs_revision`
- `blocked`
- `cancelled`

Only one task should normally be the active implementation task unless parallel execution is explicitly planned.

## Rule

A task should be small enough that Cursor can complete and verify it without needing a new architectural decision.
