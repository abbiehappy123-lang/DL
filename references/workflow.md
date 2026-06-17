# 页面搭建工作流

基于 9.0 规范在 Figma 中搭建页面的标准流程。

---

## 🚦 出图标准检查清单（每次出图必须按顺序执行）

### 阶段一：出图前准备
- [ ] **0. 输出内容确认表并等待用户确认**，再写任何代码。格式如下，用户只需确认内容正确，无需了解组件细节；内部同步完成组件映射：
  ```
  ## 出图前确认

  | 模块 | 展示内容 | 状态/变体 |
  |------|----------|----------|
  | 任务卡片 | 标题 + 截止时间 + 去上传按钮 | 待办 / 空状态 / 多任务 |
  | 历史任务入口 | 标题 + 最近一条记录 + 查看全部 | — |
  ```
  内部同步维护的组件映射（不对用户展示）：
  ```
  任务卡片 → CellCard（CardHeader None+Subtitle, Content=false, Button idx=2）
  历史任务 → CellCard（CardHeader Link, Content Editorial, Button 全隐藏）
  FAQ     → CellCard（CardHeader Link, Content 隐藏, Button 全隐藏）
  标签    → tag 库实例
  ```
- [ ] **1. 阅读 PRD，整理文案清单**：把页面所有需要显示的文案逐条列出，后续每加一个文字节点都要核对，没有的文案一律不加
- [ ] **1.1 PRD 有歧义或信息缺失时，必须向用户二次确认，等待明确答复后再继续**：禁止自行推测或补全 PRD 未明确的内容；确认问题须一次性列出，不可逐条打断用户
- [ ] **2. 去规范库验证 skill**：打开规范库文件（`sxQXbLdcTfITwow8YCnmOJ`）查询当前组件列表，与 `components.md` 对比，发现不一致立即更新 skill，再开始出图
- [ ] **3. 做组件映射表**：把页面每个模块对应的库组件列出来，只有确认库里不存在对应组件时，才手动创建

### 阶段二：出图中规范
- [ ] **4. App bars 尺寸确认**：原始尺寸 375×88px，禁止 resize 高度，内容区起始 y 固定为 88，不使用 `instance.height` 推算
- [ ] **5. 按 CellCard 标准操作流程**（见下方）
- [ ] **6. 所有 Frame 通过 `createAutoFrame` 封装函数创建，禁止直接调用 `figma.createFrame()`**：
  ```js
  function createAutoFrame(name, layoutMode = 'VERTICAL') {
    const f = figma.createFrame();
    f.name = name;
    f.layoutMode = layoutMode;
    f.primaryAxisSizingMode = 'AUTO';
    f.counterAxisSizingMode = 'FIXED';
    f.fills = [];
    return f;
  }
  ```
- [ ] **7. 组件报错必须继续排查原因，不得降级为手动拼装**：Key 失效 → 尝试其他导入方式；setProperties 报错 → 检查属性值大小写和可选值
- [ ] **8. `visible=false` 节点若需脱离布局流，必须检查 `layoutPositioning`**：实例内部节点无法直接修改时，记录为已知限制，不绕过
- [ ] **9. 每完成一个模块立即截图验证**：不要等全部完成再看，发现问题及时修复

### 阶段三：出图后核对
- [ ] **10. 对照 PRD 文案清单逐条核对**：删除所有不在 PRD 里的文案和内容
- [ ] **11. 检查所有节点类型**：确认没有违规的手动 Frame/Text 拼装库组件

---

## ✅ 交付前自查清单（输出前逐项确认，不可跳过）

> 参考 br-fintech p0-rules 机制引入。每次生成完毕、截图/交付前，必须逐项过一遍。有任何一项为「否」，立即修复再交付。

### Token 正确性
- [ ] 所有颜色值是否来自 `colors.md` 中的变量，没有凭记忆写入的 hex？
- [ ] 是否使用了 `--text-primary: #222222`，没有出现 `#000000` 纯黑？
- [ ] 页面底色是否为 `#F0F1F5`，卡片色是否为 `#FFFFFF`，没有混用？
- [ ] 间距和圆角值是否与 `spacing.md` 中的 4px 阶梯吻合？

### 视觉质量

> 待补充（对应 custom-rules.md「视觉质量量化铁律」）。

### 组件规范
- [ ] 所有 UI 组件是否优先使用了库实例，没有手动拼装库中已有的组件？
- [ ] 所有组件实例是否已完成「组件三问」（文本填写 / 多余元素隐藏 / 属性修改）？
- [ ] 没有占位文（「正文内容示意」「副标题信息内容示意」等）残留在画面中？

### 文案与内容
- [ ] 页面内所有文案是否均来自 PRD 文案清单，没有 AI 自行补全的内容？
- [ ] 空状态是否只显示 PRD 指定文案，没有自行添加副文案？

### 布局结构
- [ ] Phone frame 宽度是否为 375px，没有使用 390px？
- [ ] 卡片宽度是否为 351px，左右各 12px margin？
- [ ] Home Indicator 颜色是否与背景匹配（浅背景→黑色，深背景→白色）？

---

## ⚠️  执行前必读

**在写任何 use_figma 代码前，必须完成 Step 1-2（检查文件 + 搜索导入组件）。**
**违反此流程的后果：手动拼装、字体不匹配、无法复用更新。**

## 开始前必读 ⚠️

**在写任何 use_figma 代码前，必须回答这些问题：**

- [ ] 我列出了页面需要的所有组件了吗？
- [ ] 我查过 `components.md` 索引表了吗？
- [ ] 我用 `search_design_system` 搜索过所有需要的组件了吗？
- [ ] 我导入了所有能用的库组件了吗？
- [ ] 我现在要 `createFrame` / `createText` / `createRectangle` 的东西，**确定库里没有**吗？

**如果任何一个答案是"否"，立即停下来，先完成它。**

违反这个检查清单的后果：
- 手动拼装的组件缺少系统图标、插图、正确的分割线实现
- 字体、字重、颜色不匹配规范
- 无法复用设计系统的更新
- 增加维护成本

## 核心原则

**必须优先使用组件库实例，禁止手动拼装已有库组件。**

手动用 Frame/Rectangle/Text 拼装会导致：
- 状态栏缺少系统图标（时间、电池、WiFi、信号）
- 分割线实现方式错误（矩形 vs inner shadow）
- 图片/插图丢失（灰色占位 vs 实际插图）
- 图标细节不准确（手绘 vector vs 原始图标）
- 字体/字重不匹配

## 标准流程

### Step 1：检查目标文件

```js
// 查看文件现有页面和内容
const pages = figma.root.children.map(p => `${p.name} id=${p.id}`);
return pages;
```

### Step 2：搜索并导入组件库

**这一步是强制性的，不可跳过。**

#### 2.1 列出页面所需的所有组件

在写任何代码前，先列出页面需要的所有 UI 元素：
- 导航栏 → App bars
- 按钮 → Button / Button Full-width
- 卡片 → card / CellCard
- 标签页 → tabs
- 标签 → Tag
- 提示条 → Alert
- 状态栏 → Status
- 返回按钮 → 返回
- 文字链接 → TextLink / ExpandLink
- 图标 → arrow
- 状态蒙层 → StatusOverlay

#### 2.2 查找 Component Key

**先查 `components.md` 中的 Component Key 索引表**，直接使用已知的 Key 导入。

如果索引表中没有需要的组件，再用 `search_design_system` 搜索：

```
search_design_system(
  query: "组件名",
  fileKey: "目标文件Key",
  includeLibraryKeys: ["lk-2da8834b5155e15c43aaff36eb3d6dfd723be0037508c3655ce7ee6ff6915f7514fbedede0db3112d0b39eec678b7cb800311cfbc5084939677f5fa9b42fff39"]
)
```

#### 2.3 一次性导入所有组件

**不要边写边导入**，先把所有需要的组件都导入好：

```js
// 一次性导入所有需要的组件
const appBarCompSet = await figma.importComponentSetByKeyAsync("c921a6bd...");
const buttonCompSet = await figma.importComponentSetByKeyAsync("cc277429...");
const cardComp = await figma.importComponentByKeyAsync("75e370d8...");
const tabsCompSet = await figma.importComponentSetByKeyAsync("tabs_key...");
// ... 导入所有需要的组件

// 然后再开始创建实例
```

### Step 3：导入组件

```js
// 组件集（有变体）
const compSet = await figma.importComponentSetByKeyAsync("component_key");
const variant = compSet.children.find(c => c.name.includes("Flat"));
const instance = variant.createInstance();

// 单一组件
const comp = await figma.importComponentByKeyAsync("component_key");
const instance = comp.createInstance();
```

### Step 4：创建页面框架

```js
const phone = figma.createFrame();
phone.name = "iPhone 14 - 页面名称";
phone.resize(375, 812);
phone.fills = [{ type: 'SOLID', color: { r: 240/255, g: 241/255, b: 245/255 } }]; // #F0F1F5
phone.layoutMode = 'VERTICAL';
phone.clipsContent = true;
```

### Step 5：放置库组件实例

按页面结构从上到下放置：

```js
// 1. App bars（导入 Flat 变体）
phone.appendChild(appBarInstance);
appBarInstance.layoutSizingHorizontal = 'FILL';

// 2. 内容区域（手动创建，因为是自定义布局）
const content = figma.createFrame();
content.layoutMode = 'VERTICAL';
phone.appendChild(content);
content.layoutSizingHorizontal = 'FILL';
content.layoutSizingVertical = 'FILL';

// 3. 底部按钮（导入 Button Full-width Primary Default 变体）
phone.appendChild(buttonInstance);
```

**⚠️ 关键检查点：**

在这一步，每次要 `createFrame()` / `createText()` / `createRectangle()` 前，问自己：
- **这个元素库里有现成的组件吗？**
- **我是不是应该用库组件实例而不是手动创建？**

如果不确定，回到 Step 2.1 的组件清单，或者重新搜索 `search_design_system`。

### Step 6：定制实例内容

```js
// 修改文本 — 先查找文本节点，加载字体后再修改
const titleNode = instance.findOne(n => n.type === 'TEXT' && n.characters === '标题文案');
// 先尝试加载原字体
try {
  await figma.loadFontAsync(titleNode.fontName);
} catch(e) {
  // 原字体不可用时替换为 Noto Sans SC
  await figma.loadFontAsync({ family: "Noto Sans SC", style: "Bold" });
  titleNode.fontName = { family: "Noto Sans SC", style: "Bold" };
}
titleNode.characters = "新标题";

// 切换变体
instance.setProperties({ "Property 1": "Flat" });
```

### Step 7：手动构建自定义部分

**只有组件库中不存在的部分才手动构建**，例如：
- CellCard 内的 Body 信息网格（自定义键值对布局）
- 自定义的内容组合
- 特定业务逻辑的排列

**再次确认：**
- 我要手动创建的这个元素，**真的**在组件库里找不到吗？
- 我检查过 `components.md` 的完整列表了吗？
- 我用 `search_design_system` 搜索过了吗？

如果以上任何一个答案是"否"，回到 Step 2。

### Step 8：截图验证

```
get_screenshot(fileKey, nodeId)
```

## 字体回退策略

9.0 规范指定字体为 PingFang SC，但该字体在部分 Figma 环境中不可用。

| 规范字体 | 回退字体 |
|---------|---------|
| PingFang SC Semibold | Noto Sans SC Bold |
| PingFang SC Regular | Noto Sans SC Regular |
| Barlow Semi Condensed | Barlow Semi Condensed（通常可用） |

回退步骤：
1. 先尝试 `loadFontAsync({ family: "PingFang SC", style: "Semibold" })`
2. 若失败，使用 `loadFontAsync({ family: "Noto Sans SC", style: "Bold" })`
3. 对库组件实例中的文本，需先设 `fontName` 再改 `characters`

## 常见错误清单

| 错误做法 | 正确做法 |
|---------|---------|
| 手动用 Frame 拼装 App bars | 导入库组件 Flat 变体实例 |
| App bars 之外额外单独放 Status 实例 | App bars 内已内嵌 Status，只放 App bars 一个实例即可 |
| 空白 Frame 做状态栏 | 使用库中的 Status 组件（已含时间/电池/WiFi/信号） |
| 矩形做底部分割线 | App bars Flat 变体自带 inner shadow 分割线 |
| 手绘 vector 做返回按钮 | 库中的 App bars 已包含标准返回图标 |
| 手动构建 Button Full-width | 导入库组件 Primary/Default 变体实例 |
| iPhone 框架高度被 HUG 压缩 | `resize(375, 812)` 后设 `primaryAxisSizingMode = 'FIXED'` |
| HORIZONTAL 布局行高默认 100px | 设 `counterAxisSizingMode = 'AUTO'` 使高度 HUG 内容 |
| 直接调用 `figma.createFrame()` | 必须用 `createAutoFrame()` 封装函数，默认 `primaryAxisSizingMode = 'AUTO'` |
| 组件 Key 失效或 setProperties 报错就改为手动拼装 | 必须继续排查：检查 Key 是否过期、属性值大小写、可选值枚举 |
| `visible=false` 认为不占布局空间 | `visible=false` 在 AutoLayout 中仍占位，需检查 `layoutPositioning` |
| 用库中语义不符的组件凑合（如用 Alert warning 表达 error） | 库中无合适变体时手动构建，手动构建是合规的最后手段 |
| 通过 `setProperties` TEXT key 写文案（如 `TitleText#xxx`） | 用 `findOne(n => n.type === 'TEXT')` 找节点后直接赋值，先 `loadFontAsync` 再替换字体 |
| 切换实例变体后不 `resetOverrides()` 直接填文案 | 对已有实例修改变体前必须先 `instance.resetOverrides()`，再重新 `setProperties` + 填文案 |
| 假设 `setProperties` 写入即生效 | 写入后必须回读 `instance.componentProperties['xxx'].value` 验证，尤其是 ShowSubtitle、ShowTag、visible |
| 展开/收起交互用 `Actiontype=Link` | 展开/收起必须用 `Actiontype=Expand`：`ExpandStated=Expand`（展开按钮）/ `ExpandStated=Collapsed`（收起按钮） |
| 需要展示图片时 CardContent 沿用默认 `Editorial` 布局 | 必须显式设置 `ContentLayout=Media`，`Media size=Large`；Media Large 内置 StatusOverlay，直接 `findOne` 后 `setProperties({ State: 'failed/Success/None' })` |
| 先 `resize(375, 10)` 写死高度再改 `primaryAxisSizingMode = 'AUTO'` | `AUTO` 模式不会重算已被 resize 写死的高度。**正确做法：创建 Frame 时直接设 `primaryAxisSizingMode = 'AUTO'`，完全不调用 `resize()` 设高度，只用 `counterAxisSizingMode = 'FIXED'` 控制宽度** |
| 实例内部深层节点被破坏后尝试 `resize()` 修复 | 实例内节点尺寸被实例锁定，外部 `resize()` 会被还原。**正确做法：重新 `createInstance()` 整个组件替换；设置文字时只碰 TEXT 节点，绝不连带改其他元素** |
| 修复一个页面的问题后就结束 | 修复一类问题后必须全量扫描所有页面是否存在相同问题，尤其是不同批次/单独创建的元素易被遗漏 |
| 对绝对定位节点设 `layoutSizingHorizontal = 'FILL'` | 绝对定位节点（`layoutPositioning === 'ABSOLUTE'`，如 AppBar 标题）不支持 FILL，会报错。设前必须判断：`if (node.layoutPositioning !== 'ABSOLUTE') { node.layoutGrow = 1; node.layoutSizingHorizontal = 'FILL'; }` |
| 仅凭截图判断对齐/布局是否正确 | 截图视觉正常 ≠ 数据层正确（x=128 却看起来左对齐）；截图异常也可能是旧缓存（数据层已正确但截图未刷新）。**数据层 x/y 坐标自查（`Math.round(node.x) === 0`）才是唯一可靠验证手段，截图只作辅助参考** |

---

## setProperties 操作规范

### 文案设置（禁止用 TEXT key）

```js
// ❌ 错误：TEXT key 会因组件内字体不可用而报错
instance.setProperties({ 'TitleText#1137:0': '仪容车貌反馈' });

// ✅ 正确：直接找到 TEXT 节点赋值
const titleNode = instance.findOne(n => n.type === 'TEXT' && n.name === 'header');
try { await figma.loadFontAsync(titleNode.fontName); } catch(e) {}
titleNode.fontName = { family: "Noto Sans SC", style: "Bold" };
titleNode.textAutoResize = 'WIDTH_AND_HEIGHT';
titleNode.characters = '仪容车貌反馈';
```

### 切换变体前必须 resetOverrides

```js
// ❌ 错误：直接 setProperties，旧变体的 position override 残留
header.setProperties({ 'ShowTag': 'true', 'Actiontype': 'Expand' });

// ✅ 正确：先 reset，再 set，再填文案
header.resetOverrides();
header.setProperties({ 'ShowTag': 'true', 'Actiontype': 'Expand', 'ExpandStated': 'Expand' });
// 然后重新填写所有文案 override
```

### 写入后必须回读验证

```js
header.setProperties({ 'ShowSubtitle#578:18': true });

// ✅ 回读验证
const actual = header.componentProperties['ShowSubtitle#578:18']?.value;
if (actual !== true) {
  // 值未生效，检查变体组合是否合法，或换其他方式设置
}
```

### 实例内部节点被破坏时：重新实例化，不要 resize

```js
// ❌ 错误：实例内深层节点（如 tab 的 underline）被撑宽，resize 改不动
underline.resize(32, underline.height); // 回读仍是旧值，被实例还原

// ✅ 正确：重新实例化整个组件替换
const comp = await figma.importComponentByKeyAsync(tabKey);
const fresh = comp.createInstance();
parent.insertChild(oldIndex, fresh);
fresh.layoutSizingHorizontal = 'FILL';
// 设置文字时只碰 TEXT 节点，绝不连带改 underline 等其他元素
const texts = fresh.findAll(n => n.type === 'TEXT');
for (let i = 0; i < texts.length; i++) {
  texts[i].fontName = { family: "Noto Sans SC", style: i === activeIdx ? "Bold" : "Regular" };
  texts[i].characters = labels[i];
}
oldTabs.remove();
```

**原则**：设置实例文字时，操作范围严格限定在目标 TEXT 节点，不要因为 textAutoResize 或其他副作用波及兄弟元素（underline、图标等）。

## 修复后全量排查

修复任何一类问题后，必须在**所有页面/画板**扫描同类问题，不能只改当前看到的页面。

```js
// 全量排查示例：检查所有页面所有卡片的 header 标题 / Body 是否 x 偏移
const allPages = [/* 所有画板 id */];
const problems = [];
for (const pgId of allPages) {
  const page = figma.getNodeById(pgId);
  const container = page.findOne(n => n.name === 'Content' || n.name === 'ScrollArea');
  for (const card of container.children) {
    const title = card.findOne(n => n.type === 'TEXT' && n.name === 'header');
    if (title && Math.round(title.x) !== 0) problems.push(`${page.name}: 标题 x=${Math.round(title.x)}`);
    // ...其他检查项
  }
}
return problems;
```

**重点关注**：不同批次创建、或单独手工搭建的元素（如早期建的空状态卡片），最容易遗漏统一修复。
