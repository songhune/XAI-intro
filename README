# XAI-intro (Colab First)

This repository is designed for **Google Colab-first practice**, assuming many students do not have a local Python environment.

## Additional Documents

- Korean translation: `README.ko.md`
- Instructor notes: `LECTURE_NOTES.ko.md`

## 1) Getting Started in Colab (Recommended)

1. Open Google Colab: `https://colab.research.google.com`
2. Go to `File -> Open notebook -> GitHub` and open notebooks from this repository
3. In `Runtime -> Change runtime type`, start with `CPU` (or use `T4 GPU` when needed)
4. Run the **first dependency/setup cell** in each notebook
5. If you see a restart warning after install, do `Runtime -> Restart session` and run from the top again

## 1.5) Very Detailed Run Guide (For Non-CS Students)

If this is your first time running Python notebooks, follow this exactly.

### A. Open the notebook

1. Go to `https://colab.research.google.com`
2. Click `File -> Open notebook`
3. Click the `GitHub` tab
4. Paste this repository URL or search for it
5. Click one notebook (start with `[0430]1.Decision_Tree_lab.ipynb`)

### B. Save your own copy first (important)

1. Click `File -> Save a copy in Drive`
2. Work on your copied version (not the original read-only view)

### C. Run one code cell

1. Click inside a code cell
2. Press the play button on the left of the cell
3. Wait until the spinning icon stops
4. Read the output shown right below that cell

Shortcuts:
- Run current cell: `Shift + Enter`
- Run without moving: `Ctrl/Cmd + Enter`

### D. Run all cells in correct order

1. Click `Runtime -> Run all`
2. Wait for all cells to finish
3. If any red error appears, stop and read Section 5 (Troubleshooting)

### E. What to do when install cell appears

The first setup cell installs packages. This is normal and may take 1-3 minutes.

If you see a message like restart required:
1. Click `Runtime -> Restart session`
2. Click `Runtime -> Run all` again

### F. How to read outputs

- Table output: scroll and inspect values
- Plot/image output: check title, axis labels, and legend
- Metric output (accuracy, RMSE, F1): larger/smaller is better depending on metric context in markdown instructions

### G. Most common mistakes

- Running middle cells first
- Skipping the install/setup cell
- Editing variable names accidentally
- Not restarting runtime after dependency installation

If you get stuck, restart and rerun:
1. `Runtime -> Restart session`
2. `Runtime -> Run all`

### Quick Checklist

- [ ] Opened the notebook from the GitHub tab in Colab
- [ ] Ran the setup/install cell first
- [ ] Restarted runtime (if prompted) and reran all cells in order
- [ ] Saved a working copy via `File -> Save a copy in Drive`

## 2) Recommended Study Order

1. `[0430]1.Decision_Tree_lab.ipynb`
2. `[0430]2.Decision_Tree_solution.ipynb`
3. `[0430]3.Surrogate_lab.ipynb`
4. `[0430]4.Surrogate_solution.ipynb`

## 2.5) Data Folder Convention (Updated)

All dataset files are now under `data/`.

- `data/wine.csv`
- `data/diabetes.csv`
- `data/pima-indians-diabetes.csv`

For Google Colab, uploaded files are often placed in `/content` first.
Move them to `/content/data` so notebook paths are consistent:

```bash
mkdir -p /content/data
# Example for wine dataset
mv /content/wine.csv /content/data/wine.csv
```

## 3) Colab Dependency Guide

Common Colab/package ecosystem issues include:

- NumPy 2.x migration binary compatibility issues
- Version-sensitive behavior between `shap` and `xgboost`
- Runtime restart requirement after package installation

To reduce these issues, Surrogate notebooks use pinned versions in setup cells:

```python
# Surrogate notebooks pinned set
lime==0.2.0.1
scikit-image==0.25.2
shap==0.46.0
xgboost==2.1.4
```

## 4) Dependency Audit (2026-04-29)

Scope: full `*.ipynb` scan + targeted Surrogate notebook checks

### Verified

- `[0430]3.Surrogate_lab.ipynb`:
  - Setup/install cell exists
  - Uses `perf_counter` instead of `%%time`
  - Includes `fetch_openml` context for Boston fallback
- `[0430]4.Surrogate_solution.ipynb`:
  - Setup/install cell exists
  - Uses code/comments avoiding deprecated `reg:linear`
  - Uses `fetch_openml` fallback when `shap.datasets.boston()` is unavailable
- `[0430]1.Decision_Tree_lab.ipynb`, `[0430]2.Decision_Tree_solution.ipynb`:
  - Colab-ready `%pip install ...` pattern exists

### Notes

- If you import libraries before running the setup cell, version mismatches may occur.
- After package installation, restarting runtime is often required for clean behavior.
- Some optional/legacy plotting steps may require extra dependencies such as `graphviz` and `pdpbox`.

## 5) Troubleshooting

### Q. I get `ModuleNotFoundError`

1. Rerun the setup cell
2. Restart runtime
3. Rerun all cells from top to bottom

### Q. Installation succeeded, but behavior looks like old versions

Your runtime still has old modules in memory. Restart runtime and rerun all.

### Q. Colab session disconnected

Colab sessions are ephemeral. Save progress frequently to Google Drive.

## 6) Execution Rules

- Always run cells **top to bottom**
- Before sharing/submitting, do `Restart session -> Run all` to verify reproducibility
- Do not remove dependency/setup cells

