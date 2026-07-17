# TDD Generator Skill

Test-first development cycle extracted from robin warship's self-verification system.

## The Red-Green-Refactor Loop

### Step 1: Spec → Test (Red)
Given a function spec, generate tests FIRST:

```python
# spec: validate_email(email: str) -> bool
# Tests MUST cover:
def test_validate_email_valid():
    assert validate_email("user@example.com") == True

def test_validate_email_no_at():
    assert validate_email("userexample.com") == False

def test_validate_email_empty():
    assert validate_email("") == False

def test_validate_email_special_chars():
    assert validate_email("user+tag@example.com") == True

def test_validate_email_long_domain():
    assert validate_email("user@a.b.c.example.com") == True
```

### Step 2: Implement (Green)
Write minimum code to pass tests. No over-engineering.

### Step 3: Refactor
Improve code quality while keeping ALL tests passing.

## Test Categories Required

| Category | Coverage | Examples |
|----------|----------|----------|
| Normal cases | 60% | Happy path, expected inputs |
| Edge cases | 20% | Empty strings, max length, boundary values |
| Error cases | 15% | Invalid inputs, type mismatches, nulls |
| Performance | 5% | Large inputs, repeated calls |

## Verification Gate

After each implementation, verify:
1. `pytest` passes (all tests green)
2. `mypy --strict` passes (type safety)
3. No new uncovered lines (<80% coverage = BLOCK)
4. Cyclomatic complexity < 12 per function
