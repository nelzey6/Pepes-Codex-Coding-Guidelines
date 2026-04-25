Start a long-running autonomous coding task.

Follow `AGENTS.md` and use root `PLANS.md` as the blueprint. Create or continue
one run-scoped `docs/runs/<date>-<slug>/STATUS.md`. Do not create root
`STATUS.md` and do not write live task state into root `PLANS.md`.

Goal:
<Describe the long-running goal here.>

Before coding, reassess from evidence and perform an architecture decision
review: owner, seam/interface, dependency direction, state owner, file cohesion,
and why this is the simplest durable shape.

Then iterate autonomously:

- prefer deletion, reshaping, and reuse over guards or patch layers
- do not add a replacement layer without retiring or fencing the old one
- keep durable code generic; never hardcode the current validation example
- validate, reassess health, simplify, and update the run-scoped `STATUS.md`
- do not stop after shallow progress, queued work, or deferred outcomes

Continue until the run-scoped `STATUS.md` completion criteria are met,
validations pass, or a genuinely user-owned decision is required.
