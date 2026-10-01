# Multitask probabilistic compatibility: selected figure data

Selected plotting materials for *Learning-dependent global probabilistic compatibility in multitask neural networks*, by Yi Zhou and Yuexian Hou.

This repository contains three main-figure PNGs, five processed plotting-data CSVs, and scripts for redrawing the main figures. It is a **selected figure-data release**, not the complete experimental dataset or training implementation.

## Contents

- `figures/`: Figure 1 at 450 dpi; Figures 2 and 3 at 400 dpi.
- `result/`: five CSVs supporting the main figures; no archive extraction is needed.
- `RESULTS_INDEX.md`: figure-to-data mapping and data-field descriptions.
- `draw_pra_compatibility_map.py`: conceptual Figure 1; no experimental dataset is needed.
- `update_learning_visuals.py`: Figures 2 and 3, using only the distributed CSVs.
- `PUBLIC_MANIFEST.csv` and `verify_public_data.py`: file-integrity verification.

Full experimental protocols, appendix-table datasets, training code, model checkpoints, and individual prediction arrays are not included. In particular, MNIST curves are provided as saved means and confidence intervals, not their underlying repeat-level observations. These materials support redrawing the figures, not recomputing every interval or independently reproducing all manuscript results. Publication or acceptance is not implied.

## Use

Download using **Code → Download ZIP** and extract the repository. From its root:

```sh
python3 verify_public_data.py
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
python3 draw_pra_compatibility_map.py
python3 update_learning_visuals.py
```

The verifier requires only Python's standard library. Plotting overwrites the three PNGs but never rewrites the five input CSVs. Work in a copy to preserve the downloaded images. Fonts and plotting-library versions may affect rendering. Curve means and confidence limits are read directly from `curve_source.csv`; the script does not retrain models or rerun the original bootstrap analysis.

The script name containing `pra` is historical and does not indicate publication in Physical Review A. The experiments involve classical multitask networks; their success-coded CHSH-type statistic is not a claim of physical Bell nonlocality.

No reuse license has been assigned. Please attribute the manuscript and source materials when referring to these results.

## Figures

![Figure 1: compatibility construction](figures/fig1_compatibility_map.png)

![Figure 2: KCBS-type learning evidence](figures/fig2_kcbs.png)

![Figure 3: CHSH-type capacity and success composition](figures/fig3_chsh.png)
