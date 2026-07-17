# Refactoring Skill

Safe, pattern-based code transformation adapted from 50,000+ CONTEXT_REPLACE edits.

## Safety Rules

1. **One pattern at a time** — never mix concerns in a single pass
2. **Tests must pass before AND after** — verify with CI
3. **Small diffs only** — max 15 lines changed per edit
4. **CONTEXT_REPLACE format** — exact original code match required

## Refactoring Patterns

### Extract Method
```
WHEN: A function body has 2+ distinct logical blocks
WHAT: Extract each block into named private methods
WHY: Readability, testability, reusability
```

### Replace Condition with Polymorphism
```
WHEN: if/elif chain checking object type
WHAT: Move each branch into a subclass method
WHY: Open/closed principle, easier to extend
```

### Introduce Parameter Object
```
WHEN: Function takes 4+ related parameters
WHAT: Group into a dataclass/typed dict
WHY: Reduces signature complexity, groups validation
```

### Separate Query from Modifier
```
WHEN: A function both reads state AND changes it (CQRS violation)
WHAT: Split into read-only query + void modifier
WHY: Predictable side effects, easier testing
```

### Replace Magic Literal
```
WHEN: Raw numbers/strings with no explanation
WHAT: Extract to named constants at module level
WHY: Self-documenting, single source of truth
```

## Gate Check

Before committing each refactor:
```
[ ] All existing tests pass
[ ] No new type errors (mypy strict)
[ ] Cyclomatic complexity unchanged or reduced
[ ] No dead code introduced
[ ] Public API unchanged (unless intentional)
```
