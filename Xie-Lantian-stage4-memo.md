# Final Analysis Memo — Apple Inc. Accounting Ratio Review

**Company:** Apple Inc. (AAPL)
**Analyst:** Lantian Xie, Financial Analyst — Strategic Finance
**Date:** May 1, 2026
**Audience:** CFO, VP Finance, Director of FP&A
**Classification:** Internal / Finance

---

## A. Company & Data Summary

This memo concludes a four-stage ratio analysis of **Apple Inc.** for fiscal year 2024 (52-week period ended September 28, 2024) with prior-year comparatives drawn from FY2023 (ended September 30, 2023). All financial statement data is sourced from Apple's Form 10-K filed with the SEC on November 1, 2024 (via SEC EDGAR), supplemented by Apple Investor Relations for share data and Yahoo Finance for closing market price.

The supporting model — `Lantian-Xie-stage2-model.xlsx` — computes 30+ ratios across six categories using a named-range architecture documented in `stage3-spec-Xie.md`. Two analyst-supplied assumptions materially affect interpretation: a placeholder cost of capital of 10.0% and an effective tax rate of 24.1% (elevated above Apple's normalized ~15.8% rate by a one-time EU State Aid charge in FY2024).

---

## B. Ratio Results Summary

| Category | Ratio | FY2024 Value | Read |
| --- | --- | ---: | --- |
| **Performance** | Market Value Added (MVA) | $3,856,786M | Massive value creation |
| | Market-to-Book | 68.73x | Distorted high — buyback effect |
| | Economic Value Added (EVA) | $57,034M | Positive even at 10% WACC |
| **Profitability** | ROA (avg) | 26.1% | World-class |
| | ROC (avg) | 57.6% | World-class |
| | ROE (avg) | 157.4% | Mechanically inflated by buybacks |
| **Efficiency** | Asset Turnover | 1.11x | Solid for hardware-led business |
| | Days Sales Outstanding | 27.5 days | Tight collection |
| | Days in Inventory | 11.0 days | Best-in-class supply chain |
| | Operating Margin | 31.5% | Premium pricing flowing through |
| **Leverage** | Total Debt Ratio | 84.4% | High — but mechanically driven |
| | Debt-to-Equity | 1.51x | Manageable on its own |
| | Times Interest Earned | 34.2x | Effortless coverage |
| | Equity Multiplier | 6.41x | Buyback-driven |
| **Liquidity** | Current Ratio | 0.87x | Sub-1 by design |
| | Quick Ratio | 0.83x | Sub-1 by design |
| | Cash Ratio | 0.37x | Worth monitoring |
| **Du Pont** | Margin × Turnover × Multiplier | 24.0% × 1.109 × 5.67 | = 150.8% (matches direct ROE) |

---

## C. Interpretation & Key Findings

Five findings warrant CFO attention:

**1. Apple is unambiguously creating economic value.** EVA of $57.0B at a conservative 10% WACC, paired with $3.86T in Market Value Added, confirms that the gap between market expectations and book equity is supported by real after-tax operating earnings. Apple is not a "narrative" stock; the cash engine validates the multiple.

**2. The leverage and ROE figures are buyback artifacts and must be communicated as such.** Equity declined from $62.1B (FY2023) to $57.0B (FY2024) despite $93.7B in net income — a ~$99B return of capital to shareholders within the year. This shrinking denominator pushes ROE to 157% and the equity multiplier to 6.41x, but it does not reflect operational risk. The total debt ratio of 84.4% looks alarming in isolation; with $134.7B EBITDA and 34.2x interest coverage, it is not.

**3. Working capital efficiency is the most underappreciated operational strength.** Days in inventory of 11.0 — meaning Apple holds roughly 1.5 weeks of finished goods at any time — and a 27.5-day collection period reflect a supply chain that has compressed working capital to a structural minimum. This is the lever that frees up cash for buybacks, not the other way around.

**4. Liquidity ratios below 1.0 are structural, not stressed.** Negative net working capital of −$23.4B (NWC-to-assets of −6.4%) is sustained by accounts payable and deferred revenue financing operations. The cash ratio of 0.37x is the only liquidity figure with monitoring value: while $65.2B in cash and marketable securities is substantial in absolute terms, current liabilities of $176.4B mean Apple maintains a thinner cash buffer than industry norms would suggest.

**5. EVA is understated by approximately $7–9B due to the EU State Aid charge.** The 24.1% effective tax rate is elevated above Apple's normalized ~15.8% by a one-time provision related to the EU General Court's reversal of the State Aid decision. Normalizing the tax rate would lift after-tax operating income and EVA materially — a useful adjustment for internal performance attribution.

---

## D. Du Pont Analysis Discussion

The Du Pont decomposition produces a clean reconciliation:

> **ROE** = Net Margin × Asset Turnover × Equity Multiplier
> **150.8%** = 24.0% × 1.109 × 5.674

Each factor tells a different story.

**Margin (24.0%)** is strong but not the dominant driver. It reflects the durable pricing premium of the iPhone franchise and the higher-margin services mix, but margin alone would justify a healthy mid-teens ROE — not 150%.

**Asset turnover (1.109x)** is solid for a hardware-led business but unremarkable relative to pure software peers. It is consistent across the comparison years and is not where Apple is winning.

**Equity multiplier (5.674x)** is the dominant lever. This is not a product of new debt issuance — long-term debt actually fell from $95.3B to $85.7B in FY2024 — but of the buyback program eroding the equity base. The implication for the CFO is clear: Apple's reported ROE will continue to drift upward as long as buybacks outpace retained earnings, and the figure will become progressively less informative for cross-period or peer comparison without normalization.

A normalized-equity ROE — using, for example, average equity from FY2018 forward — would land in the 35–45% range. That is the figure that should anchor internal performance discussions and external IR communication.

---

## E. Strategic Recommendations

**1. Disclose normalized ROE alongside reported ROE in board and investor materials.** Reported ROE of 157% is mathematically correct but conceptually misleading and creates avoidable communication risk. A footnoted normalized figure (using a stable equity base) would let the market interpret the trend without requiring analysts to back into the buyback adjustment themselves.

**2. Promote free cash flow and cash return on invested capital (CROIC) as the primary internal performance metrics.** With $118.3B operating cash flow and $108.8B free cash flow on a $364.9B asset base, FCF-based ratios produce a roughly 30% cash return on assets that is unaffected by buyback distortion. This is a cleaner signal for FP&A target-setting and incentive design than ROE or ROA computed on shrinking equity.

**3. Implement a normalized-tax-rate toggle in EVA tracking.** Build a parallel EVA calculation using Apple's three-year average effective tax rate (~16%). The EU State Aid charge inflates GAAP tax expense in FY2024, depresses after-tax operating income by an estimated $7–10B, and contaminates the EVA series for the next three years of trend analysis unless adjusted.

**4. Hold long-term debt steady rather than continuing the FY2024 paydown.** Term debt declined by $9.5B year-over-year. Given a 24% effective tax rate and EBITDA-to-interest of 34x, the after-tax cost of marginal debt remains well below the equity cost. Continued paydown sacrifices tax shield without meaningfully improving credit profile (Apple is already at the strongest credit tier). Treasury should re-evaluate the optimal debt level using a formal capital-structure model in advance of the next major refinancing window.

---

## F. Executive Justification

**Financial health.** Apple's income statement and cash flow statement are operating in a different regime than the balance sheet would superficially suggest. The 84% total debt ratio reads as fragile only until paired with 34x interest coverage and $118B in annual operating cash flow. Health is excellent.

**Operational efficiency.** The combination of 11-day inventory and 27.5-day receivables reflects a supply chain operating near its theoretical floor for a global hardware business. Further marginal gains here are unlikely to be material; the operational focus should be defending the current state, not optimizing it further.

**Capital structure.** Apple has elected a leverage profile that prioritizes shareholder distributions over balance sheet conservatism. This is a defensible policy given the cash generation engine, but it does mean conventional leverage metrics will continue to look stressed and require normalization for any meaningful peer comparison.

**Liquidity position.** Structurally negative NWC is a feature, not a bug — but the cash ratio of 0.37x is the figure that deserves quarterly monitoring rather than annual review.

**Value creation track record.** EVA of $57B and MVA of $3.86T constitute the strongest single piece of evidence in this analysis. These are not narrative metrics; they are anchored in audited after-tax operating earnings and a market-validated equity value. They should feature prominently in the next investor day.

**Accounting and reporting implications.** Three figures in this analysis — ROE, the equity multiplier, and the total debt ratio — are mechanically distorted by capital return policy. Internal performance reporting should normalize for this distortion to preserve year-over-year comparability.

---

## G. Structured AI Prompt (Reproducibility Artifact)

The following prompt, when paired with this repository's spec file (`stage3-spec-Xie.md`) as context, will reproduce the Stage 2 spreadsheet model. It is provided as a standalone reproducibility artifact and to demonstrate the conversion of domain knowledge into machine-readable instruction.

---

```
# GOAL
Build an Excel workbook (.xlsx) computing 30+ accounting ratios for Apple Inc.
using FY2024 10-K data (52-week period ended September 28, 2024) with FY2023
comparatives. Output must include a Balance Sheet tab, an Income Statement tab,
a Cash Flow tab, a Market Data & Assumptions tab, and a Ratios tab. All ratio
formulas must reference workbook-level named ranges — no direct cell references.

# AUDIENCE
The deliverable will be reviewed by a CFO. Prioritize auditability, formula
transparency, and consistent formatting over visual flourish.

# COMPANY FINANCIAL DATA — ALL FIGURES IN $ MILLIONS UNLESS NOTED

## Balance Sheet (FY2024 / FY2023)
- Cash and cash equivalents:           29,943  / 29,965
- Marketable securities (current):     35,228  / 31,590
- Accounts receivable, net:            33,410  / 29,508
- Inventories:                          7,286  /  6,331
- Total current assets:               152,987  / 143,566
- Total assets:                       364,980  / 352,583
- Total current liabilities:          176,392  / 145,308
- Term debt (non-current):             85,750  / 95,281
- Total liabilities:                  308,030  / 290,437
- Total shareholders' equity:          56,950  / 62,146

## Income Statement (FY2024)
- Net sales:                          391,035
- Cost of sales:                      210,352
- Operating income (EBIT):            123,216
- Depreciation and amortization:       11,445
- EBITDA:                             134,661
- Interest expense (estimated):         3,600
- Income before taxes:                123,485
- Provision for income taxes:          29,749
- Net income:                          93,736

## Cash Flow Statement (FY2024)
- Cash from operating activities:     118,254
- Cash from investing activities:       2,935
- Cash from financing activities:    (121,983)
- Capital expenditures:                (9,447)

## Market Data & Analyst Assumptions
- Share price ($):                       258.90
- Shares outstanding (thousands):  15,116,786
- Market capitalization ($M):       3,913,736
- Cost of capital (WACC):                10.0%
- Effective tax rate:                    24.1%

# NAMED RANGE CONVENTIONS
Use these prefixes — do not invent alternatives:
- startYear_*    : prior-year (FY2023) balance sheet items
- currentYear_*  : current-year (FY2024) balance sheet items
- INC_*          : income statement flows (FY2024)
- CASH_*         : cash flow statement items (FY2024)
- avg_*          : two-year averages computed from start/current
- market_*       : market-data inputs
- tax_rate       : effective tax rate (single named cell)

Required named ranges (non-exhaustive): currentYear_cash, currentYear_mkt_sec,
currentYear_AR, currentYear_inv, currentYear_CA, currentYear_assets,
currentYear_CL, currentYear_lt_debt, currentYear_liab, currentYear_equity,
currentYear_nwc, currentYear_total_cap, startYear_assets_total, startYear_equity,
startYear_lt_debt, startYear_receivables, startYear_inventories,
startYear_total_cap, INC_revenue, INC_ebit, INC_ebitda, INC_net, INC_depr,
INC_interest, INC_daily_sales, INC_after_tax_op, avg_equity, avg_total_assets,
avg_total_cap, market_share_price, market_shares_out, market_cap, market_wacc,
tax_rate.

# DERIVED INPUTS (compute before ratios)
- INC_after_tax_op    = INC_ebit * (1 - tax_rate)
- INC_daily_sales     = INC_revenue / 365
- currentYear_nwc     = currentYear_CA - currentYear_CL
- currentYear_total_cap = currentYear_lt_debt + currentYear_equity
- startYear_total_cap   = startYear_lt_debt   + startYear_equity
- avg_equity            = (startYear_equity + currentYear_equity) / 2
- avg_total_assets      = (startYear_assets_total + currentYear_assets) / 2
- avg_total_cap         = (startYear_total_cap + currentYear_total_cap) / 2

# RATIO FORMULAS

## Performance
- MVA              = market_cap - currentYear_equity
- Market-to-Book   = market_cap / currentYear_equity
- EVA              = INC_after_tax_op - market_wacc * currentYear_assets

## Profitability (compute both start-of-year and average versions)
- ROA (SOY) = INC_net / startYear_assets_total
- ROA (avg) = INC_net / avg_total_assets
- ROC (SOY) = INC_after_tax_op / startYear_total_cap
- ROC (avg) = INC_after_tax_op / avg_total_cap
- ROE (SOY) = INC_net / startYear_equity
- ROE (avg) = INC_net / avg_equity

## Efficiency
- Asset Turnover         = INC_revenue / startYear_assets_total
- Receivables Turnover   = INC_revenue / startYear_receivables
- Avg Collection Period  = startYear_receivables / INC_daily_sales
- Inventory Turnover     = (INC_revenue - (INC_revenue - 210352)) / startYear_inventories
                            [equivalent: COGS / startYear_inventories]
- Days in Inventory      = 365 / Inventory Turnover
- Profit Margin          = INC_net / INC_revenue
- Operating Profit Margin= INC_ebit / INC_revenue

## Leverage
- Long-term Debt Ratio  = currentYear_lt_debt / (currentYear_lt_debt + currentYear_equity)
- Debt-Equity Ratio     = currentYear_lt_debt / currentYear_equity
- Total Debt Ratio      = currentYear_liab / currentYear_assets
- Times Interest Earned = INC_ebit / INC_interest
- Cash Coverage         = INC_ebitda / INC_interest
- Debt Burden           = INC_net / INC_ebit
- Leverage Ratio        = currentYear_assets / currentYear_equity

## Liquidity
- NWC-to-Assets  = currentYear_nwc / currentYear_assets
- Current Ratio  = currentYear_CA / currentYear_CL
- Quick Ratio    = (currentYear_CA - currentYear_inv) / currentYear_CL
- Cash Ratio     = (currentYear_cash + currentYear_mkt_sec) / currentYear_CL

## Du Pont Decomposition
- ROA Du Pont = (INC_net / INC_revenue) * (INC_revenue / startYear_assets_total)
- ROE Du Pont = (INC_net / INC_revenue)
              * (INC_revenue / startYear_assets_total)
              * (startYear_assets_total / startYear_equity)

# FORMATTING REQUIREMENTS
Apply consistent cell coloring across all tabs:
- YELLOW fill : raw input cells (any value the analyst types directly)
- BLUE fill   : assumption cells (WACC, tax rate)
- GREEN fill  : formula cells (anything derived)
- GRAY fill   : section headers and output summary cells

Use bold for tab titles and section headers. Use number format with thousands
separators for $ values and percentage format (1 decimal) for ratios stated as
percentages. Tab order: Balance Sheet, Income Statement, Cash Flow, Market Data
& Assumptions, Ratios.

# VERIFICATION CHECKS
The workbook must include three reconciliation checks on the Ratios tab:

1. Balance Sheet check (both years):
   currentYear_assets == currentYear_liab + currentYear_equity   → must equal zero
   startYear_assets_total == startYear_liab_total + startYear_equity → must equal zero

2. Du Pont vs. direct ROA:
   |ROA_DuPont - ROA_SOY| < 0.0001                               → must equal TRUE

3. Du Pont vs. direct ROE:
   |ROE_DuPont - ROE_SOY| < 0.0001                               → must equal TRUE

# OUTPUT
Return a single .xlsx file. Do not include narrative analysis — that is the
analyst's responsibility in the Stage 4 memo. Do include a Notes section on the
Ratios tab citing: SEC EDGAR, Apple FY2024 10-K filed November 1, 2024; the
$3,600M interest expense as an analyst estimate (per FY2023 10-K disclosure of
$3,933M scaled to FY2024 term debt levels); WACC as a 10% placeholder; and the
24.1% effective tax rate as elevated by the EU State Aid one-time charge.
```

---

*Prepared by: Lantian Xie, Financial Analyst — Strategic Finance*
*Distribution: CFO, VP Finance, Director of FP&A*
*Repository: https://github.com/LantianXie3/financial-analysis*
