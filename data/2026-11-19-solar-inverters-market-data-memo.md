Stage 4 — Market Data Memo

Student: Leilani Lopez
Scenario: 37 — Solar Inverters
Market Data Date: November 19, 2026
Exposure: EUR 5,400,000 receivable in 273 days
Currency Convention: USD per EUR

1. Market Data Inputs

The following inputs were collected or retained for the FX hedging model.

Named Range

Value

Source

Date / Status

FC_AMT

EUR 5,400,000

Assigned Scenario 37

Contract input

S0_in

1.0992 USD/EUR

European Central Bank reference exchange rates

Nov. 19, 2026

F0_in

1.1756 USD/EUR

Assigned scenario forward quote

Retained

R_USD

4.60%

Federal Reserve H.15, 1-year Treasury constant maturity

Nov. 17, 2026

R_FC

2.65%

European Central Bank, main refinancing operations

Sept. 16, 2026 effective date

K_PUT

1.0992 USD/EUR

Set at the sourced spot rate

Nov. 19, 2026

K_CALL

1.0992 USD/EUR

Set at the sourced spot rate

Nov. 19, 2026

PREM_PUT

0.0224 USD/EUR

Assigned scenario premium

Retained

PREM_CALL

0.0376 USD/EUR

Assigned scenario premium

Retained

T_DAYS

273

Assigned Scenario 37

Contract input

Source links:

ECB exchange rates: https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html

Federal Reserve H.15: https://www.federalreserve.gov/releases/h15/

ECB key interest rates: https://www.ecb.europa.eu/stats/policy_and_exchange_rates/key_ecb_interest_rates/html/index.en.html

Retrieval: Sources were accessed on November 19, 2026, during the morning in the user's local time zone. Exact retrieval timestamps were not recorded.

2. Interest Rate Selection

The USD rate of 4.60% represents the most recently observed 1-year Treasury constant maturity yield from the Federal Reserve H.15 table.

The EUR rate of 2.65% represents the ECB main refinancing operations policy rate. It is used as a publicly documented EUR interest-rate proxy, although it is not a directly comparable 1-year market yield.

The two rates therefore do not represent perfectly matched financing instruments. The model uses them as transparent proxies and identifies this limitation.

3. Forward Rate and Covered Interest Parity

The assigned forward quote remains unchanged at 1.1756 USD/EUR.

The implied forward rate is calculated as:

F_IMPLIED = S0 × (1 + R_USD × 273 / 360) / (1 + R_FC × 273 / 360)

Using the selected market inputs:

F_IMPLIED = 1.115134 USD/EUR

Comparison:

Metric

Value

Assigned forward rate

1.175600

CIP-implied forward rate

1.115134

Implied minus assigned rate

-0.060466 USD/EUR

Assigned forward proceeds

$6,348,240.00

Money-market proceeds

$6,021,724.73

Money-market minus forward proceeds

-$326,515.27

The difference exceeds the model's parity tolerance. It is retained as a documented discrepancy rather than changing the assigned forward quote.

Possible contributing factors include the illustrative nature of the assigned quote and the use of non-matched interest-rate proxies.

4. Option Assumptions

Both option strikes are set equal to the sourced spot rate of 1.0992 USD/EUR.

The assigned put and call premiums remain unchanged. They are scenario-provided inputs rather than independently verified executable option prices.

The model carries upfront option premium costs forward to settlement using the USD interest rate.

5. Workbook Population and Validation

The Stage 3 workbook will be updated through its named input cells using the values documented above.

The following validation activities remain to be completed:

Recalculate all hedge proceeds using the sourced inputs.

Confirm that the sensitivity table and chart update around the new spot rate.

Review the Checks worksheet and document the forward-parity warning.

Compare the workbook outputs with the professor's FX Hedging Lab.

Record any formula corrections or differences identified during validation.

6. Data Limitations

The ECB reference spot rate is an indicative reference rate, not a guaranteed executable transaction quote.

The USD Treasury yield and ECB policy rate are proxies rather than matched 273-day borrowing and investment rates.

The assigned forward quote and option premiums have been retained in accordance with the scenario requirements.

These limitations should be considered when interpreting the hedging recommendation in Stage 5.

7. Status

Market inputs have been identified and documented. Workbook population, recalculation, and FX Hedging Lab cross-check are pending.
