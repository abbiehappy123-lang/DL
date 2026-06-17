# 颜色体系

## 一、基础色板 (_Primitives)

基础色值定义，供语义色引用。

| Token 名称 | 色值 | 用途 |
|------------|------|------|
| `Color/主色` | `#FF6435` | 品牌主色 |
| `Color/辅助色` | `#FFB19A` | 辅助/完成态色 |
| `Color/驾驶色` | `#222444` | 驾驶模式主色 |
| `Color/驾驶环境色` | `#222444` | 驾驶环境背景色 |
| `Color/错误色` | `#FF1930` | 错误/危险 |
| `Color/标题` | `#222222` | 标题文字色 |
| `Color/正文` | `#444444` | 正文文字色 |
| `Color/辅助信息` | `#757575` | 辅助信息文字色 |
| `Color/次要信息` | `#999999` | 次要信息文字色 |
| `Color/灰态` | `#CCCCCC` | 禁用/灰态色 |
| `Color/反白` | `#FFFFFF` | 白色/反白 |
| `Color/分割线色` | `#EBECF2` | 分割线/描边 |
| `Color/全局背景色` | `#F0F1F5` | 页面背景色 |
| `Color/局部填充色` | `#F6F8FB` | 卡片/区块填充色 |
| `Color/成功色` | `#00B42A` | 成功/正确状态 |

## 二、语义色 (Primary Set)

语义化引用基础色，用于组件和界面。

### 品牌色

| Token | 色值 | 引用 |
|-------|------|------|
| `primary` | `#FF6435` | → Color/主色 |
| `on primary` | `#FFFFFF` | → Color/反白 |
| `primary container` | `#FFDBCF` | 品牌容器背景 |
| `on primary container` | `#3E1000` | 品牌容器上文字 |
| `secondary` | `#FFB19A` | → Color/辅助色 |
| `on secondary` | `#FFFFFF` | → Color/反白 |

### 表面色

| Token | 色值 | 引用 |
|-------|------|------|
| `surface canvas` | `#F0F1F5` | → Color/全局背景色 |
| `surface default` | `#FFFFFF` | → Color/反白 |
| `surface variant` | `#FFFFFF` | → Color/反白 |
| `surface inset` | `#F6F8FB` | → Color/局部填充色 |

### 边框/分割

| Token | 色值 | 引用 |
|-------|------|------|
| `outline default` | `#EBECF2` | → Color/分割线色 |
| `border active` | `#FF6435` | → Color/主色 |

### 状态色

| Token | 色值 | 引用 |
|-------|------|------|
| `error` | `#FF1930` | → Color/错误色 |
| `success` | `#00B42A` | → Color/成功色 |
| `disable` | `#CCCCCC` | → Color/灰态 |
| `on disable` | `#FFFFFF` | → Color/反白 |

## 三、文字色

| Token | 色值 | 引用 | 用途 |
|-------|------|------|------|
| `text primary` | `#222222` | → Color/标题 | 标题、重要内容 |
| `text secondary` | `#757575` | → Color/辅助信息 | 辅助说明文字 |
| `text tertiary` | `#999999` | → Color/次要信息 | 次要/弱化文字 |
| `text muted` | `#CCCCCC` | → Color/灰态 | 占位/极弱化 |
| `text error` | `#FF1930` | → Color/错误色 | 错误提示文字 |
| `text disabled` | `#CCCCCC` | → Color/灰态 | 禁用态文字 |
| `text brand` | `#FF6435` | → Color/主色 | 品牌/强调文字 |
| `text link` | `#FF6435` | → Color/主色 | 链接文字 |

### on-surface 语义映射

| Token | 色值 | 说明 |
|-------|------|------|
| `on-surface default primary` | `#222222` | 表面上一级文字 |
| `on-surface default secondary` | `#757575` | 表面上二级文字 |
| `on-surface default tertiary` | `#999999` | 表面上三级文字 |
