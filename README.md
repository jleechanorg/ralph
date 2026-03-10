# Ralph Orchestrator Benchmark Harness

![Ralph](ralph.webp)

This repo is a benchmarking harness for autonomous coding orchestrators.

- **Baseline orchestrator**: Ralph (`ralph.sh`)
- **Comparison references**:
  - Agent Orchestrator: `/Users/jleechan/projects_reference/agent-orchestrator`
  - Gas Town: `/Users/jleechan/projects_reference/gastown`

The goal is to run comparable work units and measure behavior such as setup overhead,
iteration reliability, progress tracking quality, and human intervention required.

## Why This Repo Exists

Ralph provides a simple repeatable loop: run one story, validate, commit, record progress, repeat.
That makes it useful as a baseline against more feature-rich orchestration systems.

## Repository Layout

| File/Dir | Purpose |
|---|---|
| `ralph.sh` | Main orchestration loop (Amp or Claude Code). |
| `CLAUDE.md` | Worker contract for Ralph benchmark iterations. |
| `prompt.md` | Amp prompt template. |
| `prd.json.example` | Scenario format for benchmark work units. |
| `AGENTS.md` | Tool-facing quick instructions for this benchmark repo. |
| `flowchart/` | Visual explanation of Ralph workflow. |

## Remote Fix (Repository Not Found)

If you see:

```text
fatal: repository 'https://github.com/jleechanorg/ralph.git/' not found
```

set the remote to upstream:

```bash
git remote set-url origin https://github.com/snarktank/ralph.git
git remote set-url --push origin https://github.com/snarktank/ralph.git
```

If you want to push to your own fork instead:

```bash
git remote set-url origin https://github.com/<your-user>/ralph.git
git remote add upstream https://github.com/snarktank/ralph.git
```

## Prerequisites

- One AI coding CLI:
  - Claude Code (`--tool claude`)
  - Amp (`--tool amp`)
- `jq`
- Git repository to run benchmark tasks against

## Ralph Baseline Run

```bash
# from this repo root
cp prd.json.example prd.json

# run a short baseline benchmark
./ralph.sh --tool claude 3
```

Ralph loop behavior:

1. Select highest priority story with `passes: false`
2. Execute one story in a fresh AI session
3. Run checks and commit
4. Mark story as passed
5. Append learnings to `progress.txt`

## Cross-Orchestrator Benchmarking

Use the same task definition and acceptance criteria when comparing systems.

### Agent Orchestrator (reference)

```bash
cd /Users/jleechan/projects_reference/agent-orchestrator
# follow local setup in that repo
# then run on target project with ao start / ao spawn
```

### Gas Town (reference)

```bash
cd /Users/jleechan/projects_reference/gastown
# follow local setup in that repo
# then coordinate work via gt mayor / gt convoy / gt sling
```

## Suggested Benchmark Outputs

For each orchestrator run, capture:

- Setup time
- Time to first successful task completion
- Number of retries/escalations
- Validation pass rate
- Human interventions required
- Notes on failure modes and recovery quality

## Flowchart

[![Ralph Flowchart](ralph-flowchart.png)](https://snarktank.github.io/ralph/)

To run locally:

```bash
cd flowchart
npm install
npm run dev
```
