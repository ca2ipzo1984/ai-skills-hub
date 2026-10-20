# Skill: Browser Automation (OpenClaw)

Use this skill when controlling web pages with browser tools, especially for multi-step flows, login verification, tab management, or recovering from stale refs/timeouts.

## Operating Loop & Best Practices
1. **Pre-Flight State Check:**
   - Verify browser setup availability before acting (`action="status"`).
   - Use `action="profiles"` if session or login state matters.
   - Run `action="tabs"` before opening new tabs to avoid orphaned windows.

2. **Stable Tab Handles:**
   - Always open important tabs with a label (e.g. `label="meet"`).
   - Store `suggestedTargetId` from responses and pass it as `targetId` in subsequent calls to maintain context.

3. **Read Before Click:**
   - Use `action="text"` with selectors for visible text.
   - For interactive elements, capture an `action="snapshot"` on the target ID. Prefer durable ARIA refs (`refs="aria"`).
   - Re-snapshot immediately after navigation, form submissions, or modal popups.

4. **Action Execution:**
   - Prefer `action="act"` with exact refs obtained from the freshest snapshot.
   - Avoid blind static waits; wait for visible UI states or specific elements to appear.

5. **Diagnostic & Blocker Recovery:**
   - Check network failures with `action="requests"` (limit 50).
   - Check page console errors with `action="errors"` (limit 50).
   - If the page requires CAPTCHA, 2FA, or manual login, stop execution and alert the user immediately.
