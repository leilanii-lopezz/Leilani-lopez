<div style="border-top: 6px solid #024731; border-bottom: 1px solid #B2B2B2; padding: 12px 0; margin-bottom: 24px; font-family: 'Open Sans', Helvetica, Arial, sans-serif;">
  <div style="color: #024731; font-weight: 700; letter-spacing: 0.06em; text-transform: uppercase; font-size: 0.85rem;">University of Hawaiʻi at Mānoa · Shidler College of Business</div>
  <div style="color: #000000; font-weight: 700; font-size: 1.25rem; margin-top: 4px;">FIN 321: International Finance and Securities</div>
  <div style="color: #525252; font-weight: 400; font-size: 0.95rem;">FX Transaction Hedging Project — Technical Specification</div>
</div>

<!--
BRAND FORMATTING — applied per docs/_branding/design.json (v1.0.0)
  ┌─ Colors ─────────────────────────────────────────────────────────────┐
  │ Primary green ........... #024731  RGB 2,71,49    Pantone 3435 C     │
  │ Primary black ........... #000000  RGB 0,0,0      Process Black      │
  │ Silver (secondary) ...... #B2B2B2  RGB 178,178,178 Cool Gray 5 C     │
  │ White (secondary) ....... #FFFFFF                                    │
  │ Neutral-600 (muted) ..... #525252  (secondary text, captions)        │
  │ UH-green 700 (hover) .... #013D26  (link hover, pressed state)       │
  │ UH-green 50 (tint) ...... #E6F2EF  (callout backgrounds)             │
  │ Yellow (Excel only) ..... #FFFF00  (input highlight — not brand)     │
  ├─ Typography ─────────────────────────────────────────────────────────┤
  │ Headings (web)  .......... Open Sans Bold (H1/H2) / Semibold (H3/H4) │
  │ Headings (print)  ........ Avenir Bold                               │
  │ Body (web)  .............. Open Sans Regular                         │
  │ Body (print)  ............ Avenir Book                               │
  │ Fallback stack  .......... Helvetica, Arial, sans-serif              │
  │ Monospace  ............... Consolas / ui-monospace                   │
  │ Body minimum size  ....... 10 pt (11–12 pt preferred for print)      │
  │ Leading  ................. 3–5 pt greater than type size (print)     │
  │ Alignment  ............... Flush left, ragged right                  │
  ├─ Accessibility ──────────────────────────────────────────────────────┤
  │ • ADA-compliant contrast ratios for ALL text and UI elements         │
  │ • No red body type                                                   │
  │ • No layouts that are too dark for readability                       │
  │ • No custom palettes or gradients outside the official brand         │
  └──────────────────────────────────────────────────────────────────────┘
  Full brand standard: docs/_branding/design.json · Source: https://manoa.hawaii.edu/brand/
-->

# U.S. Solar-Inverter Manufacturer — FX Transaction Hedge Model · Technical Specification

> <span style="color:#024731; font-weight:700;">Technical specification</span> for the FX transaction hedge model — the named-range contract, calculation flow, and validation checks, precise enough that an AI or a colleague could build (or rebuild) the workbook from this document alone. This spec is the input the AI-assisted build works from.

| Field | Value |
|------|------|
| **Created by** | Leilani Lopez |
| **Updated by** | Leilani Lopez |
| **Date Created** | 2026-11-06 |
| **Date Updated** | 2026-11-06 |
| **Version** | 1.0 |
| **LLM Used** (optional) | ChatGPT (GPT-6) - assisted with drafting, organizing, and reviewing the model specification |
| **Role** | Treasury Analyst / FP&A Analyst |
| **Audience** | CFO / Director of Treasury |
| **Companion Workbook** | student build |

---

## 1. Problem Statement

The company expects to receive €5,400,000 from an Italian solar developer in 273 days. Because the receivable is denominated in euros, a depreciation of the euro against the U.S. dollar would reduce the amount of USD the company receives, creating uncertainty in future cash flow. The objective is to evaluate four strategies—no hedge, a forward hedge, a money-market hedge, and an option hedge—to determine which best protects the receivable while considering costs and potential exchange-rate gains. The model will compare the dollar proceeds under each strategy and test how exchange-rate movements affect the results to support the company's final hedging decision.
---

## 2. Inputs (Known Variables)

All inputs will use standardized named ranges. Scenario values are indicative placeholders and will be replaced or verified using live market data at Stage 4.

### 2.1 Core Inputs

| Named Range | Description | Placeholder Value | Unit | Stage 4 Source |
|---|---|---|---|---|
| `FC_AMT` | EUR receivable | 5,400,000 | EUR | Assigned scenario/contract |
| `S0_in` | Initial EUR/USD spot rate | 1.1000 | USD/EUR | Live EUR/USD spot quote |
| `F0_in` | 273-day forward rate | 1.1756 | USD/EUR | Bank forward quote; verify with market data |
| `R_USD` | Annual USD interest rate | 5.30% | Annual % | Federal Reserve H.15 |
| `R_FC` | Annual EUR interest rate | 3.10% | Annual % | ECB interest-rate data |
| `K_PUT` | EUR put strike | 1.1000 | USD/EUR | At-the-money strike based on spot |
| `K_CALL` | EUR call strike | 1.1000 | USD/EUR | At-the-money strike based on spot |
| `PREM_PUT` | EUR put premium | 0.0224 | USD per EUR | Assigned scenario; verify market quote |
| `PREM_CALL` | EUR call premium | 0.0376 | USD per EUR | Assigned scenario; verify market quote |
| `T_DAYS` | Days until settlement | 273 | Days | Assigned scenario/contract |

Interest rates and spot/strike values are illustrative placeholders, not verified current market quotes. Use ACT/360 for USD and EUR interest calculations. `BASIS = 360` is a fixed model convention, not a market input.

### 2.2 Derived / Intermediate Values

| Name | Description | Calculation |
|---|---|---|
| `FV_PREM_PUT` | Future value of put premium at settlement | `PREM_PUT × FC_AMT × (1 + R_USD × T_DAYS / 360)` |
| `FV_PREM_CALL` | Future value of call premium at settlement | `PREM_CALL × FC_AMT × (1 + R_USD × T_DAYS / 360)` |
| `S_T_grid` | Settlement spot-rate sensitivity grid | `S0_in × 0.95` through `S0_in × 1.05`, in 1% increments |
| `USD_NO_HEDGE` | USD proceeds without hedging | `S_T × FC_AMT` |

These derived values will be calculated using formulas in the Stage 3 workbook, not manually entered as fixed outputs.

---

## 3. Assumptions & Constraints

- **Quote convention:** All exchange rates are expressed as USD per EUR. A higher EUR/USD rate means the euro appreciates and increases the USD value of the receivable.
- **Horizon:** The model covers a single EUR 5,400,000 receivable settling in 273 days.
- **Day-count basis:** Simple annual interest uses ACT/360 for both USD and EUR. The model uses a fixed `BASIS = 360` convention.
- **Interest rates:** The USD rate of 5.30% and EUR rate of 3.10% are illustrative placeholders, to be replaced with sourced market rates in Stage 4.
- **Forward rate:** The assigned 273-day forward quote is 1.1756 USD/EUR. The model will also calculate an implied forward rate from interest-rate parity and report any discrepancy rather than assuming the quotes match.
- **Option premiums:** The put premium is $0.0224 per EUR and the call premium is $0.0376 per EUR. Premiums are paid upfront in USD, treated as cash outflows, and carried forward at the USD interest rate for settlement-date comparisons.
- **Option strikes:** Both put and call strikes are provisionally set at the illustrative spot rate of 1.1000 USD/EUR, consistent with at-the-money options. Actual strikes will be verified in Stage 4.
- **Parity:** Under covered interest-rate parity, forward and money-market hedges should generate approximately equal USD proceeds when consistent market inputs are used. Differences will be reported and investigated.
- **Counterparty and credit risk:** Excluded from the base model; all transactions are assumed to be executable without default.
- **Transaction costs:** Bid-ask spreads, brokerage fees, and borrowing spreads are excluded from the base case and identified as limitations.
- **Tax and accounting:** Excluded; the model compares pretax cash proceeds rather than accounting earnings.
- **Scenario construction:** Future EUR/USD settlement rates vary from 95% to 105% of the initial spot rate in 1% increments, without assigning probabilities.

---

## 4. Calculation Flow

Described in named-range pseudocode so the logic is portable across Excel, Python, and AI prompts. Formulas are written for a **receivable** exposure; Step 7 shows the sign flips required for a payable.

### Step 1 — Derived inputs

1. `DF_USD` = `1 + R_USD × T_DAYS / BASIS` *(accumulation / growth factor, not a fractional discount factor)*
2. `DF_FC` = `1 + R_FC × T_DAYS / BASIS`
3. `FV_PREM_PUT` = `−PREM_PUT × FC_AMT × DF_USD`
4. `FV_PREM_CALL` = `−PREM_CALL × FC_AMT × DF_USD`

### Step 2 — Forward hedge (certainty benchmark)

- `USD_FWD` = `FC_AMT × F0_in`
- Locked-in at t₀; invariant across the `S_T` grid.

### Step 3 — Money-market hedge (parity check)

1. Borrow `FC_AMT / DF_FC` foreign currency today *(the discounted PV of the receivable)*.
2. Convert to USD at the spot rate: `(FC_AMT / DF_FC) × S0_in`.
3. Invest the USD to maturity: `USD_MM` = `(FC_AMT / DF_FC) × S0_in × DF_USD`.
4. At maturity, the FC receivable repays the foreign borrowing exactly — so the USD deposit is the locked-in proceed.

> **Parity check:** `USD_MM ≈ USD_FWD` within rounding. A persistent gap indicates a violation of covered interest-rate parity in the quoted inputs.

### Step 4 — Option hedge (floor with upside)

Put-and-hold strategy on the receivable:

- Pay `PREM_PUT × FC_AMT` USD today for a put on FC with strike `K_PUT`.
- At settlement, for each `S_T` on the grid:
- `USD_PUT(S_T)` = `FC_AMT × MAX(S_T, K_PUT) - FV_PREM_PUT`
  - Equivalently: `MAX(S_T, K_PUT) × FC_AMT + FV_PREM_PUT`

### Step 5 — Sensitivity table (rows of the grid)

For each `S_T` in `S_T_grid`:

| Column | Output | Formula |
|--------|--------|---------|
| No hedge | `USD_NO_HEDGE(S_T)` | `S_T × FC_AMT` |
| Forward | `USD_FWD` | constant across rows |
| Money market | `USD_MM` | constant across rows |
| Option (put) | `USD_PUT(S_T)` | `MAX(S_T, K_PUT) × FC_AMT - FV_PREM_PUT` |
| Hedge profit | `HEDGE_PROFIT_k(S_T)` | `USD_k − USD_NO_HEDGE` for each of `k ∈ {forward, money market, option}` — one sub-column per strategy |
| Overall winner (incl. no hedge) | label | `ARGMAX(USD_NO_HEDGE, USD_FWD, USD_MM, USD_PUT)` |
| Best active hedge (excl. no hedge) | label | `ARGMAX(USD_FWD, USD_MM, USD_PUT)` |

### Step 6 — Summary metrics (scalar outputs)

- `USD_FLOOR_PUT` = `MIN(USD_PUT)` across `S_T_grid` *(worst-case put outcome on the grid; payable tab uses `USD_CEILING_CALL = MAX(USD_CALL)` instead)*
- `USD_BASE_k` = `USD_k` evaluated at `S_T = S0_in` for each strategy *(the "baseline" row feeds §5.1)*

*`HEDGE_PROFIT_k` is per-row and lives inside the Step 5 grid, not here.*

### Step 7 — Payable variant (sign flips)

For a payable of `FC_AMT` to be settled in FC at maturity, the model mirrors Steps 2–5 with three substitutions: (a) **buy** the forward instead of sell, (b) **borrow USD today, invest in FC** for the money-market leg, and (c) use a **call on FC** with strike `K_CALL` and premium `PREM_CALL`. The sensitivity winner is the strategy that **minimizes** USD outlay at each `S_T`, not the one that maximizes it.

---

## 5. Outputs

| Output | Description | Format | Purpose |
|--------|-------------|--------|---------|
| Input panel | All named-range inputs with units, sources, and access dates | Top of each tab | Single source of truth |
| Strategy summary | `USD_FWD`, `USD_MM`, `USD_BASE_k` per strategy, plus `USD_FLOOR_PUT` (receivable) / `USD_CEILING_CALL` (payable) | Table above sensitivity grid | Executive at-a-glance |
| Sensitivity table | USD proceeds / outlay for each strategy across `S_T_grid` ± 5% | Table on each tab | Core analytical evidence |
| Hedge-profit columns | `USD_k − USD_NO_HEDGE` for each strategy per row | Sub-table | Isolates hedge value-add |
| Winner / best-hedge labels | `ARGMAX` / `ARGMIN` labels per row | Two label columns | Quick-read decision cue |
| Sensitivity chart | Line chart of USD outcome vs. `S_T` for all four strategies | Embedded chart | Visual comparison |
| Executive summary (Stage 5 decision memo) | 1–2 paragraph narrative with explicit recommendation | Separate memo | Downstream deliverable |

### 5.1 Computed Base-Case Values

The base case uses an illustrative settlement spot rate of 1.1000 USD/EUR. These results are preliminary and will be recalculated and validated in Stage 3. The model compares USD proceeds for the EUR 5,400,000 receivable under each hedging strategy.

| Strategy | Base-Case USD Proceeds | Hedge Profit vs. No Hedge |
|---|---:|---:|
| No hedge | $5,940,000 | $0 |
| Forward | $6,348,240 | +$408,240 |
| Money market | $6,023,900 (approx.) | +$83,900 (approx.) |
| Put option | $5,813,919 (approx., after financed premium) | -$126,081 (approx.) |

The forward rate is taken from the assigned scenario. Money-market proceeds use the illustrative USD and EUR interest rates from Section 2 and do not match the quoted forward rate under covered interest-rate parity. This discrepancy must be investigated and documented during validation rather than treated as a formula error. All base-case values will be updated when verified market inputs become available in Stage 4.

---

## 6. Model Review — What Worked & What to Improve

This review identifies the strengths and potential weaknesses of the proposed model before the Stage 3 workbook is built. The following items will guide the build and audit.

### 6.1 What Worked

- The specification separates the four strategies: no hedge, forward, money-market, and put option, allowing direct comparison of USD proceeds.
- Standardized named ranges make the calculations easier to follow and audit without relying on Excel cell references.
- The forward hedge provides a fixed benchmark of $6,348,240 based on the assigned 273-day forward rate.
- The sensitivity analysis will show how a changing EUR/USD rate affects each strategy and whether the put's downside protection is worth its premium.

### 6.2 What to Improve

- The illustrative USD and EUR interest rates do not produce the assigned forward rate under covered interest-rate parity. Stage 3 must calculate and flag this discrepancy rather than incorrectly treating the two hedges as equivalent.
- The model must clearly subtract the put premium, including its financing cost, when calculating net option proceeds.
- All placeholder rates and strikes must be identified and replaced or verified using documented market sources in Stage 4.
- The Stage 3 workbook must make intermediate money-market calculations visible so that errors can be identified and corrected.

### 6.3 Auditability Checklist

- [ ] All ten core inputs use the standardized named ranges defined in Section 2.
- [ ] All hedge formulas reference named inputs rather than hard-coded exchange rates or cell addresses in the specification.
- [ ] Money-market borrowing, conversion, and USD investment calculations are shown separately.
- [ ] The workbook calculates the implied forward rate and reports the difference from the assigned forward quote.
- [ ] Put-option proceeds subtract the premium and its settlement-date financing cost.
- [ ] The sensitivity grid includes spot rates from -5% to +5% in 1% increments.
- [ ] The Notes tab documents market sources, assumptions, and access dates.
- [ ] Workbook cells follow the required color convention: yellow inputs, blue assumptions, black formulas, and green cross-tab links.
- [ ] All calculated outputs are formula-driven, with no spreadsheet errors.

---

## 7. Sensitivity Plan

- **Sensitivity grid:** `S_T_grid` will range from 0.95 × `S0_in` to 1.05 × `S0_in` in 1% increments, producing 11 scenarios. With the illustrative spot rate of 1.1000 USD/EUR, the range is 1.0450 to 1.1550 USD/EUR.
- **Strategies compared:** No hedge, forward hedge, money-market hedge, and EUR put option hedge. All outcomes will be expressed as net USD proceeds at settlement.
- **Primary chart:** A line chart will plot the future EUR/USD spot rate (`S_T`) on the horizontal axis and USD proceeds on the vertical axis. The forward and money-market strategies will appear as horizontal lines, the unhedged strategy will change linearly with the spot rate, and the put option will provide a downside floor while retaining upside potential after its premium cost.
- **Secondary analysis:** A table will calculate the difference between each hedged strategy and the unhedged outcome at every exchange rate. It will also identify the strategy producing the highest net USD proceeds in each scenario.
- **Decision purpose:** The sensitivity analysis will help the CFO evaluate the trade-off between guaranteed proceeds, hedging costs, and potential gains if the euro appreciates. It will also identify the exchange-rate level at which the put option produces more net USD than the forward hedge.

---

## 8. Limitations & Next Steps

**Limitations:**
- The model assumes a single EUR 5,400,000 receivable due in 273 days and does not consider partial or dynamic hedging.
- Credit risk, counterparty risk, transaction costs, and bid-ask spreads are excluded from the base case.
- Option premiums are assigned scenario inputs rather than values calculated using an option-pricing model.
- The model excludes tax consequences, hedge accounting treatment, and the effects of other foreign currencies.
- The initial spot rate, interest rates, and option strikes are illustrative placeholders. The assigned forward rate may not satisfy covered interest-rate parity with these placeholders.

**Next Steps:**
- **Stage 3:** Use this specification to build the Excel hedging model with AI assistance, including all named ranges, formulas, strategy comparisons, and sensitivity charts. Audit the workbook against the validation requirements and document at least one correction.
- **Stage 4:** Replace or verify the illustrative inputs using sourced market data, recording sources and access dates.
- **Stage 5:** Evaluate the final results and prepare a recommendation for the CFO based on guaranteed proceeds, downside protection, costs, and potential upside.

---

## 9. Writing a Strong Specification

> <span style="color:#024731; font-weight:600;">The spec should read like a handoff document, not a lab notebook.</span>

- **Communicate like a professional:** clear, structured, no filler.
- **Think one stage ahead:** the spec feeds directly into the Stage 3 AI build prompt and the Stage 5 decision memo.
- **Be internally consistent:** variables, labels, and steps must align with the actual workbook.
- **Be reproducible:** another treasury analyst — or an AI — should be able to rebuild the model from this spec alone.
- **Be reflective:** §6 should show honest assessment of the model's strengths and gaps, not self-congratulation.
- **Be executive-relevant:** the CFO should understand *what was built* and *why it matters* for the hedging decision.

---

## 10. How This Sets Up Stages 3–5

| What's Written in Stage 2 | What It Enables in Stages 3–5 |
|---------------------------|----------------------------|
| Standardized named ranges with precise definitions | AI uses standardized variable names; no improvisation |
| Step-by-step calculation flow | AI generates correct, auditable hedge formulas |
| Model review and improvement notes (§6.2) | AI builds the *improved* version, not just a replica |
| Explicit output requirements + chart spec | AI produces the exact tables, chart, and memo sections needed |
| Base-case output values (§5.1) | Regression checkpoints for the refined model |

---

## Appendix A — Change Log

| Version | Date | Author | Change |
|---------|------|--------|--------|
| 0.1 | 2026-11-06 | Leilani Lopez | Initial Stage 2 FX hedging model specification for Scenario 37 (solar-inverters) |

