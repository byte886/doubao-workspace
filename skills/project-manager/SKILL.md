---
name: project-manager
description: "个人/小团队多项目并行时的轻量项目管理方法论。五大模块：create 创建新项目（写一页总纲、搭目录结构、进项目台账）、governance 项目治理（决策权限阈值、暂停重评触发条件、每周自查节奏）、inventory 项目盘点（季度全项目扫描、状态/健康灯更新、90 天无活动自动归档）、batch-review 分批评审（阶段门 Go/Conditional/Hold/Kill 决策，三道门：立项/验证/发布）、maintenance 维护与退役（关闭六步、退役总结、资源释放、归档不删除）。适用于：新建一个项目/知识空间、项目太多想理一理、季度复盘哪些该停哪些继续、项目做完或想砍掉时怎么收尾、给项目定'什么情况必须停下来重新评估'、个人开发者/内容创作者多项目并行（出海游戏站、AI 调研、股票投资、CPA 备考、珠宝业务等）。方法论源自 PMBOK/敏捷/PARA/GTD/阶段门，但做了减法，默认轻量版，重型指标仅在需要时启用。"
compatibility: "纯方法论与 Markdown 模板，不随附可执行脚本、不依赖操作系统，Windows/macOS/Linux 通用、无需判平台；文中提到的外部环节（飞书 lark-wiki 建空间、多维表格建台账、浏览器/终端操作等）是可替换插槽，其平台要求由对应工具决定。"
---

# project-manager · 个人项目管理五步法（轻量版）

## 平台适用（执行前先读）
- 本技能是**纯方法论 + Markdown 模板**，不含可执行脚本、不依赖操作系统，Windows / macOS / Linux 均可直接使用，无需判平台。
- 文中提到的外部环节（飞书 lark-wiki 建知识空间、多维表格建项目台账、浏览器/终端操作等）是可替换插槽，其平台要求由对应工具决定，与本方法论无关。
- 路径示例一律用 `~` 或相对路径，不硬编码 `/Users/<用户名>`。

> 一句话：**企业级项目管理做减法，让一个人也能把多个并行项目管得过来——知道该做什么、什么时候停、做完怎么收。**

## 什么时候用

命中以下任一场景就打开本技能对应模块：

- **想启动一个新项目**（新网站、新调研、新课程、新业务线）——不知道该怎么立项、目录怎么搭 → 读 [create](#模块速览)
- **项目做着做着开始失控**：不知道自己能拍板什么、什么情况该喊停 → 读 governance
- **项目太多、脑子里一团浆糊**，想盘一下哪些在做、哪些半死不活 → 读 inventory
- **到季度末/半年末，想集中决定一批项目继续还是砍掉** → 读 batch-review
- **项目做完了、或者想砍了**，但直接丢在那里心里不踏实 → 读 maintenance
- **反触发**：一次性小任务（几天内做完、单线程、无长期归档需求）不必走全套；直接做即可。

## 五大模块速览

| 模块 | 解决什么 | 核心产出 | 详细 SOP |
|---|---|---|---|
| **create** 创建 | 新项目启动时目录乱、目标模糊、和别的项目抢资源 | 一页项目总纲 + 标准目录结构 + 进入项目台账 | [`references/create.md`](references/create.md) |
| **governance** 治理 | 做着做着不知道自己能拍板什么、硬扛到爆 | 一页治理卡（独立决策阈值 + 暂停重评触发条件 + 碰节奏） | [`references/governance.md`](references/governance.md) |
| **inventory** 盘点 | 项目堆了一堆，哪些真在做、哪些早死了不知道 | 项目台账（状态 + 健康灯 + 战略对齐 + 资源占用） | [`references/inventory.md`](references/inventory.md) |
| **batch-review** 分批评审 | 每个项目都到了该判断"继续/砍掉"的节点，但没空单独开会 | 每季度一次批量评审，每项目 3 分钟，给 Go/Conditional/Hold/Kill | [`references/batch-review.md`](references/batch-review.md) |
| **maintenance** 维护与退役 | 项目做完/砍掉后直接丢着，资料散落、订阅还在扣费 | 关闭六步 + 一页退役总结 + 移入归档不删除 | [`references/maintenance.md`](references/maintenance.md) |

五模块是一条**项目生命周期主线**：create 立项 → governance 日常治理 → inventory 定期盘点 → batch-review 阶段门决策 → maintenance 关闭退役。日常可单用任一模块。

## 核心概念（通俗解释）

> 你说"可能说的不专业"——下面这些词都是企业项目管理里的行话，这里全部翻译成大白话。

| 术语 | 大白话解释 |
|---|---|
| **PARA** | Tiago Forte 的个人信息组织法，把所有东西按"可操作性"分四类：**Projects**（正在做、有截止日的事）、**Areas**（长期维持的责任，如健康/财务）、**Resources**（以后可能翻出来的素材）、**Archives**（做完或死掉的）。本技能主要用 Projects + Archives 两档。 |
| **项目状态** | 一个项目当前是"正在做/做完了/停了/砍了/还没开始"。借伯克利 BPM 的五档：Active / Completed / Cancelled / On Hold / To Be Started。 |
| **健康灯** | 红绿灯式一眼看健康：**绿** On Track（按计划走）、**橙** At Risk（有风险但还能救）、**红** Off Track（偏得远了）。 |
| **阶段门（Phase-Gate）** | 在项目阶段之间设"检查点"，像收费站一样——到点必须回答"继续往下走，还是先卡住/砍掉"。不是汇报会，是真决策。 |
| **Go / Conditional Go / Hold / Kill** | 门决策四档：直接通过 / 带条件通过 / 卡住等条件解除 / 砍掉。 |
| **治理（Governance）** | 不是"管着你"，是**提前写清楚：什么事你自己能定、什么事必须停下来重新想、多久碰一次头**。 |
| **RACI** | 责任矩阵：谁负责执行(R)、谁最终拍板(A)、 consultation 被咨询(C)、informed 被告知(I)。个人场景简化为"我=R=A，偶尔需要自己和自己商量"。 |
| **PPM（项目组合管理）** | 不是把每个项目做快，而是**选对一篮子项目**——资源就这么多，哪些值得投、哪些该砍。 |
| **GTD** | David Allen 的任务流：收集 → 两分钟法则 → 委派 → 排期 → 落到项目。和 PARA 互补：GTD 管"接下来做什么"，PARA 管"东西放哪"。 |

## 与其它技能的关系

| 能力 | 本技能负责 | 协作对象 | 怎么取舍 |
|---|---|---|---|
| 把项目里的**需求拆成可执行工单** | 本技能只管"项目这一层"（立项/治理/盘点/评审/退役） | **idea-to-tickets** | 项目总纲里的"接下来要做什么"落到工单时，交给 idea-to-tickets 做 clarify→spec→slice |
| 项目内部**知识沉淀与跨会话恢复** | 本技能只规定目录结构（00/01/02/03/09/99） | **okf-wiki** | 项目里大量、会复利的知识（架构、决策、知识点）按 okf-wiki 组织；本技能不另建记忆体系 |
| **环境/机器**层面的维护 | 与本技能无关 | **dual-machine-manager** | 项目退役时"技术退役清单"里涉及的双机同步、备份由该技能负责 |
| **飞书知识空间**的实际创建 | 本技能只给目录模板和 SOP | **lark-wiki** / **lark-base** | 真要在飞书建空间、建多维表格台账时，调用对应技能执行 |

## 文件指引（按需读，不要一次全读）

| 你要 | 读这个 | 用模板 |
|---|---|---|
| 新建一个项目/知识空间 | `references/create.md` | 项目总纲模板、目录结构模板 |
| 给项目定"什么情况自己拍板、什么情况暂停重评" | `references/governance.md` | 治理卡模板、决策记录模板 |
| 盘点所有在做项目 | `references/inventory.md` | 项目台账表（列定义） |
| 季度集中评审一批项目 | `references/batch-review.md` | 门决策记录模板、评审 Checklist |
| 项目做完/砍掉怎么收尾 | `references/maintenance.md` | 退役总结模板、关闭 Checklist |
| 一次性复制所有模板 | `references/templates.md` | 全部模板汇总 |

## 来源与边界

**方法论来源**（详见各 reference 末尾标注）：
- PARA / 个人知识组织：Tiago Forte《Building a Second Brain》 https://www.buildingasecondbrain.com/para
- GTD：David Allen《Getting Things Done》
- 项目治理三层架构 / RACI：PMBOK 8 治理绩效域、projectmanagementformula、open-exam-prep
- 项目状态定义：伯克利 BPM Office https://bpm.berkeley.edu/project-definitions
- 阶段门（Phase-Gate）：projectmanagementformula、monday.com、arcturuspro、onplana
- 项目关闭与退役：projectmanagementformula closure checklist、beefed.ai technical decommissioning、LobeHub decommission skill
- 资产退役不删除原则：ISO 27001 Annex A 5.9 / 西班牙 ENS 实践
- 结构实证：用户飞书 9 个知识空间实采（CPA 备考库、珠宝库、AI、SEO、游戏项目等），2026-09-15 调研报告

**本技能不覆盖什么**：
- 不覆盖**具体任务执行**（写代码、写文章、做设计）——那是 idea-to-tickets 之后的事。
- 不覆盖**财务记账/投资决策本身**——股票台账可以作为项目放进台账，但买卖判断不在本技能范围。
- 不覆盖**团队多人协作**的重型流程（CCB 变更控制委员会、PMO、签字审批流）——这些只在"企业级重型 vs 个人轻量"对照表里提一句，个人场景默认用轻量版。
- 不替代 **lark-wiki / lark-base** 本身的操作——本技能给"建什么结构、写什么内容"，真要在飞书动手时调对应技能。
