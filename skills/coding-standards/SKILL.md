---
name: coding-standards
description: Enforces coding standards while writing code to prevent common P0/P1 issues. Auto-activates when writing or editing code. Covers security, error handling, performance, and boundary conditions.
---

# Coding Standards

Apply these rules **while writing code** to avoid issues before review.

## Security (P0)

- **Never** concatenate user input into SQL/NoSQL queries, shell commands, or file paths — use parameterized queries, allowlists, or sanitization
- **Never** use `dangerouslySetInnerHTML`, `innerHTML`, or unescaped template output with user data
- **Never** hardcode secrets, API keys, or tokens — use environment variables
- **Never** trust client-provided roles, IDs, or flags — always validate server-side
- **Always** add auth guards and ownership checks on new endpoints
- **Always** validate and sanitize user input at system boundaries

## Error Handling (P1)

- **Never** swallow exceptions: no empty `catch {}` or catch-and-log-only
- **Always** handle async errors: `.catch()` on promises, try-catch in async functions
- **Always** return meaningful error messages to callers (without leaking internals)
- **Ask yourself**: "What happens when this operation fails?"

## Performance (P1)

- **Never** query in a loop (N+1) — batch with `IN (?)` or `$in`
- **Never** load unbounded data — always paginate or limit
- **Never** do sync I/O or heavy computation on the request path
- **Always** add timeouts on external calls (HTTP, DB, Redis)
- **Ask yourself**: "How does this behave with 100x data?"

## Boundary Conditions (P1)

- **Always** check for null/undefined before property access on external data
- **Always** handle empty arrays before accessing `[0]` or `.length - 1`
- **Always** check for division by zero
- **Never** use `if (value)` when `0`, `""`, or `false` are valid — use explicit checks
- **Ask yourself**: "What if this is null? What if this is empty?"

## Race Conditions (P1)

- **Never** do check-then-act without atomic operations (e.g., `if (exists) then create`)
- **Never** do read-modify-write without transactions (e.g., `balance = get(); balance -= x; set(balance)`)
- **Always** use atomic operations for counters (`UPDATE SET count = count + 1`, not read-then-write)
- **Ask yourself**: "What happens if two requests hit this simultaneously?"
