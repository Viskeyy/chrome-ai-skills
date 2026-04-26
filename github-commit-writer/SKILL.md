---
name: github-commit-writer
version: 1.0.0
description: 面向 Git commit 的写作与改写 skill。当用户提到 commit message、根据 diff / 文件变化生成 commit、squash commit、merge commit、Conventional Commits、branch naming，或希望把代码变更归纳成更标准的提交文案时触发。
---

# GitHub Commit Writer

目标：根据代码变更生成清晰、简洁、可追踪的 commit message，优先遵循 Conventional Commits。

## 适用场景

- 生成 commit message
- 重写 commit subject
- 补充 commit body
- 生成 squash commit message
- 生成 merge commit summary
- 生成 branch name

## 输入优先级

1. diff / 文件列表 / 变更摘要
2. 变更意图：feat / fix / refactor / perf / docs / test / ci / chore
3. 模块、目录、scope
4. 是否需要 body / squash / 多候选版本

## 默认输出

1. 最佳 commit subject
2. 需要时给出 body
3. 备选 subject 2~3 个

## 规则

- subject 使用祈使句、现在时
- 优先 <= 72 字符
- 推荐格式：`type(scope): subject`
- body 解释 why / 高层 what，不逐文件复述 diff

示例：

```text
fix(auth): avoid duplicate token refresh requests

Use a shared in-flight refresh promise to prevent concurrent
requests from triggering multiple refresh operations.
```

## 类型映射

- 新功能 → feat
- 修复 → fix
- 重构 → refactor
- 性能 → perf
- 文档 → docs
- 测试 → test
- 构建 → build
- CI/CD → ci
- 杂项 → chore

## Scope 规则

- 优先用稳定模块边界：`auth` `search` `billing` `cache` `api` `ui` `ci`
- 若涉及多个模块，可省略 scope
- 避免无意义 scope：`misc` `update` `stuff`

## Branch Name 规则

默认输出 3 个候选，格式：

```text
<type>/<scope>-<short-kebab-summary>
```

示例：

- `fix/auth-refresh-loop`
- `feat/search-repo-visibility-filter`
- `refactor/cache-invalidation-flow`

## 输出策略

### 用户给了 diff

输出：

- 最佳 commit
- 带 body 版本
- 备选 2~3 个
- branch name（如有需要）

### 用户要 squash commit

输出：

- 一个整合后的最佳 subject
- 一个简洁 body

## 质量检查

- 是否避免空泛词
- 是否能从 subject 看出核心变化
- 是否符合 Conventional Commits
- body 是否解释 why 而不是重复 what
