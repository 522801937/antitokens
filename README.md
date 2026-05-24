<p align="center">
  <img src="https://img.shields.io/badge/Claude%20Code-Skill-blue?style=for-the-badge&logo=anthropic" alt="Claude Code Skill">
  <img src="https://img.shields.io/badge/license-MIT-green?style=for-the-badge" alt="License: MIT">
  <img src="https://img.shields.io/github/stars/522801937/antitokens?style=for-the-badge" alt="GitHub stars">
  <img src="https://img.shields.io/github/languages/top/522801937/antitokens?style=for-the-badge" alt="Top language">
</p>

<h1 align="center">⚡ AntiTokens</h1>
<p align="center"><strong>Token Optimizer for Claude Code</strong> — <em>Maximum results. Minimum tokens. Zero waste.</em></p>

---

[English](#english) | [中文](#中文)

---

<a name="english"></a>
## English

### What is AntiTokens?

**AntiTokens** is a Claude Code skill that enforces aggressive token efficiency. It rewires Claude's behavior to minimize context consumption while maximizing output quality — think of it as a "token diet" for your AI coding sessions.

### Why AntiTokens?

Claude Code sessions can burn through tokens fast. Redundant file reads, overthinking, verbose output, and serial tool calls all add up. AntiTokens systematically eliminates every source of token waste:

| Waste Source | AntiTokens Solution |
|---|---|
| Reading entire files when you only need one function | **Grep-first strategy**: locate → then read with `limit`/`offset` |
| "Let me think about this..." spiral | **Decide & act**: no internal deliberation longer than the task itself |
| "Here's what I'm going to do..." followed by "Done! Here's what I did..." | **3-sentence rule**: output only what matters, no narration |
| Reading 5 files one-by-one | **Parallelize everything**: all independent calls fire simultaneously |
| Using Write when Edit would do | **Edit-first**: smaller diffs, fewer tokens |
| Launching full agents for simple grep | **Explore Agent threshold**: only offload when 3+ queries needed |

### Features

- **Context Management** — Read only what you need, when you need it. Merge independent queries. Skip what's already known.
- **Thinking Efficiency** — No deliberation loops. No option enumeration for trivial decisions. Choose → act → verify.
- **Output Compression** — Max 3 sentences per reply. No recaps. No previews. No filler.
- **Tool Call Optimization** — Parallel-first. Edit over Write. Grep/Glob over Bash equivalents.
- **Smart Agent Routing** — Explore Agent for 3+ searches. Plan Agent only for architecture. Direct tools for everything else.
- **Plan Mode Guardrails** — Only enter plan mode for 5+ file changes or architecture decisions.

### Installation

```bash
# Clone the repo
git clone https://github.com/522801937/antitokens.git

# Copy the skill into your Claude Code skills directory
mkdir -p ~/.claude/skills/
cp antitokens/token-optimizer.md ~/.claude/skills/token-optimizer.md
```

Or directly:

```bash
curl -o ~/.claude/skills/token-optimizer.md https://raw.githubusercontent.com/522801937/antitokens/main/token-optimizer.md
```

### Usage

Once installed, invoke the skill in any Claude Code session:

```
/token-optimizer
```

The skill applies automatically for the remainder of the session. Combine it with any task — coding, debugging, refactoring — and watch your token consumption drop.

### Before / After

**Before AntiTokens:**
```
User: rename getCwd to getCurrentWorkingDirectory
Claude: Let me think about this. First, I'll read the file to understand
       the current implementation. [reads entire 500-line file]
       I can see the function is defined on line 42 and called in 3 places.
       Let me trace each call site. [reads 3 more files]
       OK, I have a clear picture now. Here's my plan:
       1. Rename the definition
       2. Update call site 1
       3. Update call site 2
       ... [500+ tokens burned]
```

**With AntiTokens:**
```
User: rename getCwd to getCurrentWorkingDirectory
Claude: [Grep for getCwd → 4 matches in 2 files → parallel Edit all 4 → done]
       Renamed in file.ts:42 and 3 call sites.
       ✓
```

### Directory Structure

```
antitokens/
├── README.md              # You are here
├── token-optimizer.md     # The skill file (drop into ~/.claude/skills/)
├── LICENSE                # MIT
└── .gitignore
```

### Contributing

Found a source of token waste that AntiTokens doesn't cover yet? PRs welcome.

1. Fork the repo
2. Create a branch (`git checkout -b fix/more-savings`)
3. Edit `token-optimizer.md` with your improvement
4. Open a PR with a before/after example

### License

MIT — see [LICENSE](LICENSE).

---

<a name="中文"></a>
## 中文

### AntiTokens 是什么？

**AntiTokens** 是一个 Claude Code 技能文件，强制实施极致的 token 效率策略。它重塑 Claude 的行为模式，在保证输出质量的前提下将上下文消耗降到最低。

### 为什么需要 AntiTokens？

Claude Code 会话的 token 消耗速度极快。冗余的文件读取、过度思考、啰嗦输出、串行工具调用——每一项都在浪费宝贵的上下文。AntiTokens 系统性地消除每一处 token 浪费：

| 浪费来源 | AntiTokens 解决方案 |
|---|---|
| 只需要一个函数却读取整个文件 | **Grep 优先**：先定位，再用 `limit`/`offset` 精准读取 |
| "让我想想……"的思考螺旋 | **决策即行动**：内部推理不得长于任务本身 |
| "我打算做 X……"+"已完成 X……" | **三句话原则**：只输出有信息量的内容 |
| 逐个读取 5 个文件 | **全并行**：所有无依赖调用同时发出 |
| 能用 Edit 却用 Write | **Edit 优先**：更小的 diff，更少的 token |
| 简单搜索也启动 Agent | **Explore Agent 阈值**：3+ 次查询才卸载 |

### 功能特性

- **上下文管理** — 只读需要的，合并独立查询，跳过已知信息
- **思考效率** — 不反复推演，不枚举选项，选好路径立刻行动
- **输出压缩** — 每次回复 ≤3 句话，不复述，不预告
- **工具调用优化** — 并行优先，Edit 优先，专用工具优先
- **智能 Agent 路由** — 3+ 搜索用 Explore Agent，架构设计才用 Plan Agent
- **Plan Mode 守门** — 仅 5+ 文件改动或架构决策才进入计划模式

### 安装

```bash
git clone https://github.com/522801937/antitokens.git
mkdir -p ~/.claude/skills/
cp antitokens/token-optimizer.md ~/.claude/skills/token-optimizer.md
```

或一键安装：

```bash
curl -o ~/.claude/skills/token-optimizer.md https://raw.githubusercontent.com/522801937/antitokens/main/token-optimizer.md
```

### 使用

在 Claude Code 会话中输入：

```
/token-optimizer
```

技能会在当前会话持续生效。搭配任何任务使用——编码、调试、重构——token 消耗立竿见影地下降。

### 效果对比

**使用前：**
```
用户：把 getCwd 重命名为 getCurrentWorkingDirectory
Claude：让我分析一下这个需求……先读取文件了解当前实现
       [读取整个 500 行文件]
       函数定义在 42 行，有 3 处调用。让我逐个确认
       [读取 3 个文件]
       好的，我有了清晰的思路。我的计划是：
       1. 重命名定义
       2. 更新调用点 1
       3. 更新调用点 2
       ... [浪费 500+ tokens]
```

**使用后：**
```
用户：把 getCwd 重命名为 getCurrentWorkingDirectory
Claude：[Grep 定位 getCwd → 2 个文件 4 处匹配 → 并行 Edit → 完成]
       已重命名，2 个文件共 4 处。
       ✓
```

### 项目结构

```
antitokens/
├── README.md              # 项目说明
├── token-optimizer.md     # 技能文件（放入 ~/.claude/skills/）
├── LICENSE                # MIT 许可证
└── .gitignore
```

### 贡献

发现 AntiTokens 还没覆盖到的 token 浪费场景？欢迎 PR。

1. Fork 本仓库
2. 创建分支 (`git checkout -b fix/more-savings`)
3. 修改 `token-optimizer.md`
4. 提交 PR 并附带 before/after 示例

### License

MIT — 详见 [LICENSE](LICENSE)。

---

<p align="center">
  <sub>Built for developers who value every token.</sub>
</p>
