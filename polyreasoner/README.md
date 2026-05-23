# Polyreasoner Workspace (Staging Inside AEOS Repo)

This folder is a clean workspace for Polyreasoner development while AEOS Paper 3 remains release-focused.

## Why this exists

- `aitl-paper` stays focused on AITL + AEOS Paper 1/2/3.
- `polyreasoner/` is where you can directly add new ASRT and diversity/MoE work without mixing it into Paper 3 paths.

## Structure

| Path | Use |
|---|---|
| `experiments/asrt/` | ASRT-specific experiments and outputs |
| `experiments/panel_diversity/` | MoE vs single, panel diversity, reviewer-panel tests |
| `benchmarks/` | Benchmark datasets, benchmark runners, consolidated result files |
| `docs/` | Notes, methods, and paper-draft support docs for Polyreasoner |

## Migration Guidance

When you are ready to fully split to a dedicated repository (`polyreasoner` or `polyreasoner-v3`):

1. Move this full `polyreasoner/` directory into the new repo root.
2. Copy required benchmark artifacts from:
   - `experiments/aeos/aeos_behave/paper3_thread_b/`
   - `experiments/aeos/aeos_behave/paper3_thread_d/`
3. Keep AEOS paths untouched so Paper 3 remains reproducible.

## Naming Guidance

- Keep AEOS files under `experiments/aeos/...`
- Keep all new ASRT and Polyreasoner files under `polyreasoner/...`
- Prefer timestamped result JSON outputs to preserve run history
