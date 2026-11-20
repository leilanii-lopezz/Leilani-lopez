Stage 4 — FX Hedging Lab Cross-Check

Student: Leilani Lopez
Scenario: 37 — Solar Inverters
Date: November 19, 2026
Exposure: €5,400,000 receivable in 273 days

1. Purpose

This report compares the results of my Stage 4 Excel hedging model with the professor's FX Hedging Lab to validate calculations and identify differences.

2. Inputs

Input

Value

EUR receivable

€5,400,000

Spot exchange rate

1.0992 USD/EUR

Assigned forward rate

1.1756 USD/EUR

USD interest rate

4.60%

EUR interest rate

2.65%

Settlement

273 days

Put strike

1.0992 USD/EUR

Call strike

1.0992 USD/EUR

Put premium

0.0224 USD/EUR

Call premium

0.0376 USD/EUR

3. Results Comparison

Calculation

Excel Model

FX Hedging Lab

Result

Forward hedge proceeds

$6,348,240.00

$6,348,240

Match

Money-market hedge proceeds

$6,021,724.73

$6,021,725

Match after rounding

Put hedge net minimum proceeds

$5,810,500.51

$5,814,720

Difference identified

4. Put Option Difference

The Excel model calculates the put premium as follows:

Gross put premium today: $120,960.00

USD growth factor: 1.034883333

Financed put premium: $125,179.49

Gross minimum proceeds: $5,935,680.00

Net minimum proceeds: $5,810,500.51

The FX Hedging Lab reports $5,814,720, which equals gross minimum proceeds minus the unfinanced premium of $120,960.

Therefore, the difference of approximately $4,219.49 arises from the Excel model financing the option premium through settlement, while the lab appears to subtract the premium without financing it.

The Excel approach follows the Stage 3 model specification. The difference is documented rather than changing the existing formula.

5. Forward Parity Check

Assigned forward rate: 1.1756 USD/EUR

Implied forward rate: approximately 1.1151 USD/EUR

Forward hedge proceeds: $6,348,240.00

Money-market hedge proceeds: approximately $6,021,724.73

Difference (money market minus forward): approximately −$326,515.27

The assigned forward quote differs from the rate implied by the selected interest-rate inputs. The EUR rate is a policy-rate proxy rather than a matched-maturity borrowing rate, so this comparison is not sufficient to establish an arbitrage opportunity.

The workbook correctly flags the parity difference.

6. Validation Summary

All workbook checks passed except the forward parity flag.

The forward and money-market calculations matched the professor's lab after rounding. The put option difference was traced to the treatment of the premium's financing cost.

Conclusion: The reviewed calculations are consistent with the model's documented formulas. The identified differences are recorded for transparency. This cross-check does not establish that every workbook formula has been independently validated.
