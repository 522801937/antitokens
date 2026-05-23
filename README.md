# Token Optimizer

一个 Claude Code 技能文件，专注于 token 效率优化。核心原则：**用最少的 tokens 达成目标，不浪费任何上下文。**

## 策略概览

- **上下文管理** — 只读必要文件，用 Grep 定位而非全文读取，合并独立查询
- **思考效率** — 禁止反复推演、过度分析，确认需求后直接行动
- **输出精简** — 每次回复 3 句话以内，不复述操作，不预告步骤
- **工具调用优化** — 无依赖调用并行化，Edit 优先于 Write
- **Agent 使用** — 3+ 次查询用 Explore Agent，Plan Agent 仅用于架构级设计

## 使用方式

将 `token-optimizer.md` 放入 `.claude/skills/` 目录，通过 `/token-optimizer` 调用。
