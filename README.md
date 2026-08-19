# 🪄 千问 (Qwen) 视频图片无水印原图提取器

一款轻量、极速的通义千问（Qwen）无水印媒体提取工具。无需复杂的 AI 运算，直接从分享数据流中提取**无损原图**与**高清原视频**。

[![Chrome Extension](https://img.shields.io/badge/Chrome%20Extension-v1.0-blue?logo=googlechrome&logoColor=white)](https://github.com/Surf565/qianwen-video-image-watermark-remover/releases)
[![Edge Extension](https://img.shields.io/badge/Edge%20Extension-Supported-green?logo=microsoftedge&logoColor=white)](https://github.com/Surf565/qianwen-video-image-watermark-remover/releases)
[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📌 目录
- [功能亮点](#-功能亮点)
- [浏览器插件使用（推荐）](#-一浏览器插件使用推荐)
- [Python 脚本使用](#-二python-版本使用)
- [工作原理](#-工作原理)
- [常见问题 FAQ](#-常见问题-faq)
- [致谢与声明](#-致谢与声明)

---

## ✨ 功能亮点

- ⚡ **真正的 0 损原画质**：绕过前端渲染水印层，直取官方存储的原始高清文件。
- 🎬 **全媒体格式支持**：同时支持通义千问生成的**高清图片**与**完整视频（MP4）**。
- 🧩 **浏览器插件（零门槛）**：一键在千问网页端直接点击下载，无需任何编程基础。
- 🐍 **Python CLI & API**：支持命令行批量解析、下载，支持作为模块嵌入自动化工作流。
- 🔗 **多链接格式兼容**：
  - 活动/外部分享页：`activity.qianwen.com/r/...`
  - 对话分享页：`www.qianwen.com/share/chat/...`

---

## 🧩 一、浏览器插件使用（推荐）

适合绝大多数日常用户，无需安装 Python 环境。

### 1. 下载插件
前往 [Releases 页面](https://github.com/Surf565/qianwen-video-image-watermark-remover/releases) 下载 `qianwen-watermark-remover-extension.zip`，并解压到本地文件夹。

### 2. 加载到浏览器（Chrome / Edge）
1. 打开浏览器扩展管理页面：
   - **Chrome 浏览器**：在地址栏输入 `chrome://extensions/` 回车
   - **Edge 浏览器**：在地址栏输入 `edge://extensions/` 回车
2. 打开页面右上角的 **「开发者模式」** 开关。
3. 点击左上角的 **「加载已解压的扩展程序」** 按钮。
4. 在弹出的窗口中，选择刚刚**解压出来的插件文件夹**。

### 3. 使用方式
在浏览器中打开任意千问分享页面，插件会自动识别并提供下载按钮，点击即可直接下载无水印原图或原视频。

---

## 💻 二、Python 版本使用

适合开发者或需要批量自动下载的用户。

## ⚙️ 工作原理
通义千问在分享媒体资源时，后端接口返回的媒体数据里同时包含「渲染用水印版本」和「原始无水印版本」。本工具直接抓取无水印字段的真实地址：

链接类型	图片无水印字段 ✅	视频无水印字段 ✅	带水印字段（已忽略） 

## ❓ 常见问题 (FAQ)

- **Q: 为什么提取出的直链过了一段时间无法打开？**  
  A: 千问官方链接带有 `auth_key` 鉴权时效参数，具有有效期限制，建议解析后及时下载保存。

- **Q: 下载后的视频需要额外转码吗？**  
  A: 不需要，下载的即为原始标准的 `.mp4` 文件。

- **Q: 遇到解析失败怎么办？**  
  A: 请先检查分享链接是否能在浏览器中正常打开。如果千问官方更新了接口导致失效，请在 GitHub 提交 [Issue](https://github.com/Surf565/qianwen-video-image-watermark-remover/issues) 反馈。

---

## 🤝 致谢与声明
🤝 致谢与声明

核心解析：核心解析逻辑引用自 @hope0719，感谢 @hope0719 提供的通义千问分享接口逆向与解析逻辑。
二次开发：本项目在其解析核心基础上，二次开发并封装了浏览器插件（Chrome/Edge 扩展），方便普通用户免代码一键提取。
免责声明：本项目仅供个人学习与研究使用，请遵守相关服务协议。



## 📄 开源协议

本项目采用 [MIT License](LICENSE) 开源协议。
