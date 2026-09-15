---
name: dual-machine-manager
description: 两台 Mac（本机 cw/192.168.2.8 + 远程黑苹果 wj/192.168.2.9）的统一管家技能。覆盖系统信息、SSH 互访、launchd 后台服务、brew 服务、cron、凭证管理、OpenToken/TokenRank、远程关机、双机同步、日常巡检、故障排查等全部运维管理活。当用户提到「两台机器」「机器管家」「巡检」「服务状态」「后台进程」「远程关机」「双机同步」「OpenToken」「TokenRank」「wj」「黑苹果」「192.168.2.9」「凭证」「密码管理」等运维管理相关需求时使用本技能。
compatibility: macOS（已验证：macOS 15.7.8 x86_64，两台机器均为 Mac）；未验证 Windows / Linux
---

# 双机管家（Dual Machine Manager）

两台 Mac 的统一运维管理技能。所有管理信息、SOP、凭证位置均记录在 `references/` 下，按需加载。

## 平台适用（执行前先读）

- **已验证平台**：macOS 15.7.8 x86_64（本机 chenwenjie + 远程机 wenjiechen，均为 Mac）
- **未验证平台**：Windows、Linux
- **执行第一步**：`uname -s` 判平台，非 macOS 停下告知「该平台需先适配」，不用想当然的等价命令硬跑
- **路径可移植**：禁止硬编码 `/Users/<用户名>`，Shell 用 `$HOME`、Python 用 `Path.home()`、文档示例用 `~`；引号内和配置框内 `~` 不展开，用 `$HOME`

## 两台机器速览

| 别名 | 主机名 | 用户名 | IP | 定位 |
|---|---|---|---|---|
| `cw`（本机） | 192.168.2.8 | chenwenjie | 192.168.2.8 | 主力机，931GB，有 Homebrew |
| `wj`（远程） | 192.168.2.9 | wenjiechen | 192.168.2.9 | 黑苹果，3.7TB，无 Homebrew |

- SSH 互访：本机 `ssh wj` → 远程机；远程机 `ssh cw` → 本机
- 双机同步：`~/Doubao` git 仓库，提交统一在 wenjiechen 机执行

## 文档索引（按需加载）

| 文档 | 何时读 | 内容 |
|---|---|---|
| [references/machines.md](references/machines.md) | 需要机器详细信息、SSH 配置、网络参数时 | 两台机器硬件/系统/网络/SSH 完整档案、互访配置、同步约定、排查命令 |
| [references/services.md](references/services.md) | 需要查看/管理后台服务、launchd、brew、cron 时 | 两台机器所有后台服务清单、服务管理通用 SOP、远程服务操作 |
| [references/credentials.md](references/credentials.md) | 需要密码、token、密钥等凭证时 | sudo 密码、SSH 密钥、GitHub PAT、关机 Webhook token、OpenToken 凭证的位置与管理方式（敏感值不在这里明文存储） |
| [references/opentoken.md](references/opentoken.md) | 需要安装/验证/卸载/排查 OpenToken（TokenRank）时 | OpenToken 全流程 SOP：安装、验证（必做四项）、常用命令、文件位置、卸载、故障排查、当前部署状态 |
| [references/sop.md](references/sop.md) | 需要执行标准运维流程时 | 日常巡检、双机同步、服务管理、远程关机、故障排查、新工具接入、凭证轮换等 SOP |

## 常用快速操作

### 日常巡检
```bash
# 本机
ls -1 ~/Library/LaunchAgents/
launchctl list | grep -v "com.apple"
~/.local/bin/opentoken --version && launchctl list | grep opentoken
df -h / | tail -1

# 远程机
ssh wj 'ls -1 ~/Library/LaunchAgents/ && launchctl list | grep -v "com.apple" && df -h / | tail -1'
```

### 远程关机
```bash
ssh wj 'echo "***REMOVED***" | sudo -S shutdown -h now'
```

### OpenToken 手动上报
```bash
~/.local/bin/opentoken upload
```

### 双机同步（git 提交在远程机执行）
```bash
ssh wj 'cd ~/Doubao && git add -A && git commit -m "<msg>" && git push'
cd ~/Doubao && git pull
```

## 安全红线

1. **凭证不外露**：sudo 密码、token、密钥、webhook URL 不输出到日志、不贴到聊天、不写进非凭证文档
2. **打码义务**：对外汇报或分享时，所有 token / 密码 / 个人令牌必须打码
3. **高风险操作**：删除文件、卸载服务、关机等操作前确认范围，不主动扩展任务
4. **只读优先**：排查问题时先只读查看，不修改不删除，确认后再动手
