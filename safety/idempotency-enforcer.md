# Idempotency Enforcer

## Purpose
Ensure operations involving external side-effects (e.g., messaging, transactions, database inserts) cannot be executed multiple times accidentally.

## Operational Rules
1. **Unique Key Generation:** Require an `idempotency_key` or unique transaction hash for all write operations.
2. **Check Before Write:** Verify whether the key has already been processed within the lookback window (e.g., CacheService, Sheet index).
3. **Deduplication Handling:** If duplicate key exists, return the cached result immediately and abort downstream API calls.
4. **Atomic Locking:** Apply script locking (`LockService.getScriptLock()`) during critical state updates to avoid race conditions.
