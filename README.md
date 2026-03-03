# Fixed Income ETF Relative Value Trading During COVID

A systematic long/short ETF relative-value strategy deployed during the March–June 2020 liquidity crisis.

This project documents a live trading framework that exploited temporary breakdowns in normally stable spread relationships between highly correlated fixed income ETFs.

Full Research Paper (PDF): [Fixed Income ETF Relative Value Trading During COVID](./Fixed_Income_ETF_Relative_Value_Trading_During_COVID.pdf)

---

## Overview

During March 2020, the COVID shock triggered one of the fastest liquidity crises in modern financial history. 

Credit markets seized, dealer balance sheets contracted, and fixed income ETFs began trading at persistent and unusually large discounts to NAV. 

While traditional ETF arbitrage (price vs. NAV) requires bond inventory and balance sheet capacity, this strategy focused on a more accessible opportunity:

**Relative mispricings between economically substitutable ETFs.**

The result was a market-neutral, statistically driven spread strategy that generated strong risk-adjusted returns during a period of extreme market stress.

---

## Strategy Framework

### Core Idea

Fixed income ETFs exhibit extremely high cross-sectional correlation (often 95–99%+).

During normal markets:
- Spread deviations are small
- Convergence occurs intraday
- Deviations rarely exceed ±2 standard deviations

During March–May 2020:
- Spreads widened dramatically
- Deviations frequently exceeded 5–10σ
- Convergence extended from minutes to multiple days

These distortions created unusually favorable statistical arbitrage conditions.

---

## Trade Construction

1. Identify ETF pairs with:
   - Same asset class
   - Similar duration and credit profile
   - Identical or overlapping benchmarks
   - Historical correlation > 0.95

2. Estimate hedge ratio using:
   - Average price ratio over observation window  
   - (Avoiding OLS on daily changes due to microstructure noise)

3. Enter position:
   - Long ETF trading at larger discount
   - Short relatively richer ETF
   - Market beta minimized via hedge ratio calibration

4. Exit on:
   - Spread normalization
   - Opportunity reallocation
   - Risk/time limits

Positions were diversified across many independent spreads.

---

## Performance Summary

Period: ~6 months (March–August 2020)

| Metric | Result |
|--------|--------|
| Gross Return | 21% |
| CAGR | 55% |
| Sharpe Ratio | 3.4 |
| Max Drawdown | -1.8% |
| t-stat | 2.3 |
| Trades | ~1,800 |
| Capital Deployed | ~$100,000 |
| Dollar Turnover | ~$30MM |

Characteristics:

- 65–70% of trades intraday  
- Majority of P&L from small, repeatable convergences  
- Low correlation to equity or credit beta  
- Minimal directional exposure  

---

## Why the Opportunity Existed

Several structural factors converged:

- Dealer balance sheet constraints (e.g., SLR pressure)
- Forced deleveraging across credit markets
- Impaired ETF creation/redemption mechanism
- Large number of economically redundant products
- Underlying bond illiquidity vs continuous ETF liquidity

Under normal conditions, arbitrage compresses ETF spreads within minutes.

During the crisis, convergence horizons extended to days, temporarily allowing smaller capital bases to monetize mispricings typically absorbed by institutional arbitrage desks.

---

## Risk Profile

Primary risks included:

- Further spread widening before convergence (margin risk)
- Liquidity gaps
- Short availability constraints
- Hedge ratio miscalibration
- Regime normalization eliminating opportunity set

The strategy emphasized:

- Small position sizing per spread
- Diversification across many pairs
- Continuous monitoring of spread stability

---

## Implementation

Research and execution framework built in Python:

- Pandas-based screening and signal generation
- Real-time ETF price monitoring
- Automated spread tracking
- Scripted execution workflow
- Statistical deviation detection

Operational advantages of ETF structure:

- Continuous exchange liquidity
- Tight bid-ask spreads
- Transparent pricing
- Reliable short availability
- No bond inventory required

---

## Key Lessons

- ETF pricing relationships can temporarily decouple from fundamentals during liquidity shocks
- Microstructure noise meaningfully distorts OLS-based hedge ratio estimation
- Relative-value positioning offers more controlled risk than directional exposure
- Crisis environments often produce the clearest statistical edges
- Execution speed and operational readiness are critical

---

## Additional Materials

Full paper including:

- Structural ETF analysis
- Statistical breakdown of spread behavior
- Correlation studies
- Distribution analysis of σ extremes
- Convergence horizon comparison (normal vs crisis)
- Capacity and liquidity analysis

→ [Download Full Research Paper (PDF)](./Fixed_Income_ETF_Relative_Value_Trading_During_COVID.pdf)

   

For a list of current fixed income ETFs available in the market right now see [ETF.com Bond ETF Channel](https://www.etf.com/channels/bond-etfs)
