# Stage 5 — Hedge Decision Memo

**To:** Chief Financial Officer  
**From:** Leilani Lopez, Treasury Analyst  
**Date:** November 27, 2026  
**Subject:** Foreign Exchange Hedging Recommendation — Scenario 37, Solar Inverters

## Executive Recommendation

I recommend hedging 100% of the EUR 5,400,000 receivable using the assigned 273-day forward contract, conditional on confirming that the quoted rate of 1.1756 USD/EUR is executable.

The forward secures $6,348,240 in USD proceeds and outperforms every alternative receivable strategy across all eleven modeled exchange-rate scenarios. It provides the strongest combination of cash-flow stability, budget certainty and modeled financial performance.

## A. Exposure Summary

The company expects to receive EUR 5,400,000 in 273 days from a solar inverter transaction. Because the company's exposure is measured in USD, depreciation of the euro would reduce the dollar value of the receivable.

At the November 19 reference exchange rate of 1.0992 USD/EUR, the receivable is worth $5,935,680 before hedging.

The analysis assumes that protecting USD cash flow and supporting reliable financial planning are management's primary risk-management objectives.

The available strategies include remaining unhedged, entering a forward contract, implementing a money-market hedge and purchasing a EUR put option. A EUR call is included separately as a hypothetical payable comparison.

## B. Hedge Outcomes

| Strategy | Baseline USD Proceeds | Guaranteed Proceeds |
|---|---:|---:|
| Unhedged | $5,935,680.00 | None established |
| Forward | $6,348,240.00 | $6,348,240.00 |
| Money market | $5,997,514.98 | $5,997,514.98 |
| Put option | $5,810,500.51 | $5,810,500.51 |

### Unhedged Position

Remaining unhedged avoids upfront hedging costs and allows the company to benefit fully from euro appreciation. However, it exposes the business to potentially significant reductions in USD revenue.

A 5% euro depreciation reduces proceeds to $5,638,896, representing a $296,784 decline from the baseline. This uncertainty could complicate operating budgets and liquidity planning.

### Forward Hedge

The forward locks in $6,348,240 without an upfront option premium under the model assumptions.

It provides $412,560 more than the baseline unhedged position and $350,725.02 more than the money-market hedge.

Its primary disadvantage is the loss of potential gains if the settlement exchange rate exceeds the contracted forward rate.

### Money-Market Hedge

The money-market hedge generates fixed proceeds of approximately $5,997,514.98 by borrowing euros, converting the borrowed amount to dollars and investing the dollars until maturity.

Although this eliminates exchange-rate uncertainty, it generates lower proceeds than the assigned forward and introduces borrowing, investment and balance-sheet requirements.

### Put-Option Hedge

The put option establishes a minimum net USD receipt of $5,810,500.51 while preserving participation in euro appreciation.

This flexibility requires an upfront premium of $120,960, equivalent to $125,179.49 at settlement.

The premium reduces the guaranteed proceeds and makes the option less attractive when management prioritizes cash-flow certainty over speculative upside.

### Call-Option Comparison

For a hypothetical EUR payable, the call limits maximum net USD outlay to $6,145,802.71.

However, the assigned exposure is a receivable. The call therefore serves as an educational comparison rather than an appropriate standalone hedge for this transaction.

## C. Sensitivity Interpretation

The sensitivity analysis evaluates eleven settlement exchange rates ranging from 5% depreciation to 5% appreciation relative to the initial spot rate.

| Strategy | EUR -5% | Baseline | EUR +5% |
|---|---:|---:|---:|
| Unhedged | $5,638,896.00 | $5,935,680.00 | $6,232,464.00 |
| Forward | $6,348,240.00 | $6,348,240.00 | $6,348,240.00 |
| Money market | $5,997,514.98 | $5,997,514.98 | $5,997,514.98 |
| Put option | $5,810,500.51 | $5,810,500.51 | $6,107,284.51 |

The forward and money-market strategies eliminate settlement exchange-rate variability. The put protects against depreciation while retaining appreciation potential, and the unhedged position remains fully exposed to currency movements.

The forward produces the highest proceeds in all eleven modeled scenarios.

The unhedged position does not outperform the forward until the settlement rate exceeds 1.1756 USD/EUR, approximately 6.95% above the initial spot rate.

The put does not outperform the forward until the settlement exchange rate exceeds approximately 1.198781 USD/EUR, representing appreciation of approximately 9.06%.

Both break-even thresholds lie outside the modeled sensitivity range.

These findings support the forward recommendation. However, the sensitivity grid is not a probability forecast and does not establish that larger currency movements are impossible.

## D. Recommendation and Covered Interest Parity

I recommend entering a forward contract covering the entire EUR 5,400,000 receivable, subject to confirming the quoted rate and contractual terms.

The assigned forward quote and the covered-interest-parity implied forward do not agree.

| Parity Metric | Result |
|---|---:|
| Assigned forward rate | 1.175600 USD/EUR |
| CIP-implied forward rate | Approximately 1.110651 USD/EUR |
| Implied minus assigned rate | Approximately -0.064949 USD/EUR |
| Money-market minus forward proceeds | -$350,725.02 |

The difference is economically material and exceeds the specified parity tolerance.

Possible explanations include the illustrative nature of the assigned forward quote, differences between the selected financing instruments and executable borrowing rates, and imperfect maturity matching.

The revised EUR interest-rate assumption uses an interpolated nine-month Euribor proxy of 3.193% rather than the original ECB policy rate. The historical observations supporting this proxy require final source confirmation.

The parity discrepancy does not establish a guaranteed arbitrage opportunity. The model excludes transaction costs, financing spreads and counterparty-specific pricing.

Under the assigned scenario assumptions, the discrepancy does not change the recommendation because the forward continues to provide the highest guaranteed proceeds.

However, it changes the execution process. Treasury must obtain a confirmed executable forward quote before committing to the transaction. If the actual quote differs materially, the hedge comparison should be recalculated.

## E. Executive Justification

### Cash-Flow Stability and Budget Certainty

The forward removes uncertainty over the USD value of the receivable, allowing management to plan operating expenditures, investment decisions and cash requirements using a fixed expected receipt.

### Liquidity

The forward avoids the upfront option premium and the explicit borrowing and investment transactions required by the money-market hedge under the model assumptions.

Actual collateral, credit and counterparty requirements should be confirmed before execution.

### Optionality and Premium Cost

The put option offers valuable flexibility if management expects substantial euro appreciation. However, that flexibility costs $125,179.49 in settlement-date terms.

The modeled appreciation required for the put to outperform the forward lies beyond the specified sensitivity range. Consequently, the option's additional flexibility does not justify its premium under the assumed risk-management objective.

### Implementation

Before executing the hedge, Treasury should:

1. Confirm the EUR receivable amount and settlement date.
2. Obtain an executable 273-day forward quote.
3. Verify counterparty credit terms, collateral requirements and transaction costs.
4. Recalculate the strategy comparison if executable pricing differs materially from the assigned assumptions.
5. Monitor changes in the timing or amount of the receivable.

## Conclusion

The forward is the preferred strategy because it provides the highest guaranteed USD proceeds, eliminates exchange-rate uncertainty and outperforms all alternative receivable strategies throughout the modeled sensitivity range.

Subject to market-quote confirmation, hedging the full receivable provides the strongest financial outcome for a company prioritizing stable and predictable USD cash flow.

## Supporting Documentation

- [Validation Analysis](../../analysis/2026-11-27-solar-inverters-validation-analysis.md)
- [Independent AI Execution](../../analysis/2026-11-27-solar-inverters-ai-execution.md)
- [FX Hedging Workbook](../../capabilities/fx-hedging/model.xlsx)
