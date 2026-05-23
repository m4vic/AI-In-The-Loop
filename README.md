# AEOS Research Repository

Neuralchemy Labs code and paper artifacts for the AEOS line of research (autonomous ML engineering loops).

This repo currently tracks the AEOS papers and experiments for:
1. AITL taxonomy foundations
2. Autonomous sunk-cost behavior in single-agent loops
3. Modality-dependent stopping behavior in asymmetric reviewer-coder loops

Paper 4 work (Polyreasoner-focused MoE diversity studies) is being maintained in a separate repository.

## Quick Start

Use this repository in two main ways:
1. Reproduce paper artifacts (Paper 2 and Paper 3)
2. Run/aggregate AEOS experiments from `experiments/aeos/aeos_behave/`

Typical setup:

```bash
cd experiments/aeos/aeos_behave
pip install -r requirements.txt
cp .env.example .env
```

Then run your target experiment scripts (examples are listed below).

## Paper Map

| Paper | Title | Status | Main Assets |
|---|---|---|---|
| Paper 1 | AITL Taxonomy | Published | `paper/2026_AITL_Taxonomy_neuralchemy.pdf` |
| Paper 2 | The Autonomous Sunk-Cost Fallacy | Published | `paper/2026_Autonomous_SunkCost_AEOS_neuralchemy.pdf`, `paper2_experiments/` |
| Paper 3 | The Modality Paradox in Autonomous LLM Engineering | Preprint ready | `paper/Paper3.tex`, `paper/Paper3.pdf`, `experiments/aeos/aeos_behave/` |
| Paper 4 | Hybrid Gatekeepers and Local MoE Reasoning Panels | Moved out | maintained in separate Polyreasoner repository |
| Paper 5 | The Lab Director and Omega Function | In progress | early draft files in `paper/` |

## Repository Layout

| Path | What it contains |
|---|---|
| `paper/` | Manuscript sources (`.tex`), built PDFs, draft markdown files, and shared figures |
| `paper2_experiments/` | Paper 2 experiment code and instructions |
| `experiments/aeos/` | AEOS core code and experiment systems |
| `experiments/aeos/aeos_behave/` | Paper 3 experiment runs, aggregators, analysis scripts, and thread-specific outputs |
| `docs/` | Supporting documents |

## Paper 3: Reproducibility Path

Primary experiment area:

- `experiments/aeos/aeos_behave/`

Important scripts:

- `run_exp3_dual_tabular.ps1`
- `run_exp3_dual_vision.ps1`
- `run_exp3_dual_text.ps1`
- `run_math_ablation.py`
- `aggregate_paper3.py`
- `build_paper3_assets.py`

Main output locations:

- Raw runs: `experiments/aeos/aeos_behave/results/`
- Aggregated Thread A summary: `experiments/aeos/aeos_behave/paper3_thread_a/paper3_thread_a_results.json`
- Thread B benchmark assets: `experiments/aeos/aeos_behave/paper3_thread_b/`
- Thread D frontier benchmark assets: `experiments/aeos/aeos_behave/paper3_thread_d/`

Paper build artifacts:

- Source: `paper/Paper3.tex`
- PDF: `paper/Paper3.pdf`
- Draft notes: `paper/Paper3_Draft.md`
- Figures: `paper/figures/`

## Standard Commands

From `experiments/aeos/aeos_behave/`:

```bash
python aggregate_paper3.py
python build_paper3_assets.py
python run_math_ablation.py --all-datasets --repeats 3
```

From `paper/`:

```bash
pdflatex -interaction=nonstopmode -halt-on-error Paper3.tex
pdflatex -interaction=nonstopmode -halt-on-error Paper3.tex
```

## Notes on Historical Files

- `paper/Paper4.*` and related drafts may still exist as historical snapshots.
- Canonical Paper 4 / Polyreasoner development should proceed in the dedicated Polyreasoner repository.
- `experiments/aeos/aeos_behave/results/backup/` stores archived run JSON files that were moved out of the active result folders.

## References

- Website: https://www.neuralchemy.in/
- Main code repository: https://github.com/m4vic/AEOS
- Paper 1 (Zenodo): https://zenodo.org/records/19551173
- Paper 2 (Zenodo): https://zenodo.org/records/19846960
