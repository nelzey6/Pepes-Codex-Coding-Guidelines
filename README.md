# Pepe's Codex Coding Guidelines

Reusable coding-agent guidelines for public GitHub repositories.

This repo is a small operating system for working with Codex on real codebases:
lightweight for everyday tasks, but disciplined enough for long-running
autonomous reworks where context, architecture, and code quality can otherwise
drift.

## Core Values

- Architecture before patches: understand ownership, seams, and data flow before
  changing code.
- Simplicity over accumulation: prefer deletion, reshaping, and reuse over guard
  layers, fallback piles, and historical patch sediment.
- Clear ownership: every module, class, file, interface, and state surface
  should have a reason to exist and a place where it belongs.
- Durable autonomy: long-running tasks must survive context resets through a
  run-scoped status file, not fragile thread memory.
- Evidence over vibes: decisions should come from code, tests, logs, traces,
  runtime records, and active docs.
- Generic by default: fixes should solve the class of problem, not hardcode the
  current repro, user, tenant, workspace, dataset, or file.
- Quality is the goal: a task is not done because "something ran"; it is done
  when the system is healthier, simpler, validated, and easier to maintain.

## What Is Inside

- `AGENTS.md`: durable repository rules for Codex and other coding agents.
- `PROJECT.md`: project-specific architecture, commands, validation, debugging,
  and source-of-truth notes.
- `PLANS.md`: blueprint for extended long-running autonomous tasks.
- `PROMPT.md`: copyable starter prompt for long-running tasks.
- `docs/runs/<date>-<slug>/STATUS.md`: ignored, run-scoped live task state.

The key idea is separation of concerns: durable rules live in `AGENTS.md`,
project facts live in `PROJECT.md`, the long-running workflow blueprint lives
in `PLANS.md`, and temporary execution state lives in ignored run-scoped status
files.

## Why Use This

These guidelines are designed to prevent common agent failure modes:

- creating huge files with unclear ownership
- patching around root causes with guards and fallbacks
- adding new layers without retiring old ones
- stopping after shallow progress
- losing continuity during long tasks
- hardcoding the current bug reproduction into durable code
- treating thread context as the source of truth

## How To Use

Copy these files into your repository root:

```text
AGENTS.md
PROJECT.md
PLANS.md
PROMPT.md
.gitignore
```

Then fill in `PROJECT.md` with your repo's commands, architecture docs,
source-of-truth files, validation suites, debugging paths, and constraints.
Keep `AGENTS.md` and `PLANS.md` mostly generic.

To have Codex fill `PROJECT.md` for you, open a Codex chat in your repo and
paste:

```text
Read this repository, then fill PROJECT.md with the project-specific
architecture, commands, validation steps, debugging paths, source-of-truth files,
and long-running task notes. Keep AGENTS.md and PLANS.md generic.
```

For normal tasks, just ask Codex normally.

For an extended long-running task, copy `PROMPT.md` into a fresh Codex chat and
replace the goal placeholder. `PROMPT.md` is intended to be copy-pasted into a
new chat, not executed as a script.

## Philosophy

Good agent work should feel like a careful senior engineer is pairing with you:
curious before changing things, bold enough to simplify, disciplined about
validation, and allergic to code that only makes sense because yesterday's bug
needed a quick guard.
