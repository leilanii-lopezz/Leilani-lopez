# Stage 5 — Validation Analysis

**Student:** Leilani Lopez  
**Scenario:** 37 — Solar Inverters  
**Date:** November 27, 2026  
**Exposure:** EUR 5,400,000 receivable in 273 days

## 1. Independent AI Execution

A fresh temporary ChatGPT conversation was supplied with the Stage 2 specification and revised Stage 4 market-data memo. The Excel workbook was excluded. No follow-up coaching or corrections were provided.

The original AI response is preserved in [Independent AI Execution](2026-11-27-solar-inverters-ai-execution.md).

## 2. Workbook and AI Comparison

The following tables compare the saved workbook results against the independent AI calculations. All amounts are USD, rounded to two decimal places.

### EUR Depreciation: -5% (1.044240 USD/EUR)

| Strategy | Workbook | AI | Difference |
|---|---:|---:|---:|
| No hedge | 5,638,896.00 | 5,638,896.00 | 0.00 |
| Forward | 6,348,240.00 | 6,348,240.00 | 0.00 |
| Money market | 5,997,514.98 | 5,997,514.98 | 0.00 |
| Put option | 5,810,500.51 | 5,810,500.51 | 0.00 |
| Call payable | Not tabulated | Not tabulated | N/A |

### Baseline (1.099200 USD/EUR)

| Strategy | Workbook | AI | Difference |
|---|---:|---:|---:|
| No hedge | 5,935,680.00 | 5,935,680.00 | 0.00 |
| Forward | 6,348,240.00 | 6,348,240.00 | 0.00 |
| Money market | 5,997,514.98 | 5,997,514.98 | 0.00 |
| Put option | 5,810,500.51 | 5,810,500.51 | 0.00 |
| Call payable | 6,145,802.71 | 6,145,802.71 | 0.00 |

### EUR Appreciation: +5% (1.154160 USD/EUR)

| Strategy | Workbook | AI | Difference |
|---|---:|---:|---:|
| No hedge | 6,232,464.00 | 6,232,464.00 | 0.00 |
| Forward | 6,348,240.00 | 6,348,240.00 | 0.00 |
| Money market | 5,997,514.98 | 5,997,514.98 | 0.00 |
| Put option | 6,107,284.51 | 6,107,284.51 | 0.00 |
| Call payable | Not tabulated | Not tabulated | N/A |

Workbook references: Sensitivity rows 5, 10 and 15, columns B–F; Call Option cell B9.

AI references: Sections 4, 5 and 7 of the preserved response.

## 3. Independent Arithmetic Verification

All calculations use simple interest and ACT/360. Intermediate values are retained at full precision before rounding.

### A. Forward Hedge

USD proceeds = FC_AMT × F0_in

= 5,400,000 × 1.1756

= $6,348,240.00

Workbook reference: Forward!B4.

### B. Money-Market Hedge

USD accumulation factor:

1 + 0.046 × (273/360) = 1.0348833333

EUR accumulation factor:

1 + 0.03193 × (273/360) = 1.0242135833

Step 1: Borrow EUR today.

5,400,000 / 1.0242135833 = EUR 5,272,337.81

Step 2: Convert borrowed EUR to USD.

5,272,337.8091 × 1.0992 = $5,795,353.72

Step 3: Invest USD until settlement.

5,795,353.7198 × 1.0348833333

= $5,997,514.98

Workbook references: Money Market!B4:B6.

### C. Put Option at -5% Settlement Spot

Settlement spot = 1.0992 × 0.95 = 1.044240

Upfront premium:

5,400,000 × 0.0224 = $120,960.00

Financed premium:

120,960 × 1.0348833333 = $125,179.488

Because settlement spot is below the strike, exercise the put.

Net proceeds:

5,400,000 × MAX(1.044240, 1.0992) - 125,179.488

= $5,810,500.51

Workbook references: Put Option!B4:B8 and Sensitivity!F5.

### D. Supplemental Call-Option Verification

The call represents a hypothetical EUR payable, not a hedge for the assigned receivable.

Financed premium:

5,400,000 × 0.0376 × 1.0348833333

= $210,122.712

USD outlay = 5,400,000 × MIN(settlement spot, 1.0992) + 210,122.712

| Settlement spot | Independently calculated outlay |
|---|---:|
| 1.044240 | $5,849,018.71 |
| 1.099200 | $6,145,802.71 |
| 1.154160 | $6,145,802.71 |

These supplemental values are calculated from the documented formula. They are not presented as original AI outputs or observed workbook sensitivity cells.

## 4. Discrepancy Analysis

The four receivable strategies agree between the workbook and AI at all three selected settlement rates to the nearest cent.

The baseline call-option payable calculation also agrees. However, the original AI response and workbook sensitivity table do not tabulate call-option outlays at the two endpoint rates. Section 3D supplies these additional calculations without modifying the original AI evidence.

The independent AI response could not verify Excel-specific named ranges or workbook formatting because the workbook was intentionally excluded.

Agreement between the AI and workbook confirms computational consistency but does not independently establish the accuracy of the market-data sources.

## 5. Covered Interest Parity

Implied forward:

1.0992 × 1.0348833333 / 1.0242135833

= 1.1106509214 USD/EUR

Assigned forward: 1.175600 USD/EUR

Signed rate gap:

1.1106509214 - 1.175600 = -0.0649490786

USD proceeds gap:

5,997,514.9754 - 6,348,240.00

= -$350,725.02

The absolute rate difference exceeds the 0.0001 tolerance.

This is a documented parity exception rather than an arithmetic failure. The assigned forward quote and imperfectly matched interest-rate proxies are retained transparently.

The historical Euribor observations supporting the revised EUR rate require final source confirmation.

## 6. Workbook Validation

| Check | Result |
|---|---|
| Forward arithmetic | PASS |
| Money-market arithmetic | PASS |
| Forward parity tolerance | FLAG |
| Put floor | PASS |
| Grid count | PASS |
| Grid endpoints | PASS |
| Premium cost sign | PASS |

The saved Checks worksheet confirms these results.

The revised workbook restores named-range references in core input, money-market, option and sensitivity formulas.

## 7. Validation Conclusion

The workbook and independent AI execution agree on the principal hedge outcomes and strategy rankings.

The forward provides the highest proceeds in all eleven modeled sensitivity scenarios. It exceeds the money-market hedge by $350,725.02 and the net put-option floor by $537,739.49.

The recommendation remains conditional on confirming the executability of the assigned forward quote and the underlying market-data assumptions.
