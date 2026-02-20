---
name: css-theme-generator
description: 专门为 AionUI 生成自定义 CSS 主题的技能。支持根据风格描述（如“赛博朋克”、“清新自然”、“暗黑哥特”）或背景图片生成完整的配色方案。Triggers: "帮我生成主题", "做一个主题", "换个配色", "生成CSS", "theme", "配色方案", "用这张图做主题", "根据背景图生成", "generate theme", "create css theme".
---

# CSS Theme Generator (AionUI 主题生成器)

这是一个专门为 AionUI 设计的 CSS 主题生成技能。它能根据用户的文字描述或上传的背景图片，自动推导出一整套符合 AionUI 规范的 CSS 变量和组件样式。

## Overview (概览)

AionUI 支持通过粘贴自定义 CSS 来改变整个界面的外观。本技能通过分析用户的审美偏好或图片色调，生成约 700 行的完整 CSS 代码，并将其保存为 `.css` 文件。

## Workflow (工作流)

### Step 1: Understand User Request (理解需求)
识别用户的核心需求：
- **风格关键词**：如“极简主义”、“复古未来”、“二次元”等。
- **背景图片**：如果用户上传了图片，需优先分析图片色调。
- **模式偏好**：是否需要同时支持浅色 (Light) 和深色 (Dark) 模式（默认两者都生成）。

### Step 2: Color Palette Analysis (色彩分析)
- **有背景图时**：使用可用的图像分析工具分析图片的主导色。从最显著的非中性色中提取 `primary` 颜色，并确保文字在背景图上的可读性。
  
  **分析重点**：
  1. Primary color - 最显著的非中性色
  2. Accent color - 次要强调色
  3. Overall atmosphere/mood - 整体氛围
  4. 具体的 hex 颜色值

- **无背景图时**：根据风格描述推导配色方案（参考 `references/color-theory.md` 中的风格映射表）。

### Step 3: Variable Derivation (变量推导)
基于主色调推导全套 AionUI 变量（包括 `--bg-1`, `--text-primary`, `--accent` 等）。
- 详细的推导逻辑请参考 `references/color-theory.md`。

### Step 4: CSS Generation (生成代码)
使用 AionUI 标准模板填充变量和样式。
- 完整的 CSS 模板结构请参考 `references/css-template.md`。
- 注意：AionUI 的 `customCssProcessor` 会自动为所有属性添加 `!important`，生成时无需手动添加。

### Step 5: Save and Present (保存与交付)
将生成的 CSS 代码写入本地 `.css` 文件，并向用户提供文件路径。

**重要**：保存 CSS 文件时**必须使用 Python**，以确保 UTF-8 BOM 编码，避免中文注释乱码：

```python
# 保存 CSS 文件（必须使用此方法）
css_content = """...生成的 CSS 代码..."""
file_path = "/Users/changfenhuang/Desktop/aion-theme-[style].css"

# 用 UTF-8 BOM 编码保存（避免中文乱码）
with open(file_path, 'w', encoding='utf-8-sig') as f:
    f.write(css_content)
```

**不要使用** `mcp__acp__Write` 或 `Write` 工具，因为它们可能导致中文编码问题。

## Background Image Handling (背景图处理)

当用户提供背景图时：
1. 提取图片主色作为主题基调。
2. 在生成的 CSS 末尾包含背景图相关的样式块（设置 `body` 或特定容器的 `background-image`）。
3. 调整 UI 组件的透明度和模糊度 (backdrop-filter)，确保内容在复杂背景下依然清晰。

如果没有提供背景图，则跳过背景图相关的 CSS 块，仅生成纯色或渐变背景的主题。

## Important Notes (重要提示)

- **兼容性**：生成的 CSS 必须严格遵循 AionUI 的变量命名规范。
- **双模式**：默认同时生成浅色（`:root`）和深色（`[data-theme='dark']`）两套完整样式。AionUI 使用 `data-theme` 属性切换明暗模式，不使用 `prefers-color-scheme` 媒体查询。
- **参考文档**：
  - 完整 CSS 模板结构：`references/css-template.md`
  - 色彩推导方法论：`references/color-theory.md`

## Output Format (输出格式)

1. **保存 CSS 文件**：将生成的 CSS 保存为 `~/Desktop/aion-theme-[style].css`（例如 `aion-theme-cyberpunk.css`），**必须使用 UTF-8 BOM 编码**以避免中文注释乱码。
2. **说明配色设计**：向用户简要说明配色设计思路（3-5 句话，说明选了什么主色、为什么、整体风格感受）。
3. **提供使用说明**：告知文件路径，并提供明确的使用步骤：

### 重要：背景图主题的正确使用顺序

如果用户提供了背景图或生成带背景图的主题，**必须**按以下顺序操作：

1. **先粘贴 CSS 代码**：打开 AionUI → 设置 → 主题 → 自定义 CSS，粘贴生成的 CSS 内容
2. **再上传背景图片**：在主题设置中上传背景图片

**原因**：AionUI 会将上传图片的 base64 数据注入到 CSS 中的 `url("")` 位置。如果先上传图片再粘贴 CSS，会导致背景图无法显示。

提醒用户：如果粘贴 CSS 后背景图不显示，请重启 AionUI 并按上述顺序重新操作。

## 注意事项 (Caveats)

- AionUI 的 `customCssProcessor` 会自动为 CSS 添加 `!important`，因此生成的 CSS 中**不要手动添加** `!important`。
- 背景图的 URL 通常是 base64 data URL，由 AionUI 自动处理。如果用户提供了图片但未转换为 base64，在 CSS 中使用空字符串 `url("")`，并提醒用户在 AionUI 的主题设置中手动上传背景图。
- CSS 中的所有颜色值应使用 hex 格式（`#rrggbb`），需要透明度时使用 `rgba()` 格式。
