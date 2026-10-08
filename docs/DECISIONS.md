# Architecture Decision Log

## ADR-001 — GitHub is the durable shared state

**Decision:** Use GitHub as the persistent communication and audit layer between Claude and Cursor.

**Reason:** Plans, tasks, implementation results, evidence, and history remain available independently of a particular chat session.

## ADR-002 — Tasks are explicit contracts

**Decision:** Cursor receives bounded task files with acceptance criteria and verification steps.

**Reason:** This prevents ambiguous scope and makes autonomous execution safer.

## ADR-003 — Evidence is part of completion

**Decision:** UI/browser/Zoho changes may require screenshots or equivalent verification evidence.

**Reason:** A successful browser action does not necessarily prove the intended business state was achieved.

## ADR-004 — Separate planning from implementation

**Decision:** Claude owns planning/review; Cursor owns implementation/verification.

**Reason:** Separating responsibilities makes the workflow auditable and allows each agent to operate from the same repository state.
