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

1. Rates/quotes: 
- Exchange rates are expressed as USD per EUR
- Interest rates are annual, simple-compounded for money-market parity checks
- F₀ is the 1-year outright forward EURUSD
2. Cash flow timing: Single lump-sum collection exactly in 12 months (t = 1)
3. Premiums: Option premiums are paid upfront in USD
4. Credit/transaction costs: Excluded
5. Taxes/accounting: Not modeled
6. Liquidity: Sufficient market liquidity to execute at total value
7. Rounding: FX conversions and contract counts are rounded at the end, rather than after each step
8. Sensitivity grid: Tests different EURUSD rates at maturity around the current spot rate

---

## 4. Calculation Flow

Describe the logic and sequencing of your analysis — as if briefing a junior analyst or AI model builder. Focus on **order of operations**, not formulas.

Example flow:
1. Compute USD proceeds under the forward hedge.  
2. Recreate a synthetic forward using money market parity to validate rates.  
3. Compute option hedge outcomes for both the EUR put and EUR call under varying spot outcomes \(S_T\).  
4. Compare USD results across hedges at the base case and across sensitivity scenarios.  
5. Summarize the trade-offs (certainty vs. optionality vs. cost).  

> *Your goal: anyone reading this section should know exactly how to implement your logic in Excel or code — without you explaining formulas.*

---

## 5. Outputs

| Output | Description | Format | Purpose |
|---------|--------------|---------|----------|
| `USD_forward` | USD proceeds from forward hedge | Numeric | Certainty benchmark |
| `USD_mm` | USD proceeds from money market hedge | Numeric | Cross-check against forward |
| `USD_put` | USD proceeds from EUR put hedge | Table | Sensitivity & protection |
| `USD_call` | USD proceeds from EUR call hedge | Table | Optional upside case |
| `Chart_1` | Hedge outcomes vs. S_T | Line chart | Visual comparison |
| `Summary` | Written conclusion | 1–2 paragraphs | Executive-ready takeaway |

---

## 6. Sensitivity Plan

Define how you will test and visualize FX outcomes.

Example:
> Vary EURUSD spot at maturity \(S_T\) from 0.95×S₀ to 1.05×S₀ in increments of 0.01.  
> For each value, compute USD proceeds under all hedge strategies.  
> Present results as a comparison table and line chart.

> *Professional analysts always test sensitivity — it shows how robust their recommendations are.*

---

## 7. Limitations & Next Steps

Briefly note any analytical limits (e.g., volatility ignored, credit risk excluded) and outline your immediate next step (e.g., model build in Stage 3).

Example phrasing:
> This specification does not incorporate implied volatility or transaction costs. The next phase will involve constructing an Excel model implementing this logic to quantify results under each hedge structure.

---

