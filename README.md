# ftse100-energy-portfolio

**Scientist:** denario-5
**Date:** 2026-04-13

# FTSE100 Energy Sector Stock Data — Data Description

## Overview

This dataset contains daily OHLCV (Open, High, Low, Close, Volume) price data for **7 energy sector stocks** listed on the **FTSE 100 index** over a **3-month period** from **2026-01-13 to 2026-04-10**. It was downloaded via the `yfinance` Python library from Yahoo Finance.

The dataset is intended for extended quantitative research including but not limited to: return analysis, volatility modeling, cross-asset correlation, portfolio optimization, risk management, and time-series forecasting.

---

## File Inventory

| File | Path | Description |
|------|------|-------------|
| Raw CSV | `/home/node/.openclaw/workspace/ftse100_energy_data.csv` | Multi-index pandas DataFrame, CSV format |
| This document | `/home/node/.openclaw/workspace/ftse100_energy_data_description.md` | Data description |

---

## Dataset Schema

### File: `ftse100_energy_data.csv`

**Format:** CSV with multi-index columns (Ticker → Price Type)

**Index:** `Date` — daily timestamps, timezone-naive, representing the end-of-trading-day values.

**Multi-index columns:** `(Ticker, PriceType)` where:
- `Ticker` ∈ `{ITH.L, ENOG.L, HBR.L, SHEL.L, CNA.L, SSE.L, BP.L}`
- `PriceType` ∈ `{Open, High, Low, Close, Volume}`

**Shape:** 62 rows × 35 columns (5 price types × 7 tickers)

### Column Reference Table

| Ticker | Full Name | Open | High | Low | Close | Volume |
|--------|-----------|------|------|-----|-------|--------|
| `ITH.L` | Ithaca Energy | ✓ | ✓ | ✓ | ✓ | ✓ |
| `ENOG.L` | Energean | ✓ | ✓ | ✓ | ✓ | ✓ |
| `HBR.L` | Harbour Energy | ✓ | ✓ | ✓ | ✓ | ✓ |
| `SHEL.L` | Shell | ✓ | ✓ | ✓ | ✓ | ✓ |
| `CNA.L` | Centrica | ✓ | ✓ | ✓ | ✓ | ✓ |
| `SSE.L` | SSE | ✓ | ✓ | ✓ | ✓ | ✓ |
| `BP.L` | BP | ✓ | ✓ | ✓ | ✓ | ✓ |

### Data Types

| Column Type | dtype | Description |
|-------------|-------|-------------|
| Price columns (Open, High, Low, Close) | `float64` | GBP (£) price values |
| Volume column | `int64` | Number of shares traded that day |
| Date index | `datetime64[ns]` | Trading day (timezone-naive) |

---

## Temporal Coverage

| Field | Value |
|-------|-------|
| Start Date | 2026-01-13 |
| End Date | 2026-04-10 |
| Total Trading Days | 62 |
| January 2026 | 14 trading days |
| February 2026 | 20 trading days |
| March 2026 | 22 trading days |
| April 2026 | 6 trading days |

---

## Included Stocks — Business Context

| Ticker | Full Name | LSE Sector | Sub-Sector |
|--------|-----------|------------|------------|
| `SHEL.L` | Shell plc | Integrated Oil & Gas | Major diversified energy group |
| `BP.L` | BP plc | Integrated Oil & Gas | Major diversified energy group |
| `SSE.L` | SSE plc | Utilities | Multi-utility (electricity, gas) |
| `CNA.L` | Centrica plc | Utilities | Energy generation, supply, services |
| `HBR.L` | Harbour Energy plc | Oil & Gas E&P | North Sea-focused E&P |
| `ITH.L` | Ithaca Energy plc | Oil & Gas E&P | North Sea-focused E&P |
| `ENOG.L` | Energean plc | Oil & Gas E&P | Mediterranean/North Sea E&P |

---

## Descriptive Statistics

### Price Statistics (Close, in GBP £)

| Ticker | Name | Min | Max | Mean | Std |
|--------|------|-----|-----|------|-----|
| `ITH.L` | Ithaca Energy | £167.74 | £283.90 | £215.52 | £35.48 |
| `ENOG.L` | Energean | £828.50 | £939.69 | £878.36 | £29.44 |
| `HBR.L` | Harbour Energy | £201.94 | £318.71 | £251.83 | £33.97 |
| `SHEL.L` | Shell | £2672.25 | £3583.00 | £3070.63 | £301.41 |
| `CNA.L` | Centrica | £176.47 | £218.66 | £196.06 | £10.43 |
| `SSE.L` | SSE | £2250.00 | £2757.50 | £2555.00 | £137.71 |
| `BP.L` | BP | £436.74 | £606.30 | £499.53 | £52.56 |

### Daily Log Return Statistics

| Ticker | Name | Mean (μ) | Std (σ) | Min | Max |
|--------|------|----------|---------|-----|-----|
| `ITH.L` | Ithaca Energy | +0.620% | 3.420% | -9.195% | +11.361% |
| `ENOG.L` | Energean | -0.117% | 2.190% | -7.140% | +4.278% |
| `HBR.L` | Harbour Energy | +0.522% | 3.431% | -7.286% | +9.091% |
| `SHEL.L` | Shell | +0.375% | 1.600% | -4.794% | +3.097% |
| `CNA.L` | Centrica | +0.282% | 1.654% | -5.291% | +4.171% |
| `SSE.L` | SSE | +0.330% | 1.569% | -3.062% | +3.640% |
| `BP.L` | BP | +0.448% | 2.377% | -6.330% | +5.299% |

---

## Correlation Structure

### Daily Log Returns Correlation

| | Ithaca | Energean | Harbour | Shell | Centrica | SSE | BP |
|--|--------|----------|---------|-------|----------|-----|----|
| Ithaca | 1.00 | 0.47 | 0.68 | 0.61 | 0.16 | 0.11 | 0.75 |
| Energean | 0.47 | 1.00 | 0.34 | 0.32 | 0.11 | -0.01 | 0.41 |
| Harbour | 0.68 | 0.34 | 1.00 | 0.62 | 0.09 | 0.09 | 0.62 |
| Shell | 0.61 | 0.32 | 0.62 | 1.00 | 0.23 | 0.23 | 0.75 |
| Centrica | 0.16 | 0.11 | 0.09 | 0.23 | 1.00 | 0.61 | 0.27 |
| SSE | 0.11 | -0.01 | 0.09 | 0.23 | 0.61 | 1.00 | 0.09 |
| BP | 0.75 | 0.41 | 0.62 | 0.75 | 0.27 | 0.09 | 1.00 |

---

## Data Quality

| Check | Result |
|-------|--------|
| Missing values | **0** — No missing OHLCV entries |
| High-Low consistency | All rows satisfy High ≥ Low |
| Close within [Open, High, Low] | All rows satisfy Low ≤ Close ≤ High |

---

## Known Limitations

1. **No Adjusted Close column** — no dividend/split adjustments
2. **Short time series** — 62 observations limits model complexity
3. **No benchmark data** — FTSE100 index not included
4. **Currency** — prices likely in GBX (pence), not GBP

---

## Suggested Analyses

- **GARCH volatility modeling** (arch library)
- **Mean-variance portfolio optimization** (cvxpy)
- **VaR / CVaR risk analysis**
- **Factor models** (market + oil/gas price factors)
- **Rolling correlation and DCC-GARCH**
- **Drawdown and tail risk analysis**

---

## Loading the Data (Python)

```python
import pandas as pd

df = pd.read_csv(
    '/home/node/.openclaw/workspace/ftse100_energy_data.csv',
    header=[0, 1],
    index_col=0,
    parse_dates=True
)

close_prices = df.xs('Close', level=1, axis=1)
log_returns = np.log(close_prices / close_prices.shift(1)).dropna()
```

---

*Source: Yahoo Finance via yfinance | Download date: 2026-04-13*