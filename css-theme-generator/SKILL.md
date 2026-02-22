---
name: css-theme-generator
description: 专门为 AionUI 生成自定义 CSS 主题的技能。支持根据风格描述（如“赛博朋克”、“清新自然”、“暗黑哥特”）生成完整的配色方案。Triggers: "帮我生成主题", "做一个主题", "换个配色", "生成CSS", "theme", "配色方案", "generate theme", "create css theme".
---

# CSS Theme Generator (AionUI 主题生成器)

这是一个专门为 AionUI 设计的 CSS 主题生成技能。它能根据用户的文字描述或上传的背景图片，自动推导出一整套符合 AionUI 规范的 CSS 变量和组件样式。

## Overview (概览)

AionUI 支持通过粘贴自定义 CSS 来改变整个界面的外观。本技能通过分析用户的审美偏好或图片色调，生成约 700 行的完整 CSS 代码，并将其保存为 `.css` 文件。

## Workflow (工作流)

### Step 1: Understand User Request (理解需求)
识别用户的核心需求：
- **风格关键词**：如“赛博朋克”、“清新自然”、“暗黑哥特”、“复古未来”等。
- **背景图片**：如果用户上传了图片，仅用于提取配色灵感。
- **模式偏好**：是否需要同时支持浅色 (Light) 和深色 (Dark) 模式（默认两者都生成）。

### Step 2: Color Palette Analysis (色彩分析)
- **有背景图时**：使用可用的图像分析工具分析图片的主导色。从最显著的非中性色中提取 `primary` 颜色。

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
- **不要在 CSS 中写任何背景图相关的代码**。

### Step 5: Save and Present (保存与交付)
将生成的 CSS 代码写入本地 `.css` 文件，并向用户提供文件路径。

**重要**：确保 CSS 文件使用 UTF-8 编码，并在文件开头包含 `@charset "UTF-8";` 声明（css-template.md 模板已包含此声明）。

**推荐保存方式**（Python）：
```python
import os
css_content = """...生成的 CSS 代码..."""
file_path = os.path.expanduser("~/Desktop/aion-theme-[style].css")

# 用 UTF-8 编码保存
with open(file_path, 'w', encoding='utf-8') as f:
    f.write(css_content)
```

**也可以使用 Write 工具**，只要确保 CSS 文件第一行是 `@charset "UTF-8";` 即可避免中文乱码。

---

## 背景图处理（重要！）

**本 skill 只生成配色 CSS，不处理背景图。**

**原因**：AionUI 的背景图需要在主题设置中手动上传。当用户在 AionUI 主题编辑器中上传图片时，AionUI 会**自动在 CSS 末尾追加**一个完整的背景图样式块（使用 `/* AionUi Theme Background Start */` 标记）。

**使用方法**：
1. 用本 skill 生成配色 CSS
2. 在 AionUI 主题设置中上传背景图（设置 → 主题 → 选择/创建主题 → 上传背景图）

这样配色和背景图分开处理，更加灵活。

---

## Important Notes (重要提示)

- **编码问题**：生成的 CSS 文件必须使用 **UTF-8 编码**，并在文件开头包含 `@charset "UTF-8";` 声明，避免中文注释乱码。
- **兼容性**：生成的 CSS 必须严格遵循 AionUI 的变量命名规范。
- **双模式**：默认同时生成浅色（`:root`）和深色（`[data-theme='dark']`）两套完整样式。AionUI 使用 `data-theme` 属性切换明暗模式，不使用 `prefers-color-scheme` 媒体查询。
- **背景图**：本 skill 不处理背景图，用户需要在 AionUI 主题设置中手动上传。
- **参考文档**：
  - 完整 CSS 模板结构：`references/css-template.md`
  - 色彩推导方法论：`references/color-theory.md`

## Output Format (输出格式)

1. **保存 CSS 文件**：将生成的 CSS 保存为 `~/Desktop/aion-theme-[style].css`（例如 `aion-theme-cyberpunk.css`），确保 UTF-8 编码。
2. **说明配色设计**：向用户简要说明配色设计思路（3-5 句话，说明选了什么主色、为什么、整体风格感受）。
3. **提供使用说明**：告知文件路径，提醒用户：
   - 打开 AionUI → 设置 → 主题 → 自定义 CSS → 粘贴内容
   - 如需背景图，在主题设置中单独上传

## 注意事项 (Caveats)

- AionUI 的 `customCssProcessor` 会自动为 CSS 添加 `!important`，因此生成的 CSS 中**不要手动添加** `!important`。
- **背景图**：本 skill 不处理背景图，请用户在 AionUI 主题设置中手动上传。
- CSS 中的所有颜色值应使用 hex 格式（`#rrggbb`），需要透明度时使用 `rgba()` 格式。
