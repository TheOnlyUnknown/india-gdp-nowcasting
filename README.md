# India GDP Nowcasting — Mixed-Frequency Bayesian VAR

A macroeconomic nowcasting model that estimates Indian quarterly GDP growth 
in real-time using high-frequency monthly indicators, inspired by McCracken, 
Owyang & Sekhposyan (2020).

## What it does
Uses 5 monthly economic indicators to produce a GDP growth estimate before 
the official MOSPI release — updating the forecast as each new monthly 
datapoint arrives within the quarter.

## Indicators
| Series | Source | Transformation |
|--------|--------|----------------|
| Index of Industrial Production (IIP) | FRED | Log-change |
| Manufacturing PMI | FRED | Levels |
| Nifty 50 | Yahoo Finance | Log-change |
| CPI Inflation | FRED | Log-change |
| RBI Repo Rate | RBI / Manual | Levels |

## Methodology
- Mixed-frequency stacking (monthly indicators → quarterly blocks)
- Bayesian VAR with Minnesota prior and GLP hyperparameter selection
- Conditional forecasting via Waggoner & Zha (1999)
- Evaluated against AR(2) benchmark and RBI published projections

## Project Structure
```
india-gdp-nowcast/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_stacking.ipynb
│   ├── 03_var_baseline.ipynb
│   ├── 04_bayesian_var.ipynb
│   ├── 05_conditional_forecasting.ipynb
│   └── 06_scenario_analysis.ipynb
│
├── src/
│   ├── data_loader.py
│   ├── stacking.py
│   ├── minnesota_prior.py
│   ├── var_model.py
│   ├── conditional_forecast.py
│   └── evaluation.py
│
├── tests/
│
├── results/
│   ├── forecasts/
│   └── figures/
│
├── requirements.txt
└── README.md
```

## Status
- [x] Phase 1 — Data collection & stationarity
- [x] Phase 2 — Mixed-frequency stacking
- [x] Phase 3 — Baseline VAR
- [x] Phase 4 — Bayesian estimation
- [x] Phase 5 — Conditional forecasting (nowcasting engine)
- [ ] Phase 6 — Evaluation
