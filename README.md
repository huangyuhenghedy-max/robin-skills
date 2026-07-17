# 🚀 Robin Skills

> Production-grade AI agent skills, battle-tested in the 知更鸟 warship.

Drop these skills into any AI coding assistant (Claude Code, Codex, Cursor, Windsurf) and get instant expert-level code analysis, security auditing, architecture review, and more.

## Skills

| Skill | Description | Lines |
|-------|-------------|-------|
| [Code Review](skills/code-review/SKILL.md) | Multi-layered PR review: syntax, security, logic, architecture | 320+ |
| [Security Audit](skills/security-audit/SKILL.md) | 15+ attack vector detection: API keys, SQLi, XSS, command injection | 280+ |
| [Architecture Analysis](skills/architecture-analysis/SKILL.md) | DDD, coupling analysis, SOLID principles, tech debt assessment | 260+ |
| [TDD Generator](skills/tdd-generator/SKILL.md) | Test-first workflow: spec→test→implement→refactor cycle | 240+ |
| [Refactoring](skills/refactoring/SKILL.md) | Pattern-based code transformation with safety nets | 220+ |
| [Documentation](skills/documentation/SKILL.md) | Auto-generate README, API docs, changelogs, architecture docs | 200+ |

## Why Robin Skills?

These aren't theoretical prompts — they're extracted from **50,000+ real codebase edits** performed by the 知更鸟 warship:

- ✅ **Zero dependencies** — pure instructions, no install
- ✅ **Drop-in ready** — just `@skills/code-review` in your prompt
- ✅ **Battle-hardened** — refined across 22+ production modules
- ✅ **Tool-agnostic** — works with Claude, Codex, Cursor, Gemini

## Quick Start

```bash
# Copy a skill into your project
cp -r skills/code-review .skills/code-review

# Then reference it in your AI tool prompt:
# "Load .skills/code-review/SKILL.md and review the PR diff"
```

Or just paste the SKILL.md content directly into your conversation with any AI assistant.

## Architecture

```
robin-skills/
├── README.md
├── skills/
│   ├── code-review/
│   │   └── SKILL.md
│   ├── security-audit/
│   │   └── SKILL.md
│   ├── architecture-analysis/
│   │   └── SKILL.md
│   ├── tdd-generator/
│   │   └── SKILL.md
│   ├── refactoring/
│   │   └── SKILL.md
│   └── documentation/
│       └── SKILL.md
└── LICENSE
```

## License

MIT — use freely, build awesome things.

---

_Built by the 知更鸟 warship — a self-evolving AI agent orchestration framework._
