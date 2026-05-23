# AEOS Behave Experiments (Paper 3 Core)

This directory contains the main experiment code, scripts, and result artifacts used for Paper 3.

## Scope

The workflows here cover:
1. Single-agent AEOS runs (`exp1`)
2. Dual-agent reviewer-coder runs (`exp2`)
3. Tri-agent judge runs (`exp3`)
4. Math-prompt ablations and benchmark threads (A/B/D)

## Folder Structure

| Path | Purpose |
|---|---|
| `results/` | Raw JSON runs and generated run-level plots |
| `paper3_thread_a/` | Aggregated Paper 3 cross-modality summaries |
| `paper3_thread_b/` | Puzzle benchmark thread artifacts |
| `paper3_thread_d/` | Frontier benchmark thread artifacts |
| `data/` | Dataset helpers or inputs for experiments |

## Core Runtime Files

| File | Role |
|---|---|
| `runner.py` | Single-agent loop |
| `runner_critic.py` | Dual-agent reviewer-coder loop |
| `runner_tri_agent.py` | Tri-agent judge + coder panel loop |
| `agent.py` | Model/API wrapper for LLM calls |
| `coder.py` / `coder_bert.py` | Coder agents |
| `reviewer.py` | Reviewer directive logic (`DIRECTIVE: ...`) |
| `trainer.py` | Sandbox training/evaluation harness |
| `data_loader.py` | Dataset loading and preprocessing |

## Aggregation and Asset Scripts

| Script | Output |
|---|---|
| `aggregate_paper3.py` | `paper3_thread_a/paper3_thread_a_results.json` |
| `aggregate_single.py` | Single-agent tabular summary to console |
| `aggregate_single_vision.py` | Single-agent vision summary to console |
| `aggregate_single_text.py` | Single-agent text summary to console |
| `aggregate_dual_vision.py` | Dual-agent vision summary to console |
| `aggregate_dual_text.py` | Dual-agent text summary to console |
| `build_paper3_assets.py` | Paper-ready plots/tables from aggregated results |
| `run_math_ablation.py` | Math-prompt ablation runs and summary JSON |

## Run Scripts (PowerShell)

| Script | Purpose |
|---|---|
| `run_all.ps1` | End-to-end run sweep |
| `run_tabular2_n3.ps1` | Tabular single-agent sweep |
| `run_all_vision_overnight.ps1` | Vision sweep |
| `run_all_text_overnight.ps1` | Text sweep |
| `run_exp3_dual_tabular.ps1` | Dual tabular pairings |
| `run_exp3_dual_vision.ps1` | Dual vision pairings |
| `run_exp3_dual_text.ps1` | Dual text pairings |
| `run_exp3_dual_gpt.ps1` | Dual-agent runs with GPT/frontier settings |
| `run_exp3_tri_overnight.ps1` | Tri-agent sweep |

## Results Naming Convention

Run files follow:

```text
exp{type}_{model_or_pair}_{dataset}_run{N}_{YYYYMMDD_HHMMSS}.json
```

Where:
- `exp1` = single-agent
- `exp2` = dual-agent
- `exp3` = tri-agent

## Thread Mapping (Paper 3)

| Thread | Goal | Key Files |
|---|---|---|
| A | Cross-modality AEOS outcomes | `aggregate_paper3.py`, `paper3_thread_a/paper3_thread_a_results.json` |
| B | Puzzle panel benchmark | `paper3_thread_b/*` |
| D | Frontier benchmark and diversity analysis | `paper3_thread_d/benchmark_data_v3.json`, `paper3_thread_d/frontier_benchmark_results_v3.json` |

## Typical Workflow

1. Run experiments via `.ps1` scripts or Python entry points.
2. Inspect raw outputs under `results/`.
3. Aggregate with `aggregate_paper3.py` and other analysis scripts.
4. Build publication assets via `build_paper3_assets.py`.
5. Sync final figures/tables into `paper/` for manuscript updates.

## Environment Notes

- Copy `.env.example` to `.env` and set model/API credentials.
- Keep old run archives in `results/backup/` when cleaning active folders.
- For reproducibility, preserve original JSON files and timestamped outputs.
- New Polyreasoner/ASRT experiments should go under `../../../../polyreasoner/` to keep Paper 3 paths stable.
