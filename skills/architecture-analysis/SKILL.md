# Architecture Analysis Skill

DDD-aligned architecture review for production codebases.

## Analysis Dimensions

### 1. Bounded Contexts
Map all modules and identify:
- Context boundaries (what belongs together)
- Shared kernel (what MUST be shared)
- Anti-corruption layers (translators between contexts)

### 2. Dependency Flow
```
Rule: Dependencies point INWARD toward domain layer.
UI → Application → Domain ← Infrastructure
                                    ↑
                                    |
                              External services
```
- Violations: Infrastructure importing UI code
- Cycles: A→B→A (break with interface)

### 3. Coupling Metrics
- Afferent coupling (Ca): how many modules depend on THIS
- Efferent coupling (Ce): how many THIS depends on
- Instability = Ce / (Ca + Ce): 0=stable, 1=unstable
- Abstractness = abstract classes / total classes

### 4. Technical Debt Assessment
- TODO/FIXME density: count per 1000 LOC
- Test coverage of critical paths
- Deprecated API usage
- Dead code (never-called functions)

## Output

```markdown
## Architecture Review: project

### Strengths
- Clean context separation between auth and billing
- Well-factored domain models

### Risks
- HIGH: Shared kernel between orders and payments leaking
- MEDIUM: Infrastructure → Domain cycle in reporting

### Recommendations
1. Extract shared order/payment logic into domain service
2. Add anti-corruption layer between external API and core
3. Remove dead code in legacy/ directory (~1200 LOC)
```
