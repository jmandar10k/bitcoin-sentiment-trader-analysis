# Bitcoin Fear & Greed Index vs Hyperliquid Trader Performance

## Overview
This project explores the relationship between Bitcoin market sentiment
(Fear & Greed Index) and real trader behaviour on the Hyperliquid exchange.
The goal is to find whether traders perform better or worse depending on
the market mood — Fear, Greed, or somewhere in between.

---

## Datasets Used

| Dataset | Source | Description |
|---|---|---|
| Fear & Greed Index | Alternative.me | Daily sentiment score (0–100) for Bitcoin from Feb 2018 to May 2025 |
| Hyperliquid Trader Data | Hyperliquid | 211,224 trades by 32 traders across 246 coins from May 2023 to May 2025 |

---

## Project Structure

---

## Notebook Breakdown

### Notebook 1 — fear_greed_analysis.ipynb
Individual analysis of the Fear & Greed Index dataset.
- Shape, dtypes, null check, duplicate check
- Date range and missing day check
- Numerical EDA on `value` column — describe, KDE, histogram, boxplot, skewness
- Categorical EDA on `classification` — value counts, pie chart
- Conclusions

### Notebook 2 — trades_analysis.ipynb
Individual analysis of the Hyperliquid historical trades dataset.
- Date column created from `Timestamp IST`
- 7 unnecessary columns dropped (IDs, duplicate timestamp, Side, Size Tokens)
- Shape, dtypes, null check, duplicate check
- Numerical EDA — Execution Price, Size USD, Start Position, Closed PnL, Fee
- Categorical EDA — Account, Coin, Direction, Crossed
- Conclusions

### Notebook 3 — merged_analysis.ipynb
Main analysis notebook — merging both datasets and answering the core question.
- Both datasets cleaned then merged on `date` column
- 106,816 open trades filtered out — only closed trades used for PnL analysis
- 12 analyses performed:
  1. Trade volume by sentiment
  2. Average PnL per trade by sentiment
  3. Win rate by sentiment
  4. Total realised PnL by sentiment
  5. Average trade size by sentiment
  6. Long vs Short bias by sentiment
  7. PnL distribution boxplot by sentiment
  8. Net PnL after fees by sentiment
  9. Monthly PnL trend vs Fear/Greed index over time
  10. Top 10 traders by total PnL
  11. Top traders PnL heatmap by sentiment
  12. Top 10 coins by total PnL

---

## Key Findings

- **Fear days generated the most total profit ($3.36M)** — high volume combined with solid per-trade returns
- **Extreme Greed had the highest win rate (89.2%)** — traders are selective at market peaks
- **Traders deploy largest positions during Fear ($7,816 avg)** — treating fear as a buying opportunity
- **Long bias flips during Greed** — 65% long during Fear vs 42% long during Greed — clear contrarian behaviour
- **Top trader made $2.14M** over 2 years, most of it during Fear periods

## Overall Insight
> Hyperliquid traders follow a contrarian strategy — buying more during Fear with larger positions and reducing exposure during Greed. The data strongly supports the classic market wisdom: *"Be greedy when others are fearful, be fearful when others are greedy."*

---

## How to Run

1. Clone the repository
```bash
git clone https://github.com/jmandar10k/bitcoin-sentiment-trader-analysis.git
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn
```

3. Run notebooks in order
---

## Tools Used
- Python 3
- Pandas — data manipulation and merging
- NumPy — numerical operations
- Matplotlib — charts and visualisations
- Seaborn — statistical plots
- Jupyter Notebook — analysis environment