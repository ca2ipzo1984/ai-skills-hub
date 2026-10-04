# GAS Mock Simulator

## Purpose
Simulate Google Apps Script environment locally in Node.js/Python to enable off-cloud testing.

## Operational Rules
1. **Mock Core APIs:** Emulate classes `SpreadsheetApp`, `UrlFetchApp`, `PropertiesService`, and `Session`.
2. **In-Memory Storage:** Use local dictionaries or JSON structures to mimic spreadsheet ranges, rows, and script properties.
3. **Execution Safety:** Intercept outbound HTTP requests via `UrlFetchApp` and return stubbed responses to avoid hitting live production endpoints during testing.
4. **Error Emulation:** Raise standard Google Workspace API quotas and timeout errors during high-volume mock loops.
