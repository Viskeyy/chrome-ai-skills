---
name: github-issue-writer
version: 1.0.0
description: 面向 GitHub issue 的写作与改写 skill。当用户提到 issue title、issue description、bug report、feature request、issue comment、implementation plan、acceptance criteria、任务拆解、问题澄清，或希望把零散问题描述整理成更标准、更有逻辑、更可执行的 issue 内容时触发。
---

# GitHub Issue Writer

目标：把零散的问题、需求、讨论整理成适合提交到 GitHub issue 的高质量文本。

## 适用场景

- 重写 issue title
- 重写或生成 issue description
- bug report 规范化
- feature request 规范化
- issue comment / status update
- implementation plan
- acceptance criteria
- scope / non-goals / risks

## 输入优先级

1. issue 类型：bug / feature / refactor / task
2. 原始描述、聊天记录、日志、截图说明
3. 模块/仓库/技术上下文
4. 影响范围、复现方式、预期结果
5. 语言与风格偏好

信息不足时，也要输出可直接使用的版本，并附 `Assumptions / Open Questions`。

## 输出原则

- 先写事实，再写组织结构
- 不编造根因、数据、结果
- 标题具体、可扫描
- 描述包含背景、问题、目标、方案、范围、验收
- 面向协作，方便 PM、开发、QA 理解

## 标题规则

- 优先 72 字符内
- 使用“模块/对象 + 动作/问题”结构
- 避免空泛词：improve / optimize / update（除非具体）

示例：

- `fix(auth): prevent refresh loop on expired session`
- `feat(search): support filtering by repository visibility`
- `Refactor cache invalidation flow to reduce duplicate writes`

## Issue Description 模板

### Bug Issue

```md
## Summary
...

## Current Behavior
...

## Expected Behavior
...

## Reproduction
1. ...
2. ...

## Scope / Impact
- ...

## Suspected Cause
...

## Proposed Fix
...

## Acceptance Criteria
- [ ] ...
```

### Feature / Task Issue

```md
## Background
...

## Problem / Opportunity
...

## Goal
...

## Proposed Solution
...

## Scope
- In scope: ...
- Out of scope: ...

## Acceptance Criteria
- [ ] ...

## Risks / Dependencies
...
```

## Issue Comment 模板

```md
## Update
...

## Findings
- ...

## Proposed Next Steps
1. ...

## Open Questions
- ...
```

## 输出策略

### 用户只说“帮我改写 issue”

输出：

1. 推荐版本
2. 更简洁版本
3. 更正式版本

### 用户提供 bug 上下文

输出：

- issue title
- issue description
- acceptance criteria
- risks / assumptions

### 用户提供 feature 想法

输出：

- issue title
- feature description
- scope / non-goals
- implementation plan
- acceptance criteria

## 语言规则

- 跟随用户输入语言
- 英文仓库内容优先输出英文
- 双语时按 English / 中文 分段

## 质量检查

- 是否说明了 why，而非只写 what
- 是否可直接复制到 GitHub
- 是否有明确的 acceptance criteria
- 是否避免把未知信息写成已知事实
