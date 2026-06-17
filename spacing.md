# 间距与圆角

## 一、基础数值 (Number Primitives)

基础数值 token，供间距和圆角引用。

| Token | 值 |
|-------|-----|
| `Number/Number0` | 0 |
| `Number/Number2` | 2 |
| `Number/Number4` | 4 |
| `Number/Number8` | 8 |
| `Number/Number10` | 10 |
| `Number/Number12` | 12 |
| `Number/Number14` | 14 |
| `Number/Number16` | 16 |
| `Number/Number20` | 20 |
| `Number/Number24` | 24 |
| `Number/Number32` | 32 |
| `Number/Number 48` | 48 |
| `Number/Number 64` | 64 |

### 描边

| Token | 值 |
|-------|-----|
| `Stroke/Number0` | 0 |
| `Stroke/Number1` | 1 |

## 二、圆角 (Radius)

| Token | 值 | 用途 |
|-------|-----|------|
| `None` | 0px | 无圆角 |
| `Extra-small` | 4px | 小标签/小元素 |
| `Small` | 8px | medium toast / 子卡片内部的更小元素 |
| `Medium` | 12px | 输入框 / large卡片内子卡片（如 subtle 内容区） |
| `Large` | 16px | 页面级卡片容器 |
| `Extra-large` | 30px | 底部弹出面板 |
| `Full` | 1000px | 全圆/胶囊按钮 |

## 三、间距 (Space)

### Space 层级

| Token | 值 | 引用 |
|-------|-----|------|
| `space/space/2xs` | 2px | → Number2 |
| `space/space/xs` | 4px | → Number4 |
| `space/space/sm` | 8px | → Number8 |
| `space/space/md` | 12px | → Number12 |
| `space/space/lg` | 16px | → Number16 |
| `space/space/extra lg` | 20px | → Number20 |
| `space/space/extra  extra lg` | 24px | → Number24 |

### Layout 布局

| Token | 值 | 引用 |
|-------|-----|------|
| `space/New group/layout/margin` | 12px | → Number12 |
| `space/New group/layout/gutter` | 8px | → Number8 |

## 四、Padding 内边距

| Token | 值 | 引用 |
|-------|-----|------|
| `padding/xs` | 4px | → Number4 |
| `padding/sm` | 8px | → Number8 |
| `padding/md` | 16px | → Number16 |
| `padding/lg` | 24px | → Number24 |

### Gap 间隔

| Token | 值 | 引用 |
|-------|-----|------|
| `padding/gap/icon` | 4px | → Number4 |
| `padding/gap/text` | 4px | → Number4 |
| `padding/gap/card` | 12px | → Number12 |
| `padding/gap/text inline` | 4px | → Number4 |
| `padding/gap/text stack` | 4px | → Number4 |
| `padding/gap/button-group` | 12px | → Number12 |

## 五、Responsive（响应式）

| Token | 值 | 说明 |
|-------|-----|------|
| `Device` | `mobile` | 设备类型 |
| `Device Width` | 375 | 设备宽度 |
| `Root Font Size` | 16 | 根字号 |
| `Scale` | 1.25 | 缩放系数 |

## 六、Stroke（描边）

| Token | 值 | 引用 |
|-------|-----|------|
| `stroke/none` | 0 | → Stroke/Number0 |
| `stroke/thin` | 1 | → Stroke/Number1 |

## 七、Grid（栅格）

空集合，暂无变量定义。
