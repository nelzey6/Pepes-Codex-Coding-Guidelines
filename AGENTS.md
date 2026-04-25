# Repository Guidelines

Durable coding-agent guidance for this repository. Keep this file concise and
update it only when workflow, architecture, validation, or agent operating rules
change.

## Source Of Truth

When sources disagree, prefer:

1. Current code, schema, tests, and runtime evidence
2. Active architecture docs and ADRs
3. Project handbook docs
4. Archived docs and old run logs
5. Thread memory

Customize the project-specific docs and commands after copying this template.

## Workflow Files

- `AGENTS.md`: durable repo rules.
- `PLANS.md`: stable blueprint for extended long-running tasks.
- `docs/runs/<date>-<slug>/STATUS.md`: gitignored live state for one
  long-running task.

Do not create a root `STATUS.md`. Do not put live task state in root
`PLANS.md`.

## Normal Tasks

Unless the user explicitly asks for a long-running/autonomous workflow:

- Do not create run-scoped status files.
- Do not update root `PLANS.md`.
- Plan in the conversation when useful, then implement and validate directly.

## Fresh Session

1. Read `git status`.
2. Read the relevant project docs.
3. Identify the likely owner module before editing.
4. Inspect tests, logs, traces, or runtime evidence before broad speculation.

## Long-Running Workflow

Use only when explicitly requested, for example "start a long-running task" or
"run autonomously for hours".

1. Create or continue `docs/runs/<date>-<slug>/STATUS.md` from `PLANS.md`.
2. Reassess from evidence: code, tests, logs, traces, runtime records, debug
   artifacts, and active docs.
3. Build a broad architecture/root-cause overview before local fixes.
4. Perform architecture decision review before coding: owner, seam/interface,
   dependency direction, state owner, file/module cohesion, and why this is the
   simplest durable shape.
5. Define a complexity budget: expected deletions, allowed new guards, ownership
   seams to simplify, and what would be too complex to keep.
6. Implement the smallest durable improvement.
7. Validate with targeted checks first, then broader gates when needed.
8. Reassess from multiple scopes and continue until the run-scoped `STATUS.md`
   completion criteria are met or a user-owned decision is required.

## Architecture Rules

- Architecture review comes before patching.
- Keep files cohesive; do not grow huge catch-all files.
- Prefer clear ownership seams over scattered procedural patches.
- Use interfaces/classes/adapters only when they clarify ownership or reduce
  coupling.
- Avoid hidden cross-layer backchannels, root-cause-specific guards, and
  side-effect links.
- Route behavior through the owning seam.

## Replacement-Layer Discipline

- Do not add a replacement layer until the layer it replaces is deleted,
  retired, or fenced behind a short migration bridge.
- If a bridge is necessary, record the owner, deletion trigger, and validation
  needed to remove it.
- Do not mark work complete while old and new layers remain authoritative for
  the same responsibility.

## Complexity Rules

- Treat complexity accretion as a bug.
- Default to deletion-first and reshape-first.
- Before adding logic, look for stale compatibility paths, duplicated ownership,
  broad conditionals, misplaced responsibilities, and historical patches that
  can be removed or moved.
- Track net LOC, new conditionals, guards, fallbacks, helper layers, and state
  surfaces after major implementation passes.
- If the patch mainly wraps symptoms with guards, choose a root-cause refactor.
- Large net-new patches must be justified by clearer ownership, removed
  obsolete code, better source-of-truth boundaries, or measurable
  product/runtime gains.

## Genericity

- Durable code should be generic across users, workspaces, tenants, datasets,
  environments, and validation examples unless explicitly scoped otherwise.
- Use concrete examples only as validation evidence.
- Never hardcode the current validation user, workspace, topic, source id,
  query text, customer, file path, or dataset-specific condition into durable
  production code.

## Autonomy And Completion

- Do not stop after one shallow progress signal.
- Queued/running work, deferred outcomes, repeated requeues, retry uncertainty,
  or active background jobs are intermediate states.
- Only conclude when the run-scoped `STATUS.md` checklist is complete and
  required validations pass.
- Stop only for undiagnosable validation failures, destructive/irreversible
  choices, broad schema/API decisions, or user-owned product/architecture
  tradeoffs.
- If something fails, diagnose, fix, log evidence and resolution, and continue.

## Validation

Discover the repository's own commands. Do not assume a language, framework,
package manager, or build tool.

Common validation categories:

- formatting
- lint/static analysis
- compile/typecheck, when applicable
- targeted tests
- full test suite
- build/package
- smoke/integration checks

Find commands in project docs, `Makefile`, task runner configs, CI workflows,
or build manifests. Use the smallest targeted check that proves the change,
then run the broader gate appropriate for the risk.

Before final handoff, inspect `git diff`, confirm unrelated changes were not
reverted, run required validation, and summarize residual risks.
