# Nifty 500 Intraday Equity Backtest

An intraday long/short equity simulation covering **3 January 2022 to 16 September 2026**. Across 499 stocks with data, the backtest produced **₹87.05 lakh in net P&L** after modeled Upstox charges, using a fixed ₹10 lakh sizing base.

[Investor presentation (PDF)](Nifty500_OHL_Investor_Deck.pdf) · [Data and fee methodology](REPORT.md) · [Annual results (CSV)](annual_results.csv) · [Daily equity and drawdown (CSV)](daily_equity.csv)

## Backtest at a glance

| Measure | Simulated result |
| --- | ---: |
| Gross P&L | ₹103.87 lakh |
| Modeled trading charges | ₹16.82 lakh |
| Net P&L | ₹87.05 lakh |
| Closing simulated equity | ₹97.05 lakh |
| Cumulative net return on the ₹10 lakh base | 870.52% |
| Maximum end-of-day drawdown | 4.04% (₹71,986) on 5 July 2022 |
| Round-trip trades | 11,738 |
| Net win rate | 44.40% |
| Net profit factor | 1.63× |

## Equity and drawdown

![Simulated equity rose from ₹10 lakh to ₹97.05 lakh after modeled charges. The deepest end-of-day drawdown was 4.04% in July 2022.](equity_curve.png)

The equity curves accumulate daily P&L on the starting balance. The ₹10 lakh sizing base stayed fixed. Drawdown measures the percentage decline from the running peak in end-of-day equity after modeled charges.

## Annual results

| Calendar year | Round trips | Gross P&L (₹ lakh) | Charges (₹ lakh) | Net P&L (₹ lakh) |
| --- | ---: | ---: | ---: | ---: |
| 2022 | 2,458 | 18.90 | 3.54 | 15.37 |
| 2023 | 2,525 | 24.50 | 3.63 | 20.87 |
| 2024 | 2,466 | 24.14 | 3.56 | 20.58 |
| 2025 | 2,499 | 18.39 | 3.55 | 14.85 |
| 2026 through 16 September | 1,790 | 17.93 | 2.54 | 15.39 |
| **Total** | **11,738** | **103.87** | **16.82** | **87.05** |

Totals use unrounded values.

## Trading activity

| Side | Round trips | Net P&L (₹ lakh) |
| --- | ---: | ---: |
| Long | 6,689 | 51.70 |
| Short | 5,049 | 35.35 |

The simulation recorded trades in 386 stocks on 1,147 of 1,167 observed dates.

## How to read the results

- **Coverage.** The first trade occurred on 24 January 2022 after warm-up. The requested five-year window extends beyond the supplied data at both ends. MOTHERSON had no candles.
- **Execution and costs.** The backtest modeled execution using historical one-minute prices and applied modeled Upstox NSE equity intraday charges. Live fills, trading costs, and account returns can differ.
- **Universe and risk.** The fixed Nifty 500 membership snapshot can introduce survivorship bias. The simulation used the supplied price series without separate corporate-action adjustments or historical broker margin checks by stock. End-of-day drawdown can miss deeper intraday losses.
