# Claude Code Skills 市场调研与推荐分析

> 调研日期：2026-05-20

---

## 一、数据来源

- GitHub 热门 Skills 仓库（hesreallyhim/awesome-claude-code, onmyway133/awesome-claude-code, EricGrill/agents-skills-plugins 等）
- ClawHub 下载排行榜（13,700+ skills）
- 社区推荐帖（Reddit, Hacker News, dev.to, CSDN）
- Token 优化相关项目（caveman, SIGNAL, unclog）

---

## 二、当前已安装

| Skill | 状态 |
|---|---|
| `superpowers` (14 skills, 3 commands) | ✅ 已安装 — 基础开发框架 |

---

## 三、候选 Skills 分级评估

### 评分维度

- **实用性**：日常使用频率和价值
- **Token 成本**：对上下文窗口的影响
- **安全性**：权限需求和代码透明度

---

### ✅ Tier 1 — 强烈推荐（高价值、低 Token 成本）

| Skill | 用途 | Token 影响 | 安装方式 |
|---|---|---|---|
| **developer-essentials** | Monorepo 管理、调试策略、代码审查、SQL 优化（11 skills） | 低，按需触发 | `@agents-skills-plugins` |
| **context-management** | 跨会话保存/恢复对话上下文 | 低，手动触发 | `@agents-skills-plugins` |
| **caveman** | 削减 65-75% 输出 token，精简 Claude 输出 | **节省 token** | `JuliusBrussee/caveman` |
| **SIGNAL** | 结构化输出，65-90% token 节省 | **节省 token** | `mattbaconz/signal` |
| **unclog** | 审计已安装 skills/MCP 的上下文消耗 | 极低，诊断工具 | `thomaschill/unclog` |

### ⚠️ Tier 2 — 条件推荐（特定场景有用）

| Skill | 用途 | 注意事项 | 安装方式 |
|---|---|---|---|
| **claude-mem** / **claude-memory** | 跨会话持久记忆（SQLite + FTS5） | 与内置 memory 系统功能重叠，需评估是否必要 | `@claudest` |
| **hallucination-detector** | 阻止 Claude 做出无根据的断言 | 增加每次对话的检查开销 | 待查 |
| **find-skills** | 自动发现并安装相关 skills（60k+ 订阅） | 可能自动安装不必要的 skills 增加 bloat | `@clawhub` |
| **anthropics/skills（官方文档技能）** | PDF/PPTX/XLSX/Word 文档处理 | 按需安装，非日常必需 | `@anthropics` |
| **ui-ux-pro-max-skill** | 专业 UI/UX 设计 | 仅在做前端设计时需要 | 待查 |

### ❌ Tier 3 — 不推荐（Token 消耗大或风险高）

| Skill | 原因 |
|---|---|
| **superskillret** | 16,783-skill 语料库，每次 prompt 注入检索结果，上下文消耗巨大 |
| **superskills** | 76+ skills 捆绑包（含 173 营销 + 35 设计），大量用不到的 skill 会占用上下文 |
| **awesome-claude-skills** | 27 skills 全家桶，视频下载、图片增强等对开发无用的功能 |
| **full-stack-orchestration** | 端到端部署协调，skill 本身极其复杂，token 开销大 |
| **synthteam** | 模拟同事人格，需要加载 Slack 历史，非实用 |

---

## 四、安全警告

社区报告指出以下风险（来源：dev.to 安全分析）：

1. **第三方 Skills 可能窃取凭证** — Skill 文件可读取环境变量和配置文件
2. **未审查的 marketplace** — 部分社区 marketplace 没有代码审查机制
3. **过度权限** — 某些 skill 请求超出其功能所需的权限

**安全原则**：
- 优先使用 `@anthropics`（官方）和 `@agents-skills-plugins`（半官方）来源
- 安装前检查 install 脚本和 skill 文件内容
- 避免安装来源不明的 marketplace

---

## 五、推荐安装方案

### 方案 A：极简高效（推荐）

```
/plugin install developer-essentials@agents-skills-plugins
/plugin install caveman@JuliusBrussee
/plugin install unclog@thomaschill
```

总览：superpowers + 开发核心 + token 节省 + 诊断工具

### 方案 B：全面型

在方案 A 基础上增加：
```
/plugin install context-management@agents-skills-plugins
/plugin install claude-memory@claudest
```

### 方案 C：自定义

根据你的具体需求从 Tier 2 中挑选。

---

## 六、Token 优化配置建议

向 `~/.claude/settings.json` 添加：

```json
{
  "model": "sonnet",
  "env": {
    "MAX_THINKING_TOKENS": "10000",
    "CLAUDE_CODE_SUBAGENT_MODEL": "haiku"
  }
}
```

| 设置 | 默认 | 建议 | 原因 |
|---|---|---|---|
| model | opus | sonnet | 80% 任务足够，成本降 60% |
| MAX_THINKING_TOKENS | 31999 | 10000 | 隐藏成本降 70% |
| SUBAGENT_MODEL | 继承主模型 | haiku | 子 agent 成本降 80% |

---

> 下一步：等待用户确认后执行安装
