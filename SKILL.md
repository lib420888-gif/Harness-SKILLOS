---
name: harness-skillos
description: A personal skill-management harness that routes tasks to the right AI skills, confirms before high-risk or ambiguous actions, lets you choose between candidates, and remembers your preferences so it gets smarter every time. Use this when the user wants to organize, browse, install, recall, combine, or clean up AI skills, or when a task could match multiple skills.
license: MIT
---

# Harness SkillOS — 会记忆的技能管家

## 一句话
SkillOS 是一个"管理 AI 技能"的 harness：任务进来 → 看路由表 → 三模式决定怎么用 → 干完写记忆 → 下次更聪明。

## 工作循环（读记忆 → 干活 → 总结 → 写回）
1. **读**：开始前先读 memory/usage-log.md（信任度）和全局记忆（经验总结）
2. **路由**：读 router.md，匹配意图
3. **三模式**：自动 / 确认 / 选择（见 router.md 决策规则）
4. **干活**：加载技能（1-3 个），产出后对照「验收标准」校验；**偏离必须报告**
5. **写**：更新 usage-log；「你要的 ≠ 它给的」写进 feedback-cases

## 铁律
- 命中 0 个：先用通用能力，干完问用户要不要沉淀新技能
- 高风险 / 不可逆：必须先确认
- 偏离技能步骤：必须明说「我偏离了，因为…」
- 改技能文件前：问用户
- 陌生来源技能：先审查再装
- 环境不满足：不自动调用

## 目录
- router.md — 路由表（意图 → 技能）
- registry/ — 技能档案库（每个技能的身份证）
- memory/ — 记忆管家（usage-log / archive / feedback-cases）
- recipes/ — 配方库（命名组合）
- skills/ — 实际技能（global/ + project/）
- docs/design.md — 完整设计文档
