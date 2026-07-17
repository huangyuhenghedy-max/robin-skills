# Security Audit Skill

Expert-level security audit pattern library, battle-tested on 22 production modules.

## Attack Vectors

### 1. Hardcoded Secrets
```
Pattern: (key|secret|token|password|credential)\s*[=:]\s*['\"][A-Za-z0-9_\-]{16,}['\"]
False positive: example.com, test, placeholder, YOUR_*
```

### 2. Injection Vulnerabilities
- SQL: `f"SELECT * FROM {user_input}"` → parameterized
- NoSQL: `db.find({"$where": user_input})` → sanitize
- Command: `os.system(f"rm {path}")` → subprocess with list
- Template: `render_template_string(user_input)` → autoescape

### 3. Authentication & Authorization
- Missing rate limiting on login endpoints
- JWT without expiration or signature verification
- Role checks only in frontend
- Session fixation vulnerability

### 4. Data Exposure
- Stack traces in error responses
- Internal IPs in headers
- Debug endpoints in production
- Excessive logging of PII

### 5. Dependency Risks
- Outdated packages with known CVEs
- Deprecated APIs still in use
- Unnecessary devDependencies in production

## Audit Report Format

```markdown
## Security Audit: module_name

### CRITICAL (immediate action required)
- L45: Hardcoded AWS secret key → Move to env var

### HIGH (fix this sprint)
- L123: SQL injection in user query → Parameterize

### MEDIUM (schedule next sprint)
- L67: Missing rate limiting → Add throttle

### LOW (note for refactoring)
- L89: Debug endpoint exposed → Remove
```
