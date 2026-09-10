---
name: idea-to-tickets
description: "从想法到工单：把模糊需求一步步变成 Agent 可稳定执行的任务。四个可单用、可串联的模式——clarify 动手前反向追问对齐（grill-me）、spec 把共识写成带验收的规范（to-spec）、slice 把规范拆成可独立开工验收的垂直工单（to-tickets）、explain 用最小合适视图把代码/方案讲清楚（show-me）。适用于：让 AI 写代码/做复杂任务前的需求澄清、写需求/技术方案规范、把大任务拆成可并行工单、代码评审或讲解改动、以及非代码的选题/决策梳理。方法论与 IDE、任务系统、画图工具解耦，可在豆包/Claude Code/Cursor/Codex 间平移。"
compatibility: "方法论/格式本身跨平台；随附脚本与运行环境仅在 macOS(Darwin) 实测，Windows/Linux 未适配。执行前先判平台(uname -s)，涉及脚本/命令时非 macOS 停止并告知需另行适配、不硬跑；将来补齐后按平台分流并分别标注验证状态"
---

# idea-to-tickets · 从想法到工单（AI 软件工程四步法）

## 平台适用（执行前先读）
- 方法论/格式本身跨平台；但**随附脚本与本套运行环境仅在 macOS（Darwin）实测**。
- 动手前先 `uname -s` 判平台：Darwin 走现有流程；Windows/Linux 只能使用纯方法论部分，一旦涉及脚本/命令，停下提示需另行适配，不硬跑。
- 以后补齐 Windows 后也保留“先判平台 → 按平台分流”的结构，分别标注各平台验证状态。

> 内核来源：Matt Pocock 开源 Skills 的 `grill-me` / `to-spec` / `to-tickets` / `show-me`（本技能是其**与工具解耦的方法论封装**：不依赖特定 IDE、命令或 GitHub，只固化"怎么想、怎么问、怎么拆、怎么讲"）。
> 一句话：**把脑子里模糊的想法，逐步消除歧义，变成 Agent 真正能执行、能验收的东西。**

## 1. 什么时候用哪个模式

| 模式 | 上游原名 | 解决的痛点 | 产出 | 详细 SOP |
|---|---|---|---|---|
| **clarify** 拷问澄清 | grill-me | 需求没说清 AI 就埋头做、做完不对再返工 | 一份共识小结 | [`references/mode-1-clarify.md`](references/mode-1-clarify.md) |
| **spec** 共识成规范 | to-spec | 对齐只存在对话里，换会话就蒸发、AI 靠脑补跑偏 | 一份带验收的规范 | [`references/mode-2-spec.md`](references/mode-2-spec.md) |
| **slice** 垂直拆工单 | to-tickets | 整份 spec 一次交出会做一半、无法验收、无法并行 | 一叠可独立开工/验收的工单 + 依赖图 | [`references/mode-3-slice.md`](references/mode-3-slice.md) |
| **explain** 视图讲清楚 | show-me | 面对大量改动/字符很抽象，人和 Agent 难沟通 | 与问题匹配的最小视图 | [`references/mode-4-explain.md`](references/mode-4-explain.md) |

前三个是一条**纵向流水线**（想清楚 → 写下来 → 拆成单），第四个 **explain 横向贯穿**（澄清、评审、交付时都能用）。

## 2. 如何使用（豆包是"软模式"，不会自动触发）

本技能没有后台钩子，靠**你点名**进入；进入后按对应模式的 SOP 执行。开场话术示例：

- `用 idea-to-tickets 的 clarify 模式，先别动手，把我这个需求拷问清楚：……`
- `我们已经对齐了，用 spec 模式把它写成带验收的规范`
- `用 slice 模式把这份 spec 拆成可独立验收的工单，先读现有代码再拆，拆完先给我看`
- `用 explain 模式，选最小合适视图把这次改动讲清楚`
- `走完整链路 clarify→spec→slice：……`（组合套路见下）

> 有意不自动触发：**是否要被拷问、何时固化、拆多细，由人决定**，避免 AI 在小任务上过度流程化。简单、无歧义的任务不必走全套，单用 clarify 甚至直接做即可。

## 3. 组合套路（怎么串）

完整工程链与各档取舍见 [`references/playbook.md`](references/playbook.md)，速记：

```
模糊想法
  └ clarify  一次一问 + 先给推荐 + 能自查就不问，问到共识（产出共识小结）
     └ spec  记决策不记实现、先找可测的"接缝"，写带验收的规范
        └ slice  按功能纵向切成"垂直切片/曳光弹"工单 + 只标真实依赖（可并行）
           └ [交给编程 Agent 实现] → 评审（explain 把改动讲清楚）
```

- **只澄清**：需求模糊、还没决定做不做/怎么做 → 单用 clarify（非代码的选题、决策也适用）。
- **澄清 + 固化**：怕换会话失忆、要交接 → clarify→spec，稳定结论再交记忆技能沉淀（见 §4）。
- **全链路拆单**：多步骤、要多 Agent/多会话并行的大任务 → clarify→spec→slice。
- **只讲解**：不改东西，只为看懂/评审一批改动 → 单用 explain。

## 4. 与其它技能的关系（避免重复建设，按需替换）

| 能力 | 本技能负责 | 重叠/协作对象 | 怎么取舍 |
|---|---|---|---|
| 把图**画出来**（渲染、配色、交互、ECharts/HTML） | explain 只负责**选哪种视图、画到什么程度、放在哪** | 豆包内置 **doubao-visualization** | 在豆包：explain 定视图后，**渲染交给 doubao-visualization**，本技能不重复造画图器；换 Claude/Cursor 则改用 Mermaid/原生图。**换的是渲染后端，选型方法不变** |
| 跨会话**记忆与恢复** | 负责"生产"共识/规范/决策 | 自建 **okf-wiki** | clarify/spec 里稳定、不可逆的结论，按 okf-wiki 沉淀成 concept/log；本技能不另建记忆体系 |
| 真正**写代码/执行** | 到"可开工工单"为止 | 各 IDE 的编程 Agent（Claude Code/Cursor/Codex/豆包编程） | 工单是给执行端的输入，本技能不替它编码 |
| 任务**落地的载体** | 只定义工单/规范该含什么 | 本地 md / 飞书任务 / GitHub Issues / 任意 tracker | **同一产物、多种落点**：单人快速推进用本地 md 文件，协作发任务系统；见 slice 模式的"落点适配" |

## 5. 可平移性（为什么换 IDE/Agent 也能用）

本技能只固化**与工具无关的方法**，把三处易变环节留成可替换插槽：

1. **触发方式**：豆包靠开场话术；Claude Code/Cursor 里可做成 slash command（对应原 `/grill-me`、`/to-spec`、`/to-tickets`、`/show-me`）。
2. **任务落点**：本地 md ↔ 飞书 ↔ GitHub Issues（原生态默认 GitHub + `ready-for-agent` 标签，只是其中一种后端）。
3. **视图渲染**：Mermaid / HTML ↔ doubao-visualization ↔ IDE 内置图表。

迁移时只换插槽，四模式的判断标准、SOP、模板原样可用。

## 6. 三条贯穿纪律

1. **意图归人，AI 只给推荐不替你拍板**：clarify 每题先给推荐答案，你能否决；slice 拆完反向找你确认"粗细/依赖/合并再拆"。
2. **记决策，不记易过时的实现**：不写死文件路径/代码片段（重构即过期）；易变的进度、计数、状态放台账实时读，不抄进正文。
3. **先读真实材料再下结论**：spec 要先扫代码库用项目术语；slice 拆单前必须读真实代码——**意图（spec）≠ 现状（代码）**，很多工单只有读代码才看得见。

## 7. 文件指引（按需读，不要一次全读）

| 你要 | 读这个 | 用模板 |
|---|---|---|
| 动手前把需求问清楚 | `references/mode-1-clarify.md` | `templates/consensus.md` |
| 把对齐结果写成规范 | `references/mode-2-spec.md` | `templates/spec.md` |
| 把规范拆成工单、排依赖 | `references/mode-3-slice.md` | `templates/ticket.md`、`templates/tickets-index.md` |
| 选视图讲清代码/方案 | `references/mode-4-explain.md` | — |
| 决定走哪档、怎么串、避坑 | `references/playbook.md` | — |

## 8. 来源与边界

- clarify / spec / slice 源自 Matt Pocock 的 **mattpocock/skills「Skills For Real Engineers」(MIT)**：https://github.com/mattpocock/skills （grill-me / to-spec / to-tickets，及共用追问引擎 grilling、grill-with-docs、setup-matt-pocock-skills、implement、code-review 等；官方对 to-tickets 的原话是"tracer-bullet tickets, each declaring its blocking edges, as local text or native blocking links"）。
- explain 源自 **humanlayer/skills 的 show-me**（另一团队，**并非 Matt 仓库**，被 Matt Pocock 公开推荐）：https://www.humanlayer.com/blog/show-me-skill 。
- 中文理解经 01Coder「编码 Agent 工程链四件套」4 期视频（2026-07~09）核对；整理稿见飞书 AI 情报站编号 009。
- 本技能**不包含**两个上游仓库的安装器、任务系统集成、slash command 实现（那些绑定特定 IDE）；也不覆盖工程链后续的 implement 自动实现、code-review 双轴评审两环（上游另有其 skill）。
