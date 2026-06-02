# Merge Request Example

Input:

```text
Audience: Product Manager
Complexity: Detailed
MR: Add account lockout after five failed login attempts. Changed authentication service, login error message, audit logging, and tests.
```

Output:

### Merge Request Snapshot

- Technical summary: The authentication flow now tracks failed login attempts, locks the account after five failures, records the event in audit logs, and includes test coverage for the lockout behavior.
- Non-technical summary: The system now helps protect accounts by temporarily blocking repeated failed login attempts.
- Business impact: This reduces the risk of unauthorized access and supports stronger account security.
- Risks: Users who forget their password may need clear recovery guidance. Support teams should know how lockouts are resolved.

### 1. What is this feature?

This change adds account lockout protection after repeated failed login attempts.

### 2. Why do we need it?

Repeated failed login attempts can indicate someone is trying to guess a password. Lockout protection adds a safety barrier.

### 3. What problem does it solve?

It reduces the risk of automated or repeated attempts to access an account without permission.

### 4. How does it work?

The system counts failed login attempts. After the allowed number is reached, it temporarily blocks further login attempts for that account.

Analogy: Think of it like a building badge reader that pauses access attempts after too many incorrect PIN entries.

### 5. What changes for the user?

Most users will not notice anything. Users who enter the wrong password several times may see a message explaining that the account is temporarily locked.

### 6. What remains unchanged?

The normal login process remains the same for users who enter correct credentials.

### 7. Risks and edge cases

The message must be clear enough that legitimate users know what to do next. QA should test successful login, failed login, lockout, unlock, and password reset flows.

### 8. Real-world example

A user mistypes their password five times. The system temporarily blocks more attempts and guides them toward the correct recovery path.

### 9. Non-technical summary

This MR improves account security by limiting repeated failed login attempts while keeping the standard login experience unchanged for most users.

