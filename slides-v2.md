# AI Coding 新纪元：从辅助编码到智能体编排
**"Coding is no longer typing, but guiding."**

---

## 分享概览 (Overview)
*   **时长**: 45-60 分钟
*   **核心目标**: 建立"AI 重定义开发者角色"的认知，提供 SDD 方法论与落地路径。
*   **关键问题**:
    1.  你现在的开发时间有多少比例花在与 AI 对话上？
    2.  你的团队是否已经开始积累 `.cursorrules` 这样的工程规范资产？
    3.  你是否思考过 AI 生成代码的维护成本问题？

---

## 1. 范式转移：软件工程的代际跃迁 (The Paradigm Shift)

### 1.1 角色重定义 (Redefining the Role)
*   **Writer → Architect & Reviewer**:
    *   **旧模式 (The "How")**: 80% 精力在语法与实现 (Typing), 20% 在设计.
    *   **新模式 (The "What")**: 80% 精力在定义意图 (Intent) 与架构设计, 20% 在审查 (Review) AI 的产出.
*   **The New Learning Path (Junior 生存指南)**:
    *   **Old**: 学语法 → 写 Hello World → 做项目.
    *   **New**: 学系统设计 → 读懂 Agent 代码 → 修正 Spec → 部署上线.
    *   **Reality**: "AI 不会淘汰初级工程师，但会淘汰不使用 AI 进化的初级工程师。"
*   **场景对比**:
    *   *Traditional*: 遇 Bug → Google/StackOverflow → 理解并复制 → 调试.
    *   *AI Era*: 遇 Bug → 甩 Log 给 Agent → Agent 分析源码 & 给出 Fix → **Human Review**.

### 1.2 质量与速度的“双刃剑” (The Double-Edged Sword)
*   **杠杆效应**: 1 Senior + AI ≈ 10 Juniors.
*   **技术债务通胀**:
    *   代码生成速度 10x → 垃圾代码 (Legacy Code) 堆积速度 10x.
    *   AI 不理解业务，只是概率预测；缺乏约束会导致硬编码、风格不一等隐患。
*   **防御性编程**:
    *   **TDD (Test-Driven Development)**: 不再是可选项，而是必须项。
    *   **CI/CD**: 防止 AI 引入 Bug 的最后防线 (Guardrails).

### 1.3 交互层级提升
*   **Intent-First**: 从命令式 (Tell computer *how*) 转向声明式 (Tell AI *what*).
*   **Natural Language as Code**: 英语/中文正在成为最高级的编程语言。Prompt Engineering 是新的"语法"。

---

## 2. 演进之路 (The Evolution)

### 2.1 演进五重奏 (The 5 Stages of Evolution)
1.  **Resource**: AI 被动提供信息 (Search/Docs).
2.  **Copilot**: 高频协作, 行级补全 (Code Completion).
3.  **Workflow**: 约束流程, 完成特定任务 (e.g., 单测生成, 注释生成).
4.  **Co-Agent (Current)**: 具备规划与工具能力, 但需人类紧密协同纠错 (Human-in-the-loop).
5.  **Agent (Future)**: 融入物理世界, 24h+ 独立运行, 只有在关键决策时需要人类介入.

### 2.2 Co-Agent 时代的特征 (The Current Era)
*   **Tool Use**: 主动读写文件, 运行终端命令, 调用外部 API.
*   **ReAct Loop**: 观察 (Observe) → 思考 (Think) → 行动 (Act) → 修正 (Fix).
*   **Planning**: 能够拆解复杂任务 (e.g., "重构整个模块" vs "补全一行代码")。

### 2.3 演进背后的底层逻辑 (First Principles)
1.  **对抗概率性 (Taming Probabilities)**:
    *   LLM 是概率模型 (Stochastic)，软件工程是确定性工程 (Deterministic).
    *   **解法**: SDD 和 `.cursorrules` 作为"约束层" (Constraints)，测试作为"验证层" (Verification).
2.  **上下文密度的质变 (Context Density)**:
    *   **Copilot**: 仅关注光标周围 (Local Context).
    *   **Agent**: 必须理解整个仓库 + 业务文档 + 外部依赖 (Global Context).
    *   **基建**: 催生了 MCP (连接数据) 和 极致代码索引 (Augment Code).
3.  **智能成本的边际递减 (Drop in Cost)**:
    *   推理成本降低 → 允许 AI 试错 (Self-Correction).
    *   **Best-of-N**: 让 AI 生成 10 个方案并自我评估选出最好的 1 个。

---

## 3. 核心方法论：规范驱动开发 (Spec-Driven Development, SDD)
*解决 "Context Drift" (上下文漂移) 和 "Vibe Coding" (凭感觉写) 的核心方案.*

### 3.1 什么是 SDD?
*   **核心理念**: **Spec (文档) 是 Source of Truth，Code 只是产物。**
*   **Vibe 与 Spec 的辩证关系**:
    *   **误区**: 认为 Vibe (随性) 与 Spec (严谨) 对立。
    *   **真相**: Vibe Coding 不是代码混沌，而是人机高效协同的心流。Spec 是约束 AI "天马行空" 的锚点，让 Vibe 始终朝着目标发力。
*   **SDD Workflow**:
    1.  **Specify**: 编写 `feature-spec.md` (OAuth2 流程, JWT 签名, 错误码).
    2.  **Plan**: Agent 基于 Spec 生成架构设计.
    3.  **Implement**: Agent 读取 Spec 生成代码.
    4.  **Verify**: Agent 读取 Spec 生成测试用例 (TDD).
*   **本质**: Spec 是低熵的中间表示 (IR)，用于"锚定" AI 的生成过程，实现概率塌缩。

### 3.2 Kiro (AWS): Agentic IDE 的 SDD 实践
*   **Specs**: 自动将自然语言需求转化为结构化的 User Stories 和技术设计.
*   **Hooks**: 事件驱动自动化 (e.g., 代码变更 → 自动更新测试/文档).
*   **Steering**: 通过 Markdown 定义项目"宪法"，注入 System Prompt。

### 3.4 直观对比：SDD vs Vibe (Visualizing the Difference)
*   **Left (Vibe Coding)**:
    *   **Input**: Prompt "写个贪吃蛇".
    *   **Output**: 单个 500 行的 `main.py`，结构混乱，难以扩展。
    *   **Entropy**: High (不可控).
*   **Right (SDD)**:
    *   **Input**: `snake_spec.md` (定义 Grid, Food, Snake 接口).
    *   **Output**: 模块化代码 (Models, Views, Controllers)，包含单测。
    *   **Entropy**: Low (确定性).
*   **结论**: Spec 是降低系统熵值的唯一手段。

---

## 4. 工具生态系统 (Tooling Ecosystem)

### 4.1 AI Native IDEs: 交互革命
*   **Cursor**:
    *   **定位**: "外科医生的手术刀"。
    *   **优势**: `Composer` (多文件协同), `.cursorrules` (项目级规范)。
*   **Windsurf (Codeium)**:
    *   **定位**: "全知的副驾驶"。
    *   **优势**: `Cascade` 引擎 (Deep Context), Flow 状态维持。
*   **MarsCode (Trae)**:
    *   **定位**: "云原生极速体验" (国产代表)。
    *   **优势**: 开箱即用, 深度集成豆包模型, 网络连接与中文理解优化。
*   **Zed**:
    *   **定位**: "极速 + 协议原生"。
    *   **优势**: 原生支持 ACP/MCP, 允许 CLI Agent 控制 UI。
*   **Augment Code**:
    *   **定位**: "企业级单体仓库引擎"。
    *   **优势**: 百万行代码秒级索引, 深度静态分析。

### 4.3 极客配置参考 (Pro Configuration)
*   **Core**: Claude Code (Max会员, 深度调研).
*   **Editor**: Cursor (日常 Tab 补全) + Warp (AI 增强终端).
*   **Subagents**:
    *   `Gemini CLI`: 用于前期深度调研与方案设计.
    *   `Kiro-workflow`: 专门执行 Spec 模式.
    *   `UI-Designer`: 独立负责前端组件生成.
*   **Slash Commands**: `/think` (深度思考), `/review` (代码评审), `/commit` (自动提交).

---

## 5. 上下文工程实战 (Context Engineering)
*将 Prompt 转化为可复用的团队资产.*

### 5.1 上下文管理的三重境界 (Context Maturity)
1.  **Level 1**: 知道 AI 需要什么并精准提供 (Manual Context).
2.  **Level 2**: 知道需要什么但不知如何提供 → 借助 Agentic Search 召回 (RAG).
3.  **Level 3**: 既不知 AI 需要什么，AI 也无法搜索 → 构造探索工具链 (Discovery Tools).

### 5.2 `.cursorrules` - 项目级 System Prompt
*   **定义**: AI 的 Linter，强制统一规范。
*   **内容示例**:
    *   "Always use TypeScript with strict mode."
    *   "Use functional components in React."
    *   "Don't explain code, just give me the diff."

### 5.2 长期记忆文件 (`project_context.md`)
*   **Architecture**: 系统分层图 (Mermaid).
*   **Schema**: 关键数据库设计 & API 契约。
*   **Business Rules**: 核心业务逻辑 (鉴权、计费)。
*   **用法**: `@project_context.md` 注入，减少幻觉。

### 5.3 角色库 (`agents.md`)
*   **定义 Persona**:
    *   `Role: Architect` (只设计，不编码)。
    *   `Role: Code Reviewer` (专注于安全与性能)。
    *   `Role: Tech Writer` (文档与代码同步)。

### 5.4 Claude Code Skills
*   **机制**: 类似于插件，AI 根据 Prompt 语义自动触发。
*   **配置**: `~/.claude/skills/SKILL.md`。
*   **示例**: `explain-code` Skill (要求画 ASCII 数据流图)。

---

## 6. 基础设施与协议 (Infrastructure & Protocols)

### 6.1 多 Git Worktree 编排
*   **痛点**: 单人单光标的串行瓶颈。
*   **方案**: 
    *   Agent 在后台 Worktree 并行干活。
    *   Human 在主分支 Review 多个 PR。
    *   实现 **"1 Human Manager + 5 AI Workers"** 的异步协作。

### 6.2 MCP (Model Context Protocol)
*   **定位**: AI 的 "USB 接口" (Data Layer)。
*   **价值**: 连接本地与远程数据孤岛 (Linear, GitHub, Sentry, Postgres)。
*   **场景**: "读取 Sentry 报错 → 查阅 Linear 需求 → 修复代码"。

### 6.4 Agent-First Infrastructure (Infra for Agents)
*   **心智模型 (Mental Model)**: Agent 更喜欢"古老且稳定"的抽象 (SQL, POSIX, Git)，而非全新的框架 (LangChain)。
*   **日抛型负载与成本 (Ephemeral Workloads & Cost)**:
    *   **问题**: 传统 RDS 像"长租酒店"，Agent 试错需要的是"分钟级钟点房"。
    *   **解法**: 必须引入 **Serverless 与虚拟化** (如 TiDB Cloud Serverless)，实现极致的启动速度与按需付费。
*   **虚拟化 (Virtualization)**: 通过虚拟数据库/环境实现资源复用与隔离，支撑千倍于人类的并发探索。

---

## 7. 模型策略 (Model Strategy)

### 7.1 第一梯队 (S-Tier)
*   **Claude 3.5/3.7 Sonnet**: Coding King. 复杂重构、代码理解的首选。
*   **GPT-4o**: 综合能力强，适合作为 Orchestrator 进行规划。

### 7.2 国产化方案深度评估 (The Domestic Stack)
*   **DeepSeek R1**:
    *   **核心**: 推理模型 (Reasoning), 强化学习驱动。
    *   **场景**: 复杂算法、架构决策、竞态条件排查。
    *   **优势**: 开源权重支持**私有化部署 (VPC)**，确保数据主权与零泄露。
*   **MiniMax M2 (Babuduo)**:
    *   **核心**: MoE 架构, 极高吞吐量 (High Throughput).
    *   **场景**: 高频 Agent 循环 (Best-of-N), UI 组件生成.
    *   **优势**: 极致成本效益 (Low Cost), 适合"无限尝试"策略。
*   **Kimi (Moonshot K2)**:
    *   **核心**: 超长上下文 (Long Context), 无损检索.
    *   **场景**: 遗留代码重构 (Legacy Refactoring), 全库理解.
    *   **优势**: 一次性摄入海量文档与代码，保持上下文一致性。
*   **GLM-4 (Zhipu)**:
    *   **核心**: 工具调用专家 (Tool Use).
    *   **场景**: 编排 Agent (Orchestrator), 操作数据库/API.
    *   **优势**: Function Calling 稳定性强，不易产生参数幻觉。

### 7.3 选型矩阵
*   **复杂架构/重构** → Claude 3.7 Sonnet。
*   **日常补全/简单函数** → GPT-4o / DeepSeek。
*   **代码审查/安全** → Claude / GPT-4o。

---

## 8. 自研 Agent 实战 (Building Your Own Agent)

### 8.1 核心架构: The ReAct Loop
*   **流程**: `Observe` (看) → `Think` (想) → `Act` (做/Tool Call) → `Execute` (执行) → `Feedback` (反馈)。
*   **安全**: Agent 不直接操作，只发出"请求"，宿主程序决定是否执行。

### 8.2 Tool Use & MCP
*   **Tools**: 定义 `read_file`, `run_shell` 等基础能力。
*   **MCP**: 通过标准化协议连接外部系统，无需为每个服务写 Glue Code。

### 8.3 上下文管理与沙箱
*   **Context**: 滑动窗口 (Sliding Window) 防止 Token 溢出; 摘要 (Summarization) 保持记忆。
*   **Sandbox**: Docker 隔离，文件系统访问限制，防止 `rm -rf /`。

### 8.4 企业级安全治理 (Security Governance)
*   **Shadow AI**: 监控未经批准的 IDE 插件与 MCP 服务，防止代码外流。
*   **Data Leakage**: 实施 **ZDR (Zero Data Retention)** 策略，确保云端不存储代码。
*   **Prompt Injection**: 防止恶意代码库通过注释包含隐藏指令诱骗 Agent 执行操作。

### 8.5 新一代效能度量 (DORA 2.0)
*   **Acceptance Rate**: AI 建议的代码中有多少被人类*未修改*接受？(衡量质量)
*   **Task Autonomy**: 多少任务在初始提示后无需人类干预即可完成？(衡量独立性)
*   **Review Time**: 审查 AI 代码是否比人类代码耗时更长？(警惕生产力悖论)

---

## 9. 总结与展望 (Conclusion)

1.  **掌握新语言**: Prompt/Context Engineering 是必修课。
2.  **拥抱 SDD**: Spec 驱动，文档即源码。
3.  **关注协议**: MCP/ACP 是互联关键。
4.  **安全底线**: Review 机制与测试覆盖是生命线。
5.  **未来**: 人人都是 Engineering Manager，管理数字团队。

---

### 10. 行业暴论 (Hot Takes)

#### Category 1: 架构与资产 (Architecture & Assets)
1.  **代码资产贬值**: 源码是中间产物，**Spec (意图)** 和 **Test (验证)** 才是核心资产。
2.  **Vibe Coding 陷阱**: 不用 SDD 就是以 10 倍速制造 Legacy Code。
3.  **编程语言 SaaS 化**: 未来的编程语言是 "文档孪生" 的，代码本身只是高信息密度的原子能力。

#### Category 2: 管理与职业 (Management & Career)
4.  **管理者的达尔文时刻**: 不懂 AI 编码效率的管理者，其排期评估就是财务欺诈。
5.  **招聘逻辑重构**: Junior 必须进化为 **Reviewer (审查者)**，否则 ROI 为负。

#### Category 3: 基础设施的未来 (Future of Infra)
6.  **Infra 的新用户不是人**: 数据库/云服务的主要使用者将变成 AI Agent，它们只关心 API 的确定性与极致成本。
7.  **经济图灵测试 > 图灵测试**: 别管 AI 像不像人，关键看它创造的**真实经济价值**。

---

## 11. Action Plan: 周一回去做什么

### Week 1: 建立基础设施
*   [ ] **资产化 Prompt**: 创建 `.cursorrules` 和 `tech-stack.md`。
*   [ ] **强制 SDD 试点**: 选择一个小模块，先写 Spec 再生成代码。

### Week 2: 工具与流程
*   [ ] **工具升级**: 迁移至 Cursor/Windsurf 或配置 Claude Code。
*   [ ] **CI/CD 强化**: 确保 AI 代码必过测试 (Tests are Guardrails)。

### Week 3: 高级集成
*   [ ] **MCP 连接**: 尝试连接 Linear/Jira 或内部文档库。
*   [ ] **私有 Agent**: 有能力的团队尝试基于 SDK 构建专有 Agent。

---

**"The future of coding is not about writing lines of text, but about orchestrating intelligence."**
