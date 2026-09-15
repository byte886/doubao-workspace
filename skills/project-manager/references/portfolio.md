# L1 · portfolio 项目组合管理（PPM）

> 回答的问题：**"我现在应该做哪些项目？哪些该停？资源有限，往哪投？"**
> 这是三层架构里最顶层——先管"一篮子项目"，再谈单个项目怎么做。

## 什么是 PPM（Project Portfolio Management）

一句话：**不是把每个项目做快，而是选对一篮子项目**。

企业里的 PPM 是集中选择、排序、治理一组项目，让整体组合在给定资源/预算/风险偏好下交付最大战略价值。个人场景同理——你一周就那么多小时，同时推 12 个项目不如精推 5 个。

> 来源：https://resources.rework.com/ms/libraries/project-management/project-portfolio-management ；https://umbrex.com/resources/frameworks/project-management-frameworks/project-portfolio-management-ppm/

## PPM 四步流程（专业版）

| 步骤 | 企业级做法 | 个人轻量版（推荐你用） |
|---|---|---|
| 1. 对齐战略 | 按战略/资金类别（创新、降本、增长、维护运营）分组 | 给每个项目打"战略对齐 1-5 分" |
| 2. 评分与优先级排序 | 预期 ROI、复杂度、风险、资源可得性，加权排序 | 四维度打分（见下），算优先级分 |
| 3. 资源分配 | 把预算/人力/时间摊到各项目 | 控制活跃项目数 ≤ 7±2，每周时间预算硬约束 |
| 4. 组合平衡与监控 | 跟踪进度/成本/产出，决定 start/continue/pause/stop | 季度盘点 + 状态/健康灯更新 + 90 天无活动自动归档 |

> 关键洞见：**纯数字排序很少奏效**——评分模型必须配一次"定期组合评审"，让人对排名辩论。数字只是起点，真判断靠人。
> 来源：https://ones.com/blog/project-portfolio-management-explained-key-concepts-and-workflows/

## 项目状态定义（伯克利 BPM，五档）

| 状态 | 英文 | 含义 | 个人场景例子 |
|---|---|---|---|
| **正在做** | Active | 团队正在做 | 这周还在推进的出海游戏站 |
| **已完成** | Completed | 工作完成、交付物齐 | 某份调研报告已交付 |
| **已取消** | Cancelled | 未完成，且**不会继续** | 试过两个月放弃的方向 |
| **暂停中** | On Hold | 未完成，**暂时暂停**（以后可能回来） | 备考 CPA 期间暂停的网站改版 |
| **待启动** | To Be Started | 已立项但**还没动手** | 排期在下季度的新项目 |

> 来源：https://bpm.berkeley.edu/project-definitions

## 健康灯定义（三档）

| 灯 | 英文 | 含义 | 判断标准（个人版） |
|---|---|---|---|
| 🟢 | On Track | 按计划走 | 无触发条件命中，本周有实质进展 |
| 🟡 | At Risk | 有风险但还能救 | 出现预警信号，需要下周聚焦补救 |
| 🔴 | Off Track | 偏得远了 | 命中治理卡暂停条件，应改 On Hold 或 Kill |

## 项目台账表（多维表格列设计）

> 建议用飞书多维表格（lark-base）建一张，每个项目一行。也可以先用 Markdown 表格跑起来。

| 列名 | 类型 | 说明 |
|---|---|---|
| 项目名 | 文本 | 唯一，和知识空间同名 |
| 状态 | 单选 | Active / Completed / Cancelled / On Hold / To Be Started |
| 健康灯 | 单选 | 绿 / 橙 / 红 |
| 战略对齐 | 数字 1-5 | 对当前个人战略目标的贡献（5=核心） |
| 预期价值 | 数字 1-5 | 做完后的回报（金钱/成长/影响力） |
| 资源占用 | 数字 1-5 | 每周投入时间/精力（5=重） |
| 风险 | 数字 1-5 | 外部不确定性（5=政策/市场/技术高风险） |
| 上次盘点 | 日期 | 最近一次盘点日期 |
| 下次盘点 | 日期 | 下次计划盘点日期 |
| 知识空间 | 链接 | 对应飞书 Wiki 空间或本地路径 |
| 备注 | 文本 | 一句话备注 |

**优先级分公式**：
```
优先级分 = 战略对齐 × 0.3 + 预期价值 × 0.3 - 资源占用 × 0.2 - 风险 × 0.2
```
从高到低排，分低且资源占用高的，优先考虑 On Hold 或 Kill。

## 季度盘点 SOP（步骤清单）

每季度（如 1 月 / 4 月 / 7 月 / 10 月）跑一次：

1. **拉全量项目清单**：把所有知识空间/文件夹/台账里出现过的项目列出来，包括已经"忘了在做"的。
2. **逐项目问三问（个人版轻量化扫描，代替 PMBOK 10 领域审计）**：
   - 范围还对吗？（还是当初立项的那个目标吗？）
   - 进度还走得动吗？（最近两周有实质进展吗？）
   - 风险有新的吗？（有没有新情况让原假设失效？）
3. **给每个项目打状态 + 健康灯**。
4. **执行盘点规则**（见下）。
5. **算优先级分，重排一次**：活跃项目数应回到 ≤ 7。
6. **更新台账**：上次盘点 = 今天，下次盘点 = 下季度。
7. **把 On Hold / Cancelled 的项目**对应的知识空间子树准备归档（见 [close.md](close.md)）。

## 盘点规则（硬规则）

1. **90 天无更新的 Active → 强制改判 On Hold 或 Archived**。不是"可能还在做"，是真没动就停。
2. **退役不删除**：Cancelled/Completed 的项目不删文档，打"已归档"标签，移入 `99_归档/` 或 Archives 知识空间。保留历史可追溯性。
   > 来源：西班牙 ENS/ISO27001 "baja 不删除只标记" https://www.delbion.com/insights/inventario-activos-ens-iso-27001-guia-auditoria/
3. **活跃项目硬上限 7±2**：超过就砍或归档，不解释。
   > 来源：PARA 纪律 https://sinapsus.com/blog/how-to-build-second-brain-guide
4. **健康灯两周不更新就重新盘**：灯不是打了就完，是活的。

## PPM 评分排序法（季度重排用）

把所有 Active 项目按四维度打分（1-5）：

| 维度 | 1 分 | 5 分 |
|---|---|---|
| 战略对齐 | 与当前目标无关 | 核心目标 |
| 预期价值 | 做完没什么用 | 高回报（钱/成长/影响力） |
| 资源占用 | 每周 < 2 小时 | 每周 > 15 小时 |
| 风险 | 确定性高 | 政策/市场/技术高度不确定 |

**判断规则**：
- 战略对齐 ≥ 4 且资源占用 ≤ 3 → **继续重仓**
- 战略对齐 ≤ 2 且资源占用 ≥ 4 → **优先砍或 On Hold**
- 预期价值高但风险高 → **走 G2 验证门，先小成本试**（见 [gates.md](gates.md)）

> 来源：PPM 评分维度 https://ones.com/blog/project-portfolio-management-explained-key-concepts-and-workflows/

## PARA：个人组合的底层分类法

PPM 在企业里管"项目组合"，个人场景用 **PARA**（Tiago Forte）做底层分类。四类，按**可操作性**而非主题分：

| 类别 | 定义 | 例子 | 时间属性 |
|---|---|---|---|
| **Projects 项目** | 正在 actively 做、有明确目标和期限 | 上线新网站、备考 CPA、写季度报告 | 短期，完成即移走 |
| **Areas 领域** | 长期持续负责、需维持标准但无截止日 | 健康、财务、职业、关系 | 长期 |
| **Resources 资源** | 未来可能有用的主题 | 营销技巧、投资研究、设计灵感 | 长期参考 |
| **Archives 归档** | 其他三类中已完成或不活跃的项 | 完成的项目、暂停的项目 | 不活跃 |

> 来源：https://www.buildingasecondbrain.com/para ；https://fortelabs.com/blog/para/

**关键纪律**：活跃 Projects 列表保持短——**7±2 个**，超过就砍掉或归档。

> 你现有的飞书空间其实就是 PARA 雏形：CPA 备考/游戏项目 ≈ Projects；SEO/运维/房地产评估 ≈ Resources；项目调研/海口评估 ≈ 完成后应入 Archives。

## 现有飞书知识空间的 PARA 初判基线（首次实采，以飞书现状为准）

> 这是首次盘点的起点（空间会增减、改名，例如"学习AI"已改名"AI"）。下表按 PPM + PARA 口径给初判，以飞书实际空间为准、季度盘点时更新。

| # | 空间名 | 初判 PARA 类别 | 初判状态建议 | 说明 |
|---|---|---|---|---|
| 1 | CPA备考知识库 | Projects（备考期） | Active 🟢 | 考季驱动，按章节推进中 |
| 2 | 珠宝知识库 | Areas（长期业务）/ Projects | Active 🟢 | 业务在运转，06 视频精解标了试点 |
| 3 | AI（含 AI 情报站） | Resources（长期参考） | Active 🟢 | 持续追踪，不是短期项目 |
| 4 | 海口评估独立创业调研 | Projects → 应转 Archives | 待盘点 | 已是单报告型，结论已出，考虑退役 |
| 5 | SEO | Resources / 实践手册 | Active 🟢 | 实践手册+技能+报告三分离结构 |
| 6 | 运维 | Resources / 单手册 | On Hold 🟡 | 单手册型，无新进展时可归档 |
| 7 | 房地产评估 | Projects → 已交付 | 待 Completed | 单报告型，报告已出 |
| 8 | 项目调研（翡翠珠宝网站） | Projects → 已交付 | 待 Completed | 单报告型 |
| 9 | 游戏项目（DragonSword） | Projects | Active 🟢 | 有总纲入口，在建站阶段 |

**首次盘点动作建议**：
- #4/#7/#8 三个单报告型空间，报告已交付 → 走 [close.md](close.md) 退役流程。
- #6 运维手册若近 90 天无更新 → 改 On Hold。
- 股票投资无独立空间 → 若要纳入项目管理，按 [initiate.md](initiate.md) 新建；若只是记账，用 lark-base 多维表格做台账即可。

## 企业级重型 vs 个人轻量对照

| 主题 | 企业级重型 | 个人轻量（推荐你用） |
|---|---|---|
| PPM 流程 | 评分模型 + PMO + 组合平衡仪表盘 + 季度组合评审会 | 项目台账表 + 7±2 活跃项目上限 + 季度重排 |
| 盘点频率 | 年度审计 + PMBOK 10 领域健康扫描 | 季度盘点 + 状态/健康灯 + 90 天无活动自动归档 |
| 组织 | PMO（项目管理办公室）专职 | 自己 = PMO |

## 反模式

- 只列项目名，不打状态和健康灯 → 台账成了通讯录，没用。
- 90 天没动的项目还挂 Active → 假繁荣，占着活跃名额。
- 数字评分后不开人辩论 → 数字掩盖真判断（"这项目其实不该做"）。
- 盘点一次后台账再也不更新 → 半年后全是过期数据。

## 来源

- PPM 核心定义：https://resources.rework.com/ms/libraries/project-management/project-portfolio-management
- PMI Portfolio Management：https://www.pmi.org/learning/library/portfolio-management-complex-projects-waste-7327
- PPM 评分与优先级：https://ones.com/blog/project-portfolio-management-explained-key-concepts-and-workflows/
- 伯克利 BPM 项目状态：https://bpm.berkeley.edu/project-definitions
- PMI 项目健康度分析：https://www.pmi.org/learning/library/healthy-project-analyze-health-risks-8609
- 项目审计 vs 盘点区别：https://knowt.com/note/c01be768-5e6b-4a2d-81a6-65c9be697922/Project-Management-Audit-and-Closure-Lec
- ISO 27001 资产盘点生命周期：https://learn.daydream.ai/requirements/iso-27001-iso27001-09
- 退役不删除原则：https://www.delbion.com/insights/inventario-activos-ens-iso-27001-guia-auditoria/
- PARA 方法：https://www.buildingasecondbrain.com/para ；https://fortelabs.com/blog/para/
- PARA 7±2 纪律：https://sinapsus.com/blog/how-to-build-second-brain-guide
