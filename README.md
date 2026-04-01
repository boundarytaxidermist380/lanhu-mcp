<div align="center">

# Lanhu MCP Server

让 AI 直接读取蓝湖设计稿和需求文档

[![npm](https://img.shields.io/npm/v/mcp-lanhu)](https://www.npmjs.com/package/mcp-lanhu)
[![MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

## 使用

1. 登录 [蓝湖](https://lanhuapp.com)，F12 复制 Cookie
2. 添加到 `.cursor/mcp.json`：

```json
{
  "mcpServers": {
    "lanhu": {
      "command": "npx",
      "args": ["-y", "mcp-lanhu"],
      "env": { "LANHU_COOKIE": "你的Cookie" }
    }
  }
}
```

3. 重启客户端，对话中发蓝湖链接即可

## 功能

| 工具 | 说明 |
|------|------|
| `lanhu_analyze_designs` | 设计图 → HTML+CSS + Design Tokens |
| `lanhu_analyze_pages` | PRD/原型 → 结构化分析 |
| `lanhu_list_designs` / `lanhu_list_pages` | 列出设计图/页面 |
| `lanhu_get_slices` | 提取切图资源 |
| `lanhu_resolve_invite_link` | 解析邀请链接 |

## 开发

```bash
git clone https://github.com/MrDgbot/lanhu-mcp.git && cd lanhu-mcp
npm install && cp config.example.env .env  # 填 LANHU_COOKIE
npm run dev
```

[MIT](LICENSE)
