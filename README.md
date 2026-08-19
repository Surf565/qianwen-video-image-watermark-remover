markdown


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
- ⚡ **真正的 0 损原画质**：绕过前端渲染水印层，直取官方存储的原始高清文件。
- 🎬 **全媒体格式支持**：同时支持通义千问生成的**高清图片**与**完整视频（MP4）**。
- 🧩 **浏览器插件（零门槛）**：一键在千问网页端直接点击下载，无需任何编程基础。
- 🐍 **Python CLI & API**：支持命令行批量解析、下载，支持作为模块嵌入自动化工作流。
- 🔗 **多链接格式兼容**：
  - 活动/外部分享页：`activity.qianwen.com/r/...`
  - 对话分享页：`www.qianwen.com/share/chat/...`
---
## 📸 效果演示
> | 带水印预览（官方页面） | 提取出的无水印原图/原视频 |
> | :---: | :---: |
> | *(网页端右下角带有官方水印)* | *(原始分辨率、无任何水印遮挡)* |
---
## 🧩 一、浏览器插件使用（推荐）
适合绝大多数日常用户，无需安装 Python。
### 1. 下载插件
前往 [Releases 页面](https://github.com/Surf565/qianwen-video-image-watermark-remover/releases) 下载最新的 `qianwen-watermark-remover-extension.zip`，并解压到电脑本地文件夹中。
### 2. 加载到浏览器（以 Chrome / Edge 为例）
1. 打开浏览器扩展管理页：
   - **Chrome 浏览器**：在地址栏输入 `chrome://extensions/` 回车
   - **Edge 浏览器**：在地址栏输入 `edge://extensions/` 回车
2. 打开页面右上角的 **「开发者模式」 (Developer mode)** 开关。
3. 点击左上角的 **「加载已解压的扩展程序」 (Load unpacked)**。
4. 在弹出的文件窗口中，**选择刚刚解压出来的插件文件夹**即可。
### 3. 使用方式
- 在浏览器中打开任意通义千问分享链接，插件会自动提取无水印资源，并在页面上提供一键下载按钮。
---
## 💻 二、Python 版本使用
适合开发者、批量自动化下载或 Linux/服务器环境。
### 1. 安装环境
```bash
# 克隆本仓库
git clone https://github.com/Surf565/qianwen-video-image-watermark-remover.git
cd qianwen-video-image-watermark-remover
# 安装依赖
pip install -r qianwen_watermark_remover/requirements.txt
2. 命令行 (CLI) 快速下载
bash


python qianwen_watermark_remover/run.py "<千问分享链接>" [可选: 保存目录]
示例：

bash


# 1. 解析活动分享链接（图片/视频）
python qianwen_watermark_remover/run.py "https://activity.qianwen.com/r/ai-studio-mobile/qwen-external-share?shareId=xxx"
# 2. 解析对话分享链接并保存到指定目录
python qianwen_watermark_remover/run.py "https://www.qianwen.com/share/chat/abc123xxx" ./my_downloads
3. 作为 Python 模块引入
python


import asyncio
from qianwen_watermark_remover import parse_qianwen, download_media
async def main():
    share_url = "https://activity.qianwen.com/r/ai-studio-mobile/qwen-external-share?shareId=xxx"
    
    # 异步解析分享内容
    result = await parse_qianwen(share_url)
    print(f"标题: {result.get('title')}")
    print(f"解析到图片: {len(result.get('images', []))} 张, 视频: {len(result.get('videos', []))} 个")
    # 打印无水印直链
    for img in result.get("images", []):
        print(f"原图 URL: {img['url']}")
    # 下载全部无水印资源到本地
    download_media(result, output_dir="./output")
if __name__ == "__main__":
    asyncio.run(main())
⚙️ 工作原理
通义千问在生成与分享媒体资源时，后端接口返回的媒体数据里同时包含「渲染带水印版本」和「原始无水印版本」。本工具直接抓取无水印字段的真实地址：

链接类型	图片无水印字段 ✅	视频无水印字段 ✅	带水印字段（已忽略） ❌
Activity 活动分享页	images[].url	playInfo.url	images[].downloadUrl / playInfo.downloadUrl
Chat 对话分享页	display_list[].image	display_list[].video	watermark_image / download_video
❓ 常见问题 (FAQ)
Q1: 为什么提取出的无水印链接过了一段时间失效了？
Q2: 下载后的视频需要额外转码吗？
Q3: 遇到解析失败怎么办？
🤝 致谢与声明 (Credits & Disclaimer)
核心解析逻辑引用自 @hope0719。
免责声明：本项目仅供个人学习、技术研究与多媒体提取测试使用。使用本工具时请遵守通义千问平台相关服务协议，严禁用于任何侵权或商业违规行为。
📄 开源协议
本项目采用 
MIT License
 开源协议。

