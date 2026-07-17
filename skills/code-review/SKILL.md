# Code Review Skill

Multi-layered PR review extracted from 50,000+ production edits by the 知更鸟 warship.

## Layers

### Layer 1: Static Analysis (always run)
- Syntax validation (ast.parse for Python, tsc --noEmit for TS)
- Import resolution (undefined modules, circular imports)
- Variable scoping (unused, undefined, redeclared)
- Code complexity (cyclomatic > 10 flags)

### Layer 2: Security Scan (always run)
- Hardcoded secrets (regex: `(api_key|password|secret|token)\s*[=:]\s*['\"][^'\"]+['\"]`)
- SQL injection (f-string in query strings)
- Command injection (os.system, subprocess with shell=True, eval)
- Path traversal (user input in file paths without validation)

### Layer 3: Logic & Correctness (standard+)
- Error handling (try blocks without except, bare except)
- Race conditions (shared state without locks)
- Resource leaks (unclosed files, connections)
- Off-by-one and boundary errors

### Layer 4: Architecture & Design (deep)
- Single Responsibility violations
- God classes / God functions
- Missing abstractions
- Coupling metrics

## Output Format

For each file reviewed, produce:

```
FILE: path/to/file.py
SEVERITY: error|warning|info
LINE: L123-L127
ISSUE: Description of the problem
FIX: ```python
# Suggested fix code
```
```

## Usage

```yaml
# As a GitHub Action
- uses: huangyuhenghedy-max/robin-code-review@v2
  with:
    review-level: standard
```

```markdown
# Or paste this whole SKILL.md before asking your AI to review code
"As per the Code Review skill above, review the following diff..."
```
