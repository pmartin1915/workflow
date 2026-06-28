# DISPATCH.md — Async Task Protocol for Claude Dispatch

> This file tells Claude what it can do autonomously when receiving tasks
> via Dispatch (phone → computer). Read CLAUDE.md first for full project context.

---

## Pre-Approved Tasks (No Confirmation Needed)

These tasks can be executed end-to-end without human approval.
Claude should commit results with a descriptive message.

| Task Keyword | Command | Success Criteria |
|-------------|---------|-----------------|
| `test` | Run full test suite | All tests pass, report results |
| `lint` | Run linter + fix | Zero lint errors, commit fixes |
| `typecheck` | Run TypeScript compiler | Zero type errors |
| `audit` | Run `pal codereview` on src/ | Report findings, fix MEDIUM+ issues |
| `deps` | Update non-major dependencies | Tests still pass after update, commit |
| `clean` | Remove dead code, unused imports | Tests still pass, commit |

## Guided Tasks (Plan First, Then Execute)

These require Claude to present a plan before executing.
If dispatched from phone, Claude should execute the plan and report what was done.

| Task Keyword | Description |
|-------------|-------------|
| `fix <issue>` | Diagnose and fix a specific bug |
| `refactor <target>` | Refactor a specific module or function |
| `add-tests <target>` | Generate test cases for untested code |
| `update-docs` | Update JSDoc, README, inline comments |

## Requires Confirmation (Never Auto-Execute)

These tasks are NEVER executed autonomously. Claude must wait for explicit approval.

- `deploy` — Build and push to any environment
- `publish` — npm publish, app store submission prep
- `delete` — Remove files, branches, or data
- `security` — Changes to auth, API keys, CORS, rate limiting
- `architecture` — Structural changes to module boundaries

## Dispatch Workflow

When Claude receives a Dispatch task:

1. **Orient** — Read CLAUDE.md, ai/STATE.md, check git status
2. **Classify** — Match task to Pre-Approved, Guided, or Confirmation-Required
3. **Execute** — Run the task per its classification
4. **Verify** — Run tests + typecheck after any code changes
5. **Report** — Summarize what was done, what changed, any issues found
6. **Commit** — If Pre-Approved or Guided task succeeded, commit with message:
   `dispatch: <task keyword> — <brief description>`

## Session State

After completing a Dispatch task, update:
- `ai/STATE.md` — What changed, current status
- `HANDOFF.md` — If the task uncovered follow-up work

## Project-Specific Overrides

<!-- Override or extend the defaults above for this specific project -->
<!-- Example:
| `generate` | Run code generation pipeline | Output files created, no errors |
| `migrate` | Run database migrations | Schema updated, tests pass |
-->
