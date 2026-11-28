# **Stage 5 — Independent AI Hedge Analysis**

**Scenario:** 37 — Solar Inverters\
**Exposure:** EUR 5,400,000 receivable\
**Settlement horizon:** 273 days\
**Market data date:** November 19, 2026\
**Currency convention:** USD per EUR

## **1. Independent Execution Methodology**

This analysis uses only the Stage 2 technical specification and the revised Stage 4 market-data memo. All hedge outcomes are independently calculated from the specified formulas and updated inputs, without relying on the existing Excel workbook's calculated outputs.

The analysis compares four strategies: no hedge, forward hedge, money-market hedge, and EUR put-option hedge. The EUR call option is treated as a payable comparison rather than a recommended hedge for the receivable.&#x20;

Pasted text(20261128-092109).txt



## **2. Model Inputs**

| Named Range | Input      |
| ----------- | ---------- |
| FC_AMT      | €5,400,000 |
| S0_in       | 1.0992     |
| F0_in       | 1.1756     |
| R_USD       | 4.60%      |
| R_FC        | 3.193%     |
| K_PUT       | 1.0992     |
| K_CALL      | 1.0992     |
| PREM_PUT    | 0.0224     |
| PREM_CALL   | 0.0376     |
| T_DAYS      | 273        |
| BASIS       | 360        |

The assigned forward quote and option premiums remain unchanged. Interest calculations use simple annual interest under the ACT/360 convention.

## **3. Derived Values and Intermediate Calculations**

### **Interest accumulation factors**

\\[ DF\_{USD}=1+0.046\times\frac{273}{360} \\]

\\[ DF\_{USD}=1.034883333 \\]

\\[ DF\_{FC}=1+0.03193\times\frac{273}{360} \\]

\\[ DF\_{FC}=1.024213583 \\]

### **Option premium calculations**

| Metric                  | Put Option  | Call Option |
| ----------------------- | ----------- | ----------- |
| Premium per EUR         | $0.0224     | $0.0376     |
| Upfront premium         | $120,960.00 | $203,040.00 |
| Financing cost          | $4,219.49   | $7,082.71   |
| Settlement-date premium | $125,179.49 | $210,122.71 |

Both premiums are treated as positive costs and accumulated to settlement using the USD interest rate.

## **4. Independent Hedge Calculations**

### **A. No Hedge**

The company converts the EUR receivable into USD at the settlement spot rate.

\\[ USD\_{NO\ HEDGE}=FC\_{AMT}\times S_T \\]

At the baseline settlement rate:

\\[ 5,400,000\times1.0992 \\]

**Baseline proceeds: $5,935,680.00**

This strategy retains full exposure to exchange-rate fluctuations.

### **B. Forward Hedge**

The company sells EUR forward at the assigned contractual exchange rate.

\\[ USD\_{FWD}=5,400,000\times1.1756 \\]

**Guaranteed proceeds: $6,348,240.00**

The forward eliminates exchange-rate uncertainty and requires no option premium under the model assumptions.

### **C. Money-Market Hedge**

| Calculation Step             | Independent Result |
| ---------------------------- | ------------------ |
| EUR borrowed today           | €5,272,337.81      |
| Converted USD proceeds today | $5,795,353.72      |
| USD accumulation factor      | 1.034883333        |
| USD investment at maturity   | $5,997,514.98      |

\\[ USD\_{MM}=\frac{5,400,000}{1.024213583} \times1.0992\times1.034883333 \\]

**Guaranteed proceeds: $5,997,514.98**

The EUR receivable repays the foreign-currency borrowing at maturity.

### **D. EUR Put-Option Hedge**

The company purchases a EUR put option with a strike of 1.0992 USD/EUR.

\\[ USD\_{PUT}=5,400,000\times \max(S_T,1.0992)-125,179.488 \\]

| Metric                       | Result        |
| ---------------------------- | ------------- |
| Gross minimum proceeds       | $5,935,680.00 |
| Settlement-date premium cost | $125,179.49   |
| Net minimum proceeds         | $5,810,500.51 |
| Baseline proceeds            | $5,810,500.51 |

**Guaranteed net floor: $5,810,500.51**

The put protects against EUR depreciation while retaining the ability to benefit from EUR appreciation, less the financed premium cost.

### **E. EUR Call-Option Comparison**

The EUR call is appropriate for protecting a foreign-currency payable rather than the assigned receivable.

For an equivalent hypothetical payable:

\\[ USD\_{CALL}=5,400,000\times \min(S_T,1.0992)+210,122.712 \\]

| Metric                   | Result        |
| ------------------------ | ------------- |
| Upfront premium          | $203,040.00   |
| Settlement-date premium  | $210,122.71   |
| Maximum gross USD outlay | $5,935,680.00 |
| Maximum net USD outlay   | $6,145,802.71 |

The call is excluded from the receivable strategy rankings, consistent with the Stage 2 specification.

## **5. Base-Case Strategy Comparison**

Net USD proceeds at settlement — baseline exchange rate of 1.0992

**Forward**

$6,348,240.00

**Money market**

$5,997,514.98

**No hedge**

$5,935,680.00

**Put option**

$5,810,500.51

Bars begin at zero.

| Strategy     | Net USD Proceeds | Hedge Profit vs. No Hedge |
| ------------ | ---------------- | ------------------------- |
| No hedge     | $5,935,680.00    | $0.00                     |
| Forward      | $6,348,240.00    | +$412,560.00              |
| Money market | $5,997,514.98    | +$61,834.98               |
| Put option   | $5,810,500.51    | −$125,179.49              |

The forward generates the highest baseline proceeds and provides the greatest guaranteed USD cash flow.

## **6. Covered Interest Rate Parity Analysis**

The implied forward rate is independently calculated as:

\\[ F\_{IMPLIED}=S_0\times\frac{DF\_{USD}}{DF\_{FC}} \\]

\\[ F\_{IMPLIED}=1.0992\times \frac{1.034883333}{1.024213583} \\]

| Metric                              | Independent Result          |
| ----------------------------------- | --------------------------- |
| Assigned forward rate               | 1.175600                    |
| CIP-implied forward rate            | 1.110651                    |
| Signed exchange-rate difference     | −0.064949                   |
| Absolute exchange-rate difference   | 0.064949                    |
| Specified tolerance                 | 0.000100                    |
| Money-market minus forward proceeds | −$350,725.02                |
| Parity check                        | FAIL — documented exception |

The absolute exchange-rate difference exceeds the specified tolerance of 0.0001 USD/EUR.

The discrepancy reflects the inconsistency between the assigned forward quote and the selected interest-rate proxies. The forward quote is retained rather than adjusted to force parity. This treatment follows the Stage 2 validation requirements.&#x20;

Pasted text(20261128-092109).txt



The discrepancy does not establish a guaranteed executable arbitrage opportunity.

## **7. Sensitivity Analysis**

The settlement exchange-rate grid ranges from 95% to 105% of the revised initial spot rate, in 1% increments.

All proceeds are expressed in USD and rounded to two decimal places after calculation.

| Change | Settlement Spot | No Hedge     | Forward      | Money Market | Put Option   |
| ------ | --------------- | ------------ | ------------ | ------------ | ------------ |
| −5%    | 1.044240        | 5,638,896.00 | 6,348,240.00 | 5,997,514.98 | 5,810,500.51 |
| −4%    | 1.055232        | 5,698,252.80 | 6,348,240.00 | 5,997,514.98 | 5,810,500.51 |
| −3%    | 1.066224        | 5,757,609.60 | 6,348,240.00 | 5,997,514.98 | 5,810,500.51 |
| −2%    | 1.077216        | 5,816,966.40 | 6,348,240.00 | 5,997,514.98 | 5,810,500.51 |
| −1%    | 1.088208        | 5,876,323.20 | 6,348,240.00 | 5,997,514.98 | 5,810,500.51 |
| 0%     | 1.099200        | 5,935,680.00 | 6,348,240.00 | 5,997,514.98 | 5,810,500.51 |
| +1%    | 1.110192        | 5,995,036.80 | 6,348,240.00 | 5,997,514.98 | 5,869,857.31 |
| +2%    | 1.121184        | 6,054,393.60 | 6,348,240.00 | 5,997,514.98 | 5,929,214.11 |
| +3%    | 1.132176        | 6,113,750.40 | 6,348,240.00 | 5,997,514.98 | 5,988,570.91 |
| +4%    | 1.143168        | 6,173,107.20 | 6,348,240.00 | 5,997,514.98 | 6,047,927.71 |
| +5%    | 1.154160        | 6,232,464.00 | 6,348,240.00 | 5,997,514.98 | 6,107,284.51 |

### **Sensitivity chart**

ForwardMoney marketNo hedgePut option

$5.5M$5.8M$6M$6.2M$6.5M1.04421.05521.06621.07721.08821.09921.11021.12121.13221.14321.1542

### **Hedge profit and strategy rankings**

Hedge profit is calculated as the difference between each active hedge's net USD proceeds and the unhedged proceeds at the same settlement exchange rate.

| Change | Forward Profit | MM Profit   | Put Profit  | Overall Winner | Best Active Hedge |
| ------ | -------------- | ----------- | ----------- | -------------- | ----------------- |
| −5%    | +709,344.00    | +358,618.98 | +171,604.51 | Forward        | Forward           |
| −4%    | +649,987.20    | +299,262.18 | +112,247.71 | Forward        | Forward           |
| −3%    | +590,630.40    | +239,905.38 | +52,890.91  | Forward        | Forward           |
| −2%    | +531,273.60    | +180,548.58 | −6,465.89   | Forward        | Forward           |
| −1%    | +471,916.80    | +121,191.78 | −65,822.69  | Forward        | Forward           |
| 0%     | +412,560.00    | +61,834.98  | −125,179.49 | Forward        | Forward           |
| +1%    | +353,203.20    | +2,478.18   | −125,179.49 | Forward        | Forward           |
| +2%    | +293,846.40    | −56,878.62  | −125,179.49 | Forward        | Forward           |
| +3%    | +234,489.60    | −116,235.42 | −125,179.49 | Forward        | Forward           |
| +4%    | +175,132.80    | −175,592.22 | −125,179.49 | Forward        | Forward           |
| +5%    | +115,776.00    | −234,949.02 | −125,179.49 | Forward        | Forward           |

Forward overall wins

# **11/11**

100% of modeled scenarios

Forward active hedge wins

# **11/11**

100% of modeled scenarios

These results represent scenario coverage, not statistical probabilities.

## **8. Break-Even Analysis**

### **No Hedge vs. Forward**

The unhedged strategy equals the forward when:

\\[ S_T=F_0=1.1756 \\]

The EUR must appreciate approximately **6.95%** relative to the initial spot rate before remaining unhedged generates greater proceeds than the forward.

### **Put Option vs. Forward**

The put option equals the forward when:

\\[ FC\_{AMT}\times S_T-FV\_{PREM\\\_PUT}=USD\_{FWD} \\]

\\[ S_T=\frac{6,348,240+125,179.488}{5,400,000} \\]

\\[ S_T=1.198781387 \\]

The EUR must appreciate approximately **9.06%** before the put option generates greater net proceeds than the forward.

### **Additional break-even thresholds**

| Comparison                  | Settlement Spot |
| --------------------------- | --------------- |
| Put option vs. no hedge     | 1.076019        |
| Money market vs. no hedge   | 1.110651        |
| Put option vs. money market | 1.133832        |
| Forward vs. no hedge        | 1.175600        |
| Put option vs. forward      | 1.198781        |

Both alternatives' break-even points against the forward fall outside the specified ±5% sensitivity range.

### **Interactive exchange-rate stress test**

Explore settlement rates beyond the required sensitivity grid.

Settlement spot rate

# **1.0992**

0.9500

1.3000

Forward

$6,348,240.00

Money market

$5,997,514.98

No hedge

$5,935,680.00

Put option

$5,810,500.51

**Overall winner**

Forward

**Best active hedge**

Forward

Reset to baseline

## **9. Independent Reconciliation Against Stage 4**

| Metric                              | Stage 4 Reported | Independent AI Result | Difference |
| ----------------------------------- | ---------------- | --------------------- | ---------- |
| Forward proceeds                    | $6,348,240.00    | $6,348,240.00         | $0.00      |
| Money-market proceeds               | $5,997,514.98    | $5,997,514.98         | $0.00      |
| CIP-implied forward                 | 1.110651         | 1.110651              | 0.000000   |
| Signed forward-rate gap             | −0.064949        | −0.064949             | 0.000000   |
| USD parity gap                      | −$350,725.02     | −$350,725.02          | $0.00      |
| Reduction from previous MM proceeds | $24,209.75       | $24,209.75            | $0.00      |

All comparable numerical results reported in the revised Stage 4 memo agree with the independent calculations at the reported precision.

## **10. Validation Checks**

| Validation Check                | Status                     |
| ------------------------------- | -------------------------- |
| Forward calculation             | PASS                       |
| Money-market calculation        | PASS                       |
| Forward parity tolerance        | FAIL — documented          |
| Gross put-option floor          | PASS                       |
| Net put-option floor            | PASS                       |
| Premium subtracted exactly once | PASS                       |
| Eleven sensitivity scenarios    | PASS                       |
| Consistent currency units       | PASS                       |
| ACT/360 convention              | PASS                       |
| Excel named-range consistency   | Not independently verified |

The only numerical exception identified is the expected forward-parity discrepancy. It does not indicate an arithmetic error.

Workbook-specific formula references and cell-level consistency cannot be independently verified without inspecting the workbook, which was intentionally excluded from this execution.

## **11. Risk and Strategy Trade-Offs**

| Strategy     | Advantages                                             | Disadvantages                                         |
| ------------ | ------------------------------------------------------ | ----------------------------------------------------- |
| No hedge     | No premium; unlimited appreciation benefit             | Full currency exposure                                |
| Forward      | Highest guaranteed proceeds; eliminates FX uncertainty | Sacrifices appreciation beyond contracted rate        |
| Money market | Guaranteed proceeds; eliminates FX uncertainty         | Lower proceeds; borrowing and investment requirements |
| Put option   | Downside protection with retained upside               | Premium cost; lower guaranteed proceeds               |

The forward provides $350,725.02 more than the money-market hedge and $537,739.49 more than the put-option guaranteed floor.

## **12. Executive Recommendation**

**Recommended strategy: Hedge 100% of the EUR 5,400,000 receivable using the assigned 273-day forward contract, subject to confirmation that the quote is executable.**

The forward hedge provides guaranteed USD proceeds of $6,348,240, exceeding the money-market hedge by $350,725.02 and the baseline unhedged proceeds by $412,560. The forward also produces the highest net USD proceeds in all eleven modeled exchange-rate scenarios. Although the put option retains upside potential, the EUR would need to appreciate approximately 9.06% before the option outperforms the forward, exceeding the modeled sensitivity range.

Given the company's objective of protecting future USD cash flow, the forward offers the strongest combination of certainty and modeled financial performance. However, the material covered interest parity discrepancy warrants confirmation of the assigned forward quote before execution. Treasury should verify the contractual rate, counterparty terms, and applicable transaction costs before entering the hedge.

## **13. Limitations and Outstanding Items**

- The historical Euribor observations remain unverified, as disclosed in the Stage 4 memo.
- The assigned forward quote and option premiums are not independently confirmed executable market prices.
- Transaction costs, credit risk, borrowing spreads, taxes, and hedge accounting are excluded.
- The sensitivity grid does not assign probabilities or represent a forecast of future exchange rates.
- Partial and dynamic hedging strategies are outside the Stage 2 specification.
- Independent reconciliation against the actual Excel workbook remains outstanding.

## **14. Independent Execution Conclusion**

The revised Stage 4 market-data inputs produce internally consistent hedge calculations. All comparable reported Stage 4 numerical results are reproduced at the stated precision. The forward hedge is the preferred strategy under the supplied assumptions, winning all eleven sensitivity scenarios and providing the highest guaranteed USD proceeds.

The forward-parity discrepancy remains a documented model exception requiring market confirmation rather than a mathematical correction.

**Execution status:** Independent AI calculations complete. Workbook reconciliation and final decision documentation remain outstanding.
