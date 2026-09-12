# HelixCraft

**AI 赋能的基因工程辅助桌面软件** · AI powered Gene Engineering Tools, Multi-language

HelixCraft 面向分子克隆与植物基因功能研究，把载体图谱编辑、序列分析、引物设计、酶切模拟、
凝胶电泳分析等工作收进一个桌面应用，并提供克隆工作流、测序峰图分析、物种数据检索与可选的
AI 助手。支持 20 种界面语言。

## 下载

最新版本始终在 [**Releases · latest 频道**](https://github.com/liudab/HelixCraft/releases/tag/latest)：

| 平台 | 安装包 | 安装方式 |
|---|---|---|
| Windows 10 / 11（x64） | `HelixCraft.Setup.<版本>.exe` | 双击运行安装向导 |
| Debian / Ubuntu（x86_64） | `helixcraft_<版本>_amd64.deb` | 双击交给系统图形化安装器，或 `sudo apt install ./<文件>` |

`latest` 频道同时是应用内「检查更新」的数据源，资产随每个版本覆盖式替换。历史版本见
[Releases 列表](https://github.com/liudab/HelixCraft/releases)，每个版本都有独立存档。

### 校验下载

同目录下的 `latest.json` 是应用使用的更新清单，其中列出了每个安装包的文件名、字节数与
SHA-256 摘要，可用于校验下载是否完整、是否被篡改。例如：

```bash
# Linux
sha256sum helixcraft_<版本>_amd64.deb
# Windows PowerShell
Get-FileHash .\HelixCraft.Setup.<版本>.exe -Algorithm SHA256
```

## 安装

### Windows

- 系统要求：Windows 10 及以上（x64）。
- 运行 `HelixCraft.Setup.<版本>.exe`，按向导完成安装（默认为所有用户安装，需管理员权限）。
- **覆盖安装会保留全部既有数据**。数据目录为 `%APPDATA%\HelixCraft`（物种子库位于
  `%APPDATA%\HelixCraftData`），卸载不会删除该目录。

### Linux（Debian / Ubuntu，x86_64）

- 双击 `.deb` 会交由系统的图形化安装器（GNOME Software / App Center / KDE Discover / GDebi）；
  终端等价命令：`sudo apt install ./helixcraft_<版本>_amd64.deb`。
- 程序安装到 `/opt/HelixCraft`，用户数据在 `~/.config/HelixCraft`，**卸载不会删除**。
- 界面以中文为主，建议系统装有 CJK 字体（包内声明 `Recommends: fonts-noto-cjk`；用
  `dpkg -i` 直接安装不会带上依赖，请改用 `apt install`）。
- 依赖按 `libgtk-3-0 | libgtk-3-0t64` 这类「二选一」形式声明，因此 Ubuntu 24.04 起的 t64
  重命名不会导致依赖无法满足。
- 未提供 AppImage。

## 在线更新

应用启动约 20 秒后会在后台检查更新（默认开启，24 小时内最多检查一次，可在设置中关闭）。
发现新版本只提醒、**不会自动下载**；下载全程 HTTPS，支持断点续传与 SHA-256 校验，校验不通过
的安装包会被拒绝。Windows 上安装由 NSIS 向导完成并自动重启；Linux 上则把下载好的 `.deb`
交给系统的软件安装器，若系统无法拉起安装器，界面会给出安装包路径与「在文件夹中显示」。

## 主要功能

- **载体图谱编辑**：环形 / 线性图谱互换，元件增删改、酶切位点、引物、阅读框与序列编辑，
  撤销 / 重做与图谱导出。
- **序列分析**：GenBank / FASTA / AB1 导入，序列比对（含剪接比对）、ORF 预测与翻译、
  蛋白分析、智能标注。
- **引物设计**：常规 PCR、qPCR、测序引物，扩增区 / 跨内含子设计与二聚体 / 发夹评估。
- **酶切与凝胶**：酶切模拟与凝胶预测、真实凝胶图片的三步向导定量分析。
- **克隆工作流**：可搭图的克隆流程工作台，Golden Gate、Gibson、TOPO、BioBrick 等组装策略。
- **物种数据**：随包内置水稻物种注释数据（约 10 万条），并支持按插件接入在线数据源
  （RAP-DB / RiceXPro / Ensembl Plants）。
- **AI 助手（可选）**：接入自己的 API Key 后可用；AI 只是既有功能的另一条调用路径，
  不配置也可完整使用全部功能。

## 界面语言

简体中文、English、日本語、한국어、Français、Deutsch、Español、Português、Русский、Italiano、
العربية、हिन्दी、ไทย、Tiếng Việt、Bahasa Indonesia、Türkçe、Nederlands、Polski、Svenska、Čeština。

## 关于本仓库

本仓库仅用于**分发安装包与在线更新清单**，不包含源代码。其中 `latest` 标签的 Release 是在线
更新频道（资产随版本覆盖式替换），`v<版本>` 标签的 Release 是历史版本存档。

## 许可证

[MIT](LICENSE)

## 联系

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn

---

## English

HelixCraft is an AI-assisted desktop application for gene engineering and molecular cloning:
vector map editing, sequence analysis, primer design, restriction digestion simulation and gel
electrophoresis analysis, plus cloning workflows, Sanger chromatogram analysis, species data
lookup and an optional AI assistant. The interface is available in 20 languages.

**Download** the latest version from the
[`latest` release channel](https://github.com/liudab/HelixCraft/releases/tag/latest):

| Platform | Installer | How to install |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Run the installer wizard |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Double-click, or `sudo apt install ./<file>` |

The update manifest `latest.json` in the same release lists each installer's file name, size and
SHA-256 digest for verification. On Linux the app installs to `/opt/HelixCraft` and keeps user data
in `~/.config/HelixCraft` (uninstalling does not remove it). On Windows the data directory is
`%APPDATA%\HelixCraft`, also preserved across uninstalls. Older releases are archived under their
own version tags.

This repository hosts **installers and the online update manifest only** — it does not contain
the application source code.

Licensed under the [MIT License](LICENSE).
