# 阴影/层级体系

5 级投影体系，由低到高表达不同层次的组件浮起高度。

统一阴影颜色基底: `#0F284D`（深蓝色调），通过不同透明度区分层级。

## 层级定义

| 层级 | 样式名 | Y偏移 | 模糊半径 | 透明度 | 用途 |
|------|--------|-------|---------|--------|------|
| Level 1 | `low基础卡片` | 4px | 12px | 6% | 基础卡片、列表项 |
| Level 2 | `Mid地图上浮组件` | 8px | 24px | 8% | 地图浮层、悬浮组件 |
| Level 3 | `High重点操作` | 12px | 24px | 8% | 重点操作浮层 |
| Level 4 | `Overlay强分层组件` | 16px | 32px | 10% | 弹窗/模态框/Overlay |
| Level 5 | `Top全局最高层` | 30px | 50px | 12% | 全局最高层级 |

## 详细参数

### Level 1 — low基础卡片
```
box-shadow: 0px 4px 12px rgba(15, 40, 77, 0.06)
```

### Level 2 — Mid地图上浮组件
```
box-shadow: 0px 8px 24px rgba(15, 40, 77, 0.08)
```

### Level 3 — High重点操作
```
box-shadow: 0px 12px 24px rgba(15, 40, 77, 0.08)
```

### Level 4 — Overlay强分层组件
```
box-shadow: 0px 16px 32px rgba(15, 40, 77, 0.10)
```

### Level 5 — Top全局最高层
```
box-shadow: 0px 30px 50px rgba(15, 40, 77, 0.12)
```

## 使用指引

- 基础卡片、列表项 → Level 1
- 地图上浮按钮、浮动工具栏 → Level 2
- 关键操作区域、底部操作栏 → Level 3
- 弹窗、模态对话框、侧边栏 → Level 4
- Toast、全局通知、最高优先级浮层 → Level 5
