# Technical Specification — Accounting Ratio Analysis Model

**Company:** Apple Inc. (AAPL)
**Analyst:** Felix John, Financial Analyst — Strategic Finance
**Date:** April 24, 2026
**Audience:** CFO, Director of FP&A
**Classification:** Internal / Finance

---

## 1. Problem Statement

This specification documents a financial ratio model built for Apple Inc. covering fiscal year 2024 (52-week period ended September 28, 2024), with prior-year comparatives from fiscal year 2023 (ended September 30, 2023). The model computes 30+ ratios across six categories — Performance, Profitability, Efficiency, Leverage, Liquidity, and Du Pont decomposition — to support executive-level assessment of Apple's financial health, operational efficiency, and capital structure. All source data is drawn from Apple's FY2024 Form 10-K filed with the SEC on November 1, 2024.

---

## 2. Inputs (Known Variables)

### Balance Sheet Items

| Input | FY2024 ($M) | FY2023 ($M) | Named Range |
|-------|------------:|------------:|-------------|
| Cash and cash equivalents | 29,943 | 29,965 | `currentYear_cash` / prior |
| Marketable securities (current) | 35,228 | 31,590 | `currentYear_mkt_sec` |
| Accounts receivable, net | 33,410 | 29,508 | `currentYear_AR` / `startYear_receivables` |
| Inventories | 7,286 | 6,331 | `currentYear_inv` / `startYear_inventories` |
| Total current assets | 152,987 | 143,566 | `currentYear_CA` |
| Total assets | 364,980 | 352,583 | `currentYear_assets` / `startYear_assets_total` |
| Total current liabilities | 176,392 | 145,308 | `currentYear_CL` |
| Term debt (non-current) | 85,750 | 95,281 | `currentYear_lt_debt` / `startYear_lt_debt` |
| Total liabilities | 308,030 | 290,437 | `currentYear_liab` |
| Total shareholders' equity | 56,950 | 62,146 | `currentYear_equity` / `startYear_equity` |

### Income Statement Items

| Input | FY2024 ($M) | Named Range |
|-------|------------:|-------------|
| Net sales (revenue) | 391,035 | `INC_revenue` |
| Cost of sales | 210,352 | `INC_cogs` (via IS row) |
| Operating income (EBIT) | 123,216 | `INC_ebit` |
| Depreciation and amortization | 11,445 | `INC_depr` |
| EBITDA | 134,661 | `INC_ebitda` |
| Interest expense (estimated) | 3,600 | `INC_interest` |
| Income before taxes | 123,485 | via formula |
| Provision for income taxes | 29,749 | via formula |
| Net income | 93,736 | `INC_net` |

### Cash Flow Statement Items

| Input | FY2024 ($M) | Named Range |
|-------|------------:|-------------|
| Cash from operating activities | 118,254 | `CASH_operating` |
| Cash from investing activities | 2,935 | `CASH_investing` |
| Cash from financing activities | (121,983) | `CASH_financing` |
| Capital expenditures | (9,447) | `CASH_capex` |

### Market / Analyst Inputs

| Input | Value | Named Range |
|-------|------:|-------------|
| Share price | $258.90 | `market_share_price` |
| Shares outstanding (thousands) | 15,116,786 | `market_shares_out` |
| Market capitalization ($M) | 3,913,736 | `market_cap` |
| Cost of capital (WACC) | 10.0% | `market_wacc` |
| Effective tax rate | 24.1% | `tax_rate` |

---

## 3. Named Range Conventions

All named ranges follow a prefix-based hierarchy designed for auditability and AI prompt integration:

- **`startYear_`** — Prior-year balance sheet items (beginning of FY2024): `startYear_equity`, `startYear_assets_total`, `startYear_lt_debt`, `startYear_receivables`, `startYear_inventories`, `startYear_total_cap`.
- **`currentYear_`** — Current-year balance sheet items: `currentYear_equity`, `currentYear_assets`, `currentYear_CA`, `currentYear_CL`, `currentYear_cash`, `currentYear_lt_debt`, `currentYear_inv`, `currentYear_AR`, `currentYear_liab`, `currentYear_nwc`, `currentYear_total_cap`, `currentYear_mkt_sec`.
- **`INC_`** — Income statement flows: `INC_net`, `INC_ebit`, `INC_revenue`, `INC_interest`, `INC_depr`, `INC_ebitda`, `INC_daily_sales`, `INC_after_tax_op`.
- **`avg_`** — Computed averages of start/current year: `avg_equity`, `avg_total_assets`, `avg_total_cap`.
- **`market_`** — External market data: `market_share_price`, `market_shares_out`, `market_cap`, `market_wacc`.
- **`tax_rate`** — Effective tax rate derived from the income statement.

This naming structure allows any ratio formula to be expressed in plain pseudocode (e.g., `INC_net / startYear_equity` for ROE), making the spec directly translatable into both Excel formulas and AI prompt instructions.

---

## 4. Assumptions & Constraints

1. **Interest expense ($3,600M):** Estimated. Apple reports "Other income/(expense), net" as a single line on the income statement. The FY2023 10-K note disclosed $3,933M in interest expense; the FY2024 figure is scaled down proportionally to reflect lower outstanding term debt.
2. **WACC (10.0%):** Placeholder. A rigorous WACC would require Apple's levered beta, risk-free rate, equity risk premium, and after-tax marginal cost of debt — an exercise beyond Stage 2 scope.
3. **Effective tax rate (24.1%):** Computed from the income statement. This rate is elevated above Apple's typical ~15–16% effective rate due to a one-time charge related to the EU General Court's reversal of the State Aid decision ($10B+ tax impact in FY2024).
4. **Total capitalization:** Defined as long-term debt + shareholders' equity (excludes current-portion debt and operating lease obligations).
5. **Start-of-year convention:** All "start-of-year" items use the September 30, 2023 balance sheet, representing the opening position of FY2024.
6. **No off-balance-sheet adjustments:** Operating leases, purchase commitments, and contingent liabilities are excluded from leverage and liquidity calculations.
7. **Receivables scope:** Only "Accounts receivable, net" is used for turnover calculations. Apple's vendor non-trade receivables ($32.8B) are excluded as they represent supply-chain advances, not customer credit.

---

## 5. Calculation Flow

### 5.1 Derived Inputs

Before computing ratios, the model derives several intermediate values:

- `INC_after_tax_op` = `INC_ebit` × (1 − `tax_rate`)
- `INC_daily_sales` = `INC_revenue` / 365
- `market_cap` = `market_share_price` × `market_shares_out` / 1,000
- `currentYear_nwc` = `currentYear_CA` − `currentYear_CL`
- `currentYear_total_cap` = `currentYear_lt_debt` + `currentYear_equity`
- `startYear_total_cap` = `startYear_lt_debt` + `startYear_equity`
- `avg_equity` = (`startYear_equity` + `currentYear_equity`) / 2
- `avg_total_assets` = (`startYear_assets_total` + `currentYear_assets`) / 2
- `avg_total_cap` = (`startYear_total_cap` + `currentYear_total_cap`) / 2

### 5.2 Performance Ratios

| Ratio | Formula | FY2024 Result |
|-------|---------|---------------|
| Market Value Added (MVA) | `market_cap` − `currentYear_equity` | $3,856,786M |
| Market-to-Book | `market_cap` / `currentYear_equity` | 68.73x |
| Economic Value Added (EVA) | `INC_after_tax_op` − `market_wacc` × `currentYear_assets` | $57,034M |

### 5.3 Profitability Ratios

| Ratio | Formula | Start-of-Year | Average |
|-------|---------|---------------|---------|
| ROA | `INC_net` / assets | 26.6% | 26.1% |
| ROC | `INC_after_tax_op` / total capitalization | 59.4% | 57.6% |
| ROE | `INC_net` / equity | 150.8% | 157.4% |

Start-of-year denominators use `startYear_` values; average denominators use `avg_` values. The spread between them is small, confirming internal consistency.

### 5.4 Efficiency Ratios

| Ratio | Formula | FY2024 Result |
|-------|---------|---------------|
| Asset Turnover | `INC_revenue` / `startYear_assets_total` | 1.11x |
| Receivables Turnover | `INC_revenue` / `startYear_receivables` | 13.25x |
| Avg Collection Period | `startYear_receivables` / `INC_daily_sales` | 27.5 days |
| Inventory Turnover | COGS / `startYear_inventories` | 33.23x |
| Days in Inventory | 365 / Inventory Turnover | 11.0 days |
| Profit Margin | `INC_net` / `INC_revenue` | 24.0% |
| Operating Profit Margin | `INC_ebit` / `INC_revenue` | 31.5% |

### 5.5 Leverage Ratios

| Ratio | Formula | FY2024 Result |
|-------|---------|---------------|
| Long-term Debt Ratio | `currentYear_lt_debt` / (`currentYear_lt_debt` + `currentYear_equity`) | 60.1% |
| Debt-Equity Ratio | `currentYear_lt_debt` / `currentYear_equity` | 1.51x |
| Total Debt Ratio | `currentYear_liab` / `currentYear_assets` | 84.4% |
| Times Interest Earned | `INC_ebit` / `INC_interest` | 34.2x |
| Cash Coverage | `INC_ebitda` / `INC_interest` | 34.2x |
| Debt Burden | `INC_net` / `INC_ebit` | 0.76 |
| Leverage Ratio | `currentYear_assets` / `currentYear_equity` | 6.41x |

### 5.6 Liquidity Ratios

| Ratio | Formula | FY2024 Result |
|-------|---------|---------------|
| NWC-to-Assets | `currentYear_nwc` / `currentYear_assets` | −6.4% |
| Current Ratio | `currentYear_CA` / `currentYear_CL` | 0.87x |
| Quick Ratio | (`currentYear_CA` − `currentYear_inv`) / `currentYear_CL` | 0.83x |
| Cash Ratio | (`currentYear_cash` + `currentYear_mkt_sec`) / `currentYear_CL` | 0.37x |

Negative NWC and sub-1.0 current ratio are structurally consistent: Apple finances operations through payables and deferred revenue rather than maintaining excess current assets.

### 5.7 Du Pont Decomposition

**ROA = Profit Margin × Asset Turnover**
24.0% × 1.109 = **26.6%** ✓ Matches direct ROA (start-of-year)

**ROE = Profit Margin × Asset Turnover × Equity Multiplier**
24.0% × 1.109 × 5.674 = **150.8%** ✓ Matches direct ROE (start-of-year)

The Du Pont framework reveals that Apple's exceptional ROE is driven primarily by the equity multiplier (5.67x) — a consequence of aggressive share buybacks reducing the equity base — rather than margin expansion or asset efficiency alone.

---

## 6. Outputs

The model produces the following deliverables:

1. **Inputs Section:** Consolidated data pull from three financial statements plus market data, with all cells color-coded (yellow = editable input, green = formula, gray = header).
2. **Ratio Calculation Table:** 30+ ratios across six categories, each showing the computed value and its named-range formula for audit trail.
3. **Du Pont Verification:** Side-by-side comparison of decomposed vs. directly computed ROA and ROE, confirming internal consistency.
4. **Notes Tab:** Documentation of data sources (SEC EDGAR filing reference), assumptions, and reasonableness checks.

---

## 7. Model Review — What Worked & What to Improve

### What Worked

- **Named-range architecture:** The prefix convention (`startYear_`, `currentYear_`, `INC_`, `avg_`) made formula construction intuitive and the audit trail readable. Any formula can be understood without tracing cell references.
- **Du Pont reconciliation:** Both ROA and ROE decompositions match their directly computed counterparts exactly, confirming formula integrity across all six ratio categories.
- **Negative NWC consistency:** The model correctly reflects Apple's structural negative working capital, with the current ratio, NWC-to-assets, and quick ratio all telling a coherent story.
- **Color-coded layout:** The yellow/blue/green/gray convention follows financial modeling best practice and makes the model immediately navigable.

### What Should Be Improved

1. **Interest expense transparency:** The $3,600M interest expense is estimated because Apple buries it inside "Other income/(expense), net." A more rigorous model would extract the exact figure from the footnote disclosure in the FY2024 10-K (which was not yet available at the time of the FY2023 filing used for reference). Future iterations should source this directly.
2. **WACC calculation:** The 10% placeholder materially affects EVA. A proper build would compute WACC from Apple's beta (~1.2), the risk-free rate (~4.3%), equity risk premium (~5.5%), and after-tax cost of debt, yielding an estimate closer to 9–10%.
3. **Tax rate normalization:** FY2024's effective rate (24.1%) is distorted by the EU State Aid one-time charge. The model should offer a toggle between reported and normalized (~15.8%) tax rates, since the one-time charge cascades into after-tax operating income and EVA.
4. **Multi-year trend analysis:** The current model computes ratios for FY2024 only. Adding FY2023 and FY2022 ratio columns would enable trend identification — particularly valuable for efficiency and leverage metrics showing directional shifts.
5. **Peer benchmarking:** Ratios in isolation lack context. A companion column showing industry medians or a direct competitor (e.g., Microsoft or Samsung) would sharpen the analytical value for the CFO audience.
6. **Cash flow integration:** The model underutilizes the cash flow statement. Free cash flow, FCF yield, and cash return on invested capital (CROIC) would round out the performance picture, especially given Apple's $118B operating cash flow.
7. **Named range refinement:** Some names could be more descriptive for AI consumption — for instance, `INC_cogs` should be an explicit named range rather than requiring a direct cell reference to the Income Statement tab.

---

## 8. Limitations & Next Steps

**Excluded from this model:** Operating lease capitalization, goodwill/intangible adjustments, segment-level analysis, foreign currency impact decomposition, and forward-looking projections.

**Stage 4 integration:** This specification is designed to feed directly into the Stage 4 AI prompt. The Calculation Flow (Section 5) provides the instruction block — each ratio formula in named-range pseudocode can be dropped verbatim into a structured prompt. The Model Review (Section 7) supplies the improvement directives: normalize the tax rate, add multi-year trends, incorporate peer benchmarks, and expand into cash-flow-based metrics. The Outputs (Section 6) define the expected deliverable format for the final analysis memo to the CFO.

---

*Prepared by: Lantian Xie, Financial Analyst — Strategic Finance*
*Distribution: CFO, VP Finance, Director of FP&A*
