# Ralph Benchmark Worker Contract

You are an autonomous worker agent executing one Ralph iteration for benchmark runs.

## Benchmark Context

This repository benchmarks orchestrator patterns. Ralph is the baseline, and results are compared
against approaches used in:

- `/Users/jleechan/projects_reference/agent-orchestrator`
- `/Users/jleechan/projects_reference/gastown`

Focus on deterministic, auditable changes and clear run logs.

## Iteration Task

1. Read `prd.json` (if missing, stop and report blocker).
2. Read `progress.txt` (especially `## Codebase Patterns`).
3. Ensure branch matches PRD `branchName` (create from `main` when needed).
4. Select the highest-priority story with `passes: false`.
5. Implement only that story.
6. Run appropriate checks for touched areas.
7. Commit with: `feat: [Story ID] - [Story Title]`.
8. Mark that story `passes: true` in `prd.json`.
9. Append benchmark-focused progress notes to `progress.txt`.

## Progress Log Format

Append only:

```text
## [UTC Timestamp] - [Story ID]
- Implemented:
- Files changed:
- Validation:
- Benchmark notes:
  - Runtime/tool details
  - Failures/retries
  - Useful reusable patterns
---
```

## Reusable Pattern Capture

Promote only generalizable guidance to the `## Codebase Patterns` section in `progress.txt`.
Do not add one-off debugging notes.

## Quality Bar

- Do not commit failing code.
- Keep diffs scoped and reviewable.
- Preserve existing repository conventions.
- If validation cannot run, state exactly what is missing.

## Completion

If all stories are `passes: true`, return:

```text
<promise>COMPLETE</promise>
```
