# Ralph Benchmark Agent Instructions

## Purpose

This repository is used to benchmark orchestrator workflows, with Ralph as the local baseline and
comparison targets including:

- `agent-orchestrator` (`/Users/jleechan/projects_reference/agent-orchestrator`)
- `gastown` (`/Users/jleechan/projects_reference/gastown`)

## Scope

- Keep changes focused on benchmark harness/docs unless explicitly asked to change runtime logic.
- Treat `ralph.sh` as the baseline orchestrator loop.
- Keep benchmark runs reproducible with explicit commands and environment assumptions.

## Common Commands

```bash
# Ralph baseline
./ralph.sh --tool claude 3

# Optional: Amp baseline
./ralph.sh --tool amp 3

# Flowchart docs site
cd flowchart && npm install && npm run dev
```

## Repository Facts

- `ralph.sh`: baseline autonomous loop.
- `CLAUDE.md`: worker-agent operating contract for Ralph iterations.
- `prd.json.example`: canonical benchmark scenario shape.
- `prompt.md`: Amp-side prompt template.
- `flowchart/`: visual walkthrough of the loop.

## Remote Configuration

If GitHub returns `Repository not found` for `jleechanorg/ralph`, use the upstream URL:

```bash
git remote set-url origin https://github.com/snarktank/ralph.git
git remote set-url --push origin https://github.com/snarktank/ralph.git
```

If you later create a personal fork, set `origin` to the fork and keep `upstream` on snarktank.
