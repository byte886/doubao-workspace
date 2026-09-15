# L2 · monitor 执行与监控（Execution & Monitoring / Governance）

> 回答的问题：**"项目开工后怎么管？我能拍板什么？什么情况必须停下来？"**
> 对应专业方法：PMBOK 8 的**治理绩效域**（Governance Performance Domain）+ 执行过程组的**监控**。

## 治理到底是什么（一句话）

企业里说的"项目治理"听着很重，其实就三件事：

1. **决策权（decision rights）**：哪些事你自己能定，哪些事必须问别人/问自己。
2. **升级路径（escalation path）**：踩到什么线就必须停下来，不能继续闷头干。
3. **决策节奏（governance cadence）**：多久花点时间自查一次。

PMBOK 8 把治理提升为一级绩效域，因为审计数据显示：**"缺乏明确治理"和项目失败的相关性，强于预算、范围、技术任何单一因素**。说白了——不是钱不够、技术不行，是"没人说清楚什么时候该停"。

> 来源：https://ppmsi.net/wp-content/uploads/2026/04/ppmsi_pm_simulator.html

## 企业级三层架构（了解即可，个人场景不用）

| 层级 | 角色 | 干什么 |
|---|---|---|
| 发起层 | Sponsor（发起人） | 持有商业论证、批重大变更和预算、有权砍项目 |
| 协调层 | Steering Committee（指导委员会） | 跨干系人协调、评审项目 |
| 执行层 | PM（项目经理） | 日常执行、日常决策 |

再配上 **CCB（变更控制委员会）** 逐项审批范围变更，和 **RACI 矩阵**写清每件事谁 R 谁 A 谁 C 谁 I。

> 来源：https://projectmanagementformula.com/project-governance-framework/

## 个人场景：两层压缩法

一个人干，三层直接压成两层：

```
你自己 = PM（执行） + Sponsor（拍板）
升级 = 停下来，把项目挂 On Hold，重新评估要不要继续
```

不设 CCB，不开评审会。但**必须写清楚"退出条件"**——这是敏捷治理"信任而非控制"的个人版：不给自己设条条框框管过程，只设"什么情况必须停下来想清楚"。

## 敏捷治理三原则（个人场景直接套用）

1. **以结果而非产出衡量**：不问"这周写了多少文档"，问"假设被验证了吗"。
2. **以信任而非控制**：不搞每日站会、不写进度周报，靠每周 15 分钟自查。
3. **以适应而非合规**：计划错了就改，不要硬撑着按原计划走到底。

> 来源：https://www.pmp-guide.com/blog/governance-frameworks-pmo-2026-pmp-exam

## 个人治理卡模板（一页，放在 `02_决策记录/治理卡.md`）

```markdown
# 治理卡 · <项目名>

> 最后更新：YYYY-MM-DD

## 基本信息
- 目标：<一句话>
- 截止：YYYY-MM-DD
- Owner：<我>

## 我可以独立决定的范围
- 影响范围：<不改变项目目标和成功标准的调整，可自决>
- 预算/支出：<单笔 ≤ $X / 累计 ≤ $Y 以内自决>
- 时间：<不影响关键里程碑的进度微调自决>

## 必须暂停重评的触发条件（命中任一即停）
- [ ] 进度偏离计划 > 2 周
- [ ] 预算超支 > 20%
- [ ] 出现新风险，使项目立项时的核心假设失效
- [ ] <项目特有的触发条件，如：XX 渠道被封 / 考试政策变了 / 客户取消>

## 碰节奏（governance cadence）
- 每周 15 分钟自查：范围还对吗？进度还走得动吗？风险有新的吗？
- 每季度参加批量评审（见 gates.md）
- 门节点：G1 立项 / G2 验证 / G3 发布（见 gates.md）

## 升级路径（个人版 = 暂停重评流程）
1. 命中触发条件 → 把项目状态改为 On Hold
2. 在台账里写一句"为什么暂停"
3. 下次盘点时给 Go / Conditional Go / Hold / Kill 决策
```

## RACI 矩阵简化版（个人场景）

企业级 RACI 是一张五行五列的大表。个人场景压成一句话：

| 决策事项 | 个人版 RACI |
|---|---|
| 项目要不要做（Go/No-Go） | R=A=我（拍板） |
| 预算花多少 | R=A=我（在治理卡阈值内自决，超阈值暂停重评） |
| 范围变不变 | R=A=我（但要记进决策记录） |
| 技术路线 | R=A=我（试错成本低时直接试） |
| 对外承诺（如网站上线日、客户交付日） | R=我 / C=受影响方（如协作者、客户） |

> 企业级完整版 RACI 参考：https://open-exam-prep.com/exams/pmp/process-domain-execution-control/establishing-project-governance

## 决策记录模板（ADR，放在 `02_决策记录/`）

> 关键决策不要只存在脑子里。半年后回看不后悔的唯一办法是写下来"当时为什么这么选"。

```markdown
# 决策记录 #NN · <一句话决策标题>

- 日期：YYYY-MM-DD
- 项目：<项目名>
- 状态：Accepted / Superseded by #XX

## 背景 / 我们面对什么问题
<当时的处境、约束、压力>

## 决策
<最后选了什么>

## 备选方案（被放弃的）
- 方案 A：<…>，放弃因为 <…>
- 方案 B：<…>，放弃因为 <…>

## 后果 / 什么时候该重新评估
<这个决策的代价是什么、什么情况下要推翻它>
```

**什么时候写决策记录**：
- 选了技术栈/工具/平台
- 砍了一个原计划要做的功能
- 改了截止日或成功标准
- 预算/资源重新分配
- **不要**为日常小选择写（浪费时间）

## 每周 15 分钟自查 SOP

每周固定一个时间（比如周日晚），对每个 Active 项目问三问：

1. **范围还对吗？** 这周做的事还在往项目目标走吗，还是跑偏成了"为做而做"？
2. **进度还走得动吗？** 距计划里程碑还有多远？有没有偏离 > 2 周？
3. **风险有新的吗？** 有没有新情况让原来的假设不成立了？

答完三问：
- 全绿 → 继续
- 任一黄灯 → 在台账更新健康灯，下周聚焦补救
- 命中暂停触发条件 → 改 On Hold，等季度评审

## 风险登记册（轻量版）

企业级风险登记册是一张大表：风险、概率、影响、应对计划、owner。个人场景压成三行：

```markdown
# 风险登记 · <项目名>（每周自查时更新）

| 风险 | 概率(1-5) | 影响(1-5) | 应对 | 状态 |
|---|---|---|---|---|
| <例：Google 收录慢> | 4 | 3 | 先做 10 篇长尾，等 4 周 | 监控中 |
```

> 企业级健康扫描对照 PMBOK 10 领域（整合/范围/进度/成本/质量/资源/沟通/风险/采购/干系人）。个人版只问三问：范围还对吗 / 进度还走得动吗 / 风险有新的吗。
> 来源：https://www.pmi.org/learning/library/healthy-project-analyze-health-risks-8609

## 企业级重型 vs 个人轻量对照

| 主题 | 企业级重型 | 个人轻量（推荐你用） |
|---|---|---|
| 治理架构 | Sponsor/Steering Committee/PM 三层 + CCB + RACI 全表 | 一页治理卡：独立决策阈值 + 暂停重评触发条件 |
| 风险登记 | 完整风险登记册 + 概率影响矩阵 + 定期风险评审 | 三行表，每周自查时更新 |
| 进度监控 | 燃尽图/挣值管理 EVM/绩效报告 | 每周 15 分钟三问自查 + 健康灯 |
| 变更控制 | CCB 逐项审批 | 范围变更自己定，但记 ADR |

## 反模式

- 不写治理卡，靠"到时候再说" → 真到超支/延期时凭感觉硬扛。
- 触发条件写得模糊（"感觉不对就停"）→ 永远不会触发。
- 每周自查变成每周写周报 → 又臭又长，三周后就放弃。
- 决策只在聊天记录里 → 换个会话就失忆，半年后重蹈覆辙。

## 来源

- PMBOK 8 治理绩效域：https://ppmsi.net/wp-content/uploads/2026/04/ppmsi_pm_simulator.html
- 治理三层架构：https://projectmanagementformula.com/project-governance-framework/
- 决策权限阈值：https://trustedinstitute.com/concept/pmp-pmbok8/business-governance-compliance/governance-structures-roles/
- RACI 矩阵样表：https://open-exam-prep.com/exams/pmp/process-domain-execution-control/establishing-project-governance
- 敏捷治理三原则：https://www.pmp-guide.com/blog/governance-frameworks-pmo-2026-pmp-exam
- 升级路径：https://trustedinstitute.com/flashcards/pmp-pmbok8/business-governance-compliance/
- PMI 项目健康度分析：https://www.pmi.org/learning/library/healthy-project-analyze-health-risks-8609
