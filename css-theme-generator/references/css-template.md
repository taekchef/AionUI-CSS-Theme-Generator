# CSS 模板使用说明

本模板是 AionUI 主题生成器的核心参考。所有颜色使用 `{{PLACEHOLDER}}` 占位符，AI 生成主题时逐一替换为实际色值。

- 模板涵盖明色 (`:root`) 和暗色 (`[data-theme='dark']`) 两套完整样式
- `{{BG_IMAGE_URL}}` 替换为背景图 Base64 data URL，无背景图时留空
- AionUI 的 customCssProcessor 会自动添加 `!important`，模板中无需手动添加（部分特殊覆盖场景除外）
- 所有选择器保持与 AionUI 组件结构一致，不可修改
- 额外占位符说明：`{{ACCENT_RGB}}` 是强调色的 R,G,B 数值（如 `0, 163, 0`），`{{BG_1_RGB}}` / `{{D_BG_2_RGB}}` 是对应背景色的 RGB 数值，用于 `rgba()` 场景

## 占位符清单

| 占位符 | 说明 | 示例 |
| :--- | :--- | :--- |
| `{{THEME_NAME}}` | 主题名称 | Cyberpunk Neon |
| `{{THEME_STYLE_DESCRIPTION}}` | 风格描述 | 赛博朋克霓虹配色 |
| `{{FONT_FAMILY}}` | 字体族 | "Segoe UI", "Microsoft YaHei", sans-serif |
| `{{PRIMARY}}` | 主色 | #0078d4 |
| `{{PRIMARY_LIGHT_1/2/3}}` | 主色浅化 1-3 阶 | #1a86d9 / #3399e6 / #4da6f0 |
| `{{PRIMARY_DARK_1}}` | 主色深 1 阶 | #005a9e |
| `{{PRIMARY_RGB}}` | 主色 RGB（无#） | 0, 120, 212 |
| `{{BRAND}}`/`{{BRAND_LIGHT}}`/`{{BRAND_HOVER}}` | 品牌色系 | #0078d4 / #e6f2fa / #1a86d9 |
| `{{AOU_1}}` ~ `{{AOU_10}}` | 10 阶品牌色板 | 从最浅到最深 |
| `{{BG_1}}` ~ `{{BG_4}}` | 层级背景色 | #f0f0f0 / #ffffff / #e0e0e0 / #c0c0c0 |
| `{{BG_BASE}}`/`{{BG_HOVER}}`/`{{BG_ACTIVE}}`/`{{FILL}}` | 功能背景色 | |
| `{{TEXT_1}}`/`{{TEXT_2}}`/`{{TEXT_3}}`/`{{TEXT_0}}` | 文字色层级 | #000000 / #404040 / #808080 / #000000 |
| `{{BORDER_1}}`/`{{BORDER_2}}` | 边框色 | #808080 / #c0c0c0 |
| `{{SUCCESS}}`/`{{WARNING}}`/`{{DANGER}}`/`{{INFO}}` | 语义色 | |
| `{{ACCENT}}`/`{{ACCENT_LIGHT}}`/`{{ACCENT_DARK}}` | 强调色 | |
| `{{ACCENT_RGB}}` | 强调色 RGB 数值 | 0, 163, 0 |
| `{{MSG_USER_BG}}`/`{{MSG_TIPS_BG}}`/`{{WORKSPACE_BTN_BG}}` | 组件色 | |
| `{{DIALOG_FILL}}` | 对话框背景 rgba | rgba(255,255,255,0.95) |
| `{{SIDEBAR_BG}}` | 侧边栏背景 | #e0e0e0 |
| `{{SIDEBAR_HEADER_FROM}}`/`{{SIDEBAR_HEADER_TO}}` | 侧边栏头渐变 | |
| `{{OVERLAY_LIGHT_1/2/3}}` | 浅色遮罩 rgba | rgba(240,249,255,0.75) |
| `{{TOOLTIP_BG}}` | Tooltip 背景色 | #ffffe1 |
| `{{BORDER_RADIUS}}` | 圆角 | 4px 或 12px |
| `{{SCROLLBAR_WIDTH}}` | 滚动条宽度 | 16px 或 8px |
| `{{BG_1_RGB}}`/`{{D_BG_2_RGB}}` | 背景色 RGB 数值 | 240, 240, 240 |
| 所有 `{{D_...}}` | 暗色模式变量 | 同上加 D_ 前缀 |
| `{{D_OVERLAY_DARK_1/2/3}}` | 暗色遮罩 rgba | rgba(26,42,58,0.7) |
| `{{D_TOOLTIP_BG}}` | 暗色 Tooltip 背景 | rgba(45,45,45,0.98) |
| `{{D_ACCENT_RGB}}` | 暗色强调色 RGB | 76, 175, 80 |
| `{{BG_IMAGE_URL}}` | 背景图 data URL 或空 | |

---

## CSS 模板

```css
@charset "UTF-8";
/* ========================================
   {{THEME_NAME}} - AionUI Theme
   {{THEME_STYLE_DESCRIPTION}}
   支持明暗双模式
   ======================================== */

/* ==================== 明色模式 (Light Mode) ==================== */
/* 核心颜色变量 */
:root {
  /* 主色调 */
  --color-primary: {{PRIMARY}};
  --primary: {{PRIMARY}};
  --color-primary-light-1: {{PRIMARY_LIGHT_1}};
  --color-primary-light-2: {{PRIMARY_LIGHT_2}};
  --color-primary-light-3: {{PRIMARY_LIGHT_3}};
  --color-primary-dark-1: {{PRIMARY_DARK_1}};
  --primary-rgb: {{PRIMARY_RGB}};

  /* 品牌色 */
  --brand: {{BRAND}};
  --brand-light: {{BRAND_LIGHT}};
  --brand-hover: {{BRAND_HOVER}};
  --color-brand-fill: {{PRIMARY}};
  --color-brand-bg: {{BRAND_LIGHT}};

  /* AOU 品牌色板 */
  --aou-1: {{AOU_1}};
  --aou-2: {{AOU_2}};
  --aou-3: {{AOU_3}};
  --aou-4: {{AOU_4}};
  --aou-5: {{AOU_5}};
  --aou-6: {{AOU_6}};
  --aou-7: {{AOU_7}};
  --aou-8: {{AOU_8}};
  --aou-9: {{AOU_9}};
  --aou-10: {{AOU_10}};

  /* 背景色 */
  --color-bg-1: {{BG_1}};
  --bg-1: {{BG_1}};
  --color-bg-2: {{BG_2}};
  --bg-2: {{BG_2}};
  --color-bg-3: {{BG_3}};
  --bg-3: {{BG_3}};
  --color-bg-4: {{BG_4}};
  --bg-4: {{BG_4}};
  --bg-base: {{BG_BASE}};
  --bg-hover: {{BG_HOVER}};
  --bg-active: {{BG_ACTIVE}};
  --fill: {{FILL}};
  --color-fill: {{FILL}};

  /* 文字色 */
  --color-text-1: {{TEXT_1}};
  --text-primary: {{TEXT_1}};
  --color-text-2: {{TEXT_2}};
  --text-secondary: {{TEXT_2}};
  --color-text-3: {{TEXT_3}};
  --text-disabled: {{TEXT_3}};
  --text-0: {{TEXT_0}};

  /* 边框色 */
  --color-border: {{BORDER_1}};
  --color-border-1: {{BORDER_1}};
  --color-border-2: {{BORDER_2}};
  --border-base: {{BORDER_1}};
  --border-light: {{BORDER_2}};

  /* 语义色 */
  --success: {{SUCCESS}};
  --warning: {{WARNING}};
  --danger: {{DANGER}};
  --info: {{INFO}};

  /* 主题强调色 */
  --accent: {{ACCENT}};
  --accent-light: {{ACCENT_LIGHT}};
  --accent-dark: {{ACCENT_DARK}};

  /* 消息背景色 */
  --message-user-bg: {{MSG_USER_BG}};
  --message-tips-bg: {{MSG_TIPS_BG}};
  --workspace-btn-bg: {{WORKSPACE_BTN_BG}};

  /* 对话框颜色 */
  --dialog-fill-0: {{DIALOG_FILL}};
}

/* 全局字体 */
body {
  font-family: {{FONT_FAMILY}};
}

/* 全局背景色 */
body,
html {
  background-color: var(--bg-1, {{BG_1}});
}

.arco-layout,
[class*="layout"] {
  background-color: var(--bg-1, {{BG_1}});
}

.arco-layout-content {
  background-color: var(--bg-1, {{BG_1}});
}

/* ==================== 侧边栏 Sidebar ==================== */
.layout-sider {
  background-color: {{SIDEBAR_BG}};
  border-right: 2px solid {{BORDER_1}};
  position: relative;
  z-index: 100;
}

.layout-sider.collapsed {
  overflow: hidden;
}

.layout-sider.collapsed * {
  overflow: hidden;
}

.layout-sider.collapsed::-webkit-scrollbar {
  display: none !important;
  width: 0 !important;
  height: 0 !important;
}

.layout-sider-header {
  background: linear-gradient(180deg, {{SIDEBAR_HEADER_FROM}} 0%, {{SIDEBAR_HEADER_TO}} 100%);
  color: white;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.3), 0 1px 2px rgba(0, 0, 0, 0.2);
}

/* ==================== 背景图设置 ==================== */
.layout-content.bg-1 {
  background-color: var(--bg-1, {{BG_1}});
  position: relative;
}

.layout-content.bg-1::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    {{OVERLAY_LIGHT_1}} 0%,
    {{OVERLAY_LIGHT_2}} 50%,
    {{OVERLAY_LIGHT_3}} 100%
  );
  z-index: 0;
  pointer-events: none;
}

.chat-layout-header,
[class*="chat-layout"] .arco-layout-content,
[class*="conversation"] .arco-layout-content {
  position: relative;
}

[class*="chat-layout"] .arco-layout-content::before,
[class*="conversation"] .arco-layout-content::before {
  content: "";
  position: absolute;
  inset: 0;
  background: transparent;
  opacity: 0;
  z-index: 0;
  pointer-events: none;
}

[class*="chat-layout"] .arco-layout-content > *,
[class*="conversation"] .arco-layout-content > * {
  position: relative;
  z-index: 1;
}

.layout-content.bg-1 > * {
  position: relative;
  z-index: 1;
}

.guidLayout,
[class*="guid"] {
  position: relative;
  z-index: 10;
}

.guidInputCard textarea,
[class*="guidInputCard"] textarea {
  background-color: rgba(255, 255, 255, 0.98);
  color: var(--color-text-1);
}

/* ==================== 输入框 Input ==================== */
.sendbox-container:not([class*="model"]):not([class*="Model"]),
[class*="sendbox"]:not([class*="input"]):not([class*="textarea"]):not([class*="model"]):not([class*="Model"]):not([class*="tools"]) {
  border-radius: {{BORDER_RADIUS}};
  border: 2px outset {{BORDER_2}};
  background-color: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(4px);
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.8), inset -1px -1px 0 rgba(0, 0, 0, 0.1), 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: all 0.2s ease;
}

.guidInputCard {
  background-color: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(4px);
  border: 2px outset {{BORDER_2}};
  border-radius: {{BORDER_RADIUS}};
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.8), inset -1px -1px 0 rgba(0, 0, 0, 0.1), 0 2px 4px rgba(0, 0, 0, 0.1);
}

.sendbox-container textarea,
[class*="sendbox"] textarea {
  border: none;
  background: transparent;
  color: var(--color-text-1);
}

.sendbox-container:focus-within,
[class*="sendbox"]:focus-within {
  border: 2px inset {{BORDER_1}};
  box-shadow: inset 2px 2px 4px rgba(0, 0, 0, 0.2);
}

.sendbox-container svg:not(.sendbox-model-btn svg):not([class*="model"] svg),
[class*="sendbox"]:not([class*="model"]):not([class*="Model"]) svg:not(.sendbox-model-btn svg) {
  color: {{PRIMARY}};
  transition: color 0.3s ease;
}

.sendbox-container svg:not(.sendbox-model-btn svg):not([class*="model"] svg):hover,
[class*="sendbox"]:not([class*="model"]):not([class*="Model"]) svg:not(.sendbox-model-btn svg):hover {
  color: {{PRIMARY_LIGHT_1}};
  transform: scale(1.1);
}

/* ==================== 消息气泡 Message ==================== */
.message-item.user .message-bubble,
[class*="message"][class*="user"] .message-content {
  background: linear-gradient(180deg, {{PRIMARY}} 0%, {{PRIMARY_DARK_1}} 100%);
  color: white;
  border-radius: {{BORDER_RADIUS}};
  border: 1px solid {{PRIMARY_DARK_1}};
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.3), 0 2px 4px rgba(0, 0, 0, 0.2);
  padding: 12px 16px;
}

.message-item.ai .message-bubble,
[class*="message"][class*="ai"] .message-content,
[class*="message"][class*="assistant"] .message-content {
  background-color: rgba(255, 255, 255, 0.98);
  backdrop-filter: blur(4px);
  border: 1px solid {{BORDER_2}};
  border-radius: {{BORDER_RADIUS}};
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.8), inset -1px -1px 0 rgba(0, 0, 0, 0.1), 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 12px 16px;
  color: var(--color-text-1);
}

.message-item.ai .arco-alert,
[class*="message"][class*="ai"] .arco-alert,
[class*="message"][class*="assistant"] .arco-alert,
.message-item.ai [class*="alert"],
[class*="message"][class*="ai"] [class*="alert"],
[class*="message"][class*="assistant"] [class*="alert"] {
  background-color: rgba(255, 255, 255, 0.9);
  border: 1px solid {{BORDER_2}};
  border-radius: {{BORDER_RADIUS}};
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.8), inset -1px -1px 0 rgba(0, 0, 0, 0.1);
  backdrop-filter: none;
  margin: 4px 0;
  color: var(--color-text-1);
}

.message-item.ai .arco-card,
[class*="message"][class*="ai"] .arco-card,
[class*="message"][class*="assistant"] .arco-card,
.message-item.ai [class*="card"],
[class*="message"][class*="ai"] [class*="card"],
[class*="message"][class*="assistant"] [class*="card"] {
  background-color: rgba(255, 255, 255, 0.9);
  border: 1px solid {{BORDER_2}};
  border-radius: {{BORDER_RADIUS}};
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.8), inset -1px -1px 0 rgba(0, 0, 0, 0.1);
  backdrop-filter: none;
  margin: 4px 0;
  color: var(--color-text-1);
}

.message-item.ai [class*="tool"]:not([class*="message"]):not([class*="bubble"]),
[class*="message"][class*="ai"] [class*="tool"]:not([class*="message"]):not([class*="bubble"]),
.message-item.ai [class*="Tool"]:not([class*="message"]):not([class*="bubble"]),
[class*="message"][class*="ai"] [class*="Tool"]:not([class*="message"]):not([class*="bubble"]),
.message-item.ai [class*="WebFetch"],
[class*="message"][class*="ai"] [class*="WebFetch"],
.message-item.ai [class*="web_search"],
[class*="message"][class*="ai"] [class*="web_search"],
.message-item.ai [class*="exec_command"],
[class*="message"][class*="ai"] [class*="exec_command"],
.message-item.ai [class*="mcp_tool"],
[class*="message"][class*="ai"] [class*="mcp_tool"] {
  background-color: transparent;
  border: none;
  border-radius: 0;
  padding: 0;
  margin: 0;
}

.message-item.ai [class*="status"]:not([class*="message"]):not([class*="bubble"]),
[class*="message"][class*="ai"] [class*="status"]:not([class*="message"]):not([class*="bubble"]),
.message-item.ai [class*="Status"]:not([class*="message"]):not([class*="bubble"]),
[class*="message"][class*="ai"] [class*="Status"]:not([class*="message"]):not([class*="bubble"]) {
  background-color: rgba(255, 255, 255, 0.95);
  border: 1px solid {{BORDER_2}};
  border-radius: {{BORDER_RADIUS}};
  padding: 2px 6px;
  color: var(--color-text-1);
}

/* ==================== 按钮 Button ==================== */
.arco-btn-primary:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]),
button[type="primary"]:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]) {
  background: linear-gradient(180deg, {{PRIMARY}} 0%, {{PRIMARY_DARK_1}} 100%);
  border: 2px outset {{PRIMARY}};
  border-radius: {{BORDER_RADIUS}};
  font-weight: normal;
  color: white;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.3), 0 2px 4px rgba(0, 0, 0, 0.2);
  transition: all 0.2s ease;
}

.arco-btn-primary:hover:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]),
button[type="primary"]:hover:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]) {
  background: linear-gradient(180deg, {{PRIMARY_LIGHT_1}} 0%, {{PRIMARY}} 100%);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.4), 0 3px 6px rgba(0, 0, 0, 0.3);
}

.arco-btn-primary:active:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]),
button[type="primary"]:active:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]) {
  border: 2px inset {{PRIMARY_DARK_1}};
  box-shadow: inset 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.arco-btn-success,
button[type="success"] {
  background: linear-gradient(180deg, {{ACCENT}} 0%, {{ACCENT_DARK}} 100%);
  border: 2px outset {{ACCENT}};
  border-radius: {{BORDER_RADIUS}};
  color: white;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.3), 0 2px 4px rgba(0, 0, 0, 0.2);
  transition: all 0.2s ease;
}

.arco-btn-success:hover,
button[type="success"]:hover {
  background: linear-gradient(180deg, {{ACCENT_LIGHT}} 0%, {{ACCENT}} 100%);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.4), 0 3px 6px rgba(0, 0, 0, 0.3);
}

.arco-btn-success:active,
button[type="success"]:active {
  border: 2px inset {{ACCENT_DARK}};
  box-shadow: inset 2px 2px 4px rgba(0, 0, 0, 0.3);
}

/* 强调色点缀 */
.arco-alert[class*="success"],
[class*="alert"][class*="success"],
.arco-message-success,
[class*="message"][class*="success"] {
  background-color: rgba({{ACCENT_RGB}}, 0.1);
  border: 1px solid {{ACCENT}};
  border-left: 3px solid {{ACCENT}};
}

a:not([class*="button"]):not([class*="btn"])[class*="success"],
a:not([class*="button"]):not([class*="btn"])[class*="confirm"] {
  color: {{ACCENT}};
}

a:not([class*="button"]):not([class*="btn"])[class*="success"]:hover,
a:not([class*="button"]):not([class*="btn"])[class*="confirm"]:hover {
  color: {{ACCENT_LIGHT}};
  text-decoration: underline;
}

.arco-checkbox-checked .arco-checkbox-icon,
input[type="checkbox"]:checked {
  background-color: {{ACCENT}};
  border-color: {{ACCENT}};
}

.arco-checkbox-checked .arco-checkbox-icon::after {
  border-color: white;
}

.arco-radio-checked .arco-radio-button,
input[type="radio"]:checked {
  border-color: {{ACCENT}};
}

.arco-radio-checked .arco-radio-button::after {
  background-color: {{ACCENT}};
}

.arco-progress-line[class*="success"],
.arco-progress-line[data-status="success"] {
  background-color: rgba({{ACCENT_RGB}}, 0.1);
}

.arco-progress-line[class*="success"] .arco-progress-line-inner,
.arco-progress-line[data-status="success"] .arco-progress-line-inner {
  background-color: {{ACCENT}};
}

.arco-tag[class*="success"],
.arco-tag[data-color="green"] {
  background-color: rgba({{ACCENT_RGB}}, 0.1);
  border-color: {{ACCENT}};
  color: {{ACCENT}};
}

/* 排除模型选择按钮 */
.sendbox-model-btn,
[class*="sendbox-model"],
.sendbox-model-btn *,
[class*="sendbox-model"] * {
  color: inherit;
  fill: inherit;
  background: inherit;
  border: inherit;
  border-radius: inherit;
  box-shadow: inherit;
  transform: none;
}

.sendbox-tools,
[class*="sendbox-tools"],
.sendbox-tools *,
[class*="sendbox-tools"] * {
  color: inherit;
  fill: inherit;
  background: inherit;
  border: inherit;
  border-radius: inherit;
  box-shadow: inherit;
  transform: none;
}

/* ==================== 滚动条 Scrollbar ==================== */
::-webkit-scrollbar {
  width: {{SCROLLBAR_WIDTH}};
  height: {{SCROLLBAR_WIDTH}};
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(180deg, {{BG_4}} 0%, {{BORDER_1}} 100%);
  border: 1px solid {{BORDER_1}};
  border-radius: 0;
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.5), inset -1px -1px 0 rgba(0, 0, 0, 0.2);
  transition: background 0.2s ease;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(180deg, {{BG_HOVER}} 0%, {{BG_4}} 100%);
}

*:hover::-webkit-scrollbar-thumb {
  background: linear-gradient(180deg, {{BG_4}} 0%, {{BORDER_1}} 100%);
}

*:hover::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(180deg, {{BG_HOVER}} 0%, {{BG_4}} 100%);
}

::-webkit-scrollbar-track {
  background: {{BG_1}};
  border: 1px solid {{BORDER_1}};
  border-radius: 0;
  box-shadow: inset 1px 1px 0 rgba(0, 0, 0, 0.1);
}

::-webkit-scrollbar-button {
  background: {{BG_4}};
  border: 1px solid {{BORDER_1}};
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.5), inset -1px -1px 0 rgba(0, 0, 0, 0.2);
}

::-webkit-scrollbar-button:hover {
  background: {{BG_HOVER}};
}

/* ==================== 其他元素 ==================== */
::selection {
  background-color: {{PRIMARY}};
  color: white;
}

a:not([class*="button"]):not([class*="btn"]) {
  color: {{PRIMARY}};
  transition: color 0.2s ease;
}

a:hover:not([class*="button"]):not([class*="btn"]) {
  color: {{PRIMARY_DARK_1}};
  text-decoration: underline;
}

.arco-btn-secondary:not(.sendbox-model-btn):not([class*="model"]):not([class*="Model"]) svg,
button[type="secondary"]:not(.sendbox-model-btn):not([class*="model"]):not([class*="Model"]) svg {
  color: {{PRIMARY}};
  transition: color 0.2s ease;
}

.arco-btn-secondary:not(.sendbox-model-btn):not([class*="model"]):not([class*="Model"]) svg:hover,
button[type="secondary"]:not(.sendbox-model-btn):not([class*="model"]):not([class*="Model"]) svg:hover {
  color: {{PRIMARY_LIGHT_1}};
}

.message-item .message-content svg,
[class*="message"] [class*="content"] svg {
  color: {{TEXT_2}};
  transition: color 0.2s ease;
}

.message-item:hover .message-content svg,
[class*="message"]:hover [class*="content"] svg {
  color: {{PRIMARY}};
}

/* ==================== Tooltip 和 Popover ==================== */
.arco-tooltip-popup,
.arco-popover-popup {
  pointer-events: none;
  z-index: 10000 !important;
}

.arco-tooltip-inner,
.arco-popover-inner,
.arco-popover-content {
  background-color: {{TOOLTIP_BG}} !important;
  color: {{TEXT_1}} !important;
  border: 1px solid {{BORDER_1}} !important;
  border-radius: 0 !important;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3) !important;
  backdrop-filter: none !important;
  padding: 4px 8px !important;
  font-size: 12px !important;
  line-height: 1.4 !important;
  max-width: 200px !important;
  word-wrap: break-word !important;
}

.arco-tooltip-inner *,
.arco-popover-inner *,
.arco-popover-content * {
  color: {{TEXT_1}} !important;
  background-color: transparent !important;
}

.arco-tooltip-arrow,
.arco-popover-arrow {
  border-color: {{BORDER_1}} !important;
}

.layout-sider ~ .arco-tooltip-popup,
.layout-sider .arco-tooltip-popup {
  z-index: 10001 !important;
}

/* ==================== 对话框 Modal ==================== */
.arco-modal-body {
  background-color: rgba({{BG_1_RGB}}, 0.98);
  backdrop-filter: blur(4px);
  border: 2px outset {{BORDER_2}};
  color: var(--color-text-1);
}

.arco-modal-header {
  background: linear-gradient(180deg, {{SIDEBAR_HEADER_FROM}} 0%, {{SIDEBAR_HEADER_TO}} 100%);
  color: white;
  border-bottom: 1px solid {{PRIMARY_DARK_1}};
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.3);
}

.arco-modal-footer {
  background-color: rgba({{BG_1_RGB}}, 0.98);
  border-top: 1px solid {{BORDER_2}};
  color: var(--color-text-1);
}

/* ==================== 经典表单元素 ==================== */
.arco-input,
input[type="text"],
input[type="password"],
input[type="email"],
input[type="number"],
input[type="search"] {
  background-color: var(--bg-2);
  border: 2px inset var(--border-base);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.2);
  border-radius: 0;
  padding: 4px 6px;
  font-size: 13px;
  color: var(--color-text-1);
  transition: all 0.1s ease;
}

.arco-input:focus,
input:focus {
  border: 2px inset var(--color-primary);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.3), 0 0 0 1px var(--color-primary);
  outline: none;
}

.arco-checkbox,
.arco-radio,
input[type="checkbox"],
input[type="radio"] {
  width: 13px;
  height: 13px;
  border: 2px inset var(--border-base);
  background-color: var(--bg-2);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.2);
  border-radius: 0;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  transition: all 0.1s ease;
}

.arco-checkbox:checked,
.arco-radio:checked,
input[type="checkbox"]:checked,
input[type="radio"]:checked {
  background-color: var(--bg-active);
  border: 2px inset var(--border-base);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.3);
}

.arco-checkbox:checked::after,
input[type="checkbox"]:checked::after {
  content: "\2713";
  display: block;
  color: var(--text-primary);
  font-size: 10px;
  font-weight: bold;
  text-align: center;
  line-height: 9px;
}

.arco-radio {
  border-radius: 50%;
}

.arco-radio:checked::after,
input[type="radio"]:checked::after {
  content: "";
  display: block;
  width: 5px;
  height: 5px;
  background-color: var(--text-primary);
  border-radius: 50%;
  margin: 2px auto;
}

/* ==================== 表单标签样式 ==================== */
.arco-form-label-item,
[class*="form-label"],
[class*="arco-form-label"],
.arco-col[class*="form-label"],
.arco-form-item-label,
[class*="arco-form-item-label"] {
  background-color: transparent !important;
  border: none !important;
  box-shadow: none !important;
  padding: 0 !important;
  margin: 0 !important;
  color: var(--color-text-1) !important;
}

.arco-form-label-item *,
[class*="form-label"] *,
[class*="arco-form-label"] *,
.arco-col[class*="form-label"] *,
.arco-form-item-label *,
[class*="arco-form-item-label"] * {
  color: var(--color-text-1) !important;
  background-color: transparent !important;
}

[data-theme='dark'] .arco-form-label-item,
[data-theme='dark'] [class*="form-label"],
[data-theme='dark'] [class*="arco-form-label"],
[data-theme='dark'] .arco-col[class*="form-label"],
[data-theme='dark'] .arco-form-item-label,
[data-theme='dark'] [class*="arco-form-item-label"] {
  background-color: transparent !important;
  border: none !important;
  box-shadow: none !important;
  color: var(--color-text-1) !important;
}

[data-theme='dark'] .arco-form-label-item *,
[data-theme='dark'] [class*="form-label"] *,
[data-theme='dark'] [class*="arco-form-label"] *,
[data-theme='dark'] .arco-col[class*="form-label"] *,
[data-theme='dark'] .arco-form-item-label *,
[data-theme='dark'] [class*="arco-form-item-label"] * {
  color: var(--color-text-1) !important;
  background-color: transparent !important;
}

/* ==================== 深色模式 (Dark Mode) ==================== */
[data-theme='dark'] {
  --color-primary: {{D_PRIMARY}};
  --primary: {{D_PRIMARY}};
  --color-primary-light-1: {{D_PRIMARY_LIGHT_1}};
  --color-primary-light-2: {{D_PRIMARY_LIGHT_2}};
  --color-primary-light-3: {{D_PRIMARY_LIGHT_3}};
  --color-primary-dark-1: {{D_PRIMARY_DARK_1}};
  --primary-rgb: {{D_PRIMARY_RGB}};

  --brand: {{D_BRAND}};
  --brand-light: {{D_BRAND_LIGHT}};
  --brand-hover: {{D_BRAND_HOVER}};
  --color-brand-fill: {{D_PRIMARY}};
  --color-brand-bg: {{D_BRAND_LIGHT}};

  --aou-1: {{D_AOU_1}};
  --aou-2: {{D_AOU_2}};
  --aou-3: {{D_AOU_3}};
  --aou-4: {{D_AOU_4}};
  --aou-5: {{D_AOU_5}};
  --aou-6: {{D_AOU_6}};
  --aou-7: {{D_AOU_7}};
  --aou-8: {{D_AOU_8}};
  --aou-9: {{D_AOU_9}};
  --aou-10: {{D_AOU_10}};

  --color-bg-1: {{D_BG_1}};
  --bg-1: {{D_BG_1}};
  --color-bg-2: {{D_BG_2}};
  --bg-2: {{D_BG_2}};
  --color-bg-3: {{D_BG_3}};
  --bg-3: {{D_BG_3}};
  --color-bg-4: {{D_BG_4}};
  --bg-4: {{D_BG_4}};
  --bg-base: {{D_BG_BASE}};
  --bg-hover: {{D_BG_HOVER}};
  --bg-active: {{D_BG_ACTIVE}};
  --fill: {{D_FILL}};
  --color-fill: {{D_FILL}};

  --color-text-1: {{D_TEXT_1}};
  --text-primary: {{D_TEXT_1}};
  --color-text-2: {{D_TEXT_2}};
  --text-secondary: {{D_TEXT_2}};
  --color-text-3: {{D_TEXT_3}};
  --text-disabled: {{D_TEXT_3}};
  --text-0: {{D_TEXT_0}};

  --color-border: {{D_BORDER_1}};
  --color-border-1: {{D_BORDER_1}};
  --color-border-2: {{D_BORDER_2}};
  --border-base: {{D_BORDER_1}};
  --border-light: {{D_BORDER_2}};

  --success: {{D_SUCCESS}};
  --warning: {{D_WARNING}};
  --danger: {{D_DANGER}};
  --info: {{D_INFO}};

  --accent: {{D_ACCENT}};
  --accent-light: {{D_ACCENT_LIGHT}};
  --accent-dark: {{D_ACCENT_DARK}};

  --message-user-bg: {{D_MSG_USER_BG}};
  --message-tips-bg: {{D_MSG_TIPS_BG}};
  --workspace-btn-bg: {{D_WORKSPACE_BTN_BG}};

  --dialog-fill-0: {{D_DIALOG_FILL}};
}

/* ===== 深色模式全局样式 ===== */
[data-theme='dark'] body,
[data-theme='dark'] html {
  background-color: var(--bg-1);
  color: var(--text-primary);
}

[data-theme='dark'] .arco-layout,
[data-theme='dark'] [class*="layout"] {
  background-color: var(--bg-1);
}

[data-theme='dark'] .arco-layout-content {
  background-color: var(--bg-1);
}

/* ===== 深色模式侧边栏 ===== */
[data-theme='dark'] .layout-sider {
  background-color: var(--bg-3);
  border-right: 2px solid var(--border-base);
}

[data-theme='dark'] .layout-sider.collapsed {
  overflow: hidden !important;
}

[data-theme='dark'] .layout-sider.collapsed * {
  overflow: hidden !important;
}

[data-theme='dark'] .layout-sider.collapsed::-webkit-scrollbar {
  display: none !important;
  width: 0 !important;
  height: 0 !important;
}

[data-theme='dark'] .layout-sider-header {
  background: linear-gradient(180deg, {{D_SIDEBAR_HEADER_FROM}} 0%, {{D_SIDEBAR_HEADER_TO}} 100%);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 2px rgba(0, 0, 0, 0.4);
}

/* ===== 深色模式背景图 ===== */
[data-theme='dark'] .layout-content.bg-1::before {
  background: linear-gradient(
    135deg,
    {{D_OVERLAY_DARK_1}} 0%,
    {{D_OVERLAY_DARK_2}} 50%,
    {{D_OVERLAY_DARK_3}} 100%
  );
}

[data-theme='dark'] [class*="chat-layout"] .arco-layout-content::before,
[data-theme='dark'] [class*="conversation"] .arco-layout-content::before {
  opacity: 0.2;
  filter: brightness(0.9) saturate(1.1);
}

/* ===== 深色模式输入框 ===== */
[data-theme='dark'] .guidInputCard textarea,
[data-theme='dark'] [class*="guidInputCard"] textarea {
  background-color: rgba({{D_BG_2_RGB}}, 0.98);
  color: var(--color-text-1);
}

[data-theme='dark'] .sendbox-container:not([class*="model"]):not([class*="Model"]),
[data-theme='dark'] [class*="sendbox"]:not([class*="input"]):not([class*="textarea"]):not([class*="model"]):not([class*="Model"]):not([class*="tools"]) {
  background-color: rgba({{D_BG_2_RGB}}, 0.95);
  border: 2px outset var(--border-base);
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.1), inset -1px -1px 0 rgba(0, 0, 0, 0.3), 0 2px 4px rgba(0, 0, 0, 0.3);
}

[data-theme='dark'] .sendbox-container textarea,
[data-theme='dark'] [class*="sendbox"] textarea {
  color: var(--text-primary);
}

[data-theme='dark'] .guidInputCard {
  background-color: rgba({{D_BG_2_RGB}}, 0.95);
  border: 2px outset var(--border-base);
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.1), inset -1px -1px 0 rgba(0, 0, 0, 0.3), 0 2px 4px rgba(0, 0, 0, 0.3);
}

/* ===== 深色模式消息气泡 ===== */
[data-theme='dark'] .message-item.user .message-bubble,
[data-theme='dark'] [class*="message"][class*="user"] .message-content {
  background: linear-gradient(180deg, {{D_PRIMARY_DARK_1}} 0%, {{D_AOU_8}} 100%);
  color: white;
  border: 1px solid {{D_AOU_8}};
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 2px 4px rgba(0, 0, 0, 0.4);
}

[data-theme='dark'] .message-item.ai .message-bubble,
[data-theme='dark'] .message-item.assistant .message-bubble,
[data-theme='dark'] [class*="message"][class*="ai"] .message-content,
[data-theme='dark'] [class*="message"][class*="assistant"] .message-content {
  background: rgba({{D_BG_2_RGB}}, 0.98);
  border: 1px solid var(--border-base);
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.1), inset -1px -1px 0 rgba(0, 0, 0, 0.3), 0 2px 4px rgba(0, 0, 0, 0.3);
  color: var(--text-primary);
}

[data-theme='dark'] .message-item.ai .arco-alert,
[data-theme='dark'] [class*="message"][class*="ai"] .arco-alert,
[data-theme='dark'] .message-item.ai [class*="alert"],
[data-theme='dark'] [class*="message"][class*="ai"] [class*="alert"] {
  background-color: rgba({{D_BG_2_RGB}}, 0.9);
  border-color: var(--border-base);
  color: var(--text-primary);
}

[data-theme='dark'] .message-item.ai .arco-card,
[data-theme='dark'] [class*="message"][class*="ai"] .arco-card,
[data-theme='dark'] .message-item.ai [class*="card"],
[data-theme='dark'] [class*="message"][class*="ai"] [class*="card"] {
  background-color: rgba({{D_BG_2_RGB}}, 0.9);
  border-color: var(--border-base);
  color: var(--text-primary);
}

/* ===== 深色模式按钮 ===== */
[data-theme='dark'] .arco-btn-primary:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]),
[data-theme='dark'] button[type="primary"]:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]) {
  background: linear-gradient(180deg, {{D_PRIMARY_DARK_1}} 0%, {{D_AOU_8}} 100%);
  border: 2px outset {{D_PRIMARY_DARK_1}};
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 2px 4px rgba(0, 0, 0, 0.4);
}

[data-theme='dark'] .arco-btn-primary:hover:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]),
[data-theme='dark'] button[type="primary"]:hover:not([class*="icon"]):not([class*="circle"]):not([class*="model"]):not([class*="Model"]) {
  background: linear-gradient(180deg, {{D_PRIMARY}} 0%, {{D_PRIMARY_DARK_1}} 100%);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.3), 0 3px 6px rgba(0, 0, 0, 0.5);
}

[data-theme='dark'] .arco-btn-success,
[data-theme='dark'] button[type="success"] {
  background: linear-gradient(180deg, {{D_ACCENT_DARK}} 0%, {{D_ACCENT}} 100%);
  border: 2px outset {{D_ACCENT_DARK}};
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 2px 4px rgba(0, 0, 0, 0.4);
}

[data-theme='dark'] .arco-btn-success:hover,
[data-theme='dark'] button[type="success"]:hover {
  background: linear-gradient(180deg, {{D_ACCENT}} 0%, {{D_ACCENT_DARK}} 100%);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.3), 0 3px 6px rgba(0, 0, 0, 0.5);
}

/* 深色模式强调色点缀 */
[data-theme='dark'] .arco-alert[class*="success"],
[data-theme='dark'] [class*="alert"][class*="success"],
[data-theme='dark'] .arco-message-success,
[data-theme='dark'] [class*="message"][class*="success"] {
  background-color: rgba({{D_ACCENT_RGB}}, 0.15);
  border: 1px solid {{D_ACCENT}};
  border-left: 3px solid {{D_ACCENT}};
}

[data-theme='dark'] .arco-checkbox-checked .arco-checkbox-icon,
[data-theme='dark'] input[type="checkbox"]:checked {
  background-color: {{D_ACCENT}};
  border-color: {{D_ACCENT}};
}

[data-theme='dark'] .arco-radio-checked .arco-radio-button,
[data-theme='dark'] input[type="radio"]:checked {
  border-color: {{D_ACCENT}};
}

[data-theme='dark'] .arco-radio-checked .arco-radio-button::after {
  background-color: {{D_ACCENT}};
}

[data-theme='dark'] .arco-progress-line[class*="success"] .arco-progress-line-inner,
[data-theme='dark'] .arco-progress-line[data-status="success"] .arco-progress-line-inner {
  background-color: {{D_ACCENT}};
}

[data-theme='dark'] .arco-tag[class*="success"],
[data-theme='dark'] .arco-tag[data-color="green"] {
  background-color: rgba({{D_ACCENT_RGB}}, 0.15);
  border-color: {{D_ACCENT}};
  color: {{D_ACCENT}};
}

/* ===== 深色模式滚动条 ===== */
[data-theme='dark'] ::-webkit-scrollbar-thumb {
  background: linear-gradient(180deg, {{D_BORDER_1}} 0%, {{D_BG_4}} 100%);
  border: 1px solid {{D_BORDER_1}};
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.2), inset -1px -1px 0 rgba(0, 0, 0, 0.4);
}

[data-theme='dark'] ::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(180deg, {{D_BG_HOVER}} 0%, {{D_BORDER_1}} 100%);
}

[data-theme='dark'] ::-webkit-scrollbar-track {
  background: var(--bg-1);
  border: 1px solid var(--border-base);
  box-shadow: inset 1px 1px 0 rgba(0, 0, 0, 0.3);
}

[data-theme='dark'] ::-webkit-scrollbar-button {
  background: var(--bg-3);
  border: 1px solid var(--border-base);
  box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.1), inset -1px -1px 0 rgba(0, 0, 0, 0.4);
}

/* ===== 深色模式其他元素 ===== */
[data-theme='dark'] ::selection {
  background-color: var(--color-primary);
  color: white;
}

[data-theme='dark'] a:not([class*="button"]):not([class*="btn"]) {
  color: var(--color-primary);
}

[data-theme='dark'] a:hover:not([class*="button"]):not([class*="btn"]) {
  color: var(--color-primary-light-1);
}

[data-theme='dark'] .arco-tooltip-popup,
[data-theme='dark'] .arco-popover-popup {
  z-index: 10000 !important;
}

[data-theme='dark'] .arco-tooltip-inner,
[data-theme='dark'] .arco-popover-inner,
[data-theme='dark'] .arco-popover-content {
  background: {{D_TOOLTIP_BG}} !important;
  color: var(--text-primary) !important;
  border: 1px solid var(--border-base) !important;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5) !important;
  padding: 4px 8px !important;
  font-size: 12px !important;
  line-height: 1.4 !important;
  max-width: 200px !important;
  word-wrap: break-word !important;
}

[data-theme='dark'] .arco-tooltip-inner *,
[data-theme='dark'] .arco-popover-inner *,
[data-theme='dark'] .arco-popover-content * {
  color: var(--text-primary) !important;
  background-color: transparent !important;
}

[data-theme='dark'] .layout-sider ~ .arco-tooltip-popup,
[data-theme='dark'] .layout-sider .arco-tooltip-popup {
  z-index: 10001 !important;
}

[data-theme='dark'] .arco-modal-body {
  background: var(--bg-2);
  backdrop-filter: blur(8px);
  border: 2px outset var(--border-base);
  color: var(--text-primary);
}

[data-theme='dark'] .arco-modal-header {
  background: linear-gradient(180deg, {{D_SIDEBAR_HEADER_FROM}} 0%, {{D_SIDEBAR_HEADER_TO}} 100%);
  color: white;
  border-bottom: 1px solid rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
}

[data-theme='dark'] .arco-modal-footer {
  background: var(--bg-2);
  border-top: 1px solid var(--border-base);
  color: var(--text-primary);
}

/* ===== 深色模式输入框 ===== */
[data-theme='dark'] .arco-input,
[data-theme='dark'] input[type="text"],
[data-theme='dark'] input[type="password"],
[data-theme='dark'] input[type="email"],
[data-theme='dark'] input[type="number"],
[data-theme='dark'] input[type="search"] {
  background-color: var(--bg-2);
  border: 2px inset var(--border-base);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.4);
  color: var(--text-primary);
}

[data-theme='dark'] .arco-input:focus,
[data-theme='dark'] input:focus {
  border: 2px inset var(--color-primary);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.5), 0 0 0 1px var(--color-primary);
}

/* ===== 深色模式复选框/单选框 ===== */
[data-theme='dark'] .arco-checkbox,
[data-theme='dark'] .arco-radio,
[data-theme='dark'] input[type="checkbox"],
[data-theme='dark'] input[type="radio"] {
  background-color: var(--bg-2);
  border: 2px inset var(--border-base);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.4);
}

[data-theme='dark'] .arco-checkbox:checked,
[data-theme='dark'] .arco-radio:checked,
[data-theme='dark'] input[type="checkbox"]:checked,
[data-theme='dark'] input[type="radio"]:checked {
  background-color: var(--bg-active);
  border: 2px inset var(--border-base);
  box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.5);
}

/* ==================== 响应式调整 ==================== */
@media (max-width: 768px) {
  .guidInputCard,
  .sendbox-container {
    border-radius: {{BORDER_RADIUS}};
  }

  .message-item.user .message-bubble,
  .message-item.ai .message-bubble,
  .message-item.assistant .message-bubble {
    border-radius: {{BORDER_RADIUS}};
    padding: 10px 14px;
  }

  .arco-btn-primary,
  .arco-btn-secondary {
    border-radius: {{BORDER_RADIUS}};
    padding: 8px 16px;
  }
}

/* ==================== 打印样式 ==================== */
@media print {
  .layout-content.bg-1::before,
  [class*="chat-layout"] .arco-layout-content::before {
    display: none;
  }

  * {
    box-shadow: none !important;
    text-shadow: none !important;
  }
}

/* AionUi Theme Background Start */
body,
html,
.arco-layout,
.app-shell {
  background-image: url("{{BG_IMAGE_URL}}");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
  background-attachment: fixed;
  background-color: transparent;
}

.layout-content,
.layout-content.bg-1,
.arco-layout-content,
[class*="chat-layout"] .arco-layout-content,
[class*="conversation"] .arco-layout-content,
.bg-1,
.bg-2:not(.app-titlebar),
[class*="flex-col"][class*="h-full"],
[class*="flex-center"] {
  background-color: transparent;
  background-image: none;
}

.layout-content::before,
.layout-content.bg-1::before,
[class*="chat-layout"] .arco-layout-content::before,
[class*="conversation"] .arco-layout-content::before {
  background: transparent;
  opacity: 0;
}
/* AionUi Theme Background End */
```
