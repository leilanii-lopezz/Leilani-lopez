Stage 4 — Market Data Memo

Student: Leilani Lopez
Scenario: 37 — Solar Inverters
Market Data Date: November 19, 2026
Exposure: EUR 5,400,000 receivable in 273 days
Currency Convention: USD per EUR
Revision: November 27, 2026 — Stage 5 preparation

1. Market Data Inputs

Named Range

Value

Source

FC_AMT

EUR 5,400,000

Assigned scenario

S0_in

1.0992

ECB reference rate, Nov. 19

F0_in

1.1756

Assigned forward quote

R_USD

4.60%

Federal Reserve H.15, Nov. 17

R_FC

3.193%

Interpolated nine-month Euribor proxy

K_PUT

1.0992

Sourced spot rate

K_CALL

1.0992

Sourced spot rate

PREM_PUT

0.0224

Assigned scenario

PREM_CALL

0.0376

Assigned scenario

T_DAYS

273

Assigned scenario

BASIS

360

Model convention

Source links:

ECB exchange rates: https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html

Federal Reserve H.15: https://www.federalreserve.gov/releases/h15/

Bank of Finland: https://www.suomenpankki.fi/en/

Original market data retrieval occurred on November 19, 2026. Exact retrieval timestamps were not recorded.

2. Interest Rate Selection

The USD rate of 4.60% represents the one-year Treasury constant maturity yield.

Following Stage 4 feedback, the original ECB policy rate of 2.65% was replaced with an estimated nine-month Euribor proxy of 3.193%, based on interpolation between six-month and twelve-month rates of 3.043% and 3.343%, respectively. The underlying historical observations require final source confirmation.

The revised maturity proxy better reflects the 273-day exposure, although the USD and EUR rates remain imperfectly matched financing instruments.

3. Forward Rate and Covered Interest Parity

The assigned forward quote remains unchanged.

F_IMPLIED = S0 × (1 + R_USD × 273 / 360) / (1 + R_FC × 273 / 360)

Metric

Revised value

Assigned forward rate

1.175600

CIP-implied forward rate

1.110651

Implied minus assigned rate

-0.064949

Assigned forward proceeds

$6,348,240.00

Money-market proceeds

$5,997,514.98

Money-market minus forward proceeds

-$350,725.02

The revised EUR rate reduces money-market proceeds by $24,209.75 relative to the original Stage 4 results.

The parity difference exceeds the model tolerance. It is retained and disclosed rather than eliminated by modifying assigned scenario inputs.

4. Option Assumptions

Both option strikes equal the sourced spot rate of 1.0992 USD/EUR.

Assigned option premiums remain unchanged. They are illustrative scenario inputs rather than independently verified executable prices.

Upfront premiums are carried forward to settlement using the USD interest rate.

5. Workbook Population and Validation

The workbook has been populated with the revised market inputs. Named-range references have been restored in the core money-market, option, input and sensitivity formulas.

The corrected workbook contains 11 sensitivity scenarios. All arithmetic, put-floor, grid-count, grid-endpoint and premium-sign checks pass. The forward-parity check retains its intentional flag.

The original Stage 4 FX Hedging Lab comparison is historical evidence. The revised workbook requires a new independent comparison during Stage 5.

6. Data Limitations

The ECB reference exchange rate is indicative rather than executable.

The USD Treasury yield and interpolated Euribor rate are financing proxies.

The assigned forward quote and option premiums are retained as scenario inputs.

The observed parity gap should not be interpreted as a guaranteed executable arbitrage opportunity.

7. Status

Workbook population and recalculation are complete. Stage 5 independent AI execution, reconciliation and decision analysis remain to be completed.
