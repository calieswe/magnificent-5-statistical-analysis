# Statistical Analysis of the Magnificent 5 within the US Equity Market

## Overview

This project applies four statistical tests to compare the "Magnificent 5" US technology companies — Apple, Microsoft, Alphabet, Amazon, and Meta — against the wider universe of NASDAQ-listed companies. The goal was to test common retail-trader beliefs (such as "the giants are mostly Tech" and "Tech trades more actively") with quantitative evidence, and to assess whether the Magnificent 5 should be treated as a single homogeneous investment group.

Completed as part of the Programming for Data Analytics module on the Higher Diploma in Science in Data Analytics at the National College of Ireland.

## Dataset

Two complementary datasets were combined:

- **Magnificent 5 daily prices** — 5 years of OHLCV data for AAPL, MSFT, GOOGL, AMZN, and META (≈6,275 rows × 7 columns), pulled from Yahoo Finance via the `yfinance` Python library.
- **NASDAQ Screener** — Cross-sectional data on 7,047 NASDAQ-listed companies (11 columns including Sector, Industry, Market Cap, and Volume), obtained from the NASDAQ Stock Screener.

## Methods

The analysis is organised into four insights, each answering one research question:

1. **Descriptive analysis** — Cumulative returns, annualised volatility (standard deviation of daily returns × √252), and company-profile table merging time-series statistics with NASDAQ company attributes.
2. **Chi-square test of independence** — Tested whether sector and market-cap tier (Mega-Cap, Large-Cap, Mid-Cap, Small-Cap) are statistically independent. Cramér's V was calculated for association strength.
3. **One-way ANOVA** — Tested whether the five companies have statistically different mean daily returns.
4. **Welch's two-sample t-test** — Compared log-transformed trading volume between Technology and Finance sectors. Cohen's d was calculated for effect size.

Data preprocessing included flattening multi-index columns returned by `yfinance`, stripping currency and percentage symbols from text fields, and applying log transformation to right-skewed variables to stabilise variance.

## Key Findings

- The Magnificent 5 differ dramatically: total returns ranged from 58.6% (AMZN) to 230.7% (GOOGL); annualised volatility ranged from 26.4% (MSFT) to 43.9% (META); market caps ranged from $1.7T to $4.2T. They should not be treated as a single investment.
- **Sector × Market Cap Tier** are statistically dependent (χ² = 416.86, df = 33, p < 0.001), but the association is weak (Cramér's V = 0.148). Technology is the only sector overrepresented in Mega-Cap; Finance and Health Care are heavily concentrated in Small-Cap.
- The five companies have **statistically equivalent mean daily returns** (F = 0.15, p = 0.96) — the failure to reject the null suggests that day-to-day stock picking among them is closer to a coin toss than a skill.
- **Technology stocks trade roughly ten times more actively than Finance stocks** on NASDAQ (Welch's t = 19.15, p << 0.001, Cohen's d = 0.81, large effect size).

## Tools

- **Python** — pandas, NumPy, scipy.stats, matplotlib
- **yfinance** — Yahoo Finance API wrapper
- **Jupyter Notebook**

## Files

- `Swe Swe Aung_ID_25167219_Programming_Project_Report.pdf` — Full project report with methodology, results, and figures.
