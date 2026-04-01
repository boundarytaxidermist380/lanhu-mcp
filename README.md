<div align="center">

# Lanhu MCP Server

**让 AI 编程工具直接读取蓝湖设计稿和需求文档**

[![npm](https://img.shields.io/npm/v/mcp-lanhu)](https://www.npmjs.com/package/mcp-lanhu)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Node.js 20+](https://img.shields.io/badge/node-20+-339933.svg)](https://nodejs.org/)

</div>

---

## 一句话介绍

把蓝湖链接丢给 AI，它就能看到设计稿的完整 HTML+CSS、层级结构、Design Tokens、需求文档——不再截图粘贴。

支持 Cursor / Windsurf / Claude Code 等所有 MCP 兼容客户端。

---

## 快速开始

### 1. 获取蓝湖 Cookie

登录 [蓝湖网页版](https://lanhuapp.com) → F12 打开开发者工具 → Network → 复制任意请求的 `Cookie` 请求头。

### 2. 配置 AI 客户端

在 Cursor 的 `.cursor/mcp.json`（或对应客户端的 MCP 配置文件）中添加：

```json
{
  "mcpServers": {
    "lanhu": {
      "command": "npx",
      "args": ["-y", "mcp-lanhu"],
      "env": {
        "LANHU_COOKIE": "你的蓝湖Cookie"
      }
    }
  }
}
```

重启客户端即可使用，无需 clone 代码。

### 3. 开始使用

直接在对话中发送蓝湖链接：

```
帮我分析这个设计稿：https://lanhuapp.com/web/#/item/project/stage?tid=xxx&pid=xxx
```

```
分析这个需求文档：https://lanhuapp.com/web/#/item/project/product?tid=xxx&pid=xxx&docId=xxx
```

---

## 功能

| 工具 | 说明 |
|------|------|
| `lanhu_list_designs` | 列出项目所有设计图 |
| `lanhu_analyze_designs` | 分析设计图，返回 HTML+CSS + Design Tokens + 层级树 |
| `lanhu_get_slices` | 获取设计图切图/图标资源 |
| `lanhu_list_pages` | 列出 PRD/原型页面 |
| `lanhu_analyze_pages` | 分析原型页面（开发/测试/探索三种视角） |
| `lanhu_resolve_invite_link` | 解析蓝湖邀请链接 |

---

## 本地开发

```bash
git clone https://github.com/MrDgbot/lanhu-mcp.git
cd lanhu-mcp
npm install
cp config.example.env .env   # 填入 LANHU_COOKIE
npm run dev                   # 启动开发模式
```

本地 MCP 配置（直接运行 TS，免 build）：

```json
{
  "mcpServers": {
    "lanhu": {
      "command": "npx",
      "args": ["tsx", "src/server.ts"],
      "cwd": "/path/to/lanhu-mcp",
      "env": {
        "LANHU_COOKIE": "你的Cookie"
      }
    }
  }
}
```

> 修改源码后需在客户端中重启 MCP 服务，新代码才会生效。

```bash
npm run check   # 类型检查
npm test        # 运行测试
npm run build   # 编译
```

---

## 环境变量

| 变量 | 说明 | 必需 |
|------|------|------|
| `LANHU_COOKIE` | 蓝湖网页版 Cookie | 是 |
| `DDS_COOKIE` | DDS Cookie（默认同 LANHU_COOKIE） | 否 |

---

## 许可证

[MIT](LICENSE)
