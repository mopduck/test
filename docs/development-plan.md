# Development Plan

Date: 2026-06-13

This repository tests a GitHub-native collaboration loop between `@mopduck001` and `@mopduck`.

## Feature

Feature name: collaboration handoff smoke test

Goal: prove that framework setup, task assignment, PR handoff, pre-CR, human approval, and post-approval work can be tracked through GitHub.

## Role Contract

| Step | Owner | Required action | Notification target | Evidence |
| --- | --- | --- | --- | --- |
| Framework setup | `@mopduck001` | Confirm or adjust this plan, keep the framework simple, and split work into Task 1 and Task 2. | `@mopduck` | Comment on the Task 1 issue. |
| Task 1 | `@mopduck` | Implement the first scoped change and open a PR to `master`. | `@mopduck001` | PR with `@mopduck001` review request. |
| PR pre-CR | `@mopduck001` | Review Task 1 PR before human approval. | Human approver | PR comment: `CR passed: ready for human approval`. |
| Human approval | Manual reviewer | Approve Task 2 start after pre-CR passes. | `@mopduck` | Comment: `Approved: Task 2 can start`. |
| Task 2 | `@mopduck` | Start the second scoped change only after approval. | `@mopduck001` | Task 2 PR links the approval comment. |

## Task Breakdown

### Task 1: first developer handoff

Owner: `@mopduck`

Acceptance criteria:

- Create a branch named `mopduck/task1`.
- Add `src/task1-status.md` with a short completion note.
- Update `docs/run-log.md` with the Task 1 completion event.
- Open a PR to `master`.
- In the PR body, mention `@mopduck001` and request pre-CR.

### Task 2: approval-gated follow-up

Owner: `@mopduck`

Blocked by:

- Task 1 PR pre-CR pass from `@mopduck001`
- Manual approval comment: `Approved: Task 2 can start`

Acceptance criteria:

- Create a branch named `mopduck/task2`.
- Add `src/task2-status.md` with a link to the approval evidence.
- Update `docs/run-log.md` with the Task 2 start and completion events.
- Open a PR to `master` that links the approval comment.

## Notification Protocol

Use GitHub as the source of truth:

- Assignment when available.
- `role:*` and `phase:*` labels for routing.
- `@mention` comments for handoff notifications.
- PR review request for `@mopduck001` pre-CR.
- Explicit manual approval comment before Task 2 starts.

If `@mopduck001` has not accepted the collaborator invitation yet, use issue mentions first and add the assignee after the invitation is accepted.
