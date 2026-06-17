---
name: design-language
description: >
  9.0 设计规范 — 统一设计语言与风格规范。每当用户需要创建 UI 界面、网页、React 组件、HTML 页面、
  Figma 页面搭建、设计稿描述，或任何涉及视觉风格的任务时，必须使用此 skill 确保风格一致性。
  即使用户只是说"帮我做个界面"、"做个页面"、"搭建一下"也要触发。
  包含：颜色体系、字体规范、间距圆角、阴影层级、组件规范、自定义规则、Figma 工作流。
---

# 9.0 设计规范

基于 Figma 设计稿 `9.0规范-一致性测试` 的完整设计系统。

**Figma 源文件 Key**: `sxQXbLdcTfITwow8YCnmOJ`

---

## 核心设计语言（快速参考）

| 维度 | 规范 |
|------|------|
| 主色 | `#FF6435`（橙红）|
| 背景色 | `#F0F1F5`（全局）/ `#FFFFFF`（卡片）|
| 中文字体 | PingFang SC（回退：Noto Sans SC）|
| 数字/英文字体 | Barlow Semi Condensed |
| 圆角基准 | 4px 阶梯，Full = 1000px（胶囊形）|
| 间距网格 | 基于 4px，页面左右 margin = 12px |
| 行高规则 | 统一为字号的 **1.5 倍** |
| 阴影色基底 | `#0F284D` 不同透明度（5 级）|

---

## 参考文件索引

按需读取对应文件，不要一次性全部读取。

| 文件 | 内容 | 何时读取 |
|------|------|---------|
| `references/colors.md` | 颜色体系：基础色板 + 语义色 + 文字色 | 涉及颜色选取、色值确认时 |
| `references/typography.md` | 字体规范：字族、字重、字号层级 | 涉及文本样式、字号选择时 |
| `references/spacing.md` | 间距与圆角：Space / Padding / Radius | 涉及布局间距、圆角设定时 |
| `references/shadows.md` | 阴影/层级：5 级投影体系 | 涉及卡片、弹窗、浮层阴影时 |
| `references/components.md` | 组件规范 + Figma Component Key 索引 | 使用任何 UI 组件时（必读）|
| `references/custom-rules.md` | ⭐ 自定义规则（**优先级最高**）| 有疑问或冲突时优先查阅 |
| `references/workflow.md` | Figma 页面搭建工作流 + 常见错误清单 | 在 Figma 中搭建页面时 |

---

## 执行规则

### 优先级顺序

1. **`custom-rules.md`** — 用户自定义规则，最高优先级，覆盖所有默认值
2. 各专项规范文件（colors / typography / spacing / shadows / components）
3. 通用设计常识

### 使用组件的原则（Figma 场景）

**必须优先使用组件库实例，禁止手动拼装已有库组件。**

- 搭建任何页面前，必须先查 `references/components.md` 的 Component Key 索引
- 所有已有库组件必须用 `importComponentSetByKeyAsync` / `importComponentByKeyAsync` 导入
- 仅当组件库中确实不存在时，才手动用 Frame/Rectangle/Text 构建

### Web / React 场景

输出代码时，使用规范中的设计 token：

```css
/* 颜色变量参考 */
--primary: #FF6435;
--secondary: #FFB19A;
--text-primary: #222222;
--text-secondary: #757575;
--surface-canvas: #F0F1F5;
--surface-default: #FFFFFF;
--outline-default: #EBECF2;
--error: #FF1930;
--success: #00B42A;
--disable: #CCCCCC;
```

```css
/* 字体栈 */
font-family: 'PingFang SC', 'Noto Sans SC', sans-serif;          /* 中文 */
font-family: 'Barlow Semi Condensed', 'PingFang SC', sans-serif; /* 数字/英文 */
```

```css
/* 阴影速查 */
box-shadow: 0px 4px 12px rgba(15, 40, 77, 0.06);   /* Level 1 — 卡片 */
box-shadow: 0px 8px 24px rgba(15, 40, 77, 0.08);   /* Level 2 — 地图浮层 */
box-shadow: 0px 16px 32px rgba(15, 40, 77, 0.10);  /* Level 4 — 弹窗 */
box-shadow: 0px 30px 50px rgba(15, 40, 77, 0.12);  /* Level 5 — Toast */
```

---

## 快速决策树

```
需要什么？
├── 颜色/色值         → custom-rules.md > colors.md
├── 文字样式/字号     → custom-rules.md > typography.md（行高 = 字号 × 1.5）
├── 间距/圆角         → custom-rules.md > spacing.md（页面 margin = 12px）
├── 阴影              → shadows.md（5 级体系）
├── 按钮/导航/卡片等   → components.md（含 Figma Key）
└── Figma 搭建流程    → workflow.md（先读！违反流程会手动拼装出错）
```
