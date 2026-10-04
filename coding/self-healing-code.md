# Self-Healing Code Loop

## Purpose
Automate bug identification, patching, and regression testing in a closed loop until 100% test pass rate without human intervention.

## Operational Rules
1. **Analyze Error Trace:** Extract stack trace, line numbers, and root causes directly from test execution output.
2. **Isolate Scope:** Modify only the functions causing failure. Do not alter working signatures or delete production comments.
3. **Draft Patch:** Implement minimal code change addressing the logical failure.
4. **Execute Verification:** Run unit/mock test immediately.
5. **Convergence Limit:** Repeat cycle maximum 3 times. If unresolved, revert changes and report exact failing condition.
