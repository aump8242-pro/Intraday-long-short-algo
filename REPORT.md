# Nifty 500 intraday equity backtest

The historical simulation earned **₹87.05 lakh net** on a **₹10 lakh fixed sizing base** after **₹16.82 lakh in modeled Upstox NSE equity intraday charges**. Simulated closing equity was ₹97.05 lakh. The sizing base stayed fixed throughout the run.

## Coverage

| Item | Coverage |
|---|---|
| Requested period | 23 November 2021 to 23 November 2026 |
| Supplied data used | 3 January 2022 to 16 September 2026 |
| First trade after indicator warm-up | 24 January 2022 |
| Universe | 499 stock files from the supplied Nifty 500 list. MOTHERSON had no candles. |
| Sessions | 1,167 observed dates, with trades on 1,147 |
| Stock files | 195,952,675 source rows. One shifted row was recovered. Sessions containing any of 91 invalid rows or 2 duplicate rows were excluded for the affected stock. |

The requested period extends beyond the supplied files at both ends. The universe uses the supplied membership snapshot throughout, which can introduce survivorship and membership bias. Daily OHLCV was reconstructed from the minute candles as supplied. The replay used no separate corporate-action adjustments or historical broker margin checks by stock.

## Results

| Metric | Result |
|---|---:|
| Gross P&L | ₹103.87 lakh |
| Trading charges | ₹16.82 lakh |
| Net P&L | ₹87.05 lakh |
| Cumulative net return on ₹10 lakh | 870.52% |
| Annualized equity return over available data | 62.17% |
| Maximum end-of-day net drawdown | ₹71,986 (4.04%), trough on 5 July 2022 |
| Round-trip trades | 11,738 |
| Net trade win rate | 44.40% |
| Net trade profit factor | 1.63 |

| Year | Trades | Gross P&L | Charges | Net P&L |
|---|---:|---:|---:|---:|
| 2022 | 2,458 | ₹18.90L | ₹3.54L | ₹15.37L |
| 2023 | 2,525 | ₹24.50L | ₹3.63L | ₹20.87L |
| 2024 | 2,466 | ₹24.14L | ₹3.56L | ₹20.58L |
| 2025 | 2,499 | ₹18.39L | ₹3.55L | ₹14.85L |
| 2026 through 16 September | 1,790 | ₹17.93L | ₹2.54L | ₹15.39L |

![Gross and net equity curves with end-of-day drawdown](equity_curve.png)

## Trading activity and execution

The simulation recorded 6,689 long round trips and 5,049 short round trips across 386 stocks. Long trades contributed ₹51.70 lakh net and short trades contributed ₹35.35 lakh net.

The backtest modeled execution using historical one-minute prices. Actual fills and trading costs can differ from the model. Drawdown uses end-of-day equity and can miss larger intraday losses.

## Charges

The model uses published standard Upstox brokerage of ₹20 or 0.1% per order, whichever is lower, throughout. All orders reached the ₹20 cap. It includes sell-side STT at 0.025%, buy-side stamp duty at 0.003%, SEBI fees at ₹10 per crore, NSE turnover charges and IPFT, and 18% GST on brokerage, exchange charges and IPFT. NSE exchange and IPFT rates change by effective date, using the base member tariff before October 2024. Amounts are modeled on executed turnover without contract-note rounding. [Upstox pricing](https://upstox.com/brokerage-charges/) · [NSE 2021 tariff](https://archives.nseindia.com/content/circulars/FA46730.pdf) · [NSE April 2023 tariff](https://archives.nseindia.com/content/circulars/FA56129.pdf) · [NSE April 2024 tariff](https://nsearchives.nseindia.com/content/circulars/FA61137.pdf) · [NSE October 2024 tariff](https://nsearchives.nseindia.com/content/circulars/FA64232.pdf) · [NSE March 2026 tariff](https://nsearchives.nseindia.com/content/circulars/FA73061.pdf)

## Files and verification

[Daily equity](daily_equity.csv) · [Annual results](annual_results.csv)

The underlying trade ledger was reconciled to daily, annual and aggregate P&L.
