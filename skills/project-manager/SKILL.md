---
name: project-manager
description: "个人/小团队多项目并行时的轻量项目管理方法论，按专业项目管理骨架组织：① 项目组合管理层 PPM（选对项目组合、季度盘点、优先级排序、项目状态与健康灯、活跃项目 7±2 纪律）；② 单项目生命周期层（启动 Initiate：写项目总纲/Project Charter、搭目录结构；执行与监控 Monitor：治理卡、决策权限、升级路径、每周自查、决策记录 ADR）；③ 阶段门评审层 Phase-Gate（立项门 G1/验证门 G2/发布门 G3、Go-Conditional-Hold-Kill 决策、批量评审议程）；④ 收尾与归档层 Close（关闭六步、退役总结、资源释放、归档不删除）。适用于：新建项目、项目太多想盘一盘、季度复盘哪些继续哪些砍、项目做完或想砍掉怎么收尾、给项目定'什么情况必须停下来重评'、个人开发者/内容创作者多项目并行（出海游戏站、AI 调研、股票投资、CPA 备考、珠宝业务等）。方法论源自 PMBOK 8 治理绩效域、PPM 四步流程、伯克利 BPM 项目状态、阶段门五领域、PARA/GTD，但做了减法，默认轻量版，重型指标仅在需要时启用。"
compatibility: "纯方法论与 Markdown 模板，不随附可执行脚本、不依赖操作系统，Windows/macOS/Linux 通用、无需判平台；文中提到的外部环节（飞书 lark-wiki 建空间、lark-base 多维表格建台账、浏览器/终端操作等）是可替换插槽，其平台要求由对应工具决定。"
---

# project-manager · 个人项目管理方法论（PPM + 生命周期 + 阶段门，轻量版）

## 平台适用（执行前先读）
- 本技能是**纯方法论 + Markdown 模板**，不含可执行脚本、不依赖操作系统，Windows / macOS / Linux 均可直接使用，无需判平台。
- 文中提到的外部环节（飞书 lark-wiki 建知识空间、lark-base 建多维表格台账、浏览器/终端操作等）是可替换插槽，其平台要求由对应工具决定，与本方法论无关。
- 路径示例一律用 `~` 或相对路径，不硬编码 `/Users/<用户名>`。

> 一句话：**用企业级项目管理的骨架（PPM + 生命周期 + 阶段门），但把肌肉换成个人轻量做法——知道该做哪些项目、每个项目走到哪一步、什么时候停、做完怎么收。**

## 什么时候用

命中以下任一场景就打开本技能对应模块：

- **想启动一个新项目**（新网站、新调研、新课程、新业务线）——不知道该怎么立项、目录怎么搭 → 读 [initiate](#三层架构速览)
- **项目太多、脑子里一团浆糊**，想盘一下哪些在做、哪些半死不活、该砍哪个 → 读 portfolio
- **项目做着做着开始失控**：不知道自己能拍板什么、什么情况该喊停 → 读 monitor
- **到季度末/半年末，想集中判断一批项目继续还是砍掉** → 读 gates
- **项目做完了、或者想砍了**，但直接丢在那里心里不踏实 → 读 close
- **反触发**：一两天能做完、单线程、无长期归档需求的小任务，不必走本技能。

## 三层架构速览

专业项目管理不是"一个模块管所有"，而是分三层。本技能按这三层组织：

```
┌─────────────────────────────────────────────────────────┐
│  L1 项目组合层（Portfolio / PPM）                        │
│     回答："我现在应该做哪些项目？哪些该停？"            │
│     载体：项目台账（多维表格）+ 季度盘点                 │
│     → references/portfolio.md                           │
├─────────────────────────────────────────────────────────┤
│  L2 单项目生命周期层（Project Lifecycle）               │
│     回答："单个项目从生到死怎么走？"                     │
│     Initiate 启动 → Monitor 执行与监控 → Close 收尾归档   │
│     → references/initiate.md / monitor.md / close.md     │
├─────────────────────────────────────────────────────────┤
│  L3 阶段门评审层（Phase-Gate Review）                    │
│     回答："项目到节点了，Go 还是 Kill？"                │
│     横跨 L2 三个阶段，季度批量评审                       │
│     → references/gates.md                               │
└─────────────────────────────────────────────────────────┘
```

| 层 | 模块 | 解决什么 | 核心产出 | 详细 SOP |
|---|---|---|---|---|
| **L1 组合** | portfolio 项目组合管理 | 项目太多、不知道该砍哪个、僵尸项目占名额 | 项目台账（状态+健康灯+战略对齐+优先级分） | [`references/portfolio.md`](references/portfolio.md) |
| **L2 启动** | initiate 项目启动 | 新项目立项时目标模糊、目录乱、和别的项目抢资源 | 项目总纲（Project Charter）+ 标准目录 + 进台账 | [`references/initiate.md`](references/initiate.md) |
| **L2 监控** | monitor 执行与治理 | 做着做着不知道自己能拍板什么、硬扛到爆 | 治理卡 + 决策记录（ADR）+ 每周 15 分钟自查 | [`references/monitor.md`](references/monitor.md) |
| **L3 评审** | gates 阶段门评审 | 每个项目都到了该判断"继续/砍掉"的节点 | 季度批量评审，每项目 3 分钟，Go/Conditional/Hold/Kill | [`references/gates.md`](references/gates.md) |
| **L2 收尾** | close 收尾与归档 | 项目做完/砍掉后直接丢着，资料散落、订阅还在扣费 | 关闭六步 + 一页退役总结 + 移入归档不删除 | [`references/close.md`](references/close.md) |
| 汇总 | templates 模板汇总 | 一次性复制所有模板 | 全部模板索引 | [`references/templates.md`](references/templates.md) |

## 核心概念（通俗解释）

> 下面这些都是企业项目管理行话，这里全部翻译成大白话。

| 术语 | 大白话解释 |
|---|---|
| **PPM（Project Portfolio Management，项目组合管理）** | 不是把每个项目做快，而是**选对一篮子项目**——资源就这么多，哪些值得投、哪些该砍。像基金经理管投资组合，而不是死磕单只股票。 |
| **Project Charter（项目总纲/项目章程）** | 立项时写的一页纸：为什么做、做成什么样算成功、什么时候做完。没写清楚就开工，半年后不知道做到哪算完。 |
| **项目治理（Governance）** | 不是"管着你"，是**提前写清楚：什么事你自己能定、什么事必须停下来重新想、多久碰一次头**。PMBOK 8 把它升为一级绩效域，因为"治理不清"比"预算不够"更容易让项目死。 |
| **RACI** | 责任矩阵：谁负责执行(R)、谁最终拍板(A)、被咨询(C)、被告知(I)。个人场景简化为"我=R=A"。 |
| **项目状态** | 一个项目当前是"正在做/做完了/停了/砍了/还没开始"。借伯克利 BPM 五档：Active / Completed / Cancelled / On Hold / To Be Started。 |
| **健康灯** | 红绿灯一眼看健康：🟢 On Track（按计划走）/ 🟡 At Risk（有风险能救）/ 🔴 Off Track（偏得远了）。 |
| **阶段门（Phase-Gate）** | 在项目阶段之间设"检查点"，像收费站——到点必须回答"继续往下走，还是先卡住/砍掉"。不是汇报会，是真决策。 |
| **Go / Conditional Go / Hold / Kill** | 门决策四档：直接通过 / 带条件通过 / 卡住等条件解除 / 砍掉。 |
| **PARA** | Tiago Forte 的个人信息组织法，按"可操作性"分四类：**Projects**（有截止日的短期项目）/ **Areas**（长期维持的责任，如健康/财务）/ **Resources**（以后可能翻的素材）/ **Archives**（做完或死掉的）。 |
| **GTD** | David Allen 的任务流：收集 → 两分钟法则 → 委派 → 排期 → 落到项目。和 PARA 互补：GTD 管"接下来做什么"，PARA 管"东西放哪"。 |
| **ADR（Architecture Decision Record / 决策记录）** | 把关键决策和"为什么这么选"写下来，半年后回看不后悔。 |

## 与其它技能的关系

| 能力 | 本技能负责 | 协作对象 | 怎么取舍 |
|---|---|---|---|
| 把项目里的**需求拆成可执行工单** | 本技能只管"项目这一层"（立项/治理/盘点/评审/收尾） | **idea-to-tickets** | 项目总纲里的"接下来要做什么"落到工单时，交给 idea-to-tickets 做 clarify→spec→slice |
| 项目内部**知识沉淀与跨会话恢复** | 本技能只规定目录结构（00/01/02/03/09/99） | **okf-wiki** | 项目里大量、会复利的知识（架构、决策、知识点）按 okf-wiki 组织；本技能不另建记忆体系 |
| **环境/机器**层面的维护 | 与本技能无关 | **dual-machine-manager** | 项目退役时"技术退役清单"里涉及的双机同步、备份由该技能负责 |
| **飞书知识空间**的实际创建 | 本技能只给目录模板和 SOP | **lark-wiki** / **lark-base** | 真要在飞书建空间、建多维表格台账时，调用对应技能执行 |

## 文件指引（按需读，不要一次全读）

| 你要 | 读这个 | 用模板 |
|---|---|---|
| 盘所有项目、定优先级、季度重排 | `references/portfolio.md` | 项目台账表（列定义）、PPM 评分法 |
| 新项目启动、写项目总纲、搭目录 | `references/initiate.md` | 项目总纲模板、目录结构模板 |
| 给项目定"什么情况自己拍板、什么情况暂停重评" | `references/monitor.md` | 治理卡模板、决策记录 ADR 模板 |
| 季度集中评审一批项目、过阶段门 | `references/gates.md` | 门决策记录模板、评审 Checklist |
| 项目做完/砍掉怎么收尾、归档 | `references/close.md` | 退役总结模板、关闭 Checklist |
| 一次性复制所有模板 | `references/templates.md` | 全部模板汇总 |

## 来源与边界

**方法论来源**（详见各 reference 末尾标注）：
- **PMBOK 8 治理绩效域**：https://ppmsi.net/wp-content/uploads/2026/04/ppmsi_pm_simulator.html
- **PPM 四步流程**：PMI Project Portfolio Management https://www.pmi.org/learning/library/portfolio-management-complex-projects-waste-7327
- **项目状态定义**：伯克利 BPM Office https://bpm.berkeley.edu/project-definitions
- **阶段门五领域 / 门决策模板**：projectmanagementformula https://projectmanagementformula.com/phase-gate-process/
- **门标准二元化**：onplana https://onplana.com/blog/stage-gate-project-management-onplana
- **项目关闭 Checklist**：projectmanagementformula https://projectmanagementformula.com/project-closure-checklist/
- **技术退役时间线**：beefed.ai https://beefed.ai/en/technical-decommissioning-checklist-data-retention
- **PARA**：Tiago Forte https://www.buildingasecondbrain.com/para
- **结构实证**：用户飞书 9 个知识空间实采（CPA 备考库、珠宝库、AI、SEO、游戏项目等），2026-09-15 调研报告

**本技能不覆盖什么**：
- 不覆盖**具体任务执行**（写代码、写文章、做设计）——那是 idea-to-tickets 之后的事。
- 不覆盖**财务记账/投资决策本身**——股票台账可以作为项目放进组合，但买卖判断不在本技能范围。
- 不覆盖**团队多人协作**的重型流程（CCB 变更控制委员会、PMO、正式签字审批流）——这些只在"企业级重型 vs 个人轻量"对照表里提一句，个人场景默认用轻量版。
- 不替代 **lark-wiki / lark-base** 本身的操作——本技能给"建什么结构、写什么内容"，真要在飞书动手时调对应技能。
