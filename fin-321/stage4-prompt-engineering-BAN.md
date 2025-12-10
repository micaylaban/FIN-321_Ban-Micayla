You are a financial technologist assistant.

# GOAL
Create a fully functional Excel workbook that models forward, money market, and option hedges for a EUR receivable of a U.S. Tech Services firm.

# CONTEXT FILES (GitHub)
Use the logic in:
- https://github.com/micaylaban/FIN-321_Ban-Micayla/blob/main/fin-321/stage2-spec-BAN.md
- https://github.com/micaylaban/FIN-321_Ban-Micayla/blob/main/fin-321/stage3-model-BAN.xlsx

# INPUT VARIABLES
- FC_AMT (EUR receivable) = 12,500,000
- S0 (spot rate, USD per EUR) = 1.1481
- F0 (1-year forward rate, USD per EUR) = 1.0910
- r_USD = 3.67%
- r_EUR = 2.13% 
- K_put = 1.1481
- K_call = 1.1481
- Premium_put = 0.017
- Premium_call = 0.022
- t (years to maturity) = 1.0

# SPREADSHEET REQUIREMENTS
1. Build a single workbook with at least one main worksheet named “Model”.
2. Organize the sheet into clearly labeled sections (use bold section headers): Inputs & Assumptions, Forward Hedge, Money Market Hedge, Option Hedges (Put & Call), Sensitivity Analysis (±5% in S₀), Checks & Summary / KPIs
3. Use named ranges only for key inputs and derived parameters.
4. Color code inputs yellow, assumptions blue, formulas green, outputs gray.
5. Include forward hedge, money market hedge, option hedge, and sensitivity analysis.
6. Use clean formatting and labeled outputs.

# NAMED RANGE DEFINITIONS
Create the following workbook-scope named ranges, each pointing to the appropriate cell:
1. Inputs & Assumptions (Yellow Cells):
- FC_AMT, S0, F0, r_USD, r_EUR, K_put, K_call, Premium_put, Premium_call, t
2. Derived/Helper Named Ranges (Green Cells):
(Used explicitly in the model logic and required for auditability.)
- PV_EUR, USD_current, CIP_forward, Difference, Proceeds_diff
- Premium_put_EUR, Premium_put_USD
- Premium_call_EUR, Premium_call_USD
3. Output/KPI Named Ranges (Gray Cells):
- USD_forward, USD_mm, USD_put, USD_call
  
Do not change the core naming above.

# MODEL LOGIC
Implement the following logic using Excel formulas that reference named ranges, not hard-coded numbers:
1. Forward Hedge: USD_forward = FC_AMT * F0
2. Money Market Hedge (3-Step Synthetic Forward)
- You will receive EUR in 1 year, so construct the money market hedge as:
  - PV_EUR = FC_AMT/(1 + r_EUR * t)
  - USD_current = PV_EUR * S0
  - USD_mm = USD_current * (1 + r_USD * t)
- Add a CIP check:
  - CIP_forward = S0 * (1 + r_USD * t)/(1 + r_EUR * t)
  - Difference = F0 - CIP_forward
  - Proceeds_diff = USD_mm - USD_forward
3. Option Hedges
- Assume one unit of EUR exposure per EUR of receivable (FC_AMT), with premiums interpreted consistently with Stage 3 logic:
  - Premium_put_EUR = FC_AMT * Premium_put
  - Premium_put_USD = Premium_put_EUR * S0
  - Premium_call_EUR = FC_AMT * Premium_call
  - Premium_call_USD = Premium_call_EUR * S0
- Define a generic maturity spot S_T (this will later be a column in the sensitivity table):
  - Put Hedge Payoff (Long EUR Put): USD_put_ST = FC_AMT*S_T + MAX(K_put - S_T,0)*FC_AMT - Premium_put_USD
  - Call Hedge Payoff (Long EUR Call): USD_call_ST = FC_AMT*S_T + MAX(S_T - K_call,0)*FC_AMT - Premium_call_USD
- Base Case:
  - USD_put  = USD_put_ST at S_T = S0
  - USD_call = USD_call_ST at S_T = S0
4. Sensitivity Analysis (±5% on S₀)
- Create a table with columns: S_T, Unhedged USD proceeds, Forward hedge USD proceeds, Money Market hedge USD proceeds, Put hedge USD proceeds, Call hedge USD proceeds
- S_T ranges from 0.95 × S0 to 1.05 × S0 in increments of 0.01.
- For each S_T compute: Unhedged USD proceeds, USD_forward, USD_mm, USD_put, USD_call

Forward and money-market outcomes must remain constant across S_T.

Include a line chart of USD proceeds vs S_T for: Unhedged, Forward, Money Market, Put Hedge, Call Hedge.

Organize each hedge in a clearly labeled section.

# FORMATTING & COLOR CODING
Apply consistent color coding throughout the workbook:
- Yellow: Inputs / decision variables
- Blue: Assumptions / parameters 
- Green: All formula cells (forward hedge, MM hedge, option payoffs, sensitivity calculations, CIP checks)
- Gray: Output / KPI cells (USD_forward, USD_mm, key base-case option results, summary comparisons, headline KPIs)
Use bold section headings for each numbered section.
Align numbers with appropriate formats:
- FX rates: 4–5 decimal places
- Interest rates: percentage with 2 decimal places
- Dollar amounts: standard currency format

# OUTPUT REQUIREMENTS
- Display base-case USD outcomes (Unhedged, Forward, MM, Put, Call)
- Comparison table (hedged vs unhedged)

# VERIFICATION
Verify:
- Forward ≈ Money Market
- CIP consistency
- All named ranges exist
- Formula audit table (cell, name, formula)

# EXPORT
Return a completed downloadable .xlsx file with formulas intact.
