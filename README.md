# Pepe's Codex Coding Guidelines

Reusable coding-agent guidelines for public GitHub repositories.

Default behavior: long-running plan mode. Codex should inspect evidence, record
a run-scoped plan, then patch. Immediate patching is allowed only if the user
says:

```text
implement directly
```

## Files

- `AGENTS.md`: durable agent rules.
- `PROJECT.md`: project-specific commands, architecture, evidence, constraints.
- `PLANS.md`: long-running plan blueprint and `STATUS.md` template.
- `PROMPT.md`: starter prompt.
- `docs/runs/<date>-<slug>/STATUS.md`: ignored live state for one run.

## Rules

- Architecture before patches.
- Evidence before speculation.
- Prefer deletion, reshaping, and reuse over guards or patch layers.
- Keep ownership, seams, and state authority clear.
- Keep durable code generic; do not hardcode validation examples.
- Continue until completion criteria and validation pass, or a user-owned
  decision is required.

## Use

Copy into a repo root:

```text
AGENTS.md
PROJECT.md
PLANS.md
PROMPT.md
.gitignore
```

Fill `PROJECT.md` with the repo's commands, architecture, validation, debugging
paths, sources of truth, and constraints.

For any code-changing request, Codex should create or continue
`docs/runs/<date>-<slug>/STATUS.md`, record the goal, evidence, architecture
stance, complexity budget, validation plan, and next action, then edit.

If you want immediate patching, say `implement directly`.
