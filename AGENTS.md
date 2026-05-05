# Repository Guidelines

Durable rules for Codex and other coding agents in this repository.

## Default Mode

Default to long-running plan mode for every code-changing request.

Do not patch immediately unless the user explicitly says:

```text
implement directly
```

Without that phrase, before editing code:

1. Read `git status`.
2. Read `PROJECT.md` and relevant docs.
3. Create or continue `docs/runs/<date>-<slug>/STATUS.md` from `PLANS.md`.
4. Inspect evidence: code, tests, logs, traces, runtime records, and active docs.
5. Record the goal, root-cause/architecture stance, complexity budget,
   validation plan, and next action in the run-scoped `STATUS.md`.
6. Only then implement, validate, reassess, and update `STATUS.md`.

Read-only questions, reviews, and explanations do not need run state unless the
user asks for an implementation plan.

## Source Of Truth

When sources disagree, prefer:

1. Current code, schemas, tests, and runtime evidence
2. `PROJECT.md`
3. Active architecture docs and ADRs
4. Handbook docs
5. Archived docs and old run logs
6. Thread memory

## Workflow Files

- `AGENTS.md`: durable repo rules.
- `PROJECT.md`: project-specific commands, architecture, evidence, constraints.
- `PLANS.md`: long-running plan blueprint.
- `docs/runs/<date>-<slug>/STATUS.md`: gitignored live run state.

Do not create root `STATUS.md`. Do not put live run state in `PLANS.md`.

## Architecture Rules

- Architecture review comes before patching.
- Route behavior through the owning module/seam.
- Prefer deletion, reshaping, and reuse over guards or patch layers.
- Keep files cohesive; avoid catch-all modules.
- Do not add replacement layers unless the old layer is deleted, retired, or
  fenced with a removal trigger.
- Keep durable code generic; do not hardcode the current user, tenant,
  workspace, dataset, file path, or validation example.

## Validation

Discover commands from `PROJECT.md`, docs, CI, task runners, or build files.
Use the smallest targeted check that proves the change, then broader checks when
risk warrants it.

Before handoff, inspect `git diff`, confirm unrelated changes were not reverted,
summarize validation, and note residual risks.
