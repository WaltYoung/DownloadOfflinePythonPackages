# Download Offline Python Packages

本 GitHub Actions 工作流用于在外网下载后**于内网隔离环境**离线安装 Python 依赖包。它会在可联网的 GitHub Runner 上下载您指定的包及其所有依赖，同时打包 `pip`、`setuptools`、`wheel` 以及 `get-pip.py`，并自动生成一键安装脚本。最终产出一个压缩包，您只需将其复制到内网机器并运行脚本即可完成所有安装。

## 🚀 快速开始

### 1. 准备工作
- 将 `.github/workflows/download-offline-packages.yml` 文件推送到您的 GitHub 仓库。
- 确保仓库启用了 Actions（默认开启）。

### 2. 手动触发工作流
1. 进入 GitHub 仓库 → **Actions** 标签页。
2. 在左侧选择 **Download Offline Python Packages** 工作流。
3. 点击 **Run workflow** 按钮，填写以下参数：

| 参数 | 说明 | 示例 |
|------|------|------|
| `python_version` | 与内网机器一致的 Python 主版本 | `3.9` |
| `target_os` | 内网机器的操作系统类型 | `ubuntu-22.04`（Linux）、`windows-latest`、`macos-latest` |
| `packages` | 需要下载的包名，多个用空格分隔 | `pymysql requests` |

4. 点击 **Run workflow** 运行。

### 3. 下载离线包
工作流运行成功后，在 **Artifacts** 区域会生成一个名为 `offline-packages-py<版本>-<操作系统>.zip` 的压缩包。下载该文件。