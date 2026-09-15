# 模板汇总（templates）

> 一页索引：所有模板在哪、用在哪个模块、哪一步。需要哪个就去对应 reference 复制完整模板。

## 模板索引表

| 模板 | 用在哪个模块 | 哪个 SOP 步骤 | 完整模板位置 |
|---|---|---|---|
| 目录结构模板 | initiate 启动 | 启动 SOP 第 5 步：按目录建结构 | [initiate.md § 推荐目录模板](initiate.md#推荐目录模板融合-cpa-五级结构--para) |
| 项目总纲（Project Charter） | initiate 启动 | 启动 SOP 第 3 步：写一页项目总纲 | [initiate.md § 项目总纲一页纸模板](initiate.md#项目总纲一页纸模板project-charter-个人版) |
| 创建 Checklist | initiate 启动 | 启动 SOP 收尾自检 | [initiate.md § 创建 Checklist](initiate.md#创建-checklist) |
| 治理卡 | monitor 监控 | 启动 SOP 第 7 步 + 日常治理 | [monitor.md § 个人治理卡模板](monitor.md#个人治理卡模板一页放在-02_决策记录治理卡md) |
| 决策记录（ADR） | monitor 监控 | 启动 SOP 第 8 步 + 关键决策时 | [monitor.md § 决策记录模板](monitor.md#决策记录模板adr放在-02_决策记录) |
| 风险登记册（轻量版） | monitor 监控 | 每周 15 分钟自查时更新 | [monitor.md § 风险登记册](monitor.md#风险登记册轻量版) |
| 项目台账表（列定义） | portfolio 组合层 | 季度盘点 SOP 第 6 步：更新台账 | [portfolio.md § 项目台账表](portfolio.md#项目台账表多维表格列设计) |
| PPM 评分法 | portfolio 组合层 | 季度盘点 SOP 第 5 步：算优先级分 | [portfolio.md § PPM 评分排序法](portfolio.md#ppm-评分排序法季度重排用) |
| 门决策记录 | gates 阶段门 | 批量评审时，每个项目填一份 | [gates.md § 门决策记录模板](gates.md#门决策记录模板) |
| 评审 Checklist | gates 阶段门 | 过门前必过 | [gates.md § 评审 Checklist](gates.md#评审-checklist过门前必过) |
| 批量评审议程 | gates 阶段门 | 季度批量评审开场 | [gates.md § 批量评审议程模板](gates.md#批量评审议程模板每季度一次) |
| 退役总结 | close 收尾 | 关闭 SOP 第 2 步：正式总结 | [close.md § 退役总结一页纸模板](close.md#退役总结一页纸模板) |
| 关闭六步 Checklist | close 收尾 | 关闭 SOP 全程 | [close.md § 关闭 SOP](close.md#关闭-sop六步) |
| 技术退役清单 | close 收尾 | 关闭 SOP 第 5 步：资源释放 | [close.md § 第 5 步：资源释放](close.md#第-5-步资源释放技术退役清单) |
| 月度巡检 Checklist | close 维护 | 项目执行中每月巡检 | [close.md § 项目维护巡检 Checklist](close.md#项目维护巡检-checklist月度) |
| 工程记忆 index | execution-patterns 执行 | 跨会话恢复架构/链路/治理 | [execution-patterns.md §一](execution-patterns.md) |
| TASK_STATUS 任务台账 | execution-patterns 执行 | 中大型项目执行期唯一进度真相 | [execution-patterns.md §二](execution-patterns.md) |
| ISSUES 问题清单 | execution-patterns 执行 | 执行期开放/已解决/做不通问题 | [execution-patterns.md §二](execution-patterns.md) |
| 批次状态 JSON / JSONL | execution-patterns 执行 | 批量任务断点续传 | [execution-patterns.md §三](execution-patterns.md) |
| 文档同步检查清单 | execution-patterns 执行 | 每次 git 提交前 | [execution-patterns.md §四](execution-patterns.md) |
| 存储分工 / 数据层编号 | execution-patterns 执行 | 内容类大项目分工与编号 | [execution-patterns.md §五、§六](execution-patterns.md) |
| 项目级 AGENTS | execution-patterns 执行 | 项目开工即建 | [execution-patterns.md §七](execution-patterns.md) |

## 快速复制区（按使用顺序）

> 以下是所有模板的精简版，直接复制到项目里用。完整版见对应 reference。

### 1. 目录结构模板（initiate）

```
📁 <项目名>
├── 📄 00_项目总纲
├── 📁 01_结论与产出
├── 📁 02_决策记录
├── 📁 03_进行中的任务
├── 📁 09_调研底稿与素材
└── 📄 99_复盘与退役总结
```

### 2. 项目总纲模板（initiate）

```markdown
# 项目总纲 · <项目名>
> 最后更新：YYYY-MM-DD ｜ 状态：Active/On Hold/To Be Started ｜ 健康灯：🟢🟡🔴

## 1. 一句话目标
<项目完成后世界/我会变成什么样>

## 2. 成功标准（可量化）
- [ ] <硬指标 1>
- [ ] <硬指标 2>

## 3. 期限
- 立项：YYYY-MM-DD ｜ 计划完成：YYYY-MM-DD ｜ 里程碑：<M1/M2/M3>

## 4. 当前状态
- 现在在做：<>
- 下一步：<>
- 主要风险：<>

## 5. Owner 与资源
- Owner：<我> ｜ 时间投入：<每周 X 小时> ｜ 预算：<>

## 6. 治理卡（详见 02_决策记录/治理卡）
- 独立决定：<影响 < X / 预算 < $Y>
- 暂停重评：<进度偏离> 2周 / 预算超支> 20% / 新风险使假设失效>
- 碰节奏：<每周 15 分钟>
```

### 3. 治理卡模板（monitor）

```markdown
# 治理卡 · <项目名>
## 基本信息
- 目标：<> ｜ 截止：YYYY-MM-DD ｜ Owner：<我>

## 我可以独立决定的范围
- 影响范围：<>
- 预算/支出：<单笔 ≤ $X / 累计 ≤ $Y>
- 时间：<不影响关键里程碑的微调>

## 必须暂停重评的触发条件
- [ ] 进度偏离 > 2 周
- [ ] 预算超支 > 20%
- [ ] 新风险使核心假设失效
- [ ] <项目特有>

## 碰节奏
- 每周 15 分钟三问自查
- 每季度批量评审
- 门节点：G1 / G2 / G3
```

### 4. 决策记录 ADR 模板（monitor）

```markdown
# 决策记录 #NN · <一句话标题>
- 日期：YYYY-MM-DD ｜ 项目：<> ｜ 状态：Accepted / Superseded by #XX

## 背景
<当时处境>

## 决策
<最后选了什么>

## 备选（被放弃的）
- 方案 A：<>，放弃因为 <>
- 方案 B：<>，放弃因为 <>

## 后果 / 何时重新评估
<>
```

### 5. 项目台账表（portfolio）

| 项目名 | 状态 | 健康灯 | 战略对齐 | 预期价值 | 资源占用 | 风险 | 上次盘点 | 下次盘点 | 知识空间 | 备注 |
|---|---|---|---|---|---|---|---|---|---|---|
| | Active/Completed/Cancelled/On Hold/To Be Started | 绿/橙/红 | 1-5 | 1-5 | 1-5 | 1-5 | 日期 | 日期 | 链接 | |

### 6. 门决策记录模板（gates）

```markdown
# 门决策 · <项目名> · G<1/2/3> · YYYY-MM-DD
## 阶段交付物
<清单 + 完成状态>

## 门标准评估
| 领域 | 标准 | 是否通过 |
|---|---|---|
| 战略对齐 | <二元判断题> | ✅/❌ |
| 财务健康 | <> | ✅/❌ |
| 进度绩效 | <> | ✅/❌ |
| 风险状态 | <> | ✅/❌ |
| 交付物合规 | <> | ✅/❌ |

## 门决策
- 决策：Go / Conditional Go / Hold / Kill
- 决策者：<我> ｜ 日期：YYYY-MM-DD

## 若 Conditional Go
| 条件 | 可测量标准 | owner | 截止日 |
|---|---|---|---|
```

### 7. 退役总结模板（close）

```markdown
# 退役总结 · <项目名>
> 退役日期：YYYY-MM-DD ｜ 结果：✅成功 / ⏸暂停 / ❌取消

## 1. 概况
- 目标：<> ｜ 实际结果：<>

## 2. 关键数据
- 投入：<> ｜ 产出：<> ｜ 收益：<>

## 3. 三问复盘
- 什么让我意外？<>
- 什么值得重复？<>
- 下次怎么做？<>

## 4. 数据去向
- 保留在哪：<> ｜ 已备份：是/否

## 5. 残留事项
- 域名/服务已停？<>
- 是否还有人依赖？<>
```

### 8. 关闭六步 Checklist（close）

- [ ] 第 1 步：交付物存入 `01_结论与产出/`
- [ ] 第 2 步：写退役总结（三问复盘）
- [ ] 第 3 步：项目子树移入 `99_归档/`，保持原结构
- [ ] 第 4 步：台账状态改 Completed / Cancelled
- [ ] 第 5 步：停订阅/域名/服务，撤销 token
- [ ] 第 6 步：对外项目发 EOL 公告

---

## 实战执行模式模板（execution-patterns）

> 以下模板从真实项目（multiplatform-content-pipeline）提炼，适用于进入执行阶段的中大型项目。

### 9. TASK_STATUS.md 模板（活跃任务台账）

```markdown
# 任务状态台账

> 本页是"当前做什么、到哪"的唯一进度真相，实时更新。
> 需求溯源看 docs/REQUIREMENTS.md，开放缺陷看 ISSUES.md。
> 稳定技术结论的权威版在 ADR / 工程记忆，本页只放指针、不复制结论。

## 依赖与并行前沿
- **阶段1**：✅ 完成（commit xxx）
- **阶段2**：⏳ 进行中
- **阶段3**：📋 待启动
- 可并行：A（后台运行）与 B（前台开发）可同时进行

## 工单清单

| 编号 | 标题 | 类型 | 前置 | 状态 | 验收 / 落点 |
|------|------|------|------|------|------------|
| T-01 | xxx | feature | 无 | done | 产出物路径 |
| T-02 | xxx | feature | T-01 | doing | 预期产出 |
| T-03 | xxx | bugfix | 无 | blocked | 阻塞原因 |
| T-04 | xxx | refactor | 无 | todo | 预期产出 |

状态四档：todo / doing / blocked / done

## 关键口径（指针，不展开）
- **技术点A**：结论一句话 → 见工程记忆 concepts/xxx
- **技术点B**：结论一句话 → 见 ADR-002

## 下一步（按优先级）
1. 最高优先级任务（T-xx）
2. 次优先级任务（T-xx）
3. 可后台运行的任务（T-xx）
```

### 10. ISSUES.md 模板（问题清单）

```markdown
# 问题清单

## 开放问题（Open）

### ISSUE-001: 问题标题
- **状态**：待启动 / 研究中 / 修复中
- **发现时间**：YYYY-MM-DD
- **问题描述**：具体现象、影响范围
- **根因**：（找到后填写）
- **方案**：（确定后填写）
- **验证**：（修复后填写验证方法和结果）

## 已解决问题（Closed）
### ISSUE-00x: 问题标题 ✅
- **解决时间**：YYYY-MM-DD
- **根因**：一句话
- **方案**：一句话

## 已验证做不通的方向（Won't Fix）
- 方向A → 原因（什么情况下试过、结果是什么）
```

### 11. memory/index.md 模板（工程记忆入口）

```markdown
# 工程记忆 bundle

> 新会话恢复顺序：根 AGENTS.md（规则）→ 本页 index（有什么、在哪）
> → 按需沿每篇的「来源与下钻」深读原始文档。
> 本 bundle 只做"结论 + 指针"，不复制、不替代原文。
> 易变状态（进度、计数、当天日期）不进本 bundle，需要时实时读台账。

# 架构（Architecture）
* [架构名称](concepts/architecture-xxx.md) - 一句话说明（来源 ADR-xxx）

# 链路（Workflow）
* [链路名称](concepts/workflow-xxx.md) - 一句话说明

# 治理（Standard）
* [规则名称](concepts/standard-xxx.md) - 一句话说明
```

### 12. 批次状态 JSON 模板（批量任务）

```json
{
  "batch_id": "capture_20260915_001",
  "task_type": "video_download",
  "started_at": "2026-09-15T10:00:00+08:00",
  "updated_at": "2026-09-15T10:30:00+08:00",
  "status": "running",
  "total": 313,
  "completed": 150,
  "failed": 2,
  "skipped": 0,
  "current_item": "item_150_xxx",
  "failed_items": [
    {"name": "item_023_xxx", "reason": "下载超时", "retry_count": 3}
  ]
}
```

### 13. 文档同步检查清单模板（提交前必跑）

```markdown
## 一、任务状态同步
- [ ] TASK_STATUS.md 已更新（工单状态正确、"下一步"已更新）
- [ ] ISSUES.md 已更新（新问题已记录、已解决问题已标注）

## 二、文档关联同步
- [ ] DOCUMENTATION_MAP.md 已更新（新增文档已加入、链接有效）
- [ ] WORKFLOW.md 已更新（如流程变更）
- [ ] REQUIREMENTS.md 已更新（如需求变更）

## 三、目录结构同步
- [ ] DIRECTORY_STRUCTURE.md 已更新
- [ ] .gitignore 已检查（git status 确认没有不该提交的文件）

## 四、工具与脚本同步
- [ ] 新增脚本已加入文档地图
- [ ] 脚本参数变更已更新到对应 SOP

## 五、工程记忆同步（如稳定结论变更）
- [ ] memory/index.md 已更新
- [ ] 相关 concept 已修订

## 六、ADR 决策记录（如重要决策）
- [ ] 重要决策已记录到 ADR-xxx.md
- [ ] 决策状态正确
```

### 14. 项目级 AGENTS.md 模板（AI 操作手册）

```markdown
# 项目 AGENTS.md（AI 操作手册）

> 本文件是给 AI 看的操作手册，命令式、可执行。
> 给人看的项目概览在 README.md。
> 与全局 AGENTS.md 冲突时，本文件优先（仅本项目内）。

## 1. 项目定位与边界
- 做什么：一句话
- 不做什么：一句话（边界）

## 2. 目录约定
- 什么东西放哪：列出关键目录
- 路径规则：禁止硬编码 /Users/<用户名>，用 $HOME / 相对路径
- 禁止修改：列出绝对不能动的目录/文件

## 3. 工具用法
- 本项目用什么工具、怎么调用、有什么坑

## 4. 新会话恢复顺序
1. 读本文件（AGENTS.md）
2. 读 docs/DOCUMENTATION_MAP.md（文档地图）
3. 读 docs/project-management/memory/index.md（工程记忆）
4. 读 project-management/active/TASK_STATUS.md（当前进度）

## 5. 提交前检查
- 按 docs/project-management/standards/DOC_SYNC_CHECKLIST.md 跑一遍
- git status 确认没有不该提交的文件
```

---

> 本文件只做索引。模板改动请回到对应 reference 改，不要在这里双写（DRY）。
