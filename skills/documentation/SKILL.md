# Documentation Skill

Auto-generate production-quality documentation from code analysis.

## Document Types

### README (entry point)
Required sections:
- One-liner: what this project does (1 sentence)
- Quick start: install + run in 3 steps
- Architecture: high-level diagram in text
- API: key functions/endpoints
- Contributing: how to add code

### API Docs (per module)
```markdown
## `function_name(param1: Type, param2: Type) -> ReturnType`

Description of what the function does.

Parameters:
- `param1` (Type): What this parameter controls, defaults to X
- `param2` (Type): Edge cases: empty, None, boundary values

Returns:
- `ReturnType`: Success case returns X, error case returns Y

Raises:
- `ValueError`: When param1 is invalid format
- `ConnectionError`: When external service is unreachable

Example:
```python
result = function_name("valid", 42)
# Returns: {"status": "ok", "data": [...]}
```
```

### Changelog
Generate from git log:
```
## [1.2.0] - 2026-07-17
### Added
- New feature X (PR #123)
### Changed
- Refactored Y for performance (+40%) (PR #122)
### Fixed
- Bug Z causing crash on empty input (#121)
```
