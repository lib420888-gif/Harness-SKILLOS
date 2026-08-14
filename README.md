# Harness SkillOS — A Skill Manager That Remembers You

> The personal skill-management harness that routes tasks to the right AI skill, confirms before risky or ambiguous calls, and **gets smarter every time you use it**.

## The Problem

AI agents can install many skills, but as the library grows, two things break:

- **Token bloat** — every skill's catalog entry lives in the context window. Real case: a single service's tool definitions once burned **1.17 million tokens**; on-demand loading cut a workload from **150k to 2k tokens**.
- **Going off-track** — agents silently ignore, skip, or improvise around skills (documented in Claude Code issues #58024, #19290, #19308). The skill `description` is the *only* trigger signal — and it's often written badly.

## The Idea

What if a skill manager **remembers how you work**?

```
read memory → route the task → confirm when needed → execute → verify → write memory back → next time is smarter
```

SkillOS is a **harness** (the management layer around a model) that treats your skill library like a living system:

- It keeps only name + description in the hot context — progressive disclosure, applied to itself
- It decides *when* to ask you: **auto** for clear/low-risk tasks, **confirm** for risky ones, **choose** when multiple skills match
- It tracks trust per skill × scope, sleeps unused skills, archives them, and recalls them when a similar task returns

## Features

| | |
|---|---|
| **3-mode routing** | Auto / Confirm / Choose — driven by match count + intent clarity + risk level (evidence-backed) |
| **Multi-dimensional registry** | Every skill tagged by capability, purpose, domain, and action role — find anything from any angle |
| **5 scopes** | global / project / session / task / team — the right skill in the right place |
| **Memory manager** | trust levels, sleep → archive → recall, feedback that becomes test cases |
| **Recipes** | name and reuse skill combos ("资料文档链") |
| **Safety by design** | deviations must be reported; skill files can't be silently rewritten; unknown sources are reviewed first |

## Research-backed

The design cites the agentskills.io spec, Anthropic's internal 9-category skill taxonomy, Microsoft's Copilot orchestrator (top-5 candidate selection), and papers from CHI '26, ACL '26, and EMNLP '25 on when to ask users, where to place confirmations, and memory safety. Full details in `docs/design.md`.

## Quick start

1. Clone this repo.
2. Drop skills into `skills/global/` or `skills/project/`.
3. Register each skill in `registry/` (copy `registry/_template.md`).
4. The harness reads `router.md`, executes, and updates `memory/` — it gets smarter with use.

## Structure

```
skillos/
├── SKILL.md          # the harness itself
├── router.md         # intent → skill + 3-mode decision rules
├── registry/         # skill profiles (ID cards)
├── memory/           # usage log / archive / feedback cases
├── recipes/          # named skill combos
└── skills/           # actual skills (global/ + project/)
```

## Status

**v0.2** — live and dogfooded: it manages its own `github-publish` skill. Actively evolving.
