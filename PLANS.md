# Long-Running Task Blueprint

Stable blueprint for extended autonomous tasks. Do not store live task state in
this file. For each long-running task, create:

```text
docs/runs/<yyyy-mm-dd>-<short-slug>/STATUS.md
```

Run-scoped `STATUS.md` files are gitignored local execution state.

## Activation

Use this blueprint only when explicitly asked for a long-running/autonomous
workflow. Do not use it for ordinary plans, reviews, normal fixes,
investigations, or standard implementation requests.

## STATUS.md Template

Use this structure for `docs/runs/<date>-<slug>/STATUS.md`.

```markdown
# <Run Title>

Live plan, execution log, and resume cursor for this specific run. Not durable
architecture truth.

## Task Contract

- Goal:
- Non-goals:
- Evidence sources:
- Completion criteria:
- Stop conditions:

## Architecture Stance

- Current path:
- Owner modules/classes/services:
- Public seams/interfaces:
- Allowed dependencies:
- State owner:
- Root causes:
- File/module-size risks:
- Cross-layer coupling risks:
- Genericity risks:
- Existing seams to reuse:
- Code to delete/collapse/move:
- Current stance:

## Checklist

### Phase 1: Reassess

- [ ] Read `git status`.
- [ ] Inspect evidence before speculation.
- [ ] Inspect code, tests, logs/traces, runtime records, and active docs.
- [ ] Record root-cause stance and next improvement.

### Phase 2: Improve

- [ ] Complete architecture decision review.
- [ ] Define complexity budget.
- [ ] Prefer deletion/collapse/move before adding guards.
- [ ] If adding a replacement layer, name and retire/fence the old layer.
- [ ] Reuse existing seams instead of parallel paths.
- [ ] Keep files cohesive; split/move behavior if a file becomes a catch-all.
- [ ] Add interfaces/classes/adapters only when they clarify ownership.
- [ ] Keep durable code generic across validation examples.
- [ ] Add/update tests, docs, ADRs, traces, or debug artifacts as needed.

Acceptance criteria:

- [ ] Root cause is addressed, not wrapped.
- [ ] Ownership, seams, and state authority are clear.
- [ ] No oversized catch-all file or hidden backchannel was added.
- [ ] No old and new layer remain authoritative for the same responsibility.
- [ ] Complexity is reduced or clearly contained.

### Phase 3: Validate And Reassess

- [ ] Inspect `git diff`.
- [ ] Run targeted validation.
- [ ] Run broader validation when relevant.
- [ ] Reassess output/runtime/product health after the change.
- [ ] Inspect queued/running/deferred work when relevant.
- [ ] Audit complexity and quality deltas.

### Phase 4: Repass

- [ ] Re-read changed files and call paths as a reviewer.
- [ ] Reassess architecture, ownership, and file cohesion.
- [ ] Simplify if unnecessary layers were added.
- [ ] Record next exact action.
- [ ] Continue unless completion criteria or stop conditions apply.

## Health Scoreboard

- Loops completed:
- Actions/jobs queued/completed:
- Useful output delta:
- Quality/yield delta:
- Deferred/requeued work:
- Repeated blockers:
- Errors:
- Complexity delta:
- Current verdict:

## Complexity Audit

Before coding:

- Expected deletions/collapses:
- Replacement layer:
- Layer being replaced:
- Retirement trigger:
- Allowed new guards/conditionals:
- Owner:
- Public seam/interface:
- State owner:
- Files at risk of becoming catch-alls:
- Maximum acceptable net-new logic:

After coding:

- Net LOC:
- New conditionals:
- New guards/fallbacks/envelopes:
- New helper layers/state surfaces:
- Deleted/collapsed stale paths:
- Retired/fenced replaced layers:
- File cohesion review:
- Interface/class justification:
- Cross-layer coupling introduced/removed:
- Why the result is simpler or better owned:

## Quality Audit

- User-visible behavior:
- Runtime/product quality:
- Data quality:
- Performance/scale:
- Reliability:
- Saturation evidence:

## Execution Log

```text
Timestamp:
Action:
Evidence:
Result:
Validation:
Complexity notes:
Quality notes:
Next exact action:
```

## Validation Log

- Command/check:
- Result:
- Notes:

## Resume Cursor

- Current phase:
- Last completed action:
- Current blockers:
- Next exact action:
- Continue automatically:
```

## Long-Running Rules

- Reassess from evidence before coding.
- Review architecture before patching.
- Continue until completion criteria are met.
- Keep durable code generic across validation examples.
- Do not stop after one shallow progress signal.
- Use logs, traces, tests, runtime records, debug artifacts, and local commands
  when certainty matters.
- Treat product/runtime quality as a primary health signal.
- Treat complexity accretion as a bug.

## Complexity Rules

- Default to deletion-first and reshape-first.
- Keep files cohesive and ownership explicit.
- Do not grow huge catch-all files.
- Use interfaces/classes/adapters only when they clarify ownership.
- Avoid cross-layer backchannels and scattered root-cause-specific links.
- Do not add a replacement layer until the layer it replaces is deleted,
  retired, or fenced with a removal trigger.
- If the patch mainly wraps symptoms with guards, choose a root-cause refactor.

## Completion Rules

Complete only when run-scoped `STATUS.md` shows:

- Completion criteria are met or true saturation is proven.
- Required validations pass.
- Durable changes are generic and do not hardcode validation examples.
- Ownership is explicit, files are cohesive, and public seams are justified.
- No hidden cross-layer backchannels or huge catch-all modules were introduced.
- Complexity is reduced or clearly contained.
- Execution log, validation log, audits, and resume cursor are current.
```
