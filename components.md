# 组件规范

## 一、Button Full-width（通栏按钮）

通栏按钮，宽度 335px，高度 50px，胶囊形圆角 (`radius: Full/1000px`)。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| Property 1 (类型) | `Primary` / `Subtle` | 填充按钮 / 描边按钮 |
| Property 2 (状态) | `Default` / `Visited` / `Disabled` | 默认 / 完成态 / 禁用 |
| text (文字内容) | TEXT 属性 | 按钮文字，默认值 "默认文案" |

### 变体样式

| 类型 | 状态 | 背景 | 文字色 | 边框 |
|------|------|------|--------|------|
| Primary | Default | `--primary` (#FF6435) | `--on-primary` (白) | 无 |
| Primary | Visited | `--secondary` (#FFB19A) | `--on-secondary` (白) | 无 |
| Primary | Disabled | `--disable` (#CCCCCC) | `--on-disable` (白) | 无 |
| Subtle | Default | 透明 | `--primary` (#FF6435) | 1px `--primary` |
| Subtle | Visited | 透明 | `--secondary` (#FFB19A) | 1px `--secondary` |

### 文字规格

- 字体: PingFang SC Semibold
- 字号: 18px
- 行高: 100%
- 对齐: 居中

---

## 二、Button（常规按钮）

常规按钮，3 种尺寸 × 2 种类型 × 3 种状态。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| mode (类型) | `Primary` / `Subtle` | 填充按钮 / 描边按钮 |
| statue (状态) | `Default` / `Vistited` / `Disabled` | 默认 / 完成态 / 禁用 |
| size (尺寸) | `Large` / `Medium` / `Small` | 大 / 中 / 小 |
| Button Text (文字内容) | TEXT 属性 | 按钮文字，默认值 "默认文案" |

### 尺寸规格

| 尺寸 | 宽度 | 高度 | 字号 | 水平内边距 | 垂直内边距 |
|------|------|------|------|-----------|-----------|
| Large | 100px | 40px | 16px | 18px | 8~10px |
| Medium | 88px | 35px | 14px | 16px | 7~8px |
| Small | 88px | 28px | 14px | 16px | 4~5px |

### 变体样式

| 类型 | 状态 | 背景 | 文字色 | 边框 |
|------|------|------|--------|------|
| Primary | Default | `--primary` (#FF6435) | 白 (#FFFFFF) | 无 |
| Primary | Vistited | `--secondary` (#FFB19A) | 白 (#FFFFFF) | 无 |
| Primary | Disabled | `--disable` (#CCCCCC) | 白 (#FFFFFF) | 无 |
| Subtle | Default | 透明 | `--primary` (#FF6435) | 1px `--primary` |
| Subtle | Vistited | 透明 | `--secondary` (#FFB19A) | 1px `--secondary` |
| Subtle | Disabled | `--disable` (#CCCCCC) | `--on-disable` (白) | 无 |

### 文字规格

- 字体: PingFang SC Semibold
- Large: 16px，行高 Auto
- Medium / Small: 14px，行高 Auto
- 圆角: Full (1000px) 胶囊形

---

## 三、App bar（导航栏）

固定高度 88px，宽度 375px (iPhone 标准宽度)。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| 类型 | `Flat` / `Text` / `None` / `Icon` / `Flat white` / `Text white` / `None white` | 7 种导航栏变体 |
| icon1 | Boolean | 右侧图标 1 显示 |
| icon2 | Boolean | 右侧图标 2 显示 |

### 变体详情

#### Flat（有底线分割）
- 背景: 白色 (#FFFFFF)
- 底部分割线: `inset 0px -0.5px 0px 0px #EBECF2`
- 标题: PingFang SC Semibold 18px，居中，`--text-primary` (#222)
- 左侧返回按钮区域
- 顶部状态栏 (44px)
- ⚠️ **HitArea 不含 inner shadow**

#### Text（纯文字）
- 背景: 白色，无底线
- 标题: PingFang SC Semibold 18px，居中，`--text-primary` (#222)
- 右侧操作文字: PingFang SC Regular 14px，`--text-primary` (#222)

#### None（无标题）
- 背景: 白色，无底线
- 无标题文字
- 仅显示状态栏 + 返回按钮

#### Icon（带图标）
- 背景: 白色，无底线
- 标题: PingFang SC Semibold 18px，居中
- 右侧可配置 icon1/icon2 图标按钮

#### Flat white（白色主题有底线）
- 与 Flat 相同布局，使用白色/浅色配色
- 底部分割线

#### Text white（白色主题纯文字）
- 与 Text 相同布局，使用白色/浅色配色

#### None white（白色主题无标题）
- 与 None 相同布局，使用白色/浅色配色

### 通用结构
```
┌─────────────────────────────────┐ 88px
│  状态栏 (44px)                    │
│  ┌─────────────────────────────┐│
│  │ [返回]    标题文案    [操作] ││ 44px
│  └─────────────────────────────┘│
└─────────────────────────────────┘
```

---

## 四、CellCard（信息卡片）

**CellCard 是可直接实例化的生产组件**，内部已包含 Cardheader + CardContent + Button Full-width，通过 `setProperties` 按需开关内容，高度自动收缩。

### 使用方式

```js
// ✅ 正确：直接实例化 CellCard
const cellCardComp = await figma.importComponentByKeyAsync("14733bed207368ed2ae307898d537d8d362fea2c");
const card = cellCardComp.createInstance();
card.resize(351, card.height); // 只 resize 外层宽度，内部 H=FILL 自动跟随
```

详见下方「CellCard 标准操作流程」和 Key 索引表。

### 页面边距与对齐基准（重要）

组件库上传的填充/对齐方式即为正确设定，**禁止擅自修改组件的 `layoutSizing`**。常见的对齐误区与正确做法：

| 项目 | 正确值 |
|------|--------|
| 页面内容左右边距 | **12px**（容器 `paddingLeft/Right = 12`）|
| 卡片宽度 | **351px**（= 375 − 12×2），`layoutSizingHorizontal = 'FIXED'`，**不要用 FILL** |
| 卡片填充方式 | 保持组件默认 FIXED，不改成 FILL |

**通栏元素不参与内容边距对齐**：

- Tab、导航栏等**通栏元素**铺满整个屏幕宽度（屏幕 375 就 375，410 就 410），其内部 padding（如 tab 的 `px-8`）是组件自带的，**不是页面内容边距**。
- 通栏元素的内部内容（tab 文字、下划线）与卡片内容**本就不需要左边缘对齐**——卡片走 12px 内容边距，tab 走通栏 + 内部平分，两套对齐逻辑互不迁就。
- ❌ 错误：把卡片宽度/padding 改成迁就 tab 的 8px 内边距
- ✅ 正确：卡片固定 12px 边距，tab 保持通栏，各自正确

**Tab 内部规则**：通栏容器内，多个 tab 用 `flex-[1_0_0]` 等分；选中态下划线（underline）是**固定宽度**（amount=3 时为 32px），靠 `constraints: CENTER` 跟随文字居中，**宽度不随文字变化**。



---

### 4.1 CardHeader（卡片头部）

**生产组件，直接使用。**

#### Figma 信息

| 属性 | 值 |
|------|-----|
| Node ID | `1137:1307` |
| 类型 | COMPONENT_SET |
| 变体数量 | 4 个 |

#### 属性定义

| 属性 | 类型 | 可选值 | 说明 |
|------|------|--------|------|
| `ShowSubtitle` | BOOLEAN | `true` / `false` | 是否显示副标题 |
| `header Text` | TEXT | 文本内容 | 标题文字，默认 "卡片标题" |
| `SubtitleText` | TEXT | 文本内容 | 副标题文字，默认 "副标题信息" |
| `Actiontype` | VARIANT | `Expand` / `None` / `Link` | 右侧操作类型 |
| `ExpandStated` | VARIANT | `Expand` / `Collapsed` / `none` | 展开/收起状态（仅 Actiontype=Expand 时生效） |
| `ShowTag` | VARIANT | `true` / `false` | 是否显示状态标签（Tag） |

#### 变体组合

| Actiontype | ExpandStated | ShowTag | 右侧显示 | Tag 位置 |
|-----------|-------------|---------|---------|---------|
| `None` | `none` | `false` | 无操作 | — |
| `None` | `none` | `true` | 无操作 | 右上角（SPACE_BETWEEN） |
| `Link` | `none` | `false` | 文字链接 + 右箭头 | — |
| `Link` | `none` | `true` | 文字链接 + 右箭头 | 标题后行内 |
| `Expand` | `Expand` | `false` | "展开" + 向下箭头 | — |
| `Expand` | `Expand` | `true` | "展开" + 向下箭头 | 标题后行内 |
| `Expand` | `Collapsed` | `false` | "收起" + 向上箭头 | — |
| `Expand` | `Collapsed` | `true` | "收起" + 向上箭头 | 标题后行内 |

**Tag 位置规则**：
- `Actiontype=None` + `ShowTag=true` → Tag 放右上角（标题左，Tag 右，SPACE_BETWEEN）
- `Actiontype=Link/Expand` + `ShowTag=true` → Tag 紧跟标题文字后（行内），右侧保留操作区

**⚠️ 标题 sizing 必须按变体区分（HUG 用错会导致偏移）**：

标题 TEXT 的 `textAutoResize` 设置**取决于 Cardheader 变体**，用错会导致折行或 localX 偏移：

| 场景 | 标题 sizing | 原因 |
|------|------------|------|
| `ShowTag=true`（标题+tag 行内紧挨，如历史反馈卡片） | **HUG**（`WIDTH_AND_HEIGHT`）| 行内布局 TitleWithTag 会给标题分配固定宽度（如 w=66px）导致折行，HUG 让标题按内容宽度紧挨 tag |
| `Actiontype=Link/None`（标题独占一行，右侧 ActionText 或无） | **FILL**（`layoutGrow=1` + `layoutSizingHorizontal='FILL'`）| 这类变体用 grid 布局，标题设 HUG 会被 `place-items-start` 推到 localX=128 **反而偏移**；FILL 时标题 localX=0 左对齐且不折行（右侧 ActionText 占位） |

```js
const titleNode = header.findOne(n => n.type === 'TEXT' && n.name === 'header');
const showTag = header.componentProperties?.['ShowTag']?.value === 'true';
if (showTag) {
  titleNode.textAutoResize = 'WIDTH_AND_HEIGHT'; // HUG：行内标题+tag
} else {
  titleNode.textAutoResize = 'HEIGHT';
  titleNode.layoutGrow = 1;
  titleNode.layoutSizingHorizontal = 'FILL'; // FILL：独占行标题，localX=0
}
```

**同理，CardContent 内的 `Tittle medium` / `Body medium` 也须保持 FILL**（`layoutGrow=1` + `FILL`），否则 grid 布局下会出现 x=62/22/68 等偏移。出图后务必用 `Math.round(node.x) === 0` 全量自查所有文字节点。

#### Actiontype 语义规范

**两者都有箭头，不能以"有没有箭头"判断，应以交互行为为准。**

| 变体 | 箭头样式 | 正确使用场景 |
|------|---------|------------|
| `Actiontype=Link` | `>` 向右灰色小箭头（固定，不随状态变化） | 卡片级跳转入口：「全部」「查看」「更多」；点击后**页面跳转** |
| `Actiontype=Expand` | `∨/∧` 上下翻转箭头（随 ExpandStated 变化） | 展开/收起交互；点击后**当前卡片内容展开或收起** |
| `Actiontype=None` | 无 | 纯标题展示，无交互操作 |

**Link 使用注意：**
- `ActionText` 内文案通过 `findOne(n => n.name === '文案')` 找到后直接赋值
- **禁止隐藏 `arrow` 节点**，`>` 箭头是规范的一部分，不可省略
- 文案只写目标操作名，不含箭头符号（箭头由组件自动提供）：写「全部」不写「全部 >」

**Expand 使用注意：**
- `ExpandStated=Expand` → 显示「展开 ∨」（卡片当前为折叠态，点击可展开）
- `ExpandStated=Collapsed` → 显示「收起 ∧」（卡片当前为展开态，点击可收起）
- ⚠️ ExpandStated 命名与视觉**方向相反**：`Expand` 是展开按钮（折叠态），`Collapsed` 是收起按钮（展开态）

#### 样式规格

| 元素 | 字体 | 字号 | 字重 | 颜色 |
|------|------|------|------|------|
| 标题 | PingFang SC | 16px | Semibold | `--text-primary` (#222) |
| 副标题 | PingFang SC | 14px | Regular | `--text-secondary` (#757575) |
| 操作文字 | PingFang SC | 14px | Regular | `--primary` (#FF6435) |

---

### 4.2 CardContent（卡片内容）

**生产组件，直接使用。**

#### Figma 信息

| 属性 | 值 |
|------|-----|
| Node ID | `1136:441` |
| 类型 | COMPONENT_SET |
| 变体数量 | 10 个 |

#### 属性定义

| 属性 | 类型 | 可选值 | 说明 |
|------|------|--------|------|
| `surface` | VARIANT | `pure` / `subtle` | 内容区底色（pure=透明，subtle=灰底 #F6F8FB） |
| `contentLayout` | VARIANT | `Editorial` / `list` / `Media` | 内容布局类型 |
| `mediaSize` | VARIANT | `None` / `Medium` / `Large` | 图片尺寸（仅 Media 布局） |
| `showTitleMedium` | BOOLEAN | `true` / `false` | 是否显示加粗正文标题 |
| `showDescription` | BOOLEAN | `true` / `false` | 是否显示描述文字 |
| `showFloatingButton` | BOOLEAN | `true` / `false` | 是否显示悬浮按钮 |
| `titleText` | TEXT | 文本内容 | 正文标题 |
| `descriptionText` | TEXT | 文本内容 | 描述文字 |

#### ContentLayout 类型说明

**Editorial（编辑式内容）**
- 特征: 标题 + 正文段落 + 辅助说明
- 适用: 非结构化自然语言内容
- 结构: 垂直堆叠的文本块

**List（列表式内容）**
- 特征: 左右对齐的键值对 (Label: Value)
- 适用: 结构化信息展示
- 结构: 左黑字、右灰字成对排列

**Media（媒体式内容）**
- 特征: 图片 + 文字横向布局
- 适用: 带缩略图的内容展示
- 结构: 图左文右，水平 Flex

#### 布局选型规范

**需要展示图片时必须显式切换，不可沿用默认 Editorial。**

| 场景 | ContentLayout | Media size | 说明 |
|------|--------------|-----------|------|
| 纯文字（标题 + 描述） | `Editorial` | `None` | 默认布局，无图片 |
| 图片 + 状态蒙层 | `Media` | `Large` | 内置 StatusOverlay，无需额外引入 |

**Media Large 内置 StatusOverlay**，设置方式：
```js
cc.setProperties({
  'ContentLayout': 'Media',
  'Media size': 'Large',
  'surface': 'pure',        // Media Large 大图自带层级区分，不需要灰底
  'Action': 'Floating',     // Media Large 仅支持 Floating，不支持 None
});
// StatusOverlay 已内置，直接 findOne 后设置 State
const overlay = cc.findOne(n => n.type === 'INSTANCE' && n.name === 'StatusOverlay');
overlay.setProperties({ 'State': 'failed' }); // failed / Success / None
```

#### MediaSize 规格

| 尺寸 | 宽×高 | 比例 | 使用场景 |
|------|-------|------|---------|
| `None` | 无 | - | 纯文字内容 |
| `Medium` | 40×40px | 1:1 | 图标展示，辅助理解 |
| `Large` | 85×65px | 约 4:3 | 大图展示，可叠加 StatusOverlay |

#### Surface 规格

| Surface | 背景色 | 内边距 | 圆角 | 使用场景 |
|---------|--------|--------|------|---------|
| `pure` | 透明 | 无 | 无 | 页面一级内容，无需视觉分割 |
| `subtle` | `--surface-inset` (#F6F8FB) | 12px | 12px | 卡片内部需要区分不同信息区域、多个卡片紧密排列时区分内容区 |

#### Surface 选择规则

**核心作用**：用灰底区分 Header 和 Content 的视觉层级

**使用 `subtle` 的条件**（同时满足）：
1. Header 中有副标题（`ShowSubtitle=true`）
2. **且不是** Media Large 模式

**使用 `pure` 的条件**（任一满足）：
1. Header 没有副标题（`ShowSubtitle=false`）
2. Media Large 模式（大图本身能区分层级，不需要灰底）

**判断流程**：
```
Header 是否有副标题？
├─ 否 → pure
└─ 是 → 是否 Media Large？
         ├─ 是 → pure（大图自带区分效果）
         └─ 否 → subtle（需要灰底区分层级）
```

**示例**：
- Header 有副标题 + Editorial → `subtle`
- Header 有副标题 + List → `subtle`
- Header 有副标题 + Media Large → `pure`（例外）
- Header 无副标题 + 任何布局 → `pure`

> **注意**：Surface 选择与 ContentLayout 类型无关，仅由 Header 副标题和 Media Large 决定。

#### 间距规格

**Content 内部多个平行内容的间距规则**：

| Surface | MediaSize | 间距 (gap) | 原因 |
|---------|-----------|-----------|------|
| `pure` | `None` / `Medium` | **16px** | 透明背景，需要间距区分内容块 |
| `pure` | `Large` | **8px** | 大图本身起到分割作用，缩小间距 |
| `subtle` + `Floating` | 任意 | **8px** | 灰底包裹已提供视觉分割，使用紧凑间距 |
| `subtle` + `None` | 任意 | **12px** | 灰底包裹已提供视觉分割 |

**其他间距**：

| 场景 | gap |
|------|-----|
| Header ↔ Content | 8px |
| Content ↔ Footer | 16px |
| Editorial / List 内部（标题与描述） | 8px（pure）/ 4px（subtle） |
| Media 图片与文字 | 8px |

**规则总结**：
- **Pure + 无大图** → 16px
- **Pure + Large 图** → 8px（图片提供分割）
- **Subtle + Floating** → 8px（灰底提供分割）
- **Subtle + None** → 12px

#### ✅ 实现 CardContent 前必须检查

1. 找到对应的 CardHeader，确认 `ShowSubtitle` 是 `true` 还是 `false`
2. 确认 `contentLayout` 是否为 `Media Large`
3. 按下方 Surface 选择规则得出 `surface` 值，**不得默认使用 `pure`**

#### ✗ 禁止添加（Web/HTML 实现时）

| 位置 | 禁止项 | 原因 |
|------|--------|------|
| `CardContent / list` 行与行之间 | 分割线（border-bottom 等） | 规范未描述，不得自行补充 |
| `CardHeader` 与 `CardContent` 之间 | 分割线（.divider、border-bottom 等） | 规范未描述，不得自行补充 |
| `CardContent` 与 `CardFooter` 之间 | 分割线 | 规范未描述，不得自行补充 |

---

### 4.3 CardFooter（卡片底部）

CardFooter 直接复用 **Button Full-width** 组件（Node ID: `1094:4049`），无需单独定义。

---

### 4.4 组合使用规范

#### 完整卡片结构

```
┌─────────────────────────────────┐  355px
│  CardHeader                      │
│  ┌─────────────────────────────┐│
│  │ 标题          [操作]         ││
│  │ 副标题（可选）               ││
│  └─────────────────────────────┘│
├─────────────────────────────────┤
│  CardContent                     │
│  ┌─────────────────────────────┐│
│  │ 内容区（根据 Layout 填充）   ││
│  └─────────────────────────────┘│
├─────────────────────────────────┤
│  CardFooter                      │
│  ┌─────────────────────────────┐│
│  │ [Button Full-width]          ││
│  └─────────────────────────────┘│
└─────────────────────────────────┘
```

#### 组件间距

| 位置 | gap |
|------|-----|
| Header ↔ Content | 8px |
| Content ↔ Footer | 16px |

#### 容器规格

当手动组合卡片时，外层容器规格：

| 属性 | 值 |
|------|-----|
| 宽度 | **351px** |
| 圆角 | `Radius/Large` **16px**（页面级卡片） |
| 内边距 | 16px |
| 阴影 | Level 1 — `0px 4px 12px rgba(15, 40, 77, 0.06)` |
| 背景 | `--surface-default` (#FFFFFF) |

**圆角层级规则**：

| 层级 | 圆角 | Token | 说明 |
|------|------|-------|------|
| 页面级卡片（外层容器） | **16px** | `Radius/Large` | 直接放置在页面内容区的卡片 |
| 卡片内子卡片 | **12px** | `Radius/Medium` | 嵌套在卡片内的子块，如 CardContent `subtle` 模式下的内容区 |

#### 常见组合模式

**模式 1: 信息展示卡片（无操作）**
- Header: Actiontype=None
- Content: surface=subtle, contentLayout=list

**模式 2: 带链接的内容卡片**
- Header: Actiontype=Link, ShowSubtitle=true
- Content: surface=pure, contentLayout=Editorial

**模式 3: 可展开的列表卡片**
- Header: Actiontype=Expand
- Content: surface=subtle, contentLayout=list

**模式 4: 带底部按钮的操作卡片**
- Header: Actiontype=None, ShowSubtitle=true
- Content: surface=pure, contentLayout=Editorial
- Footer: Button Full-width (Primary, Default)

**模式 5: 媒体卡片（带大图和状态蒙层）**
- Header: Actiontype=None
- Content: surface=pure, contentLayout=Media, mediaSize=Large
- StatusOverlay: 叠加在图片上

**模式 6: 带悬浮按钮的内容卡片**
- Header: Actiontype=None
- Content: surface=subtle, showFloatingButton=true

---

### 4.5 特殊场景：多模块拼装卡片

当卡片内包含多个子组件（pic + Body + Alert）拼装时，不使用上述组合模式，而是自由组合。

| 属性 | 值 |
|------|-----|
| 内边距 | 16px |
| 模块间距 | **24px** (gap) |
| 对齐 | flex-col, 居中对齐 (items-center) |
| pic 尺寸 | 250×134px |
| Alert 尺寸 | **small** |

```
┌─────────────────────────────────┐  355px
│          padding: 16px           │
│  ┌───────────────────────────┐  │
│  │   pic (250×134, 居中)      │  │
│  └───────────────────────────┘  │
│          gap: 24px               │
│  ┌───────────────────────────┐  │
│  │   Body / 信息网格          │  │
│  └───────────────────────────┘  │
│          gap: 24px               │
│  ┌───────────────────────────┐  │
│  │   Alert / 提示条           │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

> **注意：** 此场景与 Media 模式不同。Media 是图左文右的缩略图布局，此场景是大图居中的垂直堆叠布局。

---

### 4.6 命名约定

| 组件 | 属性名 | 用途 |
|------|--------|------|
| CardHeader | `SubtitleText` | 标题下方的副标题（灰色小字） |
| CardContent | `descriptionText` | 正文标题下方的描述文字 |

**注意**: Header 的 `SubtitleText` 和 Content 的 `descriptionText` 是不同层级的内容，不要混淆。

---

## 五、Alert（提示条）

全宽或卡片内提示条，支持信息/警告两种类型，两种尺寸。

> ⚠️ **Alert 是独立模块升级项，非警示信息的默认样式。** 使用前先查 `custom-rules.md`「模块复用优先级规则（警示信息：副标题槽 vs Alert）」：副标题/描述槽空闲时，应优先复用该槽位 + 警示色（`--error` #FF1930）承载警示，**不要默认新增 Alert**；仅当槽位已占用且需独立强调时才升级为 Alert。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| variant (类型) | `info` / `warning` | 信息提示 / 警告提示 |
| mode (模式) | `standard` / `contained` | 全宽(375px) / 卡片内(355px, 圆角12px) |
| action (操作) | `link` / `pure` | 带链接操作 / 纯展示 |
| size (尺寸) | `Default` / `small` | 默认(44px) / 小(41~42px) |
| position (位置) | `top` / `default` | 顶部 / 默认 |
| 展示图标 | Boolean | 控制左侧图标显示 |
| 展示按钮 | Boolean | 控制右侧箭头按钮显示 |
| 展示图标2 | Boolean | 控制左侧图标显示（备用） |
| 展示按钮2 | Boolean | 控制右侧箭头按钮显示（备用） |

### 样式

| 类型 | 背景色 | 文字强调色 | 图标色 |
|------|--------|-----------|--------|
| info | `#FFF5E8` | `--primary` (#FF6435) | `--primary` (#FF6435) |
| warning | `#FFEAE8` | `--错误色` (#FF1930) | `--错误色` (#FF1930) |

### 规格

| 模式 | 宽度 | 圆角 | 内边距 | 使用场景 |
|------|------|------|--------|---------|
| standard | 375px | 0 | 左16px 右10px, 垂直12px | 通栏使用，贴边全宽，无圆角 |
| contained | 355px | 12px | 左16px 右10px, 垂直12px | 非通栏使用，有页边距，有圆角 |

### 内部布局

- 内容容器 (Frame 26/27): **FILL 宽度**，自适应父容器宽度
- 文案文字: **FILL 宽度 + HEIGHT 自适应**，多行时在容器内折行，保持右侧固定间距
- info 变体内容帧: `Frame 26`，warning 变体内容帧: `Frame 27`

### 尺寸与文字规格

| 尺寸 | 高度 | 字体 | 字号 | 字重 | 使用场景 |
|------|------|------|------|------|---------|
| Default | 44px | PingFang SC | 14px | Semibold | 独立模块使用，作为页面级提示条 |
| small | 41~42px | PingFang SC | 12px | Regular | 卡片内部使用，作为内容状态提示 |

- 操作链接 (link 模式): 右侧显示 arrow 图标按钮
- 图标间距: 8px (图标与文字之间)

---

## 六、arrow（图标按钮）

通用图标组件，支持多种颜色/尺寸/图标组合。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| arrowIcon (颜色) | `grey` / `white` / `orange` / `red` | 4 种颜色 |
| size (尺寸) | `L` / `M` / `S` | 大(18px) / 中(14px) / 小(10px) |
| icon (图标) | `arrow` / `down` / `up` / `close button` | 右箭头 / 向下 / 向上 / 关闭按钮 |

### 尺寸规格

| 尺寸 | 图标大小 |
|------|---------|
| L | 18px |
| M | 14px |
| S | 10px |

### 颜色映射

| 颜色 | 色值 |
|------|------|
| grey | `--辅助信息` (#757575) |
| white | `--反白` (#FFFFFF) |
| orange | `--主色` (#FF6435) |
| red | `--错误色` (#FF1930) |

### 图标类型

| 图标 | 说明 | 用途 |
|------|------|------|
| arrow | 右箭头 (→) | 链接跳转、更多操作 |
| down | 向下箭头 (↓) | 展开状态 |
| up | 向上箭头 (↑) | 收起状态 |
| close button | 关闭按钮 (×) | 关闭、删除操作 |

---

## 七、Status bar（状态栏）

系统状态栏组件，2 种配色。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| 样式 | `白` / `黑` | 白色状态栏 / 黑色状态栏 |

### 规格

| 属性 | 值 |
|------|-----|
| 高度 | 44px |
| 宽度 | 375px |

---

## 八、返回（返回按钮）

导航返回按钮，固定尺寸。

### 规格

| 属性 | 值 |
|------|-----|
| 尺寸 | 40 × 40px |
| 内含图标 | 返回箭头 |

---

## 九、pic（图片占位）

图片占位组件。

### 规格

| 属性 | 值 |
|------|-----|
| 尺寸 | 224 × 120px |
| 用途 | 卡片内图片占位 |

---

## 十、TextLink（文字链接）

文字链接组件，支持 4 种重要性等级和 3 种尺寸。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| importance (重要性) | `Important` / `Secondary` / `Theme` / `Error` | 主要 / 次要 / 主题 / 错误 |
| size (尺寸) | `L` / `M` / `S` | 大 / 中 / 小 |

### 尺寸规格

| 尺寸 | 宽度 | 高度 | 字号 |
|------|------|------|------|
| L | 50px | 18px | 16px |
| M | 46px | 18px | 14px |
| S | 42px | 18px | 12px |

### 颜色映射

| 重要性 | 文字色 | 图标色 |
|--------|--------|--------|
| Important | `--primary` (#FF6435) | `--primary` (#FF6435) |
| Secondary | `--text-secondary` (#757575) | `--text-secondary` (#757575) |
| Theme | `--text-inverted` (白色) | `--text-inverted` (白色) |
| Error | `--error` (#FF1930) | `--error` (#FF1930) |

### 文字规格

- 字体: PingFang SC Regular
- L: 16px，行高 100%
- M: 14px，行高 100%
- S: 12px，行高 100%
- 对齐: 右对齐

### 结构

```
┌──────────────────┐
│  文案    [→]     │
└──────────────────┘
```

- 文案 + 右侧箭头图标
- 箭头图标颜色与文字颜色一致

---

## 十一、ExpandLink（展开/收起链接）

可切换展开/收起状态的文字链接组件，支持 4 种重要性等级和 3 种尺寸。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| importance (重要性) | `Important` / `Secondary` / `Theme` / `Error` | 主要 / 次要 / 主题 / 错误 |
| size (尺寸) | `L` / `M` / `S` | 大 / 中 / 小 |
| state (状态) | `Expand` / `Collapse` | 展开态 / 收起态 |

### 尺寸规格

| 尺寸 | 宽度 | 高度 | 字号 |
|------|------|------|------|
| L | 50px | 18px | 16px |
| M | 46px | 18px | 14px |
| S | 42px | 18px | 12px |

### 颜色映射

| 重要性 | 文字色 | 图标色 |
|--------|--------|--------|
| Important | `--primary` (#FF6435) | `--primary` (#FF6435) |
| Secondary | `--text-secondary` (#757575) | `--text-secondary` (#757575) |
| Theme | `--text-inverted` (白色) | `--text-inverted` (白色) |
| Error | `--error` (#FF1930) | `--error` (#FF1930) |

### 文字规格

- 字体: PingFang SC Regular
- L: 16px，行高 100%
- M: 14px，行高 100%
- S: 12px，行高 100%
- 对齐: 右对齐

### 状态说明

| 状态 | 文案 | 图标方向 |
|------|------|---------|
| Expand | "展开" | 向下箭头 (↓) |
| Collapse | "收起" | 向上箭头 (↑) |

### 结构

```
┌──────────────────┐
│  展开/收起  [↓/↑] │
└──────────────────┘
```

- 文案根据状态切换："展开" / "收起"
- 箭头图标根据状态切换方向
- 图标颜色与文字颜色一致

---

## 十二、Tag（标签）

标签组件，用于状态标记、分类展示，支持多种样式变体。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| size (尺寸) | `Default` / `S` | 默认 / 小 |
| status (状态) | `Default` / `success` / `error` / `tertiary` | 主色 / 成功 / 错误 / 次要 |
| variant (变体) | `outline` / `light` / `solid` | 描边 / 浅色填充 / 实心填充 |

### 尺寸规格

| 尺寸 | 内边距 | 字号 |
|------|--------|------|
| Default | 4px (水平), 1px (垂直) | 12px |
| S | 2px (水平), 0 (垂直) | 12px |

### 样式变体

#### outline（描边）

| 状态 | 边框色 | 文字色 | 背景 |
|------|--------|--------|------|
| Default | `--primary` (#FF6435) | `--primary` (#FF6435) | 透明 |
| success | `--success` (#00B42A) | `--success` (#00B42A) | 透明 |
| error | `--error` (#FF1930) | `--error` (#FF1930) | 透明 |
| tertiary | `--text-tertiary` (#999) | `--text-secondary` (#757575) | 透明 |

#### light（浅色填充）

| 状态 | 背景色 | 文字色 |
|------|--------|--------|
| Default | #FFF0EB | `--primary` (#FF6435) |
| success | #DBFFD7 | `--success` (#00B42A) |
| error | #FFF0EB | `--error` (#FF1930) |
| tertiary | `--surface-canvas` (#F0F1F5) | `--text-secondary` (#757575) |

#### solid（实心填充）

| 状态 | 背景色 | 文字色 |
|------|--------|--------|
| Default | `--primary` (#FF6435) | `--text-inverted` (白) |
| success | `--success` (#00B42A) | `--text-inverted` (白) |
| error | `--error` (#FF1930) | `--text-inverted` (白) |
| tertiary | `--text-tertiary` (#999) | `--text-inverted` (白) |

### 文字规格

- 字体: PingFang SC Regular
- 字号: 12px
- 行高: 100%
- 对齐: 居中
- 圆角: 4px

### 默认使用规范

| 属性 | 默认值 | 说明 |
|------|--------|------|
| variant | `light` | 默认使用浅色填充样式 |
| size | `Default` | 默认使用标准尺寸 |

### 与文字组合间距

当 Tag 与文字横向组合使用时，间距为 **4px**。

```
┌────────────────────────────┐
│  文字内容 ←4px→ [Tag]       │
└────────────────────────────┘
```

### 通用位置规则

Tag 的摆放位置由**语义**决定，与所在容器（Cardheader / 列表行 / 自定义内容区）无关：

| 语义类型 | 说明 | 布局方式 |
|---------|------|---------|
| **状态指示** | 表达该条内容的整体状态（如审核中、已通过） | 放右侧，与左侧内容 `SPACE_BETWEEN` |
| **内容修饰** | 标注文字本身的属性（如类型、来源） | 紧跟文字，inline，间距 4px |

- 同一行内只有一种语义时直接按上表选择
- 若同时存在状态指示和内容修饰，状态指示优先走右侧，修饰 Tag 跟随对应文字

### 状态语义

| 状态 | 语义 | 使用场景 |
|------|------|---------|
| `Default` | 无特定功能含义 | 常规标签、分类标记 |
| `success` | 成功 | 完成、通过、已生效 |
| `error` | 失败 | 错误、拒绝、异常 |
| `tertiary` | 弱化 | 不需关注、已过期、次要信息 |

---

## 十三、Tabs（标签页）

标签页导航组件，用于内容分类切换。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| amount (数量) | `2` / `3` / `4` | 选项卡数量 |
| Property 1 (样式) | `line` | 下划线样式 |
| Active (选中位置) | `1` / `2` / `3` / `4` | 当前选中的 tab 位置（从左到右） |

### 规格

| 属性 | 值 |
|------|-----|
| 宽度 | 375px（使用时 resize 充满屏幕） |
| 高度 | 42px |
| 背景 | 白色 (#FFFFFF) |
| 内边距 | 上 8px，下 4px，左右 8px |
| 选项间距 | 8px (gap) |

### 选项样式

#### 选中状态

| 属性 | 值 |
|------|-----|
| 字体 | PingFang SC Semibold |
| 字号 | 16px |
| 颜色 | `--primary` (#FF6435) |
| 下划线 | 4px 高，圆角 2px，`--primary` (#FF6435)，居中于文字下方 |

#### 未选中状态

| 属性 | 值 |
|------|-----|
| 字体 | PingFang SC Regular |
| 字号 | 16px |
| 颜色 | `--text-secondary` (#757575) |
| 下划线 | 无 |

### 变体数量

| amount | Active 可选值 | 总变体数 |
|--------|-------------|---------|
| 2 | 1 / 2 | 2 |
| 3 | 1 / 2 / 3 | 3 |
| 4 | 1 / 2 / 3 / 4 | 4 |

共 **9 个变体**。

### 使用注意

- 创建实例后必须 `resize(375, inst.height)` 充满屏幕宽度
- 通过 `Active` 属性直接控制选中 tab，**禁止 detach 后手动移动下划线**
- 文字标签通过 override `characters` 设置（组件默认文案为"选中选项/选项二/选项三"）
- `Active` 属性已与下划线位置、文字颜色绑定，切换 Active 即可

### 结构

```
┌─────────────────────────────────────┐ 42px
│  [选中选项]    选项二    选项三  ...  │
│     ━━━                              │ 下划线 4px
└─────────────────────────────────────┘
```

- 选项等宽分布（每格 114px，gap 8px）
- 下划线居中于选中文字下方（28px 宽）

---

## 十四、StatusOverlay（状态蒙层）

叠加在图片上的状态指示组件，用于表达图片所代表条目的状态。

### 属性

| 属性 | 可选值 | 说明 |
|------|--------|------|
| State (状态) | `Success` / `failed` | 成功 / 失败 |

### 规格

| 属性 | 值 |
|------|-----|
| 高度 | 35px |
| 宽度 | 与图片宽度一致 |
| 圆角 | 底部左右 12px（与图片圆角保持一致） |

### 样式

| 状态 | 渐变背景 | 图标 | 文案 |
|------|---------|------|------|
| Success | 从透明到 `#222222` | 成功图标 (✓) | "已通过" |
| failed | 从透明到 `#DE4545` | 失败图标 (×) | "未通过" |

- 渐变方向: 从上到下 (top → bottom)
- 上方透明，下方实色

### 内部布局

| 属性 | 值 |
|------|-----|
| 图标尺寸 | 12 × 12px |
| 图标与文字间距 | 4px |
| 文字颜色 | `--surface-variant` (白色) |
| 字体 | PingFang SC Regular 12px |

### 使用规范

| 规则 | 说明 |
|------|------|
| 最小图片宽度 | 70px（宽度小于 70px 的图片不可使用） |
| 对齐方式 | 与图片底部对齐 |
| 宽度 | 与图片宽度保持一致 |

### 结构

```
┌─────────────────────────┐
│                         │  图片区域
│                         │
│  ┌───────────────────┐  │
│  │ 渐变蒙层           │  │  35px
│  │   [图标] 状态文案   │  │
│  └───────────────────┘  │
└─────────────────────────┘
```

---

## 组件 Figma Node ID 索引

| 组件 | Node ID | 类型 |
|------|---------|------|
| Button Full-width | `1094:4049` | COMPONENT_SET |
| Button | `77:249` | COMPONENT_SET |
| App bars | `80:1476` | COMPONENT_SET |
| CellCard | `1157:534` | COMPONENT |
| Cardheader | `1137:1307` | COMPONENT_SET |
| CardContent | `1136:441` | COMPONENT_SET |
| Alert | `206:196` | COMPONENT_SET |
| arrow | `376:1043` | COMPONENT_SET |
| Status | `199:121` | COMPONENT_SET |
| 返回 | `200:1537` | GROUP |
| TextLink | `376:1006` | COMPONENT_SET |
| ExpandLink | `376:1360` | COMPONENT_SET |
| tag | `478:2904` | COMPONENT_SET |
| tabs | `948:2797` | COMPONENT_SET |
| StatusOverlay | `1026:3723` | COMPONENT_SET |

---

## 组件库 Component Key 索引（用于 importComponentByKeyAsync）

搭建页面时**必须使用以下 Key 导入组件实例**，禁止手动用 Frame 拼装已有库组件。

> **Key 来源**：9.0规范 一致性测试（fileKey: `sxQXbLdcTfITwow8YCnmOJ`），页面：控件。
> 最后更新：2026-05-07，共 14 个组件。

### 生产组件（直接使用）

| 组件 | Component Key | 导入方法 | 变体数 | 用途 |
|------|--------------|---------|-------|------|
| App bars | `c921a6bd03d8d9d7a7193b4dccd244a20a3d84e3` | `importComponentSetByKeyAsync` | 7 | 导航栏 |
| Button Full-width | `6b621371f3ea976291c78391956fb07e6262aefa` | `importComponentSetByKeyAsync` | 5 | 通栏按钮（宽335px） |
| Button | `dca4a53b0ef6207ca79fe5c0cd26ccb1aace01e2` | `importComponentSetByKeyAsync` | 18 | 常规按钮（Large/Medium/Small） |
| Cardheader | 见下方「Cardheader 变体 Key 全索引」 | `importComponentByKeyAsync` | 8 | 卡片头部（set key 已失效，按变体导入）|
| CardContent | `1eb784508622d5d8589b16ecb3b647fe5f5ae5d7` | `importComponentSetByKeyAsync` | 10 | 卡片内容 |
| Status | `e2cfd75d6a1ee02b1d673bd7c0020385eba7f49c` | `importComponentSetByKeyAsync` | 2 | 状态栏（白/黑） |
| Alert | `90d822a0c181cdf093a6227335d60940fa357611` | `importComponentSetByKeyAsync` | 12 | 提示条 |
| TextLink | `73bd920a650aee79c13da0f7df285c9dcefa454f` | `importComponentSetByKeyAsync` | 12 | 文字链接 |
| arrow | `2d404421f74e0ccb4edb41e026db92e3587692a0` | `importComponentSetByKeyAsync` | 48 | 箭头/关闭图标 |
| ExpandLink | `19480cc12ab21bd6f6abd825774e461e66448981` | `importComponentSetByKeyAsync` | 24 | 展开/收起链接 |
| tag | `63e678589ef578e75704394c356d7096512db8d4` | `importComponentSetByKeyAsync` | 24 | 标签（outline/light/solid × Default/success/error/tertiary） |
| tab | `52a34936e697837a9317b62f3606926f8e6587ca` | `importComponentByKeyAsync` | - | amount=3, Active=1 |
| tabs | `948:2797` 整套 | `importComponentSetByKeyAsync` | 9 | 标签页（2/3/4 选项 × Active 1~4） |
| StatusOverlay | `c743e8946f25c9fa190f77709834381b5f60b026` | `importComponentSetByKeyAsync` | 3 | 状态蒙层（Success/failed/None） |
| CellCard | `14733bed207368ed2ae307898d537d8d362fea2c` | `importComponentByKeyAsync` | - | 完整卡片容器，按需展示内容，高度自动收缩。直接实例化使用，详见「CellCard 标准操作流程」 |

### CellCard 标准操作流程

```
Step 1. cellCardComp.createInstance()
Step 2. card.resize(351, card.height) — 只 resize 外层宽度为 351px
        ⚠️ 禁止手动 resize 内部节点（Frame 49、Cardheader、CardContent、Button Full-width）
        内部节点全部是 H=FILL，resize 外层后自动跟随，手动 resize 反而会破坏 FILL 约束
Step 3. 通过 setProperties 控制 Cardheader（先改 VARIANT/BOOLEAN，再 replaceFonts，再改 characters）
Step 4. 通过 setProperties 控制 CardContent（关闭不需要的内容）
Step 5. 隐藏不需要的 Button Full-width（visible=false）
```

⚠️ **禁止批量恢复 visible**：`findAll(n => !n.visible).forEach(n => n.visible = true)` 会破坏规范库默认隐藏的节点状态

### CardContent 变体选择指南

| 业务场景 | 应用变体 | 说明 |
|---------|---------|------|
| 主标题 + 副标题（上下纵排） | `ContentLayout=Editorial` | 单条记录的标题+描述，如"最近任务 / 上传时间" |
| 多列数据（左右横排） | `ContentLayout=list` | 左边正文、右边辅助描述对齐排列 |
| 含图片 | `ContentLayout=Media` | 带图片的内容区 |
| 不需要内容区 | `visible=false` 整个 CardContent 实例 | 如 FAQ 卡片只需要 Cardheader |

### 参考组件（仅供查看，不直接实例化）

| 组件 | Component Key | 说明 |
|------|--------------|------|
| card（旧版） | `75e370d87c58df2c1f3911f730ce3fd6965d8848` | ⚠️ 已废弃，使用 CellCard 代替 |

### 各组件关键属性速查

#### Button Full-width
- TEXT 属性 key：`text#1094:3`
- 变体属性：`Property 1`（Primary/Subtle）、`Property 2`（Default/Visited/Disabled）

#### Button
- TEXT 属性 key：`Button Text`
- 变体属性：`mode`（Primary/Subtle）、`statue`（Default/Vistited/Disabled）、`size`（Large/Medium/Small）

#### Cardheader
- TEXT 属性 key：`header Text#1114:0`（标题）、`SubtitleText#1114:155`（副标题）
- BOOLEAN 属性 key：`ShowSubtitle#578:18`（是否显示副标题）
- 变体属性：`Actiontype`（None/Link/Expand）、`ExpandStated`（none/Expand/Collapsed）
- ⚠️ **必须直接用目标变体创建实例**，禁止先用 None 变体创建再通过 `setProperties` 切换 Actiontype，切换后高度会异常压缩为 19px
- ⚠️ **禁止 resize 高度**，所有变体原始高度均为 46px，resize 高度后放入容器会被压缩
- 正确顺序：① `linkVariant.createInstance()` → ② `resize(w, inst.height)`（只改宽）→ ③ `setProperties`（只改 BOOLEAN/TEXT）→ ④ `replaceFonts` → ⑤ 改 `characters`

#### CardContent
- TEXT 属性 key：`TitleText#1137:0`（正文标题）、`DescriptionText #1114:132`（描述）
- BOOLEAN 属性 key：`Show Title Medium#578:20`、`  ShowDescription#1146:21`、`ShowFloatingButton#578:22`、`Show TagGroup#578:24`
- 变体属性：`surface`（pure/subtle）、`ContentLayout`（Editorial/list/Media）、`Media size`（None/Large/Medium）、`Action`（None/Floating）

#### tag
- 变体属性：`size`（Default/S）、`Variant`（outline/light/solid）、`Status`（Default/success/error/tertiary）
- 常用组合：待上传 → `Variant=light, Status=Default`；审核中 → `Variant=light, Status=success`；未通过 → `Variant=light, Status=error`

#### App bars
- 变体属性：`类型`（Flat/Text/None/Icon/Flat white/Text white/None white）
- 原始尺寸：**375×88px**（含内嵌 Status 44px + 导航栏 44px），创建实例后**禁止 resize**，保持原始高度
- ⚠️ **App bars 内部已内嵌 Status 实例**，页面中只需放置 App bars 一个实例，**禁止再单独放置 Status 实例**，否则状态栏会重叠显示两次
- ⚠️ **内容区起始 y 固定为 88**，不能用 `instance.height`（返回值不可靠）推算
- ⚠️ PingFang SC 字体不可用时，需先对实例内 TEXT 节点替换字体（Noto Sans SC），再修改 `characters`，不能直接 `setProperties`

#### Status
- 变体属性：`类型`（白/黑）
- ⚠️ **仅在不使用 App bars 的页面中单独使用**（如全屏沉浸式页面）。普通页面直接用 App bars 即可，App bars 内已包含 Status

#### tabs（按 Active 位置索引）

| 变体 | Key |
|------|-----|
| amount=2, Active=1 | `0eb03b529dcdf91ae914cd39b0432bce2a714383` |
| amount=2, Active=2 | `fb5165fa6d71b16b140d6218f6f93da964a8f0c3` |
| amount=3, Active=1 | `52a34936e697837a9317b62f3606926f8e6587ca` |
| amount=3, Active=2 | `6c66c98e4776b47931badcb160f14b8ed9106987` |
| amount=3, Active=3 | `0794972f8000cd0cc37635e037df1d77dbc8053a` |
| amount=4, Active=1 | `add69127a2449e2cfe8068705807a5ba0647b899` |
| amount=4, Active=2 | `04c0c0de352e58200509066901466fff33c3f9fd` |
| amount=4, Active=3 | `ff4d912d9c949646aa4e186ab27821ab0d64c099` |
| amount=4, Active=4 | `08ad9e592afac4d2418675a4ed85667b47847ae1` |

使用方式：直接按需导入对应 Active 位置的 Key，resize 到 375px，再 override 文字标签。

#### Cardheader 变体 Key 全索引

> ⚠️ 原 set key `fe4ada0b...` 已失效。按需导入目标变体，使用 `importComponentByKeyAsync`。
> 当前 set key（仅供参考，不用于导入）：`8778e924ba8176734e13ff29d1700f08ad8ddfa4`

| Actiontype | ShowTag | ExpandStated | Key |
|------------|---------|-------------|-----|
| `None` | `false` | `none` | `078d8ad09c66c27a93f80582b9352d1016db41e3` |
| `None` | `true` | `none` | `2c9fa67ef9e75199d4dfe02953c9817d6e4f4ffe` |
| `Link` | `false` | `none` | `f403ed7b48474886de9ca046708fa0bdcc6cab99` |
| `Link` | `true` | `none` | `227417125ef5d4ad9fd6f02d69f59d61fcc725ee` |
| `Expand` | `false` | `Expand`（展开态） | `066cece92b4e300fce83e2ac3e0a1d9159997adb` |
| `Expand` | `true` | `Expand`（展开态） | `0dbcb32095cc1c7e122dafd9ab7682702af9e1b7` |
| `Expand` | `false` | `Collapsed`（收起态） | `bcb22d11e8f98996ce95fec8c8a3254539e7b6b1` |
| `Expand` | `true` | `Collapsed`（收起态） | `facaabe44a44b787637532e9da7a61536e162380` |

```js
// 示例：导入 Link 类型、无 Tag 的 Cardheader
const comp = await figma.importComponentByKeyAsync("f403ed7b48474886de9ca046708fa0bdcc6cab99");
const inst = comp.createInstance();
```

#### tabs
- 变体属性：`Property 1`（line）、`amount`（2/3/4）、`Active`（1/2/3/4，控制选中 tab 位置）
- 使用 `Active` 属性直接切换选中状态，**禁止 detach 后手动移动下划线**
- 创建后必须 `resize(375, inst.height)` 充满屏幕

#### StatusOverlay
- 变体属性：`State`（Success/failed/None）

> 如需查找更多组件，使用 `search_design_system` 并限定 libraryKey:
> `lk-2da8834b5155e15c43aaff36eb3d6dfd723be0037508c3655ce7ee6ff6915f7514fbedede0db3112d0b39eec678b7cb800311cfbc5084939677f5fa9b42fff39`
