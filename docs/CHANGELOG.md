# 更新日志 / Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

---

### [2.0.0] - 2026-04-08

#### ⚡ Breaking Changes
- **Tools merged from 6 to 3**: `lanhu_design` (replaces list_designs + analyze_designs + get_slices), `lanhu_page` (replaces list_pages + analyze_pages), `lanhu_resolve_invite` (unchanged)
- Design analysis now uses `mode` parameter instead of separate tools
- Default output no longer includes base64 images (use `include: ["image"]` to opt in)

#### ✨ Added
- **Structured Design Tokens**: Extracts all colors, fonts, shadows, borders, border radii — sorted by usage frequency
- **Artboard format support**: Correctly reads `text.style.font` path for font extraction in artboard-format Sketch JSON
- **Concurrent processing**: Multiple designs analyzed in parallel (5 concurrent) with automatic retry
- **MCP Resources**: `project-designs` resource template for design list discovery
- **MCP Prompts**: `frontend-dev` and `design-review` built-in prompt templates
- **Output control**: `include` parameter in analyze mode for selective output (html, image, tokens, layout, layers, slices)

#### 🐛 Fixed
- Font data missing from artboard-format Sketch JSON (was reading wrong path `textStyle.font` instead of `text.style.font`)
- Layer coordinates all zero in artboard format (was reading `frame.x/y` instead of `frame.left/top`)
- Invalid color values (containing `undefined`/`NaN`) no longer appear in design tokens

---

## Version History

### [1.4.0] - 2026-03-26

#### Changed
- 文档与配置示例持续同步（README、元数据、格式整理）

### [1.1.0] - 2026-02-27

#### 设计图分析能力升级（Design Analysis）
- **设计图分析能力质的提升**
  - 分析设计图时可获取**详细设计参数**：组件尺寸、间距、颜色值、字体大小等精确数值，便于还原设计
  - **设计图转代码**：自动将蓝湖设计 Schema 转为 HTML+CSS，与蓝湖原生导出效果对齐，AI 可直接参考实现
  - 支持按**序号**（如 `6` 表示第 6 个）或**完整名称**（如 `6_friend页_挂件墙`）指定要分析的设计图
  - 返回结果中图片与代码一一对应，便于 AI 关联视觉与实现
- 新增依赖：htmlmin（HTML 压缩）

### [1.0.0] - 2025-12-17

#### 🎉 首次发布

首个开源版本，包含核心功能：
- ✅ Axure 原型分析
- ✅ UI 设计图查看
- ✅ 切图导出
- ✅ 设计层级结构树

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for details on how to contribute to this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

<!-- Last checked: 2026-03-31 08:56 -->
