# FX Transaction Hedging

## Capability Overview

This project demonstrates my ability to analyze foreign exchange risk and evaluate hedging strategies for an international business transaction.

## Scenario 37: Solar Inverters

A U.S. solar-inverter manufacturer expects to receive EUR 5,400,000 from an Italian solar developer in 273 days. Because the payment is in euros, changes in the EUR/USD exchange rate could affect the amount of U.S. dollars the company receives.

## Hedging Strategies

The project evaluates four approaches:

1. No hedge (unhedged position)
2. Forward contract
3. Money-market hedge
4. Currency options hedge

The goal is to compare potential USD proceeds, costs, and risks to help determine which strategy best protects the company's receivable.

## Where This Capability Was Exercised

- **Course:** FIN 321 - International Finance and Securities
- **Project:** FX Transaction Hedging
- **Scenario:** 37 - Solar Inverters
- **Stage 2 Deliverable:** [Model Specification](spec.md)

## Project Status

- Phase 0: Portfolio Repository - Complete
- Stage 1: Executive Memo - Complete
- Stage 2: Model Specification - Complete

## AI Disclosure

ChatGPT (GPT-6) assisted with drafting, organizing, and reviewing the technical specification and project documentation. I reviewed the content and checked it against my assigned scenario.
  
## Final Model and Validation — Stage 5

### Final Deliverables

- [Technical Specification](spec.md)
- [Final Excel Model](model.xlsx)
- [Revised Market Data Memo](../../data/2026-11-19-solar-inverters-market-data-memo.md)
- [Independent AI Execution](../../analysis/2026-11-27-solar-inverters-ai-execution.md)
- [Validation Analysis and Retrospective](../../analysis/2026-11-27-solar-inverters-validation-analysis.md)
- [CFO Decision Memo](../../docs/decisions/2026-11-27-solar-inverters-hedge-decision-memo.md)

### Model Validation

The final model incorporates revised market-data assumptions, restored named-range formulas, independent AI validation, personal calculator verification, and a documented covered interest parity exception.

The forward, money-market and put-option calculations were independently verified using a calculator outside Excel.

### Final Recommendation

Hedge 100% of the EUR 5,400,000 receivable using the assigned 273-day forward contract.

The forward secures $6,348,240 in USD proceeds and outperforms all alternative receivable strategies across the eleven modeled sensitivity scenarios.

The recommendation remains conditional on confirmation of executable market pricing and underlying market-data assumptions.
