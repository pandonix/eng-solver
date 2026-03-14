# eng-solver

`eng-solver` 是一个面向工程问题分析与方案评审的 workspace 模板，不是业务应用本身。

它的目标是把一个模糊的工程问题，转换成一份可审阅、可追溯、基于证据的推荐结论。仓库通过固定阶段、标准文件和角色化技能，约束分析过程，避免直接跳到拍脑袋式结论。

## 这个项目是做什么的

这个仓库定义了一套工程决策工作流：

`INTAKE -> CLARIFY -> PLAN -> DISPATCH -> COLLECT -> CROSS_EXAMINE -> SCORE -> REPORT -> USER_REVIEW -> DONE`

它适合这类场景：

- 评估某个技术方案是否值得采用
- 比较多个工程实现路径
- 在约束条件下输出架构建议
- 对外部资料、产品能力或实现成本做证据化整理
- 生成可供评审的 recommendation、scorecard 和 report

它不负责直接运行某个业务系统，而是作为“工程分析工作台”使用。

## 核心设计

仓库把工程分析拆成三层：

- 工作区规则：由 `AGENTS.md`、`SOUL.md`、`TOOLS.md` 等文件定义整体行为边界
- 角色技能：由 `skills/` 下的角色说明定义各阶段该怎么做
- 问题实例模板：由 `problems/_template/` 定义每个具体问题需要落盘的标准文件

其中几个关键约束是：

- 先定义问题，再提方案
- 先固定 success criteria，再比较选项
- 先收集 evidence，再推荐结论
- 没有 scorecard，不输出最终 recommendation
- 风险、替代方案和未解问题必须显式保留

## 目录结构

```text
.
├── AGENTS.md                  # 工作流、阶段机、核心规则
├── BOOTSTRAP.md               # 首次使用引导
├── SOUL.md                    # 行为价值观
├── TOOLS.md                   # 工具与落盘约定
├── USER.md                    # 用户角色定义
├── IDENTITY.md                # workspace 身份说明
├── HEARTBEAT.md               # 定时/巡检行为约束
├── MEMORY.md                  # 跨问题长期记忆约定
├── docs/
│   └── README.md              # workspace 包说明
├── skills/
│   ├── chief_orchestrator/    # 控制阶段流转
│   ├── clarifier/             # 澄清问题与约束
│   ├── planner/               # 拆解任务图
│   ├── browser_broker/        # 收集外部证据
│   ├── skeptic_judge/         # 审查与打分
│   └── reporter/              # 生成用户报告
└── problems/
    └── _template/             # 问题实例模板
```

## 一个问题实例包含什么

每个问题实例都应基于 `problems/_template/` 创建，并把以下文件作为事实来源：

- `problem.md`：问题定义、范围、背景、基线、假设
- `success_criteria.yaml`：成功标准与验收门槛
- `constraints.yaml`：时间、团队、技术、组织限制
- `judge_policy.yaml`：评分权重与 promote / iterate / reject 规则
- `task_graph.json`：待执行的证据任务
- `evidence/*.json`：归一化后的证据
- `drafts/*.md`：中间方案草稿
- `scorecards/*.yaml`：审查结果
- `reports/*.md`：面向用户的报告
- `decision_log.md`：阶段流转与关键决策记录

## 角色分工

- `chief_orchestrator`：决定当前阶段，维护 source of truth
- `clarifier`：澄清问题定义、范围、约束、成功标准
- `planner`：把问题拆成可验证的 evidence task
- `browser_broker`：从网页或系统界面收集证据，并结构化输出
- `skeptic_judge`：基于证据、约束和政策打分，决定 promote / iterate / reject
- `reporter`：把已 promoted 的方案整理成可评审报告

## 推荐使用方式

1. 把该仓库作为工程分析 workspace 使用。
2. 从 `problems/_template/` 复制出一个新的问题目录。
3. 先补全 `problem.md`、`constraints.yaml`、`success_criteria.yaml`。
4. 生成 `task_graph.json`，按任务收集 `evidence/*.json`。
5. 形成候选方案草稿，写入 `drafts/`。
6. 通过 `scorecards/` 审查后，只有在满足 promote 条件时才输出 `reports/`。

## 当前仓库状态

当前版本已经提供：

- 一套 workspace bootstrap 文件
- 六个角色技能定义
- 一个可复用的问题模板

当前版本没有提供：

- 具体业务代码
- 自动执行这些阶段的程序
- 固定死的运行时配置文件

如果你要把它落成真正可执行的系统，下一步通常是补一个问题实例、定义调用入口，或者增加自动化脚本来驱动这套流程。
