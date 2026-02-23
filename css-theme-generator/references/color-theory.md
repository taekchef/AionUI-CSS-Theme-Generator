# AionUI 色彩理论参考指南 (Color Theory Reference)

本文件为 AionUI CSS 主题生成器的核心色彩逻辑参考。AI 代理应遵循以下机械化规则，从极简输入（如 1 个主色或风格描述）推导出完整的 CSS 变量系统。

## 1. 从主色推导完整色板 (Deriving Full Palette from Primary Color)

AionUI 的核心色板 `AOU Brand Palette` 由 10 个阶梯组成（`--aou-1` 到 `--aou-10`）。

### 核心规则
- **--aou-6**：必须是输入的主色（Primary Color）。
- **推导逻辑**：基于 HSL 模式进行亮度（Lightness）和饱和度（Saturation）的偏移。

| 变量 | 描述 | 亮度 (Lightness) 调整 | 饱和度 (Saturation) 调整 |
| :--- | :--- | :--- | :--- |
| `--aou-1` | 极浅背景色 | 固定为 96% | 降低至 10-15% |
| `--aou-2` | 浅色背景色 | 固定为 92% | 降低至 20-25% |
| `--aou-3` | 悬停背景色 | 固定为 85% | 降低至 30-40% |
| `--aou-4` | 弱化边框色 | 固定为 75% | 保持或微降 |
| `--aou-5` | 辅助主色 | 主色 L + 10% | 保持 |
| `--aou-6` | **主色** | **原始主色 L** | **原始主色 S** |
| `--aou-7` | 悬停主色 | 主色 L - 8% | 保持 |
| `--aou-8` | 激活主色 | 主色 L - 15% | 保持 |
| `--aou-9` | 深色强调 | 固定为 25% | 增加 10% (最高 100%) |
| `--aou-10` | 极深文字色 | 固定为 12% | 增加 20% (最高 100%) |

---

## 2. 背景色推导 (Background Color Derivation)

背景色应根据主色的色相（Hue）带有轻微的冷暖倾向。

### 倾向判定
- **暖色调 (Warm)**：Hue 0-60 (红/橙/黄) 或 300-360 (紫红/粉)。
- **冷色调 (Cool)**：Hue 60-300 (绿/青/蓝/紫)。

### 浅色模式 (:root)
- **--color-bg-1 (Base)**: 暖色调使用 `hsl(H, 10%, 98%)`，冷色调使用 `hsl(H, 8%, 98%)`。
- **--color-bg-2 (Secondary)**: 亮度降至 95%。
- **--color-bg-3 (Tertiary)**: 亮度降至 92%。
- **--color-bg-4 (Quaternary)**: 亮度降至 88%。
- **--bg-hover**: `rgba(0, 0, 0, 0.04)`。
- **--bg-active**: `rgba(0, 0, 0, 0.08)`。

### 深色模式 ([data-theme='dark'])
- **--color-bg-1 (Base)**: 暖色调使用 `hsl(H, 15%, 10%)`，冷色调使用 `hsl(H, 12%, 10%)`。
- **--color-bg-2**: 亮度升至 14%。
- **--color-bg-3**: 亮度升至 18%。
- **--color-bg-4**: 亮度升至 22%。

---

## 3. 文字色推导 (Text Color Derivation)

文字色必须满足 WCAG 对比度标准。

| 变量 | 浅色模式 (Light) | 深色模式 (Dark) | 对比度目标 |
| :--- | :--- | :--- | :--- |
| `--color-text-1` (Primary) | `hsl(H, 10%, 10%)` | `hsl(H, 10%, 95%)` | 7:1 |
| `--color-text-2` (Secondary) | `hsl(H, 5%, 40%)` | `hsl(H, 5%, 70%)` | 4.5:1 |
| `--color-text-3` (Disabled) | `hsl(H, 5%, 65%)` | `hsl(H, 5%, 45%)` | 3:1 |
| `--text-primary` | 同 `--color-text-1` | 同 `--color-text-1` | - |

---

## 4. 语义色选择 (Semantic Color Selection)

语义色在深色模式下需要增加亮度以保持视觉清晰度。

| 语义类型 | 基础色值 (Light) | 深色模式调整 (Dark) |
| :--- | :--- | :--- |
| **Success** | `#52c41a` (Green) | 亮度增加 15% |
| **Warning** | `#faad14` (Amber) | 亮度增加 10% |
| **Danger** | `#ff4d4f` (Red) | 亮度增加 15% |
| **Info** | 使用主色 (`--aou-6`) | 遵循主色深色模式规则 |

---

## 5. 组件色推导 (Component Color Derivation)

| 变量 | 浅色模式推导规则 | 深色模式推导规则 |
| :--- | :--- | :--- |
| `--message-user-bg` | `--aou-1` (极浅主色) | `--aou-9` (深色强调) |
| `--message-tips-bg` | `rgba(0, 0, 0, 0.02)` | `rgba(255, 255, 255, 0.05)` |
| `--workspace-btn-bg` | `#ffffff` | `--color-bg-3` |
| `--dialog-fill-0` | `rgba(255, 255, 255, 0.8)` | `rgba(30, 30, 30, 0.8)` |
| `--sidebar-bg` | 比 `--color-bg-1` 亮度低 2% | 比 `--color-bg-1` 亮度低 3% |

---

## 6. 从风格描述到主色 (Style Description to Primary Color)

当用户提供风格描述而非具体颜色时，使用以下映射表：

| 风格描述 (Style) | 建议主色 (Primary Color) | HSL 参考 |
| :--- | :--- | :--- |
| 赛博朋克 (Cyberpunk) | `#00f0ff` (Cyan) | 184, 100%, 50% |
| 清新自然 (Nature/Fresh) | `#4caf50` (Green) | 122, 39%, 49% |
| 暗黑哥特 (Gothic/Dark) | `#8b0000` (Dark Red) | 0, 100%, 27% |
| 日式简约 (Muji/Minimalist) | `#d4a574` (Warm Tan) | 31, 53%, 64% |
| 深海海洋 (Ocean/Deep Blue) | `#0077be` (Ocean Blue) | 202, 100%, 37% |
| 薰衣草幻想 (Lavender) | `#967bb6` (Purple) | 267, 30%, 60% |
| 活力橙 (Energetic Orange) | `#ff8c00` (Dark Orange) | 33, 100%, 50% |
| 极客黑客 (Hacker/Matrix) | `#00ff41` (Matrix Green) | 135, 100%, 50% |
| 优雅金 (Elegant Gold) | `#d4af37` (Gold) | 45, 64%, 52% |
| 樱花粉 (Sakura Pink) | `#ffb7c5` (Pink) | 348, 100%, 86% |
| 商务专业 (Corporate Blue) | `#1890ff` (Blue) | 209, 100%, 54% |
| 咖啡时光 (Coffee/Brown) | `#6f4e37` (Coffee) | 25, 34%, 33% |
| 极地冰川 (Glacier/Ice) | `#f0f8ff` (Alice Blue) | 208, 100%, 97% |
| 晚霞余晖 (Sunset) | `#fd5e53` (Sunset Orange) | 4, 98%, 66% |
| 森林深处 (Deep Forest) | `#013220` (Dark Green) | 156, 96%, 10% |
| 皇家紫 (Royal Purple) | `#7851a9` (Purple) | 266, 35%, 49% |
| 柠檬汽水 (Lemonade) | `#fff44f` (Lemon Yellow) | 56, 100%, 66% |

---

## 7. 从背景图提取色彩 (Extracting Colors from Background Image)

若用户提供背景图，AI 应执行以下步骤：
1. **识别主导色**：分析图像中占比最大的非中性色（Non-neutral color）。
2. **提取主色**：若图像色彩丰富，选择视觉中心最突出的颜色作为 `--color-primary`。
3. **处理中性图**：若图像接近黑白灰，寻找最饱和的装饰色（Accent）作为主色。
4. **氛围同步**：根据图像的整体色温（Warm/Cool）决定背景色的 H 偏移。

---

## 8. 深色模式转换规则 (Dark Mode Conversion Rules)

深色模式不是简单的反色，而是亮度的重新分布。

1. **主色调整**：
   - 若主色 L < 40%，在深色模式下应将 L 提升至 55-60%，以确保在深色背景上的可读性。
   - 变量：`--color-primary` (Dark) = `hsl(H, S, 60%)`。
2. **背景色压缩**：
   - 浅色模式背景亮度跨度大 (98% -> 88%)。
   - 深色模式背景亮度跨度小 (10% -> 22%)，避免对比度过强导致视觉疲劳。
3. **边框色处理**：
   - 浅色模式：`rgba(0, 0, 0, 0.1)`。
   - 深色模式：`rgba(255, 255, 255, 0.12)`。
4. **阴影处理**：
   - 深色模式下阴影应更深、扩散半径更小，或使用发光（Glow）效果代替。


---


## 9. 其他派生变量推导规则 (Other Derived Variable Rules)


本节补充模板中出现但前面章节未覆盖的占位符的推导规则，防止 AI 生成时靠猜。


### 9.1 侧边栏头部渐变色 SIDEBAR_HEADER_FROM / TO


侧边栏顶部（`.layout-sider-header`）使用线性渐变，颜色应与主色协调。


| 场景 | `{{SIDEBAR_HEADER_FROM}}` | `{{SIDEBAR_HEADER_TO}}` |
| :--- | :--- | :--- |
| 浅色模式（Light） | `--aou-6`（主色本身） | `--aou-8`（主色深 15%） |
| 深色模式（Dark） | `hsl(H, S, 20%)` — 比深色主色再深 | `hsl(H, S, 15%)` — 更深 |


**推导规则**：
- Light: `{{SIDEBAR_HEADER_FROM}}` = `{{PRIMARY}}`，`{{SIDEBAR_HEADER_TO}}` = `{{PRIMARY_DARK_1}}`
- Dark: `{{D_SIDEBAR_HEADER_FROM}}` = `hsl(H, S*0.8, 20%)`，`{{D_SIDEBAR_HEADER_TO}}` = `hsl(H, S*0.8, 14%)`
- 若主色饱和度极低（< 10%），FROM/TO 可使用 `--aou-8` / `--aou-9`


---


### 9.2 内容区遮罩色 OVERLAY_LIGHT / OVERLAY_DARK


`.layout-content.bg-1::before` 的渐变叠加层，给背景图增加色调统一感。无背景图时此层也存在，但几乎透明（opacity 接近 0）。


**浅色模式 3 个锚点**：

```
{{OVERLAY_LIGHT_1}}  →  rgba(R, G, B, 0.03) — 极轻微主色遮罩（0° 端）
{{OVERLAY_LIGHT_2}}  →  rgba(255, 255, 255, 0.0) — 中间透明过渡
{{OVERLAY_LIGHT_3}}  →  rgba(R, G, B, 0.02) — 极轻微主色遮罩（135° 端）
```

其中 R,G,B 为主色（`{{PRIMARY}}`）的 RGB 分量。透明度保持在 0.02–0.05 之间，**不要超过 0.08**，否则会严重遮盖主题背景。


**深色模式 3 个锚点**：

```
{{D_OVERLAY_DARK_1}}  →  rgba(R, G, B, 0.08) — 深色端轻微主色叠加
{{D_OVERLAY_DARK_2}}  →  rgba(0, 0, 0, 0.0) — 中间透明
{{D_OVERLAY_DARK_3}}  →  rgba(R, G, B, 0.05) — 另一端轻微主色叠加
```

其中 R,G,B 为深色主色（`{{D_PRIMARY}}`）的 RGB 分量。透明度保持在 0.05–0.12 之间。


---


### 9.3 填充色 FILL


`--fill` / `--color-fill` 用于图标、标签等的填充色，介于背景和文字之间。


| 模式 | 推导规则 |
| :--- | :--- |
| 浅色 `{{FILL}}` | `hsl(H, 10%, 80%)` — 比 `--color-bg-4` 稍深的中性调 |
| 深色 `{{D_FILL}}` | `hsl(H, 10%, 30%)` — 比 `--color-bg-3` 稍深的中性调 |


---


### 9.4 背景色 RGB 分量 BG_1_RGB / D_BG_2_RGB


模板中多处使用 `rgba({{BG_1_RGB}}, 0.98)` 这种格式（Modal、深色输入框等），需要提供纯 RGB 数值（不含 `#`，用逗号分隔）。


| 占位符 | 对应颜色 | 示例 |
| :--- | :--- | :--- |
| `{{BG_1_RGB}}` | `{{BG_1}}` 的 RGB 分量 | 若 BG_1 = `#f0f0f0`，则填 `240, 240, 240` |
| `{{D_BG_2_RGB}}` | `{{D_BG_2}}` 的 RGB 分量 | 若 D_BG_2 = `#1e1e1e`，则填 `30, 30, 30` |


**推导方法**：将对应十六进制颜色值转换为十进制 R、G、B，用逗号空格分隔，不加括号。


---


### 9.5 其他 RGB 分量 PRIMARY_RGB / ACCENT_RGB / D_ACCENT_RGB


同 9.4 的规则，将对应颜色的十六进制转为 `R, G, B` 格式：


| 占位符 | 对应颜色 |
| :--- | :--- |
| `{{PRIMARY_RGB}}` | `{{PRIMARY}}` 的 RGB 分量 |
| `{{ACCENT_RGB}}` | `{{ACCENT}}` 的 RGB 分量 |
| `{{D_ACCENT_RGB}}` | `{{D_ACCENT}}` 的 RGB 分量 |


---


### 9.6 强调色系 ACCENT / ACCENT_LIGHT / ACCENT_DARK


`{{ACCENT}}` 用于成功状态、复选框选中、进度条等，应与主色区分但视觉协调。


**推导规则**：
- 主色为暖色（Hue 0–60 或 300–360）→ Accent 选补色或对比绿（如 `#4caf50`）
- 主色为冷色蓝/紫（Hue 180–300）→ Accent 选青绿（如 `#00bcd4`）或暖绿（`#8bc34a`）
- 主色为中性色（饱和度 < 15%）→ Accent = 主色的互补色方向，饱和度提高至 50%+
- `{{ACCENT_LIGHT}}` = Accent 亮度 +15%
- `{{ACCENT_DARK}}` = Accent 亮度 -15%
- 深色模式规则同第 8 节：若 Accent L < 40%，深色模式下提升至 55–60%
