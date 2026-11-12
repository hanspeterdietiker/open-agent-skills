# Implementation loop — <Project>

<!-- Write this note in the project's documentation language. -->

**Status:** <current cycle and state>
**Priority:** <High | Medium | Low>
**Areas:** <e.g. Backend, Frontend, Infra>
**Updated on:** <YYYY-MM-DD>
**Plan:** <link to the technical plan with the tickets>
**Epic/Issue:** <identifier, if any>

## Goal and context

You are the agent responsible for implementing <project> according to the plan, ticket by ticket (TICKET-01 → TICKET-NN). Business rules come from <designs/specs>; the plan only orders them into steps.

Do not add requirements, rules, or scope expansions without user confirmation. Updating this record at the end of each cycle is already authorized.

### User decisions — <YYYY-MM-DD>

- **Gate:** <coordinator review | external review by ...>. A ticket closes only with an approved gate.
- **Branches:** <naming pattern; base of each branch; PR target>.
- **Commits:** <authorization per ticket | standing authorization recorded in ...>.
- **Execution:** <inline | workers via /orchestration>.
- **Who implements:** <coordinator | worker ...>. **Who reviews/decides the gate:** <...>.
- **Pace:** <stop at the end of each ticket>.
- **Extra records:** <deploy checklist, sprint report, paths>.

## Before every implementation

1. Read the project instructions (CLAUDE.md/AGENTS.md), the plan, the designs, and this record.
2. Check branch, diff, and HEAD (`git status`, `git log`). Compare with the last recorded cycle.
3. Identify the first pending ticket whose dependencies have an approved gate.
4. Extract the ticket's tasks, DoD, and tests; state which go into the current increment.

## Project rules in the cycle

<!-- Obligations copied from the project's instructions (CLAUDE.md/AGENTS.md) that apply per ticket. -->
- <e.g. build every app before the gate>
- <e.g. deploy checklist when schema, volume, or env changes>
- <e.g. sprint report when closing the ticket>
- `clean-code` required in every implementation: checklist applied to the ticket's diff (project instructions win on conflict)

## Local verification

| Check | Directory | Command |
| --- | --- | --- |
| Focused tests | | |
| Test suite | | |
| Typecheck | | |
| Build | | |
| Lint | | |

Record command, directory, result, and exit code. A command not run or an environmental failure is pending.

## Ticket closing criteria

- Verification table passing, with evidence recorded.
- Every DoD criterion met, with evidence.
- Extra records updated when applicable (deploy, sprint).
- `clean-code` checklist applied to the diff, with the result and any justified exception recorded.
- Gate approved, with the verdict recorded.

## Cycle log

### Cycle <N> — <YYYY-MM-DD>

- **Ticket:**
- **State:** in progress / awaiting gate / blocked / done
- **Branch:**
- **Starting commit:**
- **Execution:** <inline | /orchestration run/task/dispatch; spec path>
- **Decisions made while writing the spec:**
- **Increments and commits:**

| Increment | What changed | Full commit | Criteria met |
| --- | --- | --- | --- |

- **Diff review before each commit:**
- **Clean-code checklist:** <result per item; justified exceptions>
- **Local verification:**
- **Gate:** <round, result, findings>
- **Pending criteria:**
- **Blockers and dependencies:**
- **Records updated:**
- **Exact next step to resume:**
