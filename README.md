# Albion Research Lab

Autonomous research orchestration on top of the [karpathy/autoresearch](https://github.com/karpathy/autoresearch) experiment contract, with OMX multi-agent tooling vendored as a submodule.

## Local path

Canonical checkout:

- `/Users/stephenbeale/Projects/albion-research-lab`

See [LOCAL_PATHS.md](LOCAL_PATHS.md) and [LINEAGE.md](LINEAGE.md) for path conventions and upstream history.

![teaser](progress.png)

## What this repo is

Albion Research Lab separates **research orchestration** (agents, policies, pipelines, study notes) from **benchmark execution** (e.g. ToM AI Research Team). It keeps the autoresearch training baseline (`prepare.py`, `train.py`, `program.md`) while adding:

- `.codex/` — customized OMX agents, prompts, and skills
- `policies/` — cross-repo pipeline and promotion rules
- `backends/` — adapter layer for Codex, Modal, and local CLI
- `oh-my-codex/` — git submodule (pinned OMX source)

## Quick start

**Requirements:** Apple Silicon Mac (M1/M2/M3/M4 with Metal/MPS) or a single NVIDIA GPU, Python 3.10+, [uv](https://docs.astral.sh/uv/), Node.js 20+.

```bash
# 1. Clone with submodule
git clone --recurse-submodules https://github.com/stephenlangsfordbeale/albion-research-lab.git
cd albion-research-lab

# 2. Build OMX submodule
cd oh-my-codex && npm install && npm run build && cd ..

# 3. Python dependencies
uv sync

# 4. One-time data prep (~2 min)
uv run prepare.py

# 5. OMX project setup
./omx setup --scope project --force --verbose
```

Verify repo structure:

```bash
python .codex/skills/autoresearch-lab/scripts/autoresearch_ops.py check-setup --json --repo-only
uv run python -m unittest discover -s tests -p 'test_*.py' -q
```

## OMX launcher

```bash
./omx doctor
./omx setup --scope project --verbose
```

See [OMX_INTEGRATION.md](OMX_INTEGRATION.md) for submodule update workflow.

## Core experiment files

- **`prepare.py`** — fixed constants, data prep, runtime utilities (do not modify)
- **`train.py`** — model, optimizer, training loop (agent modifies this)
- **`program.md`** — baseline agent instructions (human-edited)

Training runs for a **fixed 5-minute wall-clock budget**. Metric: **val_bpb** (lower is better).

## Project structure

```text
.codex/           — OMX agents, prompts, skills (tracked)
policies/         — workflow contracts and promotion rules
backends/         — execution adapters
oh-my-codex/      — OMX submodule (build required)
tests/            — unit tests
prepare.py        — data prep + utilities
train.py          — training code (agent-editable)
program.md        — agent instructions
omx               — repo-local OMX launcher
```

## Platform support

macOS-first fork lineage from [miolini/autoresearch-macos](https://github.com/miolini/autoresearch-macos). Supports Apple Silicon (MPS) and NVIDIA CUDA.

## License

MIT
