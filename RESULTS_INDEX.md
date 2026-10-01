# Main-figure data index

Paths are relative to the repository root. Only the three main figures are covered; appendix tables and full experimental protocols are outside this release.

| Figure | Image | Data | Script |
| --- | --- | --- | --- |
| Figure 1, `fig:method` | `figures/fig1_compatibility_map.png` | Conceptual schematic; no measured data | `draw_pra_compatibility_map.py` |
| Figure 2, `fig:kcbs_summary` | `figures/fig2_kcbs.png` | `result/kcbs_minibatch_fresh_repeats.csv`, `result/kcbs_minibatch_validation_trajectories.csv`, `result/kcbs_task_means.csv`, `result/curve_source.csv` | `update_learning_visuals.py` |
| Figure 3, `fig:chsh_summary` | `figures/fig3_chsh.png` | `result/chsh_success_events.csv`, `result/curve_source.csv` | `update_learning_visuals.py` |

## CSV fields and aggregation

- `kcbs_minibatch_fresh_repeats.csv`: `HD`, `repeat`, task-specific `CV_A`–`CV_E`, and `I_CV`, with retained diagnostic columns. Rows are repeat-level aggregates of fresh-probe evaluations. An averaged `replica` column is not a new independent replication identifier.
- `kcbs_minibatch_validation_trajectories.csv`: `HD`, `epoch`, `repeat`, `I_CV`, task-specific gaps, and retained task-success/loss diagnostics. Repeated epochs from the same repeat are not independent observations. This is the primary matched-minibatch validation trajectory, not the separate online-resampled full-batch control.
- `kcbs_task_means.csv`: rows A–E, columns HD 2–5. Saved task-level means used in the Figure 2 heatmap.
- `chsh_success_events.csv`: `repeat_idx`, `hidden_neurons`, `E4`, `task4_acc`, `one`, `both`, `neither`. The mutually exclusive success fractions sum to one; `one=(1-E4)/2` and `both=task4_acc-one/2`. These support Figure 3's success-composition bars.
- `curve_source.csv`: `series`, `metric`, `x`, `mean`, `low`, `high`. `low` and `high` are the saved 95% bootstrap confidence limits for plotted means; they are not standard deviations. The original plotting analysis used 10,000 bootstrap resamples with seed 49271 and 20 independent repeats for each plotted point. This release reuses the saved limits rather than recalculating every interval.

Figure 2 series: `Synthetic: fresh` / `I_CV`; `MNIST: held out` / `global_icv`; `HD=2`–`HD=5` / `I_CV`. Figure 3 series: `Synthetic` / `S`; `MNIST: matched carriers` / `S`.

The synthetic CHSH primary scan and the matched MNIST carrier scan are not automatically held-out generalization evidence. Refer to the manuscript for their distinct evaluation protocols. The release contains saved plotting statistics, not every observation necessary to independently recompute the underlying analyses.
