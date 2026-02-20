# AionUI CSS Theme Generator

专门为 AionUI 设计的 CSS 主题生成技能。根据风格描述或背景图片，自动生成完整的 AionUI 主题 CSS 代码。

## 功能特性

- 🎨 **智能配色**：从图片自动提取主色调，或根据风格描述生成配色方案
- 🌓 **双模式支持**：同时生成浅色和深色两套完整样式
- 📦 **即用即走**：生成约 700 行完整 CSS，复制粘贴即可使用
- 🖼️ **背景图支持**：可基于上传的图片生成主题，自动调整组件透明度
- 📐 **规范兼容**：严格遵循 AionUI 的变量命名和组件结构

## 安装方法

1. 将 `css-theme-generator` 文件夹复制到你的 AionUI skills 目录：
   ```bash
   cp -r css-theme-generator ~/.aionui-config/skills/
   ```

2. 重启 AionUI，skill 会自动加载

## 使用方法

### 方式一：基于图片生成主题

```
"帮我根据这张图片生成一个主题"
"用 @/path/to/image.jpg 做个主题"
"根据背景图生成一个黑神话悟空风格的主题"
```

### 方式二：基于风格描述生成主题

```
"帮我生成一个赛博朋克风格的主题"
"做一个清新自然的主题"
"生成一个暗黑哥特风格的 CSS"
```

## 依赖要求

### 必需
- **Python 3**：用于保存 CSS 文件（确保 UTF-8 BOM 编码）

### 可选
- **图像分析工具**：如果需要从图片提取颜色，需要以下任一工具：
  - `mcp__4_5v_mcp__analyze_image`
  - `mcp__zai-mcp-server__analyze_image`
  - 其他支持图像分析的 MCP 工具

## 输出说明

生成的 CSS 文件会保存到：
```
~/Desktop/aion-theme-[style].css
```

例如：`aion-theme-cyberpunk.css`、`aion-theme-black-myth.css`

## 使用步骤

### 1. 生成主题

在 AionUI 中触发 skill（见上面的"使用方法"）

### 2. 获取 CSS 文件

从桌面上找到生成的 `.css` 文件

### 3. 应用到 AionUI

**重要**：如果是带背景图的主题，请按以下顺序操作：

1. **先粘贴 CSS**：打开 AionUI → 设置 → 主题 → 自定义 CSS，粘贴 CSS 代码
2. **再上传图片**：在主题设置中上传背景图片

**原因**：AionUI 会将上传图片的 base64 数据注入到 CSS 中。如果顺序错了会导致背景图无法显示。

## 技术细节

### 参考文档

- `references/css-template.md` - 完整的 AionUI CSS 模板结构
- `references/color-theory.md` - 色彩推导方法论

### 生成的 CSS 包含

- ✅ 完整的 CSS 变量系统（颜色、间距、圆角等）
- ✅ 浅色模式（`:root`）和深色模式（`[data-theme='dark']`）
- ✅ 所有 AionUI 组件样式（侧边栏、消息气泡、按钮、输入框等）
- ✅ 滚动条、Tooltip、Modal 等细节样式
- ✅ 响应式和打印样式

### 编码说明

生成的 CSS 文件使用 **UTF-8 BOM 编码**，避免中文注释乱码。

## 常见问题

**Q: 为什么背景图不显示？**
A: 请确保按正确顺序操作：先粘贴 CSS，再上传图片。如果还是不行，重启 AionUI 后重试。

**Q: 生成的 CSS 有中文乱码？**
A: 确保使用 Python 的 `utf-8-sig` 编码保存文件。skill 已自动处理这个问题。

**Q: 可以自定义颜色吗？**
A: 可以。生成的 CSS 是标准文本文件，你可以手动修改任何颜色值。

## 许可证

MIT License

## 贡献

欢迎提交 Issue 和 Pull Request！
