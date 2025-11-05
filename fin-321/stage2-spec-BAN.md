# FIN-321_Ban-Micayla

# U.S. Tech Services Firm: Spec

**Created by:** Micayla Ban  
**Updated by:** Micayla Ban  
**Date Created:** November 4, 2025  
**Date Updated:** November 4, 2025  
**Version:** [0.0]
**LLM Used:"" [LLM] (optional if LLm used)

**Role:** Financial Analyst / Treasury Analyst  
**Audience:** CFO or Director of Treasury  

**Purpose:** Provide a professional, quantitative specification outlining the analytical structure for evaluating FX hedging alternatives.

---

## 1. Problem Statement

Our U.S. Tech Services firm expects to receive a foreign-currency receivable of  €12,500,000 in 12 months, which creates exposure to EURUSD exchange-rate risk. This specification outlines the analytical framework for quantifying, comparing, and evaluating hedging strategies to mitigate that risk. The objective is to protect the USD value of the receivable and balance certainty and cost, while aligning with the company’s corporate treasury hedging policy and overall cash flow protection goals.

---

## 2. Inputs (Known Variables)

| Variable | Description | Unit | Example | Source |
|-----------|-------------|------|----------|--------|
| `FC_AMT` | Foreign-currency receivable | EUR | 12,500,000 | Company data |
| `S₀` | Current EURUSD spot rate | USD/EUR | 1.1481 | Market data |
| `F₀` | 1-year EURUSD forward rate | USD/EUR | 1.0910 | Provided |
| `r_USD` | USD 1-year interest rate | % | 3.673 | Market data |
| `r_EUR` | EUR 1-year interest rate | % | 2.130 | Market data |
| `t` | Time to maturity | Years | 1 | Derived |
| `K_put` | EUR Put strike | USD/EUR | 1.1481 | Analyst choice |
| `K_call` | EUR Call strike | USD/EUR | 1.1481 | Analyst choice |
| `Premium_put` | Put premium | USD per contract | 0.017 | Scenario |
| `Premium_call` | Call premium | USD per contract | 0.022 | Scenario |

---

## 3. Assumptions & Constraints

1. Exchange rates are expressed as USD per EUR.
2. Interest rates are annual, simple-compounded for money-market parity checks.
3. The forward rate provided represents a 1-year maturity.
4. Single lump-sum collection exactly in 12 months (t = 1).
5. Option premiums are paid upfront in USD.
6. Transaction and credit costs are excluded from the analysis.
7. No early exercise or counterparty default is assumed.
8. All positions are held to maturity for consistency in comparison.
9. FX conversions and contract counts are rounded at the end, rather than after each step.

---

## 4. Calculation Flow

1. Forward Hedge
- Compute USD proceeds using the forward rate (F₀).
- Treat this as the certainty benchmark.
2. Money Market Hedge
- Construct a synthetic forward using interest rate parity:
-   Borrow or lend in EUR and USD at respective interest rates.
-   Cross-validate proceeds against the forward hedge outcome.
3. Options Hedge
- Model two cases:
-   EUR Put: provides downside protection for EUR depreciation.
-   EUR Call: provides upside participation for EUR appreciation.
- Deduct option premiums to obtain net USD proceeds under varying S_T.
4. Sensitivity Analysis
- Vary EURUSD spot rate at maturity (S_T).
- Compare all three hedge outcomes (Forward, Money Market, Option).
5. Summary Evaluation
- Present comparative results in tables and a line chart.
- Discuss trade-offs between certainty, optionality, and cost.

---

## 5. Outputs

| Output | Description | Format | Purpose |
|---------|--------------|---------|----------|
| `USD_forward` | USD proceeds from forward hedge | Numeric | Certainty benchmark |
| `USD_mm` | USD proceeds from money market hedge | Numeric | Cross-check against forward |
| `USD_put` | USD proceeds from EUR put hedge | Table | Sensitivity & protection |
| `USD_call` | USD proceeds from EUR call hedge | Table | Optional upside case |
| `Comparison_table` | Summary of USD outcomes across all hedges | Table | Highlights relative performance |
| `Chart_1` | Hedge outcomes vs. S_T | Line chart | Visual comparison |
| `Summary` | Written conclusion | 1–2 paragraphs | Executive-ready takeaway |

---

## 6. Sensitivity Plan

1. Variable tested: EURUSD spot rate at maturity (S_T).
2. Range: 0.95×S₀ to 1.05×S₀ (in increments of 0.01).
3. Procedure:
- Compute USD proceeds for each hedge across the range of S_T values.
- Record and visualize differences in performance.
4. Visualization: Present as a comparison table and line chart of USD proceeds vs. S_T.

---

## 7. Limitations & Next Steps

This specification assumes stable market conditions and excludes implied volatility, transaction costs, and credit risk. The model does not account for potential timing mismatches or basis risk between hedge and cash flow settlement dates. The next step will involve building an Excel model implementing this calculation logic to quantify outcomes under each hedge strategy. 

---

## 8. References

“EUR 1 Year IRS Interest Rate Swap .” Investing.Com, www.investing.com/rates-bonds/eur-1-year-irs-interest-rate-swap. Accessed 5 Nov. 2025.

“EUR/USD (EURUSD=x) Live Rate, Chart & News.” Yahoo! Finance, Yahoo!, 5 Nov. 2025, finance.yahoo.com/quote/EURUSD=X/. 

“U.S. 1 Year Treasury.” CNBC, CNBC, www.cnbc.com/quotes/US1Y. Accessed 5 Nov. 2025. 


