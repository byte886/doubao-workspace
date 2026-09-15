# 机器健康度

> 最后更新：2026-09-15
> 数据来源：双机深度盘点报告（2026-09-15 实际命令采集）。
> 本文记录资源占用、磁盘、进程、需处理问题与巡检命令。

---

## 一、资源占用对比

| 指标 | 本机 cw | 远程机 wj |
|---|---|---|
| CPU | i5-12600K（10 核/16 线程） | i5-13600KF（14 核/20 线程） |
| CPU 实时 | 68% user / 6% sys / 26% idle | 64% user / 7% sys / 30% idle |
| 内存总量 | 64 GB | 128 GB |
| **内存已用** | 🔴 **64 GB（占满）**，空闲仅 256 MB，compressor=0 | 🟢 55 GB，空闲 73 GB |
| Swap | 0 swapin/swapout | 0 swapin/swapout |
| 进程数 | 784 | 754 |
| uptime | 1 天 6:23 | 2 天 22:15 |
| Load Average | 11.68 / 12.50 / 12.53 | 15.31 / 14.63 / 14.15 |
| 电源 | AC（台式机，无电池） | AC（黑苹果台式机，无电池） |
| 温度/风扇 | powermetrics 无 SMC 读数 | powermetrics 无 SMC 读数（黑苹果） |

---

## 二、🔴 需优先处理（4 项）

| # | 问题 | 机器 | 说明 | 修复建议 |
|---|---|---|---|---|
| 1 | **内存几乎占满** | 本机 cw | 64 GB 物理内存已用 64G，空闲仅 256 MB，784 进程 | 排查高内存进程（Parallels 175G 虚拟磁盘、IDE 全家桶）；`top -o mem` 排序，关闭闲置 VM 或考虑重启 |
| 2 | **远程机 ssh-agent 未运行** | 远程机 wj | `SSH_AUTH_SOCK` 为空，密钥未加载 | `eval $(ssh-agent) && ssh-add --apple-use-keychain ~/.ssh/id_*` 并配 launchd 自启（详见 security-and-git.md 第三节） |
| 3 | **远程机 git credential helper 指向不存在的 gh** | 远程机 wj | `credential.helper=!/usr/local/bin/gh auth git-credential` 但 gh 未装 | 改为 `osxkeychain`，或在远程机装 gh（详见 security-and-git.md 第六节） |
| 4 | **iOS 模拟器卷 98% 满** | 本机 cw | `/Library/Developer/CoreSimulator` 22G 卷仅剩 551M | `xcrun simctl delete unavailable` 清理旧模拟器；再 `xcrun simctl purge -s all` |

---

## 三、🟡 建议关注

| # | 问题 | 机器 | 说明 |
|---|---|---|---|
| 5 | 备份盘 74% 满 | 本机 cw | disk0s2 HFS backup，703G / 953G |
| 6 | /Volumes/sys 80% 满 | 远程机 wj | Windows 系统分区，194G |
| 7 | ~/Doubao 占 864G | 远程机 wj | 远程机 Home 目录最大户，需确认是否为缓存/日志可清理 |
| 8 | Load Average 偏高 | 两台 | 本机 12.5 / 远程 15.3，但 idle 25-30%，多核满载属正常工作状态 |
| 9 | 两台均无 GPG 签名 | 两台 | Git commit 未做 GPG 签名 |
| 10 | 两台均无独立密码管理器 | 两台 | 凭据全靠钥匙串，无 1Password/Bitwarden/KeePass |
| 11 | Safari 27.0 待更新 | 两台 | SequoiaAuto-27.0，约 238 MB，推荐安装 |

---

## 四、🟢 健康项

- 两台系统盘用量均在 43-48%，空间充裕。
- 远程机 128G 内存仅用 55G，余量充足。
- 两台均无 swap 颠簸（swapin/swapout = 0）。
- SSH 双机互配免密 + ControlMaster 连接复用，链路通畅。
- 远程机 16TB HDD 备份盘仅用 2%，备份空间充裕。

---

## 五、磁盘空间详情

| 卷 | 本机 cw | 远程机 wj |
|---|---|---|
| 系统数据卷 | disk2s1：**438 G / 931 G（48%）** | disk2s1：**1.6 T / 3.7 T（43%）** |
| 备份盘 | disk0s2：HFS backup，**703 G / 953 G（74%）** 🟡 | disk4s1：APFS backup，270 G / 15 T（2%）🟢 |
| 其他卷 | iOS 模拟器 22 G **（98% 满）** 🔴；Nix Store 466 M | /Volumes/sys 194 G **（80% 满）** 🟡；/Volumes/s 759 G（28%）；/Volumes/Ubuntu-Serv 238 G（21%，多系统） |

---

## 六、Home 目录大户对比

**本机 cw：**

| 目录 | 大小 |
|---|---|
| ~/Parallels | 175 G |
| ~/Library | 44 G |
| ~/Desktop | 4.3 G |
| ~/go | 1.5 G |
| ~/sdk | 358 M |

**远程机 wj：**

| 目录 | 大小 |
|---|---|
| **~/Doubao** | **864 G** 🟡 |
| ~/Parallels | 381 G |
| ~/Library | 82 G |
| ~/Downloads | 75 G |
| ~/Desktop | 21 G |
| ~/go | 11 G |

> 对比要点：本机最大户是 Parallels（175G 虚拟机）；远程机最大户是 ~/Doubao（864G，异常大，需排查是否为缓存/日志/历史会话产物）。

---

## 七、系统更新状态

两台均有一条待更新：**Safari 27.0 (SequoiaAuto-27.0)**，约 238 MB，推荐安装。

```bash
# 查看待更新
softwareupdate -l
```

---

## 八、健康巡检命令清单（只读，可直接执行）

```bash
# === 本机 ===
# 资源/内存
top -l 1 -n 0 | head -20
vm_stat | head -10
memory_pressure | tail -3

# 磁盘
df -h
# 各卷用量
df -h / /Volumes/* 2>/dev/null

# Home 目录大户
du -sh ~/* | sort -rh | head -10

# 高内存进程
ps -Ao rss,comm | sort -rn | head -10

# 待更新
softwareupdate -l

# iOS 模拟器占用
xcrun simctl list devices unavailable | head
```

```bash
# === 远程机（经 ssh）===
ssh wj 'top -l 1 -n 0 | head -20; echo "---"; vm_stat | head -10; echo "---"; df -h; echo "---"; du -sh ~/* | sort -rh | head -10; echo "---"; ssh-add -l 2>&1; echo "---"; git config --global --get credential.helper'
```

> 远程机命令一次性覆盖：CPU/内存、磁盘、Home 大户、ssh-agent 状态、git credential 状态——即第二节 4 个 🔴 项的快速复查。
