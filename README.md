# test

GitHub collaboration smoke test for a two-role workflow.

## Roles

| Role | GitHub account | Responsibility | Completion signal |
| --- | --- | --- | --- |
| Framework owner | `@mopduck001` | Build the framework, split the feature, define the development plan, and notify `@mopduck` to start. | Comment on the Task 1 issue with `Framework ready: @mopduck start Task 1`. |
| Developer | `@mopduck` | Implement Task 1, open a PR, request pre-CR from `@mopduck001`, then wait for manual approval before Task 2. | PR opened for Task 1; Task 2 branch starts only after approval. |
| Human approver | Manual reviewer | Approve the handoff after `@mopduck001` says pre-CR passed. | Comment `Approved: Task 2 can start` on the approval issue or Task 1 PR. |

## Current Setup

- `@mopduck001` has been invited to the repository with write permission.
- Until that invitation is accepted, GitHub cannot assign issues to `@mopduck001`; role labels and mentions are used as the fallback notification.
- `.github/CODEOWNERS` requests `@mopduck001` for all file changes once the account has write access.
- The canonical plan is in [docs/development-plan.md](docs/development-plan.md).

## Workflow

1. `@mopduck001` accepts the repository invitation, reviews the plan, and completes framework ownership setup.
2. `@mopduck001` notifies `@mopduck` to start Task 1 through the Task 1 issue.
3. `@mopduck` implements Task 1 on a branch and opens a PR to `master`.
4. `@mopduck` requests `@mopduck001` for PR pre-CR.
5. `@mopduck001` completes pre-CR and comments `CR passed: ready for human approval`.
6. The human approver comments `Approved: Task 2 can start`.
7. `@mopduck` starts Task 2 only after that approval signal exists.

## Test Rule

Task 2 is blocked unless the Task 1 PR or approval issue contains both:

- a `CR passed: ready for human approval` comment from `@mopduck001`
- an `Approved: Task 2 can start` manual approval comment
