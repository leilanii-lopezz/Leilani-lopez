# Prompt Log

## October 9, 2026

**Task:** Complete the initial setup of my professional portfolio repository.

**Prompt:** Used AI assistance to review my README.md and RESUME.md and create the required repository structure, including AGENTS.md, CLAUDE.md, prompt-log.md, .gitignore, and required folders.

**Result:** Created and reviewed the required portfolio setup files and repository structure.

## October 30, 2026

**Task:** Complete Phase 1 — Executive Memo for my solar-inverters FX hedging scenario.

**Prompt:** Used AI assistance to help interpret the Phase 1 requirements, organize the executive memo, explain the three FX hedging alternatives, and review the draft against the rubric.

**Result:** Created and reviewed the Phase 1 executive memo for Scenario 37, solar-inverters, including the exposure, hedge alternatives, assumptions, hypothesis, and next steps.

**Check:** The original draft used the generic example instead of my assigned scenario. I caught this by checking my professor’s scenario email and Scenario 37 page, then corrected the amount, timing, filename, and assumptions to match the solar-inverters scenario.

## November 6, 2026

**Task:** Complete Stage 2 - Model Specification for my Scenario 37 solar-inverters FX hedging project.

**Prompt:** Used ChatGPT (GPT-6) to help interpret the Stage 2 instructions, draft and organize the eight sections of the technical specification, explain the calculations and validation checks, and review the document's formatting and completeness.

**Result:** Completed the FX hedging model specification in capabilities/fx-hedging/spec.md. The document describes the EUR 5,400,000 receivable due in 273 days, the unhedged position, forward hedge, money-market hedge, and options hedge, along with model inputs, calculation logic, and validation checks.

**Check:** Reviewed the specification in GitHub Preview, corrected the company name to match Scenario 37, filled in the document metadata, checked for remaining placeholders, and committed the final specification. Also updated the repository README to include the project and its progress.

Stage 3 — AI-Assisted Excel Model Build and Audit

Date: November 18–19, 2026
AI Tool: ChatGPT (GPT-6)
Project: Scenario 37 — Solar Inverters FX Hedging

Interaction 1: Excel Workbook Generation

Prompt / Request:
Using my updated Stage 2 technical specification, create an Excel workbook for the €5,400,000 receivable due in 273 days. Include the required worksheets, named inputs, hedge calculations, sensitivity analysis, chart, and validation checks.

AI Output:
ChatGPT generated an Excel workbook with 10 worksheets: Cover, Legend, Inputs, Forward, Money Market, Put Option, Call Option, Sensitivity, Checks, and Notes.

Human Review:
I downloaded and opened the workbook in Excel to check the calculations and functionality.

Interaction 2: Formula Error Identification and Correction

Prompt / Request:
I reported #NAME? errors across the Inputs, Forward, Money Market, Put Option, Call Option, Sensitivity, and Checks worksheets and asked ChatGPT to correct them.

AI Output:
ChatGPT revised the workbook formulas to use direct references to the Inputs worksheet while retaining the named ranges.

Human Review:
I opened the corrected workbook in Excel and confirmed that the previously reported #NAME? errors were gone.

Interaction 3: Sensitivity Analysis Verification

Prompt / Request:
Verify that the workbook contains the sensitivity analysis and a chart comparing the four hedging strategies.

AI Output:
ChatGPT guided me through locating and reviewing the Sensitivity worksheet.

Human Review:
I confirmed that the chart was present and compared the no-hedge, forward, money-market, and put-option strategies.

Interaction 4: Validation Checks and Forward Parity

Prompt / Request:
Review the validation results and explain the forward-parity warning.

AI Output:
ChatGPT explained that the assigned forward rate of 1.1756 USD/EUR differs from the forward rate implied by the illustrative USD and EUR interest rates. It recommended retaining the warning rather than forcing the calculations to match.

Human Review:
I confirmed that the Checks worksheet displayed PASS for the other checks and "FLAG - illustrative rates differ" for the forward-parity tolerance check.

Interaction 5: Audit Documentation

Prompt / Request:
Prepare a Stage 3 audit report documenting the workbook errors, corrections, validation results, and AI assistance.

AI Output:
ChatGPT drafted an audit report covering the named-range errors, forward-parity discrepancy, and preliminary base-case calculation differences.

Human Review:
I added the audit report to my GitHub repository as capabilities/fx-hedging/audit.md.

AI Use Disclosure

AI assisted with workbook generation, formula troubleshooting, calculation review, and audit documentation. I reviewed the workbook in Excel, identified errors, confirmed the corrections, and checked the sensitivity chart and validation results.

Stage 4 — Market Data and FX Hedging Lab Validation

Date: November 19, 2026
Project: Scenario 37 — Solar Inverters

AI Tool Used

ChatGPT (OpenAI)

Purpose

I used ChatGPT to assist with updating my FX hedging model using market data, checking calculations against the professor's FX Hedging Lab, identifying differences, and documenting the validation process.

Summary of AI Assistance

Helped identify and document exchange-rate and interest-rate inputs from the ECB and Federal Reserve.

Guided the update of the Excel workbook with the selected market inputs.

Assisted in comparing the forward and money-market hedge results with the FX Hedging Lab.

Helped investigate the put option discrepancy and identify the difference between financed and unfinanced option premiums.

Assisted in preparing the Stage 4 market-data memo and lab cross-check report.

Provided step-by-step guidance for organizing and committing deliverables to GitHub.

Human Verification

I reviewed the market-data sources, entered the inputs into Excel and the FX Hedging Lab, and checked the calculated results. I confirmed that the forward and money-market results matched after rounding. I also inspected the put option formulas and verified that the workbook checks passed except for the forward parity flag.

Limitations and Discrepancies

The USD and EUR interest-rate inputs are not perfectly maturity-matched. The assigned forward rate differs from the implied forward rate. The Excel model finances the put premium through settlement, while the lab appears to subtract the premium without financing it. These differences were documented rather than silently changing the model.

Deliverables

data/2026-11-19-solar-inverters-market-data-memo.md

capabilities/fx-hedging/model_phase4.xlsx

analysis/2026-11-19-solar-inverters-lab-cross-check.md
