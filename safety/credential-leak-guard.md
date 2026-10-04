# Credential Leak Guard

## Purpose
Prevent hardcoded API keys, tokens, and secrets from committing to git repositories or deployment files.

## Operational Rules
1. **Pre-Commit Scan:** Scan all modified lines for patterns:
   - Google API Keys (`AIza[0-9A-Za-z-_]{35}`)
   - LINE Channel Access Tokens / Secrets
   - Generic Bearer tokens, private keys (`-----BEGIN PRIVATE KEY-----`)
2. **Environment Variable Enforcement:** Every secret must originate from `process.env`, `dotenv`, or `PropertiesService.getScriptProperties()`.
3. **Action:** Block code generation and alert immediately if raw strings containing credentials are detected.
