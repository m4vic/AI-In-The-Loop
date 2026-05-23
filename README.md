# AEOS - Autonomous Empirical Optimization System

Neuralchemy Labs research code and paper artifacts for autonomous LLM machine-learning engineering loops.

This repository is now scoped to the AEOS line of work: the AITL taxonomy, the Autonomous Sunk-Cost Fallacy, and Paper 3's asymmetric reviewer-coder experiments. Paper 4 has been separated because its focus is different: local MoE reasoning panels and hybrid security gatekeepers.

## Papers

| # | Paper | Focus | Status |
|---|---|---|---|
| 1 | AITL Taxonomy | Classifying human-in-the-loop to AI-in-the-loop evaluation systems | Published |
| 2 | The Autonomous Sunk-Cost Fallacy | Stopping failures in single-agent autonomous ML loops | Published |
| 3 | The Modality Paradox in Autonomous LLM Engineering | Asymmetric agent loops, cognitive diversity, and mathematical halting in AEOS | Preprint ready |
| 4 | Hybrid Gatekeepers and Local MoE Reasoning Panels | Split to a dedicated repository |
| 5 | The Lab Director and Omega Function | Active continuation |

## Paper 3

Paper 3 is the current upload-ready manuscript:

- Source: `paper/Paper3.tex`
- PDF: `paper/Paper3.pdf`
- Draft notes: `paper/Paper3_Draft.md`
- Figures: `paper/figures/fig1_cross_modality_summary.png` through `paper/figures/fig5_tri_loop_example.png`

Core result: asymmetric reviewer-coder loops reduce sunk-cost behavior in autonomous ML engineering, but the best persistence policy is modality-dependent. Tabular tasks reward quick halting, vision tasks reward higher persistence, and sparse NLP exposes early-stopping boundary conditions.

The math-prompt ablation adds 36 runs across `tabular2`, `text`, and `vision`:

- Runner: `experiments/aeos/aeos_behave/run_math_ablation.py`
- Summary: `experiments/aeos/aeos_behave/results/math_batch_summary_all_20260522_233615.json`
- Figure builder: `experiments/aeos/aeos_behave/build_paper3_assets.py`

## Paper 2

Paper 2 is the published sunk-cost behavioral study. The paper PDF is included under `paper/`:

- `paper/2026_Autonomous_SunkCost_AEOS_neuralchemy.pdf`

The experiment engine and scripts live here:

- `paper2_experiments/`

Additional aggregated run artifacts and plots used during Paper 2 development are kept under:

- `experiments/aeos/results/`

## Repository Structure

| Path | Purpose |
|---|---|
| `paper/` | Paper sources, PDFs, and figures for the AEOS paper line |
| `paper2_experiments/` | Paper 2 single-agent sunk-cost experiments |
| `experiments/aeos/aeos_behave/` | Paper 3 single, dual, tri-agent, and math-prompt AEOS experiments |
| `docs/` | Supporting documentation |

Note: `experiments/aeos/aeos_behave/results/backup/` contains a small archive of early run JSONs that were moved out of the main results folder to avoid duplication.

## Reproduction

From `experiments/aeos/aeos_behave/`:

```bash
python aggregate_paper3.py
python build_paper3_assets.py
python run_math_ablation.py --all-datasets --repeats 3
```

To rebuild Paper 3:

```bash
cd paper
pdflatex -interaction=nonstopmode -halt-on-error Paper3.tex
pdflatex -interaction=nonstopmode -halt-on-error Paper3.tex
```

## Links

- Website: https://www.neuralchemy.in/
- Main code repository: https://github.com/m4vic/AEOS
- Paper 1 Zenodo: https://zenodo.org/records/19551173
- Paper 2 Zenodo: https://zenodo.org/records/19846960
