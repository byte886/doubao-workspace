# 双机差异对比与一致性维护

> 最后更新：2026-09-15
> 数据来源：双机深度盘点报告（2026-09-15）。
> 本文是双机定位、全维度差异、一致性策略与同步 SOP 的总览；细节见各专题 reference。

---

## 一、双机定位总结

| | 本机 cw | 远程机 wj |
|---|---|---|
| **定位** | **全能工作站**：主力开发 + 设计 + 日常办公，工具链最全 | **精简编译/提交机**：执行 git 提交、编译/服务器，刻意精简 |
| 用户名 | chenwenjie | wenjiechen |
| IP | 192.168.2.8 | 192.168.2.9 |

一句话：**本机做所有重活与多账号操作，远程机只做主力账号的 git 提交与编译。**

---

## 二、全维度差异对比总表

| 维度 | 本机 cw | 远程机 wj |
|---|---|---|
| **角色定位** | 全能开发+设计+日常 | 精简编译机 + git 提交执行机 |
| **包管理** | Homebrew 206 formulae + 10 casks + mise(node/java/maven/gradle) + cargo | 仅 Xcode Python 3.9 + 系统 gem 3.0.3.1 + 手动 rustup |
| **IDE** | VS Code(14 扩展) + Android Studio + IntelliJ + WebStorm + emacs + Codex | VS Code(无 CLI) + Trae + Xcode |
| **软件数量** | ~130 个应用 | ~70 个应用 |
| **GitHub 账号** | 三账号 SSH 分流（byte886/tinyverse/web3） | 单账号（主力） |
| **ssh-agent** | ✅ 3 把密钥常驻 | 🔴 未运行 |
| **git credential** | 正常 | 🔴 指向不存在的 gh |
| **硬件** | i5-1260K / 64G / 1TB NVMe | i5-13600KF / 128G / 4TB NVMe + 16TB HDD |
| **内存压力** | 🔴 极高（64G 占满） | 🟢 充裕（55/128G） |
| **系统版本** | macOS 15.7.8 | macOS 15.7.8（黑苹果，多系统分区） |
| **Xcode** | 26.3.0 | 16.4.0 |
| **git 用户** | softwarecheng@126.com | softwarecheng@126.com（一致） |

---

## 三、一致性维护策略

### 3.1 必须保持一致

| 项 | 原因 |
|---|---|
| SSH 私钥（3 把，已同步） | 双机互访与 GitHub 访问基础 |
| `~/Doubao` git 仓库 | 双机共享工作区，靠 git 同步 |
| 技能文件（`~/Doubao/skills/`） | 本技能及其他技能双机共用 |
| git 用户配置（user.name / user.email） | 提交署名一致 |

### 3.2 允许差异（刻意设计）

| 项 | 说明 |
|---|---|
| 包管理器 | 远程机**刻意不装 Homebrew**，保持精简机定位 |
| IDE | 远程机只需基础（VS Code/Trae/Xcode），重型 IDE 不装 |
| 软件 | 按角色选配：本机全能，远程机加微信多开/Warp/Devin/Macs Fan Control |
| GitHub 账号分流 | 仅本机配三账号，远程机单主力账号 |

### 3.3 需修复的不对称

| 项 | 机器 | 修复 |
|---|---|---|
| ssh-agent 未运行 | 远程机 | `ssh-add --apple-use-keychain ~/.ssh/id_*` + launchd 自启 |
| git credential helper 失效 | 远程机 | 改 `osxkeychain` 或装 gh |

---

## 四、双机同步 SOP（git 提交统一在远程机执行）

```bash
# 1. 在远程机提交并推送
ssh wj 'cd ~/Doubao && git add -A && git commit -m "<msg>" && git push'

# 2. 本机拉取
cd ~/Doubao && git pull
```

约定（见 `~/Doubao/AGENTS.md`）：
- 同一套 `~/Doubao` 在两台 Mac 间同步；
- git 提交统一在 `wenjiechen` 机（远程机）执行；
- 技能与脚本内**禁止硬编码 `/Users/<用户名>`**：Shell 用 `$HOME`、Python 用 `Path.home()`、文档示例用 `~`；引号内/配置框内 `~` 不展开，用 `$HOME`。

---

## 五、新工具/新软件接入的双机决策流程

装新东西前先过这张表，决定装一台还是两台：

| 类型 | 装两台？ | 判断标准 |
|---|---|---|
| SSH 密钥、git 配置、技能文件、`~/Doubao` 内容 | ✅ 必须两台 | 属于「必须一致」项 |
| 日常通讯/办公/浏览器软件 | ✅ 建议两台 | 行为对齐，避免差异 |
| 重型 IDE / 设计工具 / 效率工具 | ❌ 仅本机 | 远程机保持精简 |
| 命令行工具 | ❌ 默认仅本机 | 远程机无 Homebrew，不引入新 CLI |
| 黑苹果专属（散热监控、多系统、微信多开、AI 开发机任务） | ✅ 仅远程机 | 角色所需 |
| 加密货币/节点/服务类 | ❌ 默认仅本机 | 远程机只做编译提交 |

**决策口诀**：「基础与凭证两台一致；重活与工具只装本机；远程机专属（散热/多开/AI 任务）只装远程机。」
