# 上海合愉商贸有限公司官网 — 开发文档

**Shanghai Heyu Trading Co., Ltd. — Website Documentation**

---

## 目录

1. [项目概述](#1-项目概述)
2. [文件结构](#2-文件结构)
3. [设计理念与视觉风格](#3-设计理念与视觉风格)
4. [页面架构](#4-页面架构)
5. [CSS 设计系统](#5-css-设计系统)
6. [JavaScript 数据架构](#6-javascript-数据架构)
7. [产品详情字段说明](#7-产品详情字段说明)
8. [产品数据索引总表](#8-产品数据索引总表)
9. [色卡图片管理](#9-色卡图片管理)
10. [交互逻辑说明](#10-交互逻辑说明)
11. [响应式设计](#11-响应式设计)
12. [上线部署指南](#12-上线部署指南)
13. [后续维护指南](#13-后续维护指南)

---

## 1. 项目概述

本项目是上海合愉商贸有限公司的**纯静态企业官方网站**，面向国内文具企业采购客户，展示公司背景和 DOKUMENTAL（德国文都）品牌的全系列专业墨水产品技术规格。

| 属性 | 说明 |
|---|---|
| 网站类型 | 纯静态单页面应用（SPA-like） |
| 主要语言 | 中文（部分中英双语） |
| 技术栈 | 原生 HTML5 + CSS3 + Vanilla JavaScript，无任何框架依赖 |
| 字体来源 | Google Fonts（Cormorant Garamond、Noto Serif SC、DM Sans） |
| 外部依赖 | 仅 Google Fonts，无 CDN 库、无 jQuery |
| 目标浏览器 | Chrome、Edge、Safari、Firefox 现代版本 |

---

## 2. 文件结构

```
网站根目录/
├── index.html                    ← 唯一的 HTML 文件，包含全部 HTML/CSS/JS
└── images/
    ├── writing/                  ← 书写类墨水色卡图片
    │   ├── colorcard_3-1-X1.jpg
    │   ├── colorcard_23-74.jpg
    │   ├── colorcard_23-76.jpg
    │   ├── colorcard_31-33.jpg
    │   ├── colorcard_34-62.jpg
    │   ├── colorcard_48-05.jpg
    │   ├── colorcard_54-32.jpg
    │   ├── colorcard_62-31.jpg
    │   ├── colorcard_62-40.jpg
    │   ├── colorcard_85-74.jpg
    │   ├── colorcard_89-62.jpg
    │   ├── colorcard_SF1XX.jpg
    │   ├── colorcard_SF3XX.jpg
    │   ├── colorcard_SGP1XX.jpg
    │   ├── colorcard_SGP3XX.jpg
    │   ├── colorcard_Docu.jpg
    │   ├── colorcard_FP18XX.jpg
    │   ├── colorcard_NewBlue.jpg
    │   ├── colorcard_RB13XX.jpg
    │   ├── colorcard_GeneralBP.jpg
    │   ├── colorcard_QG88XX.jpg
    │   └── colorcard_SP35XX.jpg
    ├── fluorescent/              ← 荧光类墨水色卡图片
    │   ├── colorcard_3-43G.jpg
    │   ├── colorcard_3-43N.jpg
    │   ├── colorcard_3-71.jpg
    │   ├── colorcard_29-97.jpg
    │   ├── colorcard_30-28.jpg
    │   ├── colorcard_57-11.jpg
    │   ├── colorcard_57-12.jpg
    │   ├── colorcard_PF61XX.jpg
    │   ├── colorcard_PF62XX.jpg
    │   ├── colorcard_FH18XX.jpg
    │   └── colorcard_PF63XX.jpg
    ├── watercolor/               ← 水彩类墨水色卡图片
    │   ├── colorcard_3-14.jpg
    │   ├── colorcard_26-12.jpg
    │   ├── colorcard_26-22.jpg
    │   ├── colorcard_34-74.jpg
    │   ├── colorcard_61-16.jpg
    │   ├── colorcard_67-89.jpg
    │   ├── colorcard_ColorChange.jpg
    │   ├── colorcard_NT5XX.jpg
    │   └── colorcard_TripleColor.jpg
    ├── marker/                   ← 马克类墨水色卡图片
    │   ├── colorcard_2-53.jpg
    │   ├── colorcard_3-36.jpg
    │   ├── colorcard_46-33.jpg
    │   ├── colorcard_48-83.jpg
    │   ├── colorcard_48-84.jpg
    │   ├── colorcard_48-88.jpg
    │   ├── colorcard_62-95.jpg
    │   ├── colorcard_65-30.jpg
    │   ├── colorcard_70-44.jpg
    │   ├── colorcard_71-50.jpg
    │   ├── colorcard_71-71.jpg
    │   ├── colorcard_78-55.jpg
    │   ├── colorcard_80-55.jpg
    │   ├── colorcard_83-11.jpg
    │   ├── colorcard_BOL82XX.jpg
    │   ├── colorcard_OL82XX.jpg
    │   ├── colorcard_MA30XX.jpg
    │   └── colorcard_WB73XX.jpg
    └── special/                  ← 特殊定制类墨水色卡图片
        ├── colorcard_3-37.jpg
        ├── colorcard_5-41.jpg
        ├── colorcard_21-86.jpg
        └── colorcard_49-99.jpg
```

> **注意：** `index.html` 文件自身体积轻量（约 171KB），所有产品数据以 JavaScript 对象形式内嵌，色卡图片以相对路径引用，不再使用 base64 内嵌。

---

## 3. 设计理念与视觉风格

### 3.1 品牌定位

网站面向 B2B 采购客户，目标是传递**专业、精准、历史感**的品牌形象。整体取"编辑排版风格（Editorial）"——在专业与美感之间取得平衡，避免通用的"AI审美"，以接近高端文具品牌官网的气质呈现。

### 3.2 色彩体系

```
背景主色（--ink-black）:  #f7f4ef  ← 温暖米白，模拟优质纸张质感
次级背景（--ink-deep）:   #efeae0  ← 稍深的羊皮纸色，用于交替区段
强调金色（--gold）:       #8a6420  ← 深暗金，在浅底上保持足够对比度
正文主色（--text-main）:  #1e1a14  ← 近黑深褐，墨水般的书写色
辅助文字（--text-muted）: #4a4640  ← 中深棕，用于次要说明文字
边框色（--border）:       rgba(138, 100, 32, 0.22)  ← 半透明金色边框
```

金色是整个视觉系统的强调色，贯穿导航、板块标题、悬停效果、数据表头、标签等所有交互层级，呼应"高档专业墨水"的产品定位。

### 3.3 字体体系

| 字体 | 用途 | 风格 |
|---|---|---|
| **Noto Serif SC** | 中文标题、导航、板块标签 | 衬线，传统感 |
| **Cormorant Garamond** | 英文标题、副标题、引用、型号代码 | 高档衬线，优雅 |
| **DM Sans** | 正文、按钮、技术参数 | 无衬线，清晰易读 |

三种字体形成明确的层级：Cormorant Garamond 负责装饰性英文，Noto Serif SC 负责权威性中文，DM Sans 负责功能性内容。

### 3.4 空间与布局哲学

- **水平留白充足**：全站统一 `4vw` 横向内边距，最大内容宽度 1200px
- **垂直节奏规律**：各 section 统一 `7rem` 上下内边距
- **两栏对称布局**：公司介绍、联系我们均采用 1:1 两栏网格
- **五等分产品卡片**：产品中心采用 `repeat(5, 1fr)` 精确等分

---

## 4. 页面架构

整个网站是一个**单 HTML 文件**，页面分为以下六个主要区块，通过锚点 `#id` 实现导航跳转：

```
┌─────────────────────────────────────────┐
│  <nav>  固定顶部导航栏                   │
│  Logo + 公司介绍 / 产品中心 / 联系我们   │
├─────────────────────────────────────────┤
│  <section id="hero">  全屏首屏           │
│  墨水涟漪动画 + 品牌标语 + 统计数字      │
├─────────────────────────────────────────┤
│  <section id="about">  公司介绍          │
│  左：公司文字 + 引言框                   │
│  右：DOKUMENTAL 品牌介绍框              │
├─────────────────────────────────────────┤
│  <section id="products">  产品中心       │
│  五大类别卡片（点击弹出模态框）          │
├─────────────────────────────────────────┤
│  <section id="contact">  联系我们        │
│  左：联系人信息                          │
│  右：地图占位（网格+定位点动效）         │
├─────────────────────────────────────────┤
│  <footer>  页脚                          │
│  版权信息 + 品牌标识                     │
├─────────────────────────────────────────┤
│  .modal-overlay  产品详情弹窗（隐藏层）  │
│  分类列表视图 ↔ 单品详情视图             │
└─────────────────────────────────────────┘
```

### 4.1 导航栏（`<nav id="mainNav">`）

- **初始状态**：透明背景，融入首屏
- **滚动后**：JS 监听 `scroll` 事件，超过 60px 时添加 `.scrolled` 类，切换为磨砂玻璃效果（`backdrop-filter: blur(12px)`）
- **导航项**：三个锚点链接，悬停有下划线展开动画

### 4.2 首屏 Hero（`<section id="hero">`）

- **背景**：两个径向渐变叠加，营造空间感
- **墨水涟漪**：四个 `.ink-ring` 圆环，通过 `animation-delay` 错开时间，模拟墨滴入水扩散
- **入场动画**：`heroFadeIn` 关键帧，内容从下方 30px 淡入
- **统计数字**：绝对定位于右下角，Cormorant Garamond 大字号营造视觉冲击
- **滚动提示**：左下角呼吸动效引导向下探索

### 4.3 公司介绍（`<section id="about">`）

- 两栏网格（`1fr 1fr`，间距 5rem）
- 左栏：三段正文 + 引言块（带装饰大引号 `"` 伪元素）
- 右栏：DOKUMENTAL 品牌信息框（渐变背景 + 金色顶部边框）
- 区段顶部用 CSS 伪元素绘制中心渐变金线分隔符

### 4.4 产品中心（`<section id="products">`）

五张产品类别卡片，采用 `repeat(5, 1fr)` 等宽布局：

| 类别 | 图标类型 | 产品数量 |
|---|---|---|
| 书写类墨水 | Emoji ✒️ | 22款 |
| 荧光类墨水 | 内嵌 SVG（横向荧光笔） | 11款 |
| 水彩类墨水 | Emoji 🎨 | 9款 |
| 马克类墨水 | 内嵌 SVG（竖向马克笔） | 18款 |
| 特殊定制墨水 | Emoji ⚗️ | 4款 |

> 荧光笔和马克笔使用**内嵌 SVG**而非 emoji，以精确还原笔的形态（笔帽、笔身高光、笔夹、笔尖细节）。

卡片悬停效果：`translateY(-6px)` 上浮 + 金色顶部边框 + 增强阴影。

### 4.5 产品详情弹窗（`.modal-overlay`）

弹窗采用**两级视图**，由 JavaScript 动态渲染：

```
打开类别卡片
     ↓
【产品列表视图】
  - 该类别所有产品的卡片网格
  - 有详细数据的产品显示金色"详细规格"标签
     ↓ 点击某产品
【单品详情视图】
  - 产品型号代码（金色，小型大写）
  - 产品中文名称（大号衬线字体）
  - 各信息字段（detail-grid 两栏网格）
     ↑ 点击"← 返回产品列表"
```

### 4.6 联系我们（`<section id="contact">`）

- 两栏网格，左侧联系信息，右侧地图占位
- 地图占位用 CSS 网格线 + 脉冲动效定位点模拟，无需嵌入真实地图 API

---

## 5. CSS 设计系统

### 5.1 CSS 自定义属性（变量）

所有颜色、字体均通过 `:root` 中的 CSS 变量统一管理。修改主题色时只需改动 `:root` 部分即可全站生效：

```css
:root {
  --ink-black: #f7f4ef;     /* 主背景 */
  --ink-deep:  #efeae0;     /* 次级背景（交替区段）*/
  --gold:      #8a6420;     /* 全站强调色 */
  --text-main: #1e1a14;     /* 主文字 */
  --text-muted: #4a4640;    /* 辅助文字 */
  --border: rgba(138,100,32,0.22); /* 边框 */
}
```

### 5.2 核心布局类

| CSS 类 | 作用 |
|---|---|
| `.about-grid` | 公司介绍两栏网格（`1fr 1fr`） |
| `.categories-grid` | 产品五栏网格（`repeat(5,1fr)`） |
| `.contact-grid` | 联系两栏网格（`1fr 1fr`） |
| `.detail-grid` | 产品详情两栏网格（`1fr 1fr`） |
| `.detail-field` | 详情单个字段框（米色背景+金色边框） |
| `.detail-full` | 跨满两栏的字段（`grid-column: 1/-1`） |
| `.product-list` | 产品列表自适应网格（`minmax(200px,1fr)`） |

### 5.3 物理参数表格样式

`.phys-table` 是产品详情中最复杂的组件，具备：
- 表头：品牌玫红色背景（`#e8006a`），白色文字，呼应 DOKUMENTAL 原版 TDS 文件风格
- 斑马纹：偶数行淡金色背景
- 悬停：行高亮效果
- 支持 `colStyles`：可为特定列单独设定宽度（用于列名较长时防止换行）
- 支持分组行：型号第一列空值时渲染为金色标题行（如`【钢笔墨水】`、`【擦液】`）

### 5.4 动效清单

| 动效名 | 作用 | 位置 |
|---|---|---|
| `inkExpand` | 墨滴涟漪扩散（循环） | Hero 背景 |
| `heroFadeIn` | 首屏文字淡入上滑 | Hero 内容 |
| `scrollPulse` | 滚动提示线呼吸闪烁 | Hero 左下 |
| `pinPulse` | 地图定位点脉冲扩散 | 联系页地图 |
| `modalIn` | 弹窗出现上滑淡入 | 产品弹窗 |
| nav `.scrolled` | 滚动触发导航玻璃效果 | 顶部导航 |
| `.category-card:hover` | 卡片上浮 + 金线 | 产品卡片 |

---

## 6. JavaScript 数据架构

所有数据集中在 `<script>` 标签内，采用纯 JavaScript 对象组织，不依赖任何外部库。

### 6.1 总体结构

```javascript
// ① 分类目录数据（用于产品列表视图）
const categories = {
  writing:     { label, title, products: [...], colors: [...] },
  fluorescent: { label, title, products: [...], colors: [...] },
  watercolor:  { label, title, products: [...], colors: [...] },
  marker:      { label, title, products: [...], colors: [...] },
  custom:      { label, title, products: [...], colors: [...] }
};

// ② 无数据产品的通用占位
const defaultDetail = { overview, surface, solvent, ... };

// ③ 各产品详细技术数据（键名格式：'分类__索引'）
const productDetailData = {
  'writing__0':  { overview, surface, solvent, physicalTable, colorCardImg, ... },
  'writing__1':  { ... },
  // ... 共 64 个产品条目
};
```

### 6.2 `categories` 对象（分类目录）

每个分类包含：

```javascript
writing: {
  label: '书写类墨水 · Writing Inks',  // 弹窗顶部显示
  title: '书写类墨水',                  // 弹窗标题
  products: [
    { name: '签字笔墨水（水性）', code: '3-1-X.1 Fineliner ink' },
    // ... 每款产品：中文名 + 英文型号代码
  ],
  colors: ['#f9c900', '#f47920', ...]   // 保留字段（现已不用于色块渲染）
}
```

### 6.3 `productDetailData` 条目结构

每个产品条目的完整字段：

```javascript
'writing__0': {
  overview:    '产品概况文字',          // String，支持 \n\n 段落换行
  surfaceLabel: '应用范围',             // 可选，覆盖"适用书写表面"标题
  surface:     '适用书写表面文字',      // String
  extraAfterSurface: [                  // 可选，在 surface 后插入额外板块
    { label: '应用范围', text: '...' },
    { label: '证书/认证/法规', text: '...' }
  ],
  solvent:     '水性',                  // '水性' | '油性' | '醇性'
  physicalTable: {                      // 物理参数表，null 则不显示
    colStyles: [...],                   // 可选，各列宽度（CSS 字符串数组）
    headers:   [...],                   // 表头数组，支持 \n 换行
    rows:      [...],                   // 数据行，空值行渲染为分组标题
    colorMap:  { '颜色名': '#hex' }     // 颜色映射，用于渲染颜色圆点
  },
  colorCardImg: 'images/writing/colorcard_XXX.jpg', // 色卡图片路径，null 不显示
  components:  '合适的配件文字',        // String，支持 \n\n 段落换行
  storage:     '仓储运输文字',          // String，支持 \n\n 段落换行
  extra: [                              // 可选，在 storage 后插入额外板块
    { label: '中性墨水的处理', text: '...' },
    { label: '笔头保护', text: '...' }
  ],
  packaging:   '包装文字',              // String，占满整行
  manufacturer: ''                      // 已置空，不在页面展示
}
```

> `\n` 渲染为 `<br>`，`\n\n` 渲染为段落间距（`<p>` 标签）。

### 6.4 键名索引规则

产品键名格式为 `'分类__序号'`，序号从 0 开始，对应 `categories.分类.products` 数组的下标：

```
writing__0   → categories.writing.products[0]   → 签字笔墨水
writing__1   → categories.writing.products[1]   → 可擦钢笔墨水
...
fluorescent__0 → categories.fluorescent.products[0]
...
custom__3    → categories.custom.products[3]     → 验钞笔墨水
```

---

## 7. 产品详情字段说明

产品详情弹窗中各字段的显示规则：

| 字段 | 显示位置 | 宽度 | 必填 |
|---|---|---|---|
| `overview`（产品概况） | 信息区首位 | 整行 | ✓ |
| `solvent`（溶剂体系） | 第二行左 | 半行 | ✓ |
| `surface`（适用书写表面） | 第二行右 | 半行 | ✓ |
| `extraAfterSurface`（额外板块） | 紧跟 surface 后 | 整行 | 可选 |
| `physicalTable`（25℃物理参数） | 参数表格 | 整行 | 可选（null跳过） |
| `colorCardImg`（色卡） | 色卡图片 | 整行 | 可选（null跳过） |
| `components`（合适的配件） | 配件说明 | 整行 | ✓ |
| `storage`（仓储运输） | 仓储说明 | 整行 | ✓ |
| `extra`（storage后额外板块） | 紧跟 storage 后 | 整行 | 可选 |
| `packaging`（包装） | 包装说明 | 整行 | ✓ |

> **溶剂体系** 和 **适用书写表面** 并排在同一行（各占半行），是刻意设计的——两者信息量相对较少，并排可节省垂直空间，并使视觉层次更丰富。

---

## 8. 产品数据索引总表

### 书写类（writing，22款）

| 键名 | 中文名 | 英文型号 | 溶剂 |
|---|---|---|---|
| writing__0 | 签字笔墨水 | 3-1-X.1 Fineliner ink | 水性 |
| writing__1 | 可擦钢笔墨水 | 23-74 19-23 Erasable Fountain Pen Inks | 水性 |
| writing__2 | 钢笔墨水 | 23-76 Fountain Pen Inks | 水性 |
| writing__3 | 颜料型签字笔墨水 | 31-33 Pigmented Fineliner Inks | 水性 |
| writing__4 | 宝珠笔墨水 | 34-62 36-20 46-63 rollerball inks | 水性 |
| writing__5 | 颜料型宝珠笔墨水 | 48-05 Pigmented Rollerball Inks | 水性 |
| writing__6 | 中性荧光墨水 | 54-32-X.1 Fluorescent Color Gel Inks | 水性 |
| writing__7 | 直液式宝珠笔墨水 | 62-31 Rollerball Ink for Free Ink System | 水性 |
| writing__8 | 宝珠笔浓缩墨水 | 62-40 83-35 Rollerball Ink Concentrate | 水性 |
| writing__9 | 圆珠笔油墨 | 85-74 Ball Pen Inks | 油性 |
| writing__10 | 宝珠笔墨水 | 89-62 Rollerball Inks | 水性 |
| writing__11 | 超低黏度圆珠笔油墨 | SF 1XX Ball Pen Inks | 油性 |
| writing__12 | 超低黏度圆珠笔油墨 | SF 3XX Ball Pen Inks | 油性 |
| writing__13 | 超低黏度圆珠笔油墨 | SGP 1XX Ball Pen Inks | 油性 |
| writing__14 | 超低黏度彩色圆珠笔油墨 | SGP 3XX Ball Pen Inks | 油性 |
| writing__15 | 经济型圆珠笔油墨 | Docu Ball Pen Inks | 油性 |
| writing__16 | 钢笔墨水 | FP 18XX Fountain Inks | 水性 |
| writing__17 | 新蓝色圆珠笔油墨 | New Blue Ball Pen Inks | 油性 |
| writing__18 | 直液式宝珠笔墨水 | RB13XX Water-based Rollerball Inks | 水性 |
| writing__19 | 通用圆珠笔油墨 | General Ball Pen Inks | 油性 |
| writing__20 | 中性墨水 | QG 88XX | 水性 |
| writing__21 | 签字笔墨水 | SP35XX Fineliner Inks | 水性 |

### 荧光类（fluorescent，11款）

| 键名 | 中文名 | 英文型号 | 溶剂 |
|---|---|---|---|
| fluorescent__0 | 闪光荧光记号笔墨水 | 3-43-X(G) Glitter Highlighter Marker Inks | 水性 |
| fluorescent__1 | 闪光水彩墨水 | 3-43-X(N) Glitter Highlighter marker inks | 水性 |
| fluorescent__2 | 颜料型粉彩荧光墨水 | 3-71 Pigmented pastel Highlighter inks | 水性 |
| fluorescent__3 | 染料型荧光墨水 | 29-97 29-73 Dye-based highlighter | 水性 |
| fluorescent__4 | 淡彩荧光墨水 | 30-28 Dye-based Pastel Highlighter Inks | 水性 |
| fluorescent__5 | 可擦荧光墨水 | 57-11 Erasable Highlighter Inks | 水性 |
| fluorescent__6 | 可擦粉彩荧光墨水 | 57-12 Erasable Pastel Highlighter Inks | 水性 |
| fluorescent__7 | 高亮荧光墨水 | PF61XX.1 Pigmented Highlighter Inks | 水性 |
| fluorescent__8 | 荧光墨水浓缩液 | PF62XX Pigmented Highlighter Ink Concentrates | 水性 |
| fluorescent__9 | 速干荧光墨水 | FH 18XX Quick Dry Highlighter Inks | 水性 |
| fluorescent__10 | 高亮荧光墨水 | PF63XX.8 Highlighter Inks | 水性 |

### 水彩类（watercolor，9款）

| 键名 | 中文名 | 英文型号 | 溶剂 |
|---|---|---|---|
| watercolor__0 | 水彩笔墨水 | 3-14-X Coloring Marker inks | 水性 |
| watercolor__1 | 覆盖型可擦墨水 | 26-12 Linebriter Marker Ink | 水性 |
| watercolor__2 | 可擦水彩墨水 | 26-22 Erasable Marker Inks | 水性 |
| watercolor__3 | 超级可洗水彩墨水 | 34-74 Super Washable Color Marker Inks | 水性 |
| watercolor__4 | 纹身笔墨水 | 61-16 Temporary Tattoo Inks | 水性 |
| watercolor__5 | 挂图墨水 | 67-89 Chart Marker Inks | 水性 |
| watercolor__6 | 变色墨水 | Color Change Marker Inks | 水性 |
| watercolor__7 | 安全系数高的水彩墨水 | NT5XX | 水性 |
| watercolor__8 | 二次变色墨水 | Triple Color Changing Coloring Marker Inks | 水性 |

### 马克类（marker，18款）

| 键名 | 中文名 | 英文型号 | 溶剂 |
|---|---|---|---|
| marker__0 | 灯板笔墨水 | 2-53 DWO Waterbased valve-action marker inks | 水性 |
| marker__1 | 闪光水彩墨水 | 3-36 Glitter marker inks | 水性 |
| marker__2 | 醇性永久记号墨水 | 46-33 Alcohol Permanent Inks | 醇性 |
| marker__3 | 水性油漆笔墨水 | 48-83 Colorburst Paint Marker Inks | 水性 |
| marker__4 | 水性油漆笔墨水 | 48-84 Colorburst Acrylic Paint Marker Inks | 水性 |
| marker__5 | 闪光水性油漆笔墨水 | 48-88 Glitter Acrylic Paint Marker Inks | 水性 |
| marker__6 | 水粉永久记号笔墨水 | 62-95 Colorburst Permanent Inks | 水性 |
| marker__7 | 非永久阀门笔墨水 | 65-30 32 36 Non-Permanent Valve Action Inks | 水性 |
| marker__8 | 织物墨水 | 70-44 40-22 Fabric Marker Inks | 水性 |
| marker__9 | 水性金属墨水 | 71-50 Water-based Metallic Inks | 水性 |
| marker__10 | 水性金属墨水 | 71-71 Water-based Metallic Inks | 水性 |
| marker__11 | 经济型永久记号笔墨水 | 78-55-XN Economy Permanent Inks | 醇性 |
| marker__12 | 玻璃记号笔墨水 | 80-55 Colorburst Window Marker Inks | 水性 |
| marker__13 | 荧光永久记号笔墨水 | 83-11-XN Permanent Inks | 醇性 |
| marker__14 | 轮廓笔墨水 | BOL 82XX Outline Marker Inks | 醇性 |
| marker__15 | 轮廓笔墨水 | OL 82XX Outline Marker Inks | 醇性 |
| marker__16 | 记号笔墨水 | MA30XX Quick Drying Permanent Marker Inks with Excellent Cap-off Properties | 醇性 |
| marker__17 | 白板笔墨水 | WB73XX Pigmented Whiteboard Inks With Extended Cap-off Time | 醇性 |

### 特殊定制类（custom，4款）

| 键名 | 中文名 | 英文型号 | 溶剂 |
|---|---|---|---|
| custom__0 | 幻灯片墨水 | 3-37 Non-permanent OHP inks | 水性 |
| custom__1 | 外科手术用记号笔墨水 | 5-41 3-34 Surgical marker inks | 醇性 |
| custom__2 | 紫外线荧光保安记号笔墨水 | 21-86 57-52 UV Security Inks | 水性/醇性 |
| custom__3 | 验钞笔墨水 | 49-99 Special Paper Inks | 水性 |

---

## 9. 色卡图片管理

### 9.1 引用方式

所有色卡图片均以**相对路径**引用，格式统一：

```javascript
colorCardImg: 'images/分类目录/colorcard_型号简称.jpg'
```

例：
```javascript
colorCardImg: 'images/writing/colorcard_3-1-X1.jpg'
colorCardImg: 'images/fluorescent/colorcard_PF61XX.jpg'
```

### 9.2 无色卡产品

若某产品暂无色卡图片，将该字段设为 `null`，色卡板块将自动隐藏：

```javascript
colorCardImg: null
```

### 9.3 替换/更新图片

直接替换 `images/` 目录下的同名图片文件即可，无需修改 HTML。图片建议：
- 格式：`.jpg`（文件更小）或 `.png`（透明背景）
- 尺寸：宽度建议不超过 1200px，保持原始比例
- 命名：严格按照上文"文件结构"中的命名规则

---

## 10. 交互逻辑说明

### 10.1 弹窗开关

```javascript
openModal(catKey)         // 打开某分类弹窗，渲染产品列表
closeModal()              // 关闭弹窗
closeModalOnBg(event)     // 点击遮罩层关闭（点击弹窗本体无效）
```

键盘 `Escape` 键也可关闭弹窗。

### 10.2 产品列表渲染（`renderProductList`）

1. 遍历 `categories[catKey].products`
2. 检查 `productDetailData[catKey__index]` 是否存在
3. 存在则添加 `.has-detail` 类和金色"详细规格"徽章
4. 渲染为可点击的卡片网格

### 10.3 产品详情渲染（`openProductDetail`）

1. 查找 `productDetailData[catKey__index]`，不存在则使用 `defaultDetail`
2. 按字段顺序依次渲染（见第 7 节字段说明）
3. 物理参数表调用 `buildPhysicalTable(tbl)` 函数独立渲染

### 10.4 物理参数表渲染（`buildPhysicalTable`）

- 读取 `colStyles` 生成 `<colgroup>` 控制列宽
- 表头支持 `\n` 换行（渲染为 `<br>`）
- 数据行颜色列自动查 `colorMap` 插入彩色圆点
- 第一列全空的行渲染为金色分组标题行（用于多组产品的分隔）

### 10.5 文本换行规则

| 场景 | 写法 | 渲染结果 |
|---|---|---|
| 同一段内换行 | `\n` | `<br>` 换行 |
| 段落之间空行 | `\n\n` | `<p>` 段落间距 |
| 物理参数表头换行 | `\n` | `<br>` 换行 |

---

## 11. 响应式设计

网站在以下断点做了适配：

```css
@media (max-width: 900px) {
  /* 两栏布局 → 单栏 */
  .about-grid, .contact-grid { grid-template-columns: 1fr; }
  /* 产品五列 → 两列 */
  .categories-grid { grid-template-columns: repeat(2, 1fr); }
  /* 弹窗内详情 → 单栏 */
  .detail-grid { grid-template-columns: 1fr; }
  /* 弹窗内边距缩小 */
  .modal-body { padding: 2rem 1.5rem; }
}

@media (max-width: 600px) {
  /* 产品五列 → 单列 */
  .categories-grid { grid-template-columns: 1fr; }
  /* 导航缩小 */
  .nav-links { gap: 1.2rem; }
  /* 区段内边距缩小 */
  section { padding: 5rem 5vw; }
}
```

---

## 12. 上线部署指南

### 12.1 推荐方案：阿里云 / 腾讯云静态网站托管

1. **在云平台创建 Bucket**（对象存储），开启静态网站托管
2. **上传以下内容**（保持目录结构不变）：
   ```
   index.html
   images/
   ├── writing/     （22张色卡）
   ├── fluorescent/ （11张色卡）
   ├── watercolor/  （9张色卡）
   ├── marker/      （18张色卡）
   └── special/     （4张色卡）
   ```
3. 在 Bucket 设置中将 `index.html` 指定为**默认首页**
4. 可绑定自定义域名并开启 HTTPS（推荐）

### 12.2 其他可选方案

| 平台 | 费用 | 国内访问 | 适合场景 |
|---|---|---|---|
| 阿里云/腾讯云 OSS | 月几元起 | 快 | **推荐，正式上线** |
| GitHub Pages | 免费 | 较慢 | 测试预览 |
| Vercel / Netlify | 免费 | 一般 | 测试预览 |

### 12.3 上线前检查清单

- [ ] 所有 64 张色卡图片已放置到对应子目录
- [ ] 图片命名与 `colorCardImg` 路径完全一致（大小写敏感）
- [ ] 在浏览器本地打开 `index.html` 验证所有产品弹窗正常
- [ ] 检查手机端显示效果
- [ ] 联系邮箱链接 `mailto:coinfjq@163.com` 可正常唤起邮件客户端

---

## 13. 后续维护指南

### 13.1 新增一个产品

**步骤一：** 在 `categories.分类.products` 数组末尾添加：
```javascript
{ name: '新产品中文名（水性）', code: 'XX-XX Product Code' }
```

**步骤二：** 在 `productDetailData` 中添加对应条目（键名为 `'分类__新索引'`）：
```javascript
'writing__22': {
  overview: '...',
  surface: '...',
  solvent: '水性',
  physicalTable: { headers: [...], rows: [...], colorMap: {...} },
  colorCardImg: 'images/writing/colorcard_XXXX.jpg',
  components: '...',
  storage: '...',
  packaging: '...',
  manufacturer: ''
}
```

**步骤三：** 更新对应产品卡片上的产品数量：
```html
<div class="cat-count">23 款产品</div>
```

**步骤四：** 将色卡图片放入对应目录。

### 13.2 修改某产品信息

直接找到 `productDetailData` 中对应的键（如 `'writing__5'`），修改对应字段值即可。

### 13.3 修改公司联系信息

在 HTML 的 `<section id="contact">` 区段中直接修改文字内容。

### 13.4 修改品牌/公司介绍

在 `<section id="about">` 区段中直接修改 `<p>` 标签内的文字内容。

### 13.5 修改 Hero 统计数字

在 `<section id="hero">` 的 `.hero-stats` 区域直接修改 `.stat-num` 和 `.stat-label` 的内容。

### 13.6 添加真实地图

将 `<section id="contact">` 中的 `.contact-map-placeholder` 替换为高德地图 / 百度地图 iframe：
```html
<iframe
  src="https://uri.amap.com/marker?position=121.xxxx,31.xxxx&name=上海合愉商贸&src=mypage"
  width="100%" height="320" frameborder="0">
</iframe>
```

---

*文档生成日期：2025年*
*网站版本：1.0（含全部 64 款产品技术数据）*
