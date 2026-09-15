# L2 · close 收尾与归档（Closing & Archival）

> 回答的问题：**"项目做完了或想砍了，怎么收尾才不留尾巴？"**
> 对应专业方法：PMBOK 的**项目收尾过程组** + 技术退役（Decommissioning）Playbook。

## 关闭不是"停止工作"

项目关闭不是"不做了"就完事。企业级项目关闭要完成六件事：

1. 交付物验证并移交
2. 正式干系人签字
3. 预算结算、供应商合同关闭
4. 释放项目资源
5. **归档全部文档**（让不熟悉项目的人也能看懂发生了什么）
6. 关闭后两周内做 lessons learned 复盘

> 来源：https://projectmanagementformula.com/project-closure-checklist/

个人场景把这六件事压成"关闭六步"，见下。

## 关闭 SOP（六步）

### 第 1 步：交付物移交
- 最终产出（报告/网站/数据）存入 `01_结论与产出/`。
- 若对外交付（如客户、读者），确认对方已收到。

### 第 2 步：正式总结（退役总结三问）
- 写一页"退役总结"（模板见下）。
- 必答三问：
  1. **什么让我意外？**（立项时没想到的事）
  2. **什么值得重复？**（下次项目可以照搬的做法）
  3. **下次怎么做？**（要改进的一点）

> 来源：https://projectmanagementformula.com/project-closure-checklist/

### 第 3 步：文档归档
- 整个项目子树移入 `99_归档/` 或 Archives 知识空间。
- **保持原结构**，不拆散、不删除——让不熟悉项目的人也能看懂发生了什么。
- 退役不删除，只打"已归档"标签。

> 来源：西班牙 ENS/ISO27001 "baja 不删除只标记" https://www.delbion.com/insights/inventario-activos-ens-iso-27001-guia-auditoria/

### 第 4 步：更新台账
- 在项目台账把状态改为 `Completed`（做完）或 `Cancelled`（砍掉）。
- 健康灯改为绿（完成）。
- 上次盘点 = 今天。

### 第 5 步：资源释放（技术退役清单）
- 停掉相关订阅、域名、服务、token。
- 个人版技术退役清单：
  - [ ] 域名续费停掉 / 转入停放
  - [ ] Vercel / Cloudflare / 第三方服务项目删除
  - [ ] API token / 密钥撤销
  - [ ] 数据库快照备份后删除
  - [ ] 订阅类服务（如 Ahrefs / SimilarWeb 独立子账号）取消

> 企业级技术退役时间线（T-90~T-7）个人版可大幅简化，见下。

### 第 6 步：通知
- 对外项目（如网站、公众号、服务）发 EOL（End of Life）公告。
- 对内（协作者、客户）告知项目正式结束、后续支持归谁。
- 关闭需要**主动沟通而非默认**——不能假设别人知道。

> 来源：https://projectmanagementformula.com/closing-phase-deliverables-checklist/

## 退役总结一页纸模板

```markdown
# 退役总结 · <项目名>

> 退役日期：YYYY-MM-DD ｜ 结果：✅ 成功 / ⏸ 暂停 / ❌ 取消

## 1. 项目概况
- 目标：<一句话>
- 实际结果：<一句话>

## 2. 关键数据
- 投入时间：<X 周 / Y 小时>
- 产出：<交付物清单>
- 收益/成果：<金钱 / 成长 / 数据指标>

## 3. 三问复盘
- 什么让我意外？<…>
- 什么值得重复？<…>
- 下次怎么做？<…>

## 4. 数据去向
- 保留在哪：<归档链接 / 本地路径>
- 已备份：<是/否>

## 5. 残留事项
- <域名/服务是否已停>
- <是否有人还在依赖此项目>
```

## 技术退役时间线（企业版，个人版简化）

企业级技术退役有严格时间线：

| 时间点 | 动作 |
|---|---|
| T-90 天 | 对外公告 EOL；开始盘点与法务界定 |
| T-60 天 | 确定数据保留分级、法务冻结、归档要求 |
| T-30 天 | 完成依赖映射；冻结 schema 迁移与 feature flag |
| T-14 天 | 最终备份与恢复测试；确认 owner 与签字 |
| T-7 天 | 关闭写入；服务转只读；撤销非关键 token |

> 来源：https://beefed.ai/en/technical-decommissioning-checklist-data-retention

**个人版简化**：
- 没有法务、没有依赖系统、没有 feature flag。
- 压成两步：① 备份关键数据 → ② 停订阅/域名/服务。
- 对外网站若有用户，提前 2 周发 EOL 公告。

## 退役报告结构（企业版参考）

| 章节 | 内容 |
|---|---|
| 系统描述 | 名称、版本、用途、分级 |
| 退役理由 | 为什么退役 |
| 数据处置摘要 | 数据去了哪里（迁移/归档/销毁） |
| 验证证据 | 迁移验证结果、归档校验 |
| 残留风险 | 仍存的数据保留义务 |
| 审批 | 系统 owner、QA、IT 签字 |

> 来源：https://lobehub.com/skills/pjt222-development-guides-decommission-validated-system

**个人版**：这张表压成"退役总结一页纸"即可，不需要 QA/IT 签字。

## 归档 vs 删除原则

- **退役不删除**：Cancelled/Completed 的项目**不删文档**，打"已归档"标签，移入 `99_归档/`。
- 保留历史可追溯性——半年后你可能想回头看"当时为什么砍了这个项目"。
- 真正删除只发生在：① 有隐私/合规要求（如个人数据必须销毁）；② 空间实在不够且已备份。
- 删除前必须确认已备份 + 已写退役总结。

> 来源：ISO 27001 Annex A 5.9 资产生命周期管理 https://learn.daydream.ai/requirements/iso-27001-iso27001-09

## 日常维护要点（月度巡检）

项目还在做的时候，每月做一次轻量巡检：

- [ ] 项目总纲的"当前状态"是否还是最新？
- [ ] `03_进行中的任务` 里有没有已完成但没移走的任务？
- [ ] `09_调研底稿与素材` 里有没有过期/失效的链接？
- [ ] 关键数据（网站后台、数据库）是否已备份？
- [ ] 订阅/域名/服务是否还在花钱？有没有可以砍的？

## 项目维护巡检 Checklist（月度）

```markdown
# 月度巡检 · <项目名> · YYYY-MM

## 总纲更新
- [ ] 当前状态已更新到本周
- [ ] 健康灯已更新（绿/橙/红）

## 任务清理
- [ ] 03_进行中的任务/ 里已完成的任务已移到 01_结论与产出/
- [ ] 过期任务已删除或标记

## 数据与备份
- [ ] 关键数据已备份（最近 30 天内）
- [ ] 订阅/域名/服务清单已核对，无多余支出

## 风险
- [ ] 风险登记册已更新
- [ ] 命中暂停触发条件的，已改 On Hold
```

## 企业级重型 vs 个人轻量对照

| 主题 | 企业级重型 | 个人轻量（推荐你用） |
|---|---|---|
| 关闭流程 | 正式签字 + 预算结算 + 合同关闭 + lessons learned 工作坊 | 关闭六步 + 一页退役总结三问 |
| 技术退役 | T-90~T-7 时间线 + 法务/合规/QA 签字 | 备份数据 → 停订阅/域名/服务，两步 |
| 退役报告 | 完整退役报告（系统描述/理由/数据处置/验证/残留风险/审批） | 一页退役总结模板 |
| 关闭度量 | Closure Cycle Time + Administrative Closure Completeness | 不跟踪 |
| 归档 | 正式归档到项目档案库 | 打"已归档"标签，移入 99_归档/ |

## 反模式

- 项目做完直接丢着 → 半年后订阅还在扣费、域名还在续费。
- 砍掉项目时不写退役总结 → 半年后重蹈覆辙。
- 退役即删除文档 → 想回看"当时为什么砍"时什么都没了。
- 对外网站关停不公告 → 用户突然打不开，投诉。
- 关项目时不更新台账 → 项目台账里还挂着 Active。

## 来源

- 项目关闭 Checklist：https://projectmanagementformula.com/project-closure-checklist/
- 关闭交付物与通知：https://projectmanagementformula.com/closing-phase-deliverables-checklist/
- 技术退役时间线：https://beefed.ai/en/technical-decommissioning-checklist-data-retention
- 退役报告结构：https://lobehub.com/skills/pjt222-development-guides-decommission-validated-system
- 关闭度量：https://streamlineprojects.com.au/sops/project-delivery/project-closure
- 退役不删除原则：https://www.delbion.com/insights/inventario-activos-ens-iso-27001-guia-auditoria/
- ISO 27001 资产生命周期：https://learn.daydream.ai/requirements/iso-27001-iso27001-09
