# Claude Code 使用手册

## 一、当前可用的 Skills 一览

### Superpowers 系列（开发工作流）

| Skill | 用途 | 触发场景 |
|---|---|---|
| `superpowers:using-superpowers` | 了解如何使用 skills 体系 | 每次对话开始时 |
| `superpowers:brainstorming` | 需求分析、方案头脑风暴 | 创建新功能、修改行为前 |
| `superpowers:writing-plans` | 编写实施计划 | 有明确需求、多步骤任务、动手写代码前 |
| `superpowers:executing-plans` | 按计划逐步执行 | 已有书面计划，需要分批执行并审查 |
| `superpowers:subagent-driven-development` | 并行派发独立任务给子 agent | 当前会话中有多个独立任务 |
| `superpowers:dispatching-parallel-agents` | 并行派发 2 个以上独立任务 | 同上，更通用的并行派发 |
| `superpowers:test-driven-development` | 测试驱动开发 | 实现功能或修 bug 前，先写测试 |
| `superpowers:systematic-debugging` | 系统性调试 | 遇到 bug、测试失败、异常行为 |
| `superpowers:requesting-code-review` | 请求代码审查 | 完成任务、实现大功能、合并前 |
| `superpowers:receiving-code-review` | 处理审查反馈 | 收到 code review 意见后 |
| `superpowers:verification-before-completion` | 完成前的验证 | 声称任务完成、修复完毕、测试通过前 |
| `superpowers:finishing-a-development-branch` | 完成开发分支 | 所有测试通过，需要决定如何合并 |
| `superpowers:using-git-worktrees` | 创建隔离工作空间 | 需要隔离的功能开发 |
| `superpowers:writing-skills` | 创建/编辑 skills | 需要自定义新的 skill |

### 工具类 Skills

| Skill | 用途 |
|---|---|
| `update-config` | 配置 Claude Code 设置（权限、环境变量、hooks 等） |
| `keybindings-help` | 自定义键盘快捷键 |
| `simplify` | 检查代码质量，消除冗余 |
| `fewer-permission-prompts` | 减少频繁的权限弹窗 |
| `loop` | 定时循环执行任务（如每 5 分钟检查一次部署状态） |
| `claude-api` | 构建和调试 Claude API / Anthropic SDK 应用 |
| `init` | 为新项目初始化 CLAUDE.md |
| `review` | Review Pull Request |
| `security-review` | 安全审查当前分支的改动 |

---

## 二、怎么使用 Skills

### 方式一：直接输入 slash command

```
/brainstorming
/writing-plans
/systematic-debugging
```

### 方式二：自然语言触发

直接描述你的意图，Claude Code 会自动调用合适的 Skill。

例如："帮我调试这个报错" → 自动触发 `superpowers:systematic-debugging`

---

## 三、日常使用最佳实践

### 1. 提需求的最佳方式

```
❌ 不好: "帮我改一下登录"
✅ 好:   "登录接口返回 500 错误，帮我定位原因并修复"
          "我要在设置页加一个暗色模式开关，先帮我规划方案"
```

**关键：说清楚做什么 + 上下文 + 期望结果。**

### 2. 复杂任务先规划再执行

对于涉及多个文件、不确定怎么做的任务，先进入计划模式：

```
/brainstorming     → 先理清需求和方案
/writing-plans     → 写出详细实施步骤
```

确认计划后再动手写代码，避免走弯路。

### 3. 修 Bug 的推荐流程

```
/systematic-debugging    → 系统性地定位根因，而不是猜
```

Claude Code 会：
- 复现并理解错误信息
- 追溯调用链找到根因
- 验证修复方案而不是盲目改代码

### 4. 写功能的推荐流程

```
/test-driven-development   → 先写测试，再写实现
```

确保代码正确且不会引入回归。

### 5. 完成前的检查

在声称"完成了"之前，可以要求运行验证：

```
/verification-before-completion   → 运行测试、检查类型、确认无误后再交差
```

### 6. 并行处理多个任务

```
"帮我同时做 A、B、C 三件事"
→ 自动用 dispatching-parallel-agents 并行处理
```

### 7. Code Review

```
/requesting-code-review    → 写完代码后自查质量
/review                    → Review 某个 PR
/security-review           → 安全审查
```

### 8. 减少打断

如果觉得每次操作都要点"允许"很烦：

```
/fewer-permission-prompts   → 自动扫描并配置常用命令的白名单
```

### 9. 定时任务

```
/loop 5m 检查部署状态          → 每 5 分钟执行一次
/loop 30m /babysit-prs        → 每 30 分钟执行
```

### 10. 项目初始化

```
/init    → 分析项目结构，生成 CLAUDE.md 让后续对话更精准
```

### 11. 快捷键自定义

```
/keybindings-help   → 自定义按键绑定
```

---

## 四、快速参考卡

| 我想做什么 | 用这个 |
|---|---|
| 头脑风暴/设计方案 | `/brainstorming` |
| 制定实施计划 | `/writing-plans` |
| 修 Bug | `/systematic-debugging` |
| 写新功能 | `/test-driven-development` |
| 代码自查 | `/requesting-code-review` |
| 完成确认 | `/verification-before-completion` |
| 安全审查 | `/security-review` |
| 定时重复任务 | `/loop 5m 任务描述` |
| 减少权限弹窗 | `/fewer-permission-prompts` |
| 项目初始化 | `/init` |

---

## 五、配置文件说明

### settings.json

位置：
- 项目级：`.claude/settings.json`
- 用户级：`~/.claude/settings.json`

用途：配置权限、环境变量、hooks 等。可通过 `/update-config` 进行修改。

### CLAUDE.md

项目根目录下的 `CLAUDE.md` 文件，用于告诉 Claude Code 项目背景、技术栈、代码风格等。通过 `/init` 自动生成。

### keybindings.json

位置：`~/.claude/keybindings.json`

用途：自定义键盘快捷键。通过 `/keybindings-help` 进行配置。

---

## 六、常用 slash commands

| 命令 | 用途 |
|---|---|
| `/help` | 显示帮助信息 |
| `/clear` | 清除对话上下文 |
| `/config` | 打开配置面板 |
| `/compact` | 压缩对话上下文 |
| `/review` | Review 当前 PR |
| `/init` | 初始化项目 CLAUDE.md |
| `/plugin` | 管理插件 |
| `/status` | 查看当前状态 |
| `/tasks` | 查看后台任务 |
| `/memory` | 查看记忆系统 |
| `/loop` | 定时循环任务 |

---

> 最后更新：2026-05-20
