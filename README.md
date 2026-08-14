# Harness SkillOS — A Skill Manager That Remembers You

> 一个会记忆的技能管家：让 AI 的技能越用越懂你。

## Why
AI agents can install many skills, but two problems appear as the library grows:
- **Token bloat**: too many skills flood the context window.
- **Going off-track**: the agent picks the wrong skill, or silently improvises instead of following it.

**Harness SkillOS** is a **harness** (a management layer) that fixes both: it routes tasks to the right skills, confirms before risky or ambiguous actions, and **remembers your choices so it gets smarter every time** — a compounding loop: read memory → work → summarize → write back → get better.

## Features
- **3-mode routing**: auto (low-risk, clear intent) / confirm (high-risk) / choose (multiple candidates)
- **Multi-dimensional registry**: every skill tagged by capability, purpose, domain, and action role
- **5 scopes**: global / project / session / task / team
- **Memory manager**: trust levels, sleep → archive → recall, feedback → test cases
- **Recipes**: name and reuse skill combos ("资料文档链")

## Quick start
1. Clone this repo.
2. Drop skills into `skills/global/` or `skills/project/`.
3. Register each skill in `registry/` (copy `registry/_template.md`).
4. Let the harness read `router.md`, execute, and update `memory/`.

## Structure
```
skillos/
├── SKILL.md          # the harness itself
├── router.md         # intent → skill table + 3-mode decision rules
├── registry/         # skill profiles (ID cards)
├── memory/           # usage log / archive / feedback cases
├── recipes/          # named skill combos
└── skills/           # actual skills (global/ + project/)
```

## Status

**v0.1 skeleton** — the design is complete and research-backed (agentskills.io, Anthropic, Microsoft, CHI/ACL papers; see `docs/design.md`). Real skills and a live demo are being added. This repo evolves publicly — watch it grow.
