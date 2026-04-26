---
name: github-pr-writer
version: 1.0.0
description: 面向 GitHub Pull Request 的写作与改写 skill。当用户提到 PR title、PR description、变更总结、根据 diff 或文件列表生成 PR 文案、测试说明、风险说明、migration notes、rollback notes、reviewer summary，或希望把代码变更整理成标准 PR 内容时触发。
---

# GitHub PR Writer

目标：根据 diff、文件变化、提交记录和上下文生成清晰、结构化、便于 review 的 PR 文案。

## 适用场景

- 生成 PR title
- 生成 PR description
- 根据 diff 总结变更
- 生成 reviewer summary
- 生成 testing instructions
- 生成 risks / migration / rollback notes
- 把口语化 change summary 改写为工程化 PR 文案

## 输入优先级

1. diff / 文件列表 / 变更摘要
2. 当前 PR title / body
3. 模块、仓库、上下文
4. 变更目标：feat / fix / refactor / perf / docs / test / ci
5. 风格与语言偏好

## PR Title 规则

- 优先使用 Conventional Commits 风格
- 默认控制在 72 字符内
- 聚焦“变更主题”，不要逐文件描述

示例：

- `fix(auth): prevent duplicate refresh attempts on expired sessions`
- `feat(search): add repository visibility filters`
- `refactor(cache): simplify invalidation flow`

## PR Description 模板

```md
## Summary
...

## Why
...

## What Changed
- ...
- ...

## Impacted Areas
- ...

## How to Test
1. ...
2. ...

## Risks
- ...

## Follow-ups
- ...
```

## 归纳原则

- 先抽象为 2~5 个变更主题
- 不机械逐文件翻译 diff
- 强调 why、impact、test、risk
- 如果是关键路径（auth、payment、cache、migration），明确 reviewer focus

## 推荐附加产物

在上下文足够时，可一并输出：

- reviewer summary
- regression checklist
- migration notes
- rollback notes
- release note draft

## 输出策略

### 用户给 diff / 文件列表

输出：

1. 最佳 PR title
2. PR description
3. 风险等级与 reviewer focus
4. 备选 title 2~3 个

### 用户只说“写个 PR”

输出：

- 标准版
- 更简洁版
- 更正式版

## 风险与测试推断

可保守推断：

- 风险级别：low / medium / high
- 测试建议：unit / integration / manual / regression / smoke
- reviewer focus：最值得看的 2~4 点

不得编造线上结果或性能数据。

## 语言规则

- 跟随用户与仓库主语言
- 英文优先使用 `Summary / Why / What Changed / How to Test / Risks`

## 质量检查

- 是否归纳了变更主题
- 是否写清楚 why
- 是否给出 test 和 risk
- title 是否具体且可扫描
