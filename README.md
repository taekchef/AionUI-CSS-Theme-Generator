# AionUI CSS Theme Generator

> 专门为 AionUI 设计的 CSS 主题生成技能
> 根据风格描述或背景图片，自动生成完整的 AionUI 主题 CSS 代码

---

## ✨ 功能亮点

| 功能 | 说明 |
|:---|:---|
| 🎨 **智能配色** | 从图片自动提取主色调，或根据"赛博朋克"、"清新自然"等风格描述生成配色方案 |
| 🌓 **双模式支持** | 同时生成浅色和深色两套完整样式 |
| 📦 **即用即走** | 生成约 700 行完整 CSS，复制粘贴即可使用 |
| 🖼️ **背景图支持** | 在 AionUI 主题设置中上传背景图，自动适配 |
| 🧠 **智能决策** | 快速判断单色/双色、圆角大小、特殊效果，并可选询问细节偏好 |
| 🔄 **迭代调整** | 支持"再红一点"、"再亮一点"等量化调整 |
| 📚 **高级技巧** | 支持毛玻璃、霓虹发光、像素边框等特殊效果 |
| 📐 **规范兼容** | 严格遵循 AionUI 的变量命名和组件结构 |

## 安装方法

在终端运行以下命令：

**macOS / Linux:**
```bash
git clone https://github.com/taekchef/aionui-css-theme-generator.git /tmp/css-theme-gen && \
cp -r /tmp/css-theme-gen/css-theme-generator ~/.aionui-config/skills/ && \
rm -rf /tmp/css-theme-gen
```

**Windows:**
```powershell
git clone https://github.com/taekchef/aionui-css-theme-generator.git %TEMP%\css-theme-gen
xcopy /E /I "%TEMP%\css-theme-gen\css-theme-generator" "%USERPROFILE%\.aionui-config\skills\"
rmdir /s /q "%TEMP%\css-theme-gen"
```

安装完成后，你可以选择以下两种使用方式：

---

### 方式 A：直接使用 Skill（需要触发关键词）

在任意对话中，使用以下关键词触发 skill：

```
"帮我生成主题"
"做一个赛博朋克风格的主题"
"用这张图生成主题"
```

**特点**：
- ✅ 快速上手，无需额外配置
- ❌ 需要记住触发关键词
- ❌ 每次都需要明确说明需求

---

### 方式 B：创建专用助手（推荐 ⭐）

创建一个专门的"主题设计师"助手，让对话更自然：

**📌 步骤 1：在 AionUI 中创建新助手**
- 打开 AionUI → **助手管理** → **创建助手**
- 助手名称：`主题设计师`
- 助手描述：`专门生成 AionUI CSS 主题`

**📌 步骤 2：配置助手规则（重要！）**

助手规则文件位置：`theme-designer-assistant-rule.md`

**获取方式：**
- GitHub 在线查看：点击仓库中的 `theme-designer-assistant-rule.md` 文件
- 本地查看：如果你已克隆本仓库，文件在根目录下

**操作方法：**
1. 打开 `theme-designer-assistant-rule.md` 文件
2. **复制全部内容**（Ctrl+A / Cmd+A，然后 Ctrl+C / Cmd+C）
3. 粘贴到助手的"规则"输入框中

**📌 步骤 3：关联 Skill**
- 在助手的技能配置中，勾选 ✅ `css-theme-generator`

**📌 步骤 4：开始使用**
- 切换到"主题设计师"助手
- 直接说："帮我生成一个赛博朋克风格的主题"
- 或上传图片说："根据这张图片生成主题"

**✨ 特点：**
- ✅ 对话更自然，无需特定关键词
- ✅ 助手始终专注于主题生成
- ✅ 更符合日常使用习惯

---

**总结**：两种方式都依赖同一个 skill，方式 B 是在方式 A 的基础上创建了专门的对话入口，使用体验更流畅。

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

### 推荐
- **Python 3**（可选）：用于保存 CSS 文件，确保 UTF-8 编码。也可以使用其他工具，只要确保 CSS 文件是 UTF-8 编码即可。

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

1. **打开主题设置**：AionUI → 设置 → 主题
2. **添加主题**：点击"添加"或选择现有主题
3. **粘贴 CSS**：在自定义 CSS 输入框中粘贴生成的 CSS 代码
4. **上传背景图**（可选）：在主题设置中上传背景图片

**注意**：如果需要背景图，先粘贴 CSS，再上传图片。

## 技术细节

### 参考文档

- `SKILL.md` - Skill 定义和工作流程
- `theme-designer-assistant-rule.md` - 助手规则文件（用于创建专用助手）
- `references/css-template.md` - 完整的 AionUI CSS 模板结构
- `references/color-theory.md` - 色彩推导方法论

### 生成的 CSS 包含

- ✅ 完整的 CSS 变量系统（颜色、间距、圆角等）
- ✅ 浅色模式（`:root`）和深色模式（`[data-theme='dark']`）
- ✅ 所有 AionUI 组件样式（侧边栏、消息气泡、按钮、输入框等）
- ✅ 滚动条、Tooltip、Modal 等细节样式
- ✅ 响应式和打印样式

### 编码说明

生成的 CSS 文件使用 **UTF-8 编码**，并在文件开头包含 `@charset "UTF-8";` 声明，确保中文注释正常显示。

## 常见问题

**Q: 为什么背景图不显示？**
A: 请确保按正确顺序操作：先粘贴 CSS，再上传图片。如果还是不行，重启 AionUI 后重试。

**Q: 生成的 CSS 有中文乱码？**
A: 生成的 CSS 文件已包含 `@charset "UTF-8";` 声明，确保 UTF-8 编码即可正常显示。

**Q: 可以自定义颜色吗？**
A: 可以。生成的 CSS 是标准文本文件，你可以手动修改任何颜色值。

## 许可证

MIT License

## 贡献

欢迎提交 Issue 和 Pull Request！
