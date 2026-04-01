<div align="center">

# 🎨 Lanhu MCP Server

**The official MCP server for [Lanhu (蓝湖)](https://lanhuapp.com) — Bridge AI coding assistants with your design system**

[![npm version](https://img.shields.io/npm/v/mcp-lanhu)](https://www.npmjs.com/package/mcp-lanhu)
[![npm downloads](https://img.shields.io/npm/dm/mcp-lanhu)](https://www.npmjs.com/package/mcp-lanhu)
[![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/node-%3E%3D20-brightgreen)](https://nodejs.org)

[English](#overview) · [中文](#概述)

</div>

---

## Overview

**Lanhu MCP Server** (`mcp-lanhu`) is a [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) server that connects AI coding assistants — such as **Cursor**, **Windsurf**, **Claude Desktop**, and **Claude Code** — directly to your [Lanhu (蓝湖)](https://lanhuapp.com) design projects. It enables AI to **read design specs, extract HTML/CSS, parse PRD documents, and download image assets** without leaving the editor.

> **One command, zero config** — just `npx -y mcp-lanhu` and paste your Lanhu link in chat.

### Why Lanhu MCP?

- **Design-to-code in seconds**: AI reads your Lanhu design and generates pixel-accurate HTML + CSS, complete with design tokens (colors, fonts, shadows, gradients).
- **PRD-aware coding**: Feed your product requirements document (PRD) or Axure prototype to AI for context-aware implementation.
- **Asset pipeline**: Extract slices, icons, and images directly from Lanhu — no manual export needed.
- **Works with any MCP client**: Cursor, Windsurf, Claude Desktop, Claude Code, and any future MCP-compatible IDE.
- **Stdio transport**: Standard MCP stdio protocol — lightweight, fast, and universally compatible.

---

## 概述

**Lanhu MCP Server**（`mcp-lanhu`）是一个 [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) 服务器，让 **Cursor、Windsurf、Claude Desktop、Claude Code** 等 AI 编程助手直接连接你的蓝湖设计项目。AI 可以**读取设计稿、提取 HTML/CSS、解析需求文档（PRD）、下载切图资源**，全程无需离开编辑器。

> **一行命令，零配置** — 只需 `npx -y mcp-lanhu`，在对话中粘贴蓝湖链接即可使用。

### 为什么选择 Lanhu MCP？

- **设计稿秒变代码**：AI 读取蓝湖设计稿，生成像素级精准的 HTML + CSS，包含完整的 Design Tokens（颜色、字体、阴影、渐变）。
- **需求文档驱动开发**：将 PRD 或 Axure 原型交给 AI，实现需求感知的智能编码。
- **自动化资源管线**：直接从蓝湖提取切图、图标和图片，无需手动导出。
- **兼容所有 MCP 客户端**：Cursor、Windsurf、Claude Desktop、Claude Code，以及任何未来的 MCP 兼容 IDE。
- **Stdio 传输协议**：标准 MCP stdio 协议，轻量、高效、通用兼容。

---

## 安装 / Quick Start

无需 clone 代码，直接在 AI 客户端配置中使用 `npx` 自动安装运行。

### Cursor / Windsurf

编辑 `.cursor/mcp.json`（或 `.windsurf/mcp.json`）：

```json
{
  "mcpServers": {
    "lanhu": {
      "command": "npx",
      "args": ["-y", "mcp-lanhu"],
      "env": { "LANHU_COOKIE": "your_cookie_here" }
    }
  }
}
```

### Claude Desktop

编辑 `claude_desktop_config.json`：

```json
{
  "mcpServers": {
    "lanhu": {
      "command": "npx",
      "args": ["-y", "mcp-lanhu"],
      "env": { "LANHU_COOKIE": "your_cookie_here" }
    }
  }
}
```

### Claude Code

```bash
claude mcp add lanhu -- npx -y mcp-lanhu
```

然后在环境变量或 `.env` 文件中设置 `LANHU_COOKIE`。

### 本地开发 / Local Development

```json
{
  "mcpServers": {
    "lanhu": {
      "command": "node",
      "args": [
        "--env-file=/absolute/path/to/lanhu-mcp/.env",
        "/absolute/path/to/lanhu-mcp/dist/server.js"
      ],
      "cwd": "/absolute/path/to/lanhu-mcp"
    }
  }
}
```

先执行 `npm run build` 生成 `dist/`。可选配置项（日志级别、超时等）见 `config.example.env`。

### 获取 Cookie

1. 登录 [蓝湖](https://lanhuapp.com)
2. 打开浏览器开发者工具（F12）→ Network 标签
3. 复制任意请求的 `Cookie` 请求头

配置完成后重启客户端，在对话中粘贴蓝湖链接即可使用。

---

## Tools / 工具一览

| Tool | Description | 说明 |
|------|-------------|------|
| `lanhu_analyze_designs` | Design → HTML + CSS + Design Tokens | 设计图 → HTML+CSS + 设计令牌 |
| `lanhu_analyze_pages` | PRD / Axure → Structured analysis | PRD/原型 → 结构化分析 |
| `lanhu_list_designs` | List all design images in a project | 列出项目设计图 |
| `lanhu_list_pages` | List all pages in a PRD document | 列出 PRD 页面 |
| `lanhu_get_slices` | Extract icon & image assets (slices) | 提取切图资源 |
| `lanhu_resolve_invite_link` | Resolve Lanhu invite/share links | 解析蓝湖邀请链接 |

---

## Use Cases / 使用场景

- **Frontend development**: Paste a Lanhu design link → AI generates responsive components matching the design spec.
- **前端开发**：粘贴蓝湖设计链接 → AI 生成与设计稿匹配的响应式组件。
- **Design QA**: Compare implementation against design tokens (spacing, colors, typography).
- **设计走查**：对比实现与设计令牌（间距、颜色、字体）。
- **PRD implementation**: Feed PRD pages to AI for requirement-aware feature development.
- **需求实现**：将 PRD 页面交给 AI，实现需求驱动的功能开发。
- **Asset export**: Batch-extract icons and images without opening Lanhu manually.
- **资源导出**：批量提取图标和图片，无需手动打开蓝湖。

---

## Compatibility / 兼容性

| MCP Client | Supported | Transport |
|------------|-----------|-----------|
| Cursor | ✅ | stdio |
| Windsurf | ✅ | stdio |
| Claude Desktop | ✅ | stdio |
| Claude Code | ✅ | stdio |
| Any MCP-compatible IDE | ✅ | stdio |

---

## 开发 / Development

```bash
git clone https://github.com/MrDgbot/lanhu-mcp.git && cd lanhu-mcp
npm install && cp config.example.env .env  # 填入 LANHU_COOKIE
npm run dev    # 开发模式（热重载）
npm run build  # 构建生产版本
npm test       # 运行测试
```

---

## 常见问题 / FAQ

**Q: 什么是 MCP？/ What is MCP?**
A: [Model Context Protocol](https://modelcontextprotocol.io/) 是一个开放标准，让 AI 助手安全连接外部数据源和工具。

**Q: 支持哪些蓝湖套餐？/ Which Lanhu plans are supported?**
A: 任何可以网页访问的蓝湖账号均可使用，服务器通过浏览器 Cookie 认证。

**Q: 支持 SSE/HTTP 传输吗？/ Does it work with SSE/HTTP transport?**
A: 目前仅支持 stdio，SSE 支持已在计划中。

**Q: 不用 Cursor 也能用吗？/ Can I use it without Cursor?**
A: 可以 — 支持所有 MCP 客户端，包括 Claude Desktop、Claude Code、Windsurf 等。

---

## License

[MIT](LICENSE) © [MrDgbot](https://github.com/MrDgbot)
