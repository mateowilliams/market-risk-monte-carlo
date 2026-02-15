# market-risk-monte-carlo
Monte Carlo (GBM) simulation of YPF stock price with a SQLite ETL step and Value-at-Risk (VaR) estimation in Python.
# YPF Monte Carlo VaR (GBM + SQLite ETL)

**English:** Monte Carlo simulation of YPF stock price using **Geometric Brownian Motion (GBM)**, with a simple **SQLite ETL step** (post-2022 filtering) and **Value at Risk (VaR)** estimation.

**Español (resumen):** Simulación Monte Carlo (GBM) para proyectar el precio de YPF a 1 año, filtrando el régimen post-2022 con SQL y estimando riesgo (VaR).

---

## What this repo does
- Downloads historical **Adjusted Close** prices for `YPF` using `yfinance` (2020-01-01 → 2024-12-01)
- Stores data in **SQLite** and filters the series from **2022-01-01** onward (post-pandemic regime)
- Calibrates GBM parameters from **log-returns**
- Runs a **Monte Carlo simulation**:
  - Trading days: **252**
  - Paths: **1000**
- Produces:
  - Simulated price paths (first 100 shown for readability)
  - Terminal price distribution + reference lines (mean / today / VaR)
  - Summary metrics (expected return, probability of gain)

---

## Method (high level)
We model prices with **Geometric Brownian Motion**:

$
S_{t} = S_{t-1}\,\exp\Big((\mu - 0.5\sigma^2) + \sigma Z_t\Big)
$

where ($Z_t$) is a standard normal shock. Parameters are estimated from historical **log-returns**.

**VaR (95%) in this notebook** is computed as the **5th percentile of the terminal price distribution** (i.e., a price “floor” under this model).

---

## Quickstart

### 1) Install dependencies
```bash
pip install -r requirements.txt
