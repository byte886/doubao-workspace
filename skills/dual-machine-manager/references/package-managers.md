# 包管理工具深度盘点

> 最后更新：2026-09-15
> 数据来源：双机深度盘点报告（2026-09-15 实际命令采集）。
> 本机 `cw` = chenwenjie @ 192.168.2.8；远程机 `wj` = wenjiechen @ 192.168.2.9（黑苹果，无 Homebrew）。

---

## 一、全量对比总表

| 包管理器 | 本机 cw | 远程机 wj | 差异要点 |
|---|---|---|---|
| **Homebrew** | ✅ 7.0.1-5-g66413cb，prefix `/usr/local`，**206 formulae + 10 casks** | ❌ 未安装（黑苹果） | 最大能力差距来源 |
| **npm** | ⚠️ 10.9.8，**仅在 Doubao sandbox 内**，全局仅 corepack+npm | ❌ 无 | 系统级两台都没有 |
| **pip3** | ⚠️ 26.2.1 / Python 3.14（sandbox 内），仅 pip 一包；另有 brew 安装的 python@3.10~3.14 | ✅ 21.2.4 / Python 3.9（Xcode 自带框架） | 远程机 Python 版本旧且固定 |
| **gem** | ✅ 3.6.3，`/usr/local/opt/ruby/bin/gem`，89 个 gem（多为 ruby 默认自带） | ✅ 3.0.3.1（系统自带） | 远程机 gem 版本旧 |
| **cargo / rustup** | ✅ cargo 1.81.0，rustup 管 **12 个 toolchain**，默认 1.81 | ✅ cargo 1.70.0，rustup 管 **9 个 toolchain**，默认 1.70 | 两台都用 rustup 多版本 |
| **mise**（版本管理） | ✅ `~/.local/bin/mise`，管 node/java/maven/gradle | ❌ 无 | 仅本机 |
| **nvm** | ❌ 无（已改用 mise） | ❌ 无 | — |
| **pnpm** | ✅ mise shim | ❌ 无 | 仅本机 |
| **yarn** | ✅ `/usr/local/bin/yarn`（brew） | ❌ 无 | 仅本机 |
| **go** | ✅ `~/go/bin/go` | ❌ 无 | 仅本机 |
| **java** | ✅ mise temurin-17.0.20 | ✅ `/usr/bin/java`（系统自带） | 来源不同 |
| **maven** | ✅ mise 3.9.16 | ❌ 无 | 仅本机 |
| **gradle** | ✅ mise 8.1.1 | ❌ 无 | 仅本机 |

---

## 二、各包管理器详情

### 2.1 Homebrew（本机独有）

- **版本/路径**：7.0.1-5-g66413cb，prefix `/usr/local`（Intel Mac 默认路径）。
- **规模**：206 formulae + 10 casks。
- **是否系统自带**：否，手动安装。
- **用途定位**：本机命令行工具链与 GUI 应用的统一入口。

#### formulae 分类摘要（206 个，按用途归类）

| 分类 | 关键包（节选） |
|---|---|
| **开发工具链** | cmake, gcc, llvm, ninja, meson, make, autoconf, automake, pkg-config, swig, lld, tree-sitter, emacs, ripgrep (rg), fzf, jq, wget, curl, netcat, nmap, tmux, tmuxinator, screen, watch, tree, hugo |
| **运行时/语言** | python@3.10~3.14（5 个版本）, ruby, lua, openjdk, pyenv, uv, yarn |
| **网络/服务** | nginx, postgresql@14, mysql, docker, docker-completion, autossh, tailscale 相关 |
| **媒体处理** | ffmpeg 全套（x264/x265/svt-av1/dav1d/libvpx/libvmaf/opus/lame/webp）, HandBrake 依赖 |
| **加密货币相关** | bitcoin, bfgminer, electrum, ord, parity, sui, rocksdb, leveldb, zeromq, libsodium, libusb |
| **其他** | gh, gita, tldr, nexttrace, displayplacer, trzsz-ssh, trzsz-go, miniupnpc, gnutls |

#### casks（10 个）

`cc-switch`, `chromedriver`, `electrum`, `font-fira-code`, `keycastr`, `rustdesk`, `stretchly`, `tailscale-app`, `temurin`, `wechattweak-cli`

### 2.2 npm（sandbox 隔离，非系统级）

- **现状**：本机 npm 10.9.8 位于 Doubao sandbox 运行时内（`.../sandbox_runtime/bases/.../bin/npm`），**系统级 shell 中没有 npm**。
- **全局包**：仅 corepack + npm 两个。
- **含义**：需要在终端全局安装 node CLI 工具时，不能依赖 `npm i -g`；node 运行时与 pnpm 实际由 **mise** 提供（见 2.6）。
- **远程机**：完全无 npm。

### 2.3 pip3 / Python

- **本机**：sandbox 内 pip 26.2.1（Python 3.14）；系统级另有 brew 安装的 python@3.10~3.14 共 5 个版本。
- **远程机**：pip 21.2.4 / Python 3.9，来自 Xcode 自带框架，**版本旧且无法用 brew 升级**。

### 2.4 gem

- **本机**：3.6.3，`/usr/local/opt/ruby/bin/gem`（brew ruby），89 个 gem，绝大多数为 ruby 默认自带。
- **远程机**：3.0.3.1，系统自带。

### 2.5 cargo / rustup（两台都有）

| 项目 | 本机 cw | 远程机 wj |
|---|---|---|
| cargo | 1.81.0 | 1.70.0 |
| rustup toolchain 数 | 12 个 | 9 个 |
| 默认 toolchain | 1.81 | 1.70 |
| 含旧版本 | 1.63/1.66/1.67/1.75/1.76/1.79/1.80/1.81 + stable/nightly | 1.67/1.75/1.76/1.79/1.80 等 |

两台均通过 rustup 手动管理多 toolchain，**这是远程机唯一较完整的语言工具链**。

### 2.6 mise（本机版本管理器）

- **路径**：`~/.local/bin/mise`
- **管理对象**：
  - node 23.11.1（pnpm 为其 shim）
  - java temurin-17.0.20
  - maven 3.9.16
  - gradle 8.1.1
- **作用**：替代 nvm/jenv 等单一语言管理器，统一管理 node/java/maven/gradle 版本，是本机「无系统级 npm」问题的实际解法。
- **远程机**：未安装。

---

## 三、远程机无 Homebrew 的影响与应对

### 影响

远程机命令行工具安装能力极弱：仅靠 Xcode 自带 Python 3.9 + 系统 gem 3.0.3.1 + 手动安装的 rustup。装新工具没有统一入口。

### 应对方案（按需选择）

1. **继续不装 Homebrew（当前策略，推荐）**：远程机定位为精简编译/提交机，原则上不引入新命令行工具；确需用到的工具尽量在本机装好后通过代码/产物交付。
2. **临时安装单个工具**：从官方 Releases 下载预编译二进制，放入 `~/.local/bin/` 或 `~/bin/`（远程机 powerwebhook 即用此方式放脚本）。
3. **手动编译**：`./configure && make && make install` 到 `~/local/`，不污染系统目录。
4. **如确实需要 Homebrew**（不推荐，破坏「精简机」定位）：
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
   安装前先确认这是否符合远程机角色定位。

---

## 四、包管理一致性维护建议

1. **远程机刻意保持「无 Homebrew」**，不要为图方便在远程机 brew install，避免破坏精简机定位。
2. **本机新工具优先走 Homebrew**（`brew install`），装完在 `references/package-managers.md` 记录关键包。
3. **node/java 相关以 mise 为准**，不再引入 nvm/jenv，避免多套版本管理器并存。
4. **cargo toolchain 保持双机兼容**：跨机编译的 Rust 项目，默认 toolchain 版本差距较大（1.81 vs 1.70），涉及固定版本的项目用 `rust-toolchain.toml` 锁定，不依赖机器默认。
5. **Python 注意版本**：远程机只有 3.9，脚本不要用 3.10+ 专属语法。
