# Project Guide

Project-specific adapter for the generic Codex guidelines. Fill this in after
copying the template into a real repository.

Keep durable workflow rules in `AGENTS.md` and `PLANS.md`. Keep facts about this
specific project here.

## Project Snapshot

- Purpose:
- Primary users:
- Tech stack:
- Runtime/deployment:
- Main directories:
- Critical constraints:

## Source Of Truth

- Code/schema:
- Architecture docs/ADRs:
- Product/domain docs:
- Tests/fixtures:
- Generated/archive docs:
- Evidence/logs/traces/runtime records:

## Architecture And Ownership

- Core modules/services:
- Ownership boundaries:
- Public seams/interfaces:
- State/data owners:
- Dependency direction:
- Anti-patterns to avoid:

## Commands

- Setup:
- Development:
- Format:
- Lint/static analysis:
- Typecheck/compile:
- Targeted tests:
- Full test suite:
- Build/package:
- Smoke/integration checks:
- Database/migrations:

## Debugging And Evidence

- Logs/traces:
- Runtime records:
- Reproduction commands:
- Local services:
- Useful scripts:
- Known flaky/slow checks:

## Long-Running Task Notes

- Health signals:
- Quality/yield signals:
- Scale/performance constraints:
- Topic/data independence rules:
- Completion expectations:

## Update Rules

- Update this file when durable project-specific architecture, commands,
  validation, debugging paths, source-of-truth lists, or operating constraints
  change.
- Do not store live run state here. Use
  `docs/runs/<date>-<slug>/STATUS.md` for long-running task state.
- Do not duplicate generic workflow rules here. Keep those in `AGENTS.md` and
  `PLANS.md`.
