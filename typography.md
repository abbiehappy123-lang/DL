# 字体规范

## 一、字族 (Font Theme)

| Token | 字族 | 用途 |
|-------|------|------|
| `Text` | PingFang SC | 中文文本 |
| `Number` | Barlow Semi Condensed | 数字/英文展示 |

### 字重映射

| Token | 实际字重 |
|-------|---------|
| `Regular` | Regular |
| `Medium` | Medium |
| `Bold` | SemiBold |
| `SemiBold` | Bold |

## 二、文本样式 (Text Styles)

文本样式按分组命名，格式为 `分组/样式名`。

> 注：Figma 中 Headline 分组拼写为 `Healine`，Label 分组拼写为 `Lable`（均为原始拼写）。

### Display 展示类（数字字体 Barlow Semi Condensed）

| 样式名 | Figma 路径 | 字族 | 字重 | 字号 | 行高 | 用途 |
|--------|-----------|------|------|------|------|------|
| Display Large | `Display/Display large` | Barlow Semi Condensed | SemiBold | 45px | Auto | 超大数字展示 |
| Display Medium | `Display/Display Medium` | Barlow Semi Condensed | Bold | 36px | Auto | 大数字展示 |
| Display Small | `Display/Display small` | Barlow Semi Condensed | Bold | 30px | Auto | 中数字展示 |
| Display small数字2 | `Display/small数字2` | Barlow Semi Condensed | Bold | 27px | Auto | 小数字展示 |

### Headline 标题类（中文字体 PingFang SC）

| 样式名 | Figma 路径 | 字族 | 字重 | 字号 | 行高 | 用途 |
|--------|-----------|------|------|------|------|------|
| Headline Large | `Healine/Headline Large` | PingFang SC | Semibold | 22px | Auto | 页面大标题 |
| Headline Medium | `Healine/Headline Medium` | PingFang SC | Semibold | 18px | Auto | 区块标题 |
| Headline Small | `Healine/Headline Small` | PingFang SC | Semibold | 16px | Auto | 卡片/小标题 |

### Title 次标题类

| 样式名 | Figma 路径 | 字族 | 字重 | 字号 | 行高 | 用途 |
|--------|-----------|------|------|------|------|------|
| Title | `Title/Title` | PingFang SC | Semibold | 16px | Auto | 列表项标题 |
| Title Medium | `Title/Title Medium` | PingFang SC | Semibold | 14px | Auto | 次级标题/按钮文字 |
| Title 2 (Typescale) | — | PingFang SC | Semibold | 16px | Auto | 备用标题 |

### Body 正文类

| 样式名 | Figma 路径 | 字族 | 字重 | 字号 | 行高 | 用途 |
|--------|-----------|------|------|------|------|------|
| Body Large | `Body/Body Large` | PingFang SC | Regular | 14px | Auto | 正文/描述 |
| Body Medium | `Body/Body Medium` | PingFang SC | Regular | 12px | Auto | 辅助正文 |

### Label 标签类

| 样式名 | Figma 路径 | 字族 | 字重 | 字号 | 行高 | 用途 |
|--------|-----------|------|------|------|------|------|
| Label Large | `Lable/Lable Large` | PingFang SC | Regular | 12px | Auto | 标签/注释 |
| Label Medium | `Lable/Lable Medium` | PingFang SC | Regular | 11px | Auto | 小标签/角标 |

## 三、Typescale Variables (字号变量)

完整的字号阶梯，可用于代码中动态引用：

| 层级 | Font | Weight | Size |
|------|------|--------|------|
| Display Large | Barlow Semi Condensed | SemiBold | 45 |
| Display Medium | Barlow Semi Condensed | Bold | 36 |
| Display Small | Barlow Semi Condensed | Bold | 30 |
| Headline Large | PingFang SC | SemiBold | 22 |
| Headline Medium | PingFang SC | SemiBold | 18 |
| Headline Small | PingFang SC | SemiBold | 16 |
| Title Large | PingFang SC | SemiBold | 16 |
| Title Medium | PingFang SC | SemiBold | 12 |
| Title 2 | PingFang SC | SemiBold | 16 |
| Body Large | PingFang SC | Regular | 14 |
| Body Medium | PingFang SC | Regular | 12 |
| Label Large | PingFang SC | Regular | 14 |
| Label Medium | PingFang SC | Regular | 11 |

## 四、字号速查

| 字号 | 对应样式 |
|------|---------|
| 45px | Display Large |
| 36px | Display Medium |
| 30px | Display Small |
| 27px | Display small数字2 |
| 22px | Headline Large |
| 18px | Headline Medium |
| 16px | Headline Small / Title / Title 2 |
| 14px | Title Medium / Body Large / Label Large |
| 12px | Body Medium / Label Large |
| 11px | Label Medium |
