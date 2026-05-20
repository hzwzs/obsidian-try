# 个人化 Skills 推荐方案 — 韩孜汶

> 分析日期：2026-05-20
> 基于：E:\han 全文件夹分析 + GitHub/社区调研

---

## 一、已安装 Skills（3/3 完成）

| Skill | 状态 | 用途 |
|---|---|---|
| `superpowers` | ✅ 已启用 | 基础开发框架：TDD、调试、Code Review、头脑风暴 |
| `developer-essentials` | ✅ 已启用 | Monorepo、SQL优化、Git高级工作流、调试策略（11 skills） |
| `caveman` | ✅ 已启用 | 削减 65-75% 输出 token，提效降本 |

---

## 二、用户画像分析

| 维度 | 信息 |
|---|---|
| 学历 | 合肥工业大学 信息管理与信息系统（2025届）→ 同济大学 经济与管理学院 学术型硕士（2026级） |
| 研究方向 | 复杂网络、传播动力学、计算社会科学 |
| 技术栈 | Python、MySQL、爬虫（从预科研经历推断） |
| 竞赛经历 | 三创、互联网+、挑战杯、大创、学创杯、企业竞争模拟、计算机设计大赛等 10+ 项 |
| 毕设 | 大学生科研智能管理系统（含系统开发） |
| 预科研 | 商品期货交易所数据分析（大连/上海/广州/中金所），含爬虫+MySQL+动态交互 |
| 其他 | 支教志愿者、心理健康协会、有AI变现意愿 |

---

## 三、科研学术类 Skills 推荐

### Tier 1 — 强烈推荐

#### 1. Academic Research Skills (ARS)
- **仓库**：`Imbad0202/academic-research-skills`（6,400+ ⭐）
- **安装**：`/plugin marketplace add Imbad0202/academic-research-skills` → `/plugin install academic-research-skills@academic-research-skills`
- **包含**：
  - `deep-research` — 13 agents 系统文献综述（支持 PRISMA）
  - `academic-paper` — 12 agents 论文写作（大纲→论证→初稿→双语摘要→图表）
  - `academic-paper-reviewer` — 7 agents 模拟期刊审稿（主编+3审稿人+魔鬼代言人）
  - `academic-pipeline` — 10 阶段全流程编排
- **亮点**：Semantic Scholar 引文验证、反谄媚协议、AI 失败模式检查清单
- **成本**：15,000 字论文约 $4-6
- **Token 评估**：中等，按需触发，非持续消耗

#### 2. Efficient Literature Survey
- **仓库**：`namooubn/efficient-literature-survey`
- **安装**：`/plugin marketplace add namooubn/efficient-literature-survey`
- **特点**：99%+ token 节省，30 篇论文 → 30K 字符精读
- **功能**：多格式提取（PDF/DOCX/TXT）、主题聚类、优先级分层精读
- **Token 评估**：极低（设计初衷就是省钱）

#### 3. AI Research Skills
- **仓库**：`WenyuChiou/ai-research-skills`
- **安装**：`/plugin marketplace add WenyuChiou/ai-research-skills`（5 插件 marketplace，一键安装）
- **包含**：文献检索矩阵、研究设计助手、论文记忆构建器、学术写作规范、Zotero 集成
- **Token 评估**：低，按需触发

### Tier 2 — 按需选装

| Skill | 用途 | 适合场景 |
|---|---|---|
| `luwill/research-skills` | 5-agent 中文协作综述系统 | 需要中文文献综述 |
| `claesbackman/AI-research-feedback` | 6-agent 期刊审稿模拟 | 投稿前自查 |
| `Ar9av/PaperOrchestra` | Google PaperOrchestra 实现 | 需要图表+文献+写作全自动化 |

---

## 四、AI 变现类 Skills 推荐

### 强烈推荐

#### show-me-the-money
- **仓库**：`iamzifei/show-me-the-money`
- **安装**：`/plugin marketplace add iamzifei/show-me-the-money`
- **作者背景**：独立开发者，运营 6 款 SaaS 产品，累计收入 $1M+
- **包含**（25 skills）：
  - `/money-discover` — AI 扫描市场，验证需求
  - `/money-strategy` — 市场研究、SWOT、商业模式压力测试
  - `/money-product` — 构建和部署 MVP（落地页+支付+SEO）
  - `/money-content` — 博客、邮件、社交媒体内容
  - `/money-ops` — 24/7 自主运营
  - `/money-finance` — 收入追踪、单位经济学
- **Token 评估**：中低，按需触发

### 变现路径参考（基于你的背景）

| 路径 | 你的优势 | 起步建议 |
|---|---|---|
| **技术博客/自媒体** | 竞赛经验+考研经历+AI工具使用 | 分享 Claude Code 使用技巧、考研经验 |
| **学术服务** | 信管背景+Python+爬虫 | 数据采集、文献综述辅助 |
| **SaaS 小工具** | 毕设系统开发经验+MySQL | 面向高校的科研管理工具 |
| **Skill/Template 售卖** | 丰富的 AI 工具使用经验 | 打包常用 skills 售卖 |

---

## 五、不推荐的 Skills（Token 黑洞 + 安全风险）

| Skill | 原因 |
|---|---|
| superskillret | 16,783 skill 语料库，每次 prompt 注入检索结果 |
| superskills | 76+ skills 捆绑（含 173 营销+35 设计），实际用不到 |
| awesome-claude-skills | 27 skills 全家桶，视频下载/图片增强等无关功能 |
| full-stack-orchestration | 极其复杂的编排逻辑，token 开销巨大 |
| PaperOrchestra | 论文写作全自动流水线（~20-30 次 LLM 调用/步骤），消耗大 |

---

## 六、推荐安装计划

### 立即安装（学术+变现）

```bash
# 学术三件套
/plugin marketplace add Imbad0202/academic-research-skills
/plugin install academic-research-skills@academic-research-skills

/plugin marketplace add namooubn/efficient-literature-survey
/plugin install efficient-literature-survey@efficient-literature-survey

/plugin marketplace add WenyuChiou/ai-research-skills
/plugin install ai-research-skills@ai-research-skills

# AI 变现
/plugin marketplace add iamzifei/show-me-the-money
/plugin install show-me-the-money@show-me-the-money
```

### 后续评估

- `claude-memory` / `context-management` — 等跨会话需求明确后再装
- `luwill/research-skills` — 需要中文文献综述时再装
- Dodo Payments MCP — 真的要做 SaaS 收费时再配

---

## 七、关于自我提升的建议

基于你的背景（信管→经管学术硕），这些方向值得投入：

1. **AI + 学术工作流** — 用 Claude Code 辅助文献综述、论文写作、数据分析，这本身就是稀缺技能
2. **Python + 复杂网络** — 网络科学（NetworkX, igraph）与传播动力学是这个方向的核心工具
3. **数据工程能力** — 你已有爬虫+MySQL基础，深化为数据管线能力
4. **技术写作** — 把学习过程输出为内容（博客/视频），既巩固知识又积累影响力

---

> 等待确认后执行安装
