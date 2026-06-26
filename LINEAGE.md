# Lineage

Albion Research Lab is a standalone orchestration repo derived from the OMX/autoresearch work previously housed in `albion-research-lab`.

## Upstream chain

- [karpathy/autoresearch](https://github.com/karpathy/autoresearch) — original autonomous LLM pretraining experiment
- [miolini/autoresearch-macos](https://github.com/miolini/autoresearch-macos) — macOS port
- [chaosste/autoresearch-macos](https://github.com/chaosste/autoresearch-macos) — fork with OMX integration
- [stephenlangsfordbeale/albion-research-lab](https://github.com/stephenlangsfordbeale/albion-research-lab) — prior working fork (`tomx` branch)

## OMX dependency

- Submodule: [chaosste/oh-my-codex](https://github.com/chaosste/oh-my-codex) pinned to the local checkout at `/Users/stephenbeale/Projects/oh-my-codex`
- Upstream OMX: [Yeachan-Heo/oh-my-codex](https://github.com/Yeachan-Heo/oh-my-codex)

## What moved here

- `.codex/` agents, prompts, and skills customizations
- `policies/`, `backends/`, `tests/`, and pipeline validator
- Research docs under `docs/` and `studies/`

## What stayed out

- `graphify-out/` generated cache
- `.omx/` runtime state and logs
- `node_modules/` and `.venv/` (recreated locally)
