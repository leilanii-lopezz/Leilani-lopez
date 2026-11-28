## 8. Specification Retrospective

The independent AI execution demonstrated that the Stage 2 specification and revised Stage 4 market-data memo communicate the core hedge methodology without requiring access to the Excel workbook or additional coaching.

However, the execution also revealed opportunities to improve the specification.

### What the AI Got Wrong or Had to Interpret

The AI correctly distinguished the EUR call as a hypothetical payable hedge rather than a hedge for the assigned receivable. However, it excluded the call from its sensitivity table. This prevented a complete comparison of all five strategies at consistent settlement exchange rates.

The AI also reproduced figures already reported in the market-data memo. Although this demonstrated consistency, agreement alone is not sufficient evidence of independent computational accuracy.

Additionally, the AI could not verify the historical interest-rate observations or Excel-specific formula references from the two supplied documents.

### Improvements for Version 2

A revised specification would:

- Explicitly require all five strategies at each selected settlement exchange rate, with the call clearly labeled as a hypothetical payable.
- Require full numerical precision during intermediate calculations and rounding only for presentation.
- Define the expected output tables and reconciliation tolerances more precisely.
- Distinguish assigned scenario quotes from independently verified market observations.
- Require a clear explanation of any missing or unverified inputs.
- Separate computational validation from market-data validation.

### Lessons Learned

Earlier instructor feedback highlighted the importance of consistent named-range references, appropriate market-rate proxies, accurate documentation and descriptive commit messages.

During Stage 5, I restored named-range formulas in several core workbook calculations, revised the EUR interest-rate methodology and updated the market-data documentation.

The project demonstrated that AI is useful for generating and checking financial models, but its conclusions must be evaluated rather than accepted automatically. Independent arithmetic, transparent assumptions and clear documentation remain essential to responsible financial decision-making.

The remaining parity discrepancy and unverified historical Euribor observations demonstrate why computational consistency should not be confused with market accuracy.
