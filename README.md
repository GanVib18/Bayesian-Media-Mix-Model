# MapleThread MMM

A full-stack Bayesian Media Mix Modelling pipeline built from scratch for a fictional outdoor apparel brand — five global markets, four media channels, three years of weekly data.

 **[Medium Blog](https://medium.com/@gandhivibhuti1802/building-a-bayesian-media-mix-model-from-scratch-af14a2e4485b)**

---

## What's in this repo

| Phase | File | Description |
|-------|------|-------------|
| 1 | `code/data_generation.py` | Synthetic DGP with known ground truth — trend, Fourier seasonality, holiday spikes, channel spend, adstock & saturation transformations, revenue |
| 2 | `code/transformations.py` | Geometric adstock, Weibull adstock, Hill saturation — pure functions with full unit test suite |
| 3 | `code/single_region_model.py` | Single-region Bayesian MMM (Canada) in PyMC — prior predictive checks, NUTS sampling, diagnostics, parameter recovery |
| 4 | `code/hierarchical_model.py` | Full 5-region hierarchical extension with partial pooling and non-centered parameterisation |
| 5 | `code/posterior_analysis.py` | Channel attribution decomposition, response curves, marginal ROAS with credible intervals |
| 6 | `code/budget_optimization.py` | Posterior budget optimisation via SciPy SLSQP — optimal allocations with uncertainty, budget response curves |

---

## Key results

- **Zero MCMC divergences** across 4 chains × 1,000 draws; R-hat < 1.01 for all channel parameters
- **90% parameter recovery rate** — true DGP values fall inside the 94% HDI for 18 of 20 parameters
- **Consistent finding across all five markets**: reallocate from Social → Paid Search, estimated uplift of 8–15% revenue with no change to total budget
- Budget response curves show all markets are in aggregate diminishing returns — a 25% budget cut produces a less-than-proportional revenue decline

<img src="https://github.com/GanVib18/Bayesian-Media-Mix-Model/blob/main/graphs/fig_optimal_allocation.png">

---

## Stack

```
PyMC · ArviZ · NumPy · Pandas · SciPy · Matplotlib
```

---

## Quickstart

```bash
git clone https://github.com/yourname/Bayesian-Media-Mix-Model
cd Bayesian-Media-Mix-Model

python code/data_generation.py        # generates data/ outputs
python code/single_region_model.py    # Phase 3
python code/hierarchical_model.py     # Phase 4 — saves idata_hierarchical.nc
python code/posterior_analysis.py     # Phase 5
python code/budget_optimization.py    # Phase 6
```

---

## Repo structure

```
├── code/
│   ├── data_generation.py
│   ├── transformations.py
│   ├── single_region_model.py
│   ├── hierarchical_model.py
│   ├── posterior_analysis.py
│   └── budget_optimization.py
├── data/
│   ├── synthetic_raw.csv
│   └── ground_truth.csv
├── graphs/
├── LICENSE
└── README.md
```
