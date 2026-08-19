<div align="center">

# 🪄 千问 (Qwen) 视频图片无水印原图提取器
### Qianwen Video & Image Watermark Remover

一款轻量、极速的通义千问（Qwen）无水印媒体提取工具。  
无需复杂的 AI 运算，直接从分享数据流中提取**无损原图**与**高清原视频**。

[![Chrome Extension](https://img.shields.io/badge/Chrome%20Extension-v1.0-blue?logo=googlechrome&logoColor=white)](https://github.com/Surf565/qianwen-video-image-watermark-remover/releases)
[![Edge Extension](https://img.shields.io/badge/Edge%20Extension-Supported-green?logo=microsoftedge&logoColor=white)](https://github.com/Surf565/qianwen-video-image-watermark-remover/releases)
[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Stars](https://img.shields.io/github/stars/Surf565/qianwen-video-image-watermark-remover?style=social)](https://github.com/Surf565/qianwen-video-image-watermark-remover)

[🚀 浏览器插件安装](#-一浏览器插件使用推荐) • [💻 Python 命令行/代码调用](#-二python-版本使用) • [⚙️ 工作原理](#-工作原理) • [❓ 常见问题](#-常见问题-faq)

</div>

---

## ✨ 功能亮点

- ⚡ **真正的 0 损原画质**：绕过前端渲染水印层，直取官方存储的原始文件。
- 🎬 **全媒体格式支持**：同时支持通义千问生成的**高清图片**与**完整视频（MP4）**。
- 🧩 **浏览器插件（零门槛）**：一键在千问网页端直接点击下载，无需任何编程基础。
- 🐍 **Python CLI & API**：支持命令行批量解析、下载，支持作为模块嵌入自动化工作流。
- 🔗 **多链接格式兼容**：
  - 活动/外部分享页：`activity.qianwen.com/r/...`
  - 对话分享页：`www.qianwen.com/share/chat/...`

---

## 📸 效果演示

<!-- 提示：上传一张插件使用界面或前后对比图到 GitHub Issues/仓库，将下面的图片链接替换为您自己的图片 -->
> | 带水印预览（官方页面） | 提取出的无水印原图/原视频 |
> | :---: | :---: |
> | *(网页端右下角带有官方水印)* | *(原始分辨率、无任何水印遮挡)* |

---

## 🧩 一、浏览器插件使用（推荐）

适合绝大多数日常用户，无需安装 Python。

### 1. 下载插件
前往 [Releases 页面](https://github.com/Surf565/qianwen-video-image-watermark-remover/releases) 下载最新的 `qianwen-watermark-remover-extension.zip`，并解压到本地文件夹。

### 2. 加载到浏览器（以 Chrome / Edge 为例）
1. 打开浏览器扩展管理页：
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. 打开右上角的 **「开发者模式」 (Developer mode)**。
3. 点击左上角的 **「加载已解压的扩展程序」 (Load unpacked)**。
4. 选择刚刚解压出来的插件文件夹即可。

### 3. 使用方式
- 打开任意通义千问分享链接，插件将自动检测媒体资源，并在页面提供一键下载无水印文件按钮。

---

## 💻 二、Python 版本使用

适合开发者、批量下载需求或 Linux/服务器环境。

### 1. 安装环境

```bash
# 克隆本仓库
git clone https://github.com/Surf565/qianwen-video-image-watermark-remover.git
cd qianwen-video-image-watermark-remover

# 安装唯一轻量依赖
pip install -r qianwen_watermark_remover/requirements.txt
