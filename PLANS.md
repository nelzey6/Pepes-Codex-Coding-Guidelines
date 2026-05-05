# Long-Running Plan Blueprint

Default for every code-changing task. Do not patch immediately unless the user
explicitly says:

```text
implement directly
```

Otherwise create or continue:

```text
docs/runs/<yyyy-mm-dd>-<short-slug>/STATUS.md
```

`STATUS.md` is gitignored live state. Do not store live state here.

## Planning Gate

Before coding, `STATUS.md` must contain:

- goal, non-goals, completion criteria, stop conditions
- evidence inspected: code, tests, logs/traces, runtime records, docs
- architecture stance: owner, seam/interface, dependencies, state owner,
  root-cause hypothesis, file-cohesion risks
- complexity budget: delete/collapse opportunities, allowed guards, replacement
  layer retirement trigger, max net-new logic
- validation plan and next exact action

## STATUS.md Template

```markdown
# <Run Title>

Live plan and resume cursor. Not durable architecture truth.

## Contract

- Goal:
- Non-goals:
- Completion criteria:
- Stop conditions:

## Evidence

- `git status`:
- Docs read:
- Code/tests/logs/traces/runtime records inspected:

## Architecture

- Owner/seam:
- Dependencies/state owner:
- Root cause:
- Code to delete/collapse/move:
- File-cohesion risks:
- Stance:

## Complexity Budget

- Expected deletions/collapses:
- Allowed guards/conditionals:
- Replacement layer and retirement trigger:
- Max net-new logic:

## Plan

- [ ] Reassess from evidence.
- [ ] Review architecture.
- [ ] Implement smallest durable change.
- [ ] Validate.
- [ ] Inspect diff and reassess complexity.

## Log

- Action:
- Evidence:
- Result:
- Validation:
- Next:

## Resume

- Phase:
- Blockers:
- Next:
- Continue automatically:
```

## Rules

- Default to long-running plan mode.
- `implement directly` is the only immediate-patching override.
- Prefer root-cause fixes, deletion, reshaping, and reuse.
- Do not leave old and new layers both authoritative.
- Keep durable code generic across examples, users, workspaces, and data.
- Continue until completion criteria pass or a user-owned decision is required.
