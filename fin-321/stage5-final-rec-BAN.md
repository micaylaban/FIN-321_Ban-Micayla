# U.S. Tech Services Firm: Final Analysis & Recommendation

## A. Exposure Summary
The firm expects to receive a €12,500,000 EUR receivable in 12 months, which creates exposure to fluctuations in the EUR/USD exchange rate. A depreciation of the euro would reduce USD cash inflows, and negatively affect cash flow predictability and financial planning. The objective of this analysis is to evaluate hedging strategies that stabilize USD proceeds, and balance cost, risk, and flexibility.

---

## B. Summary of Hedge Outcomes
Three hedging approaches were evaluated using the Stage 4 spreadsheet model:
- Forward Hedge: Locks in a fixed EUR/USD rate, delivers known USD proceeds regardless of spot rate movements.
- Money Market Hedge: Creates a synthetic forward using interest rate parity. USD proceeds closely match the forward hedge, confirming covered interest parity.
- Option Hedge:
  - A EUR put option limits downside risk from euro depreciation while preserving upside potential.
  - A EUR call option is not well-suited for a receivable and underperforms in depreciation scenarios due to premium costs.

The forward and money market hedges provide the highest certainty, while the option hedge trades certainty for flexibility at a cost.

---

## C. Sensitivity Interpretation
Sensitivity analysis across ±5% changes in the EUR/USD rate at maturity reveals:
- EUR Depreciation:
  - Forward and money market hedges deliver stable USD proceeds.
  - The put hedge limits losses, but results in lower proceeds than the forward because of the premiums.
  - Unhedged exposure experiences significant decline.
- EUR Appreciation:
  - Unhedged and put-hedged positions benefit from upside.
  - Forward and money market hedges remain fixed, without gains.
    
Overall, certainty increases as flexibility decreases, which highlights the trade-off between protection and upside participation.

---

## D. Strategic Recommendation
Recommend: Forward Hedge
- The forward hedge best aligns with the firm’s objective of stabilizing future USD cash inflows. It provides full downside protection at no upfront cost and avoids the operational complexity of money market hedging. While option hedges offer upside participation, the premium cost reduces expected net proceeds and is not justified given the firm’s preference for predictability.

---

## E. Executive Justification
- Cash Flow Stability: Guarantees known USD proceeds, simplifying planning and budgeting.
- Budget Certainty: Removes FX volatility from earnings and performance metrics.
- Liquidity Efficiency: No upfront premium or borrowing required.
- Risk Alignment: Matches a conservative treasury risk profile focused on certainty instead of speculation.
- Accounting Simplicity: Easier hedge documentation and effectiveness testing relative to options.
 
---

# Areas for Further Study & Improvement
1. OpenAI Codex / Code Interpreter

OpenAI Codex helps reduce operational risk by allowing hedge models to be regenerated directly from written specifications. This minimizes spreadsheet errors, prevents accidental formula changes, and ensures that model logic remains consistent over time. Codex can also validate formulas and run extended scenario or sensitivity analysis, improving reliability and transparency in hedge evaluation.

2. GitHub Automation & Version Control

Version control records every change as a permanent and reversible revision, which prevents silent spreadsheet errors and improves transparency. In finance, this supports hedge accounting documentation and internal controls.
GitHub enables structured collaboration through branching, pull requests, and issue tracking, ensuring that model updates are reviewed before implementation. For this project, versioning the Stage 2-4 models and prompts ensures consistency, auditable model regeneration, and provides clear evidence for audits.

3. Accounting / Audit Integration

Hedge accounting requires clear documentation and reproducible calculations to determine whether gains and losses are recorded in OCI or P&L. Version-controlled models support this by providing a record of hedge assumptions, calculations, and updates. Therefore, GitHub serves as effective audit evidence and supports compliance with hedge accounting requirements.

