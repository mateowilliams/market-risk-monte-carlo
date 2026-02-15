# 📉 Financial Risk Simulation: YPF (Monte Carlo + GBM)

> **Summary:** Monte Carlo simulation (GBM) of YPF prices (252 trading days, 1,000 paths) + VaR estimation.

## 📌 Overview
I simulate the evolution of YPF’s price using **Geometric Brownian Motion (GBM)** calibrated with **log returns** from **January 2022** onward (post-pandemic regime), and estimate risk via **Value at Risk (VaR 95%)**.

## 🧪 Data
- Source: `yfinance`
- Ticker: `YPF`
- Window: 2020–2024 (filtered from 2022 onward using SQL)

## 🧠 Method
1. Download adjusted prices (`Adj Close`)
2. Store + filter data in **SQLite** (`WHERE Date >= '2022-01-01'`)
3. Estimate parameters (μ, σ) from log returns
4. Run Monte Carlo simulation (252 days, 1,000 paths)
5. Metrics: terminal price distribution, **VaR (95%)**, probability of profit

## 🚀 Quickstart
```bash
pip install -r requirements.txt
jupyter notebook
