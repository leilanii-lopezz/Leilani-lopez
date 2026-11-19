Stage 3 — FX Hedging Model Audit Report

Student: Leilani Lopez
Scenario: 37 — Solar Inverters
Project: FX Transaction Hedging Model
Exposure: EUR 5,400,000 receivable in 273 days

1. Audit Objective

The purpose of this audit was to review the AI-assisted Excel hedging model against the Stage 2 technical specification, identify calculation and implementation errors, and verify that the workbook produces reliable results for the four strategies: no hedge, forward hedge, money-market hedge, and EUR put-option hedge.

2. Audit Findings and Corrections

Finding 1 — Excel Named-Range Formula Errors

Issue: The initial workbook displayed #NAME? errors across the Inputs, Forward, Money Market, Put Option, Call Option, Sensitivity, and Checks worksheets.

Cause: Excel was not correctly resolving some named-range references used in the generated formulas.

Correction: The workbook was revised to use direct references to the Inputs worksheet while retaining the named ranges for documentation and consistency.

Verification: The corrected workbook was reopened in Excel, and the previously reported #NAME? errors were no longer present.

Finding 2 — Forward and Money-Market Parity Discrepancy

Issue: The assigned forward rate of 1.1756 USD/EUR did not match the forward rate implied by the illustrative USD and EUR interest rates.

Cause: The model uses an illustrative USD interest rate of 5.30% and EUR interest rate of 3.10%, which are not consistent with the assigned forward quote under covered interest-rate parity.

Correction: The workbook retains the assigned forward rate and calculates the money-market hedge independently. The Checks worksheet identifies the difference rather than forcing the results to match.

Verification: The forward-parity tolerance check displays "FLAG - illustrative rates differ." This is an expected input inconsistency, not an indication that the hedge formulas failed.

Finding 3 — Preliminary Base-Case Calculation Differences

Issue: The preliminary money-market and put-option proceeds in the Stage 2 specification differed from the revised workbook calculations.

Correction: The workbook calculates both strategies directly from the specified inputs, including the settlement-date financing cost of the put premium.

Verified workbook values:

Strategy

Base-Case USD Proceeds

No hedge

$5,940,000.00

Forward

$6,348,240.00

Money market

$6,036,822.86

Put option

$5,814,178.42

Verification: The recalculated results were compared with the specification's formulas, and the workbook's other validation checks displayed PASS.

3. Validation Summary

The completed workbook was reviewed for formula errors, hedge calculations, sensitivity analysis, and validation results.

The corrected workbook displayed no #NAME? errors in the previously affected cells.

The Sensitivity worksheet contained a line chart comparing the four receivable strategies.

The Checks worksheet displayed PASS for the calculation and consistency checks, with the expected forward-parity flag.

The forward-parity discrepancy was retained and documented for future review when market inputs are verified in Stage 4.

4. AI Assistance and Human Review

ChatGPT (GPT-6) assisted with generating the initial Excel workbook, correcting formula references, reviewing the hedge calculations, and drafting this audit report.

The student opened and reviewed the workbook in Excel, identified and reported the formula errors, verified the corrected workbook, confirmed the sensitivity chart was present, and reviewed the validation results.

5. Conclusion

The Stage 3 workbook has been revised following the identified formula errors and calculation discrepancies. The corrected model supports the required hedge comparisons and sensitivity analysis.

The forward-parity difference remains flagged because the illustrative interest rates do not match the assigned forward quote. This limitation should be revisited when market data is verified during Stage 4.
