---
name: ppt-master
description: "PPT 大师 —— 融合22大PPT技能/工具/设计体系的统一工作台。按用户需求智能匹配最佳生成路径：HTML幻灯片(guizang/html-ppt/ppt-skill)、PPTX文件(MiniMax/OfficeCLI/Anthropic pptx)、极速出稿(百度AI/AIPPT.cn)、交互改稿(open-slide)、朋友圈海报(定制9:16影视风)。内置设计系统+质量检查+竖屏规范+方法论溯源。用户说「做PPT」时启动方案选择树。"
license: MIT
platforms: [macos, linux, windows]
tags: [ppt, presentation, slides, deck, keynote, poster, design, methodology]
---

# 🎯 PPT 大师 —— 全能工作台

> 融合22大PPT技能/工具体系，提炼为统一方法论。先判断场景，再选生成路径，串行执行不跳步。
> 每条规则都标注了溯源暗线：**谁·在什么场景下·因为什么原因·贡献了什么**。

---

## 一、总纲：PPT大师的决策哲学

### 1.1 核心理念（5条铁律）

| # | 铁律 | 溯源 | 
|---|------|------|
| 1 | **不要从零发明** — 先找开源方案再融合。PPT不是代码，好看靠模板/设计系统，不是绝对坐标 | ← 短剧大师朋友圈海报经历4轮失败后总结 |
| 2 | **选对方案比做对内容重要10倍** — 同一份大纲，HTML vs PPTX vs 海报，选错输出差10倍 | ← frontend-slides「先出3预览」理念 + ppt-skill「Show don't tell」 |
| 3 | **HTML > PPTX**（设计感） — 需要设计感用HTML，需要编辑/交付用PPTX | ← guizang-ppt 杂志风 + html-ppt 36主题实测 |
| 4 | **Show Don't Tell** — 先出预览让用户看图选，不靠文字描述风格 | ← xiongy26/ppt-skill 核心原则 |
| 5 | **串行执行不跳步** — 需求→选方案→生成→自检→交付，每步完成再下一步 | ← hugohe3/ppt-master 串行工作流 + 短剧大师SQ流水线 |

### 1.2 为何不叫「original-ppt-designer」而要重组

**源起：** 最初的 `original-ppt-designer` 是16个技能的堆叠列表，缺乏决策优先级和错误模式记录。

**重构：** 22个技能按**角色**分类而非按名字列举：
- **视觉引擎**（设计感来源）→ guizang/html-ppt/ppt-skill/ppt-master-svg
- **生成引擎**（输出能力）→ MiniMax/OfficeCLI/Anthropic/百度AI
- **交互引擎**（改稿模式）→ open-slide/huashu-design
- **素材引擎**（模板/资源）→ html-anything/AIPPT.cn/模板填充

每种角色选一个，组合出一套生成路径。

---

## 二、方案选择树

用户说「做PPT/海报」时，秒判路径：

```
用户 需求
│
├─ ▶ 说不出要什么风格
│    → 路径A：风格勘探（ppt-skill 出3预览，看图选）
│
├─ ▶ 竖屏 9:16 / 朋友圈海报
│    → 路径B：竖屏影视风（定制HTML，见§4.1设计系统）
│
├─ ▶ 要 PPTX 文件（可编辑/可发送）
│   ├─ 快速量产 → MiniMax PptxGenJS（Node.js，5页类型+7配色+图表）
│   ├─ 命令操作 → OfficeCLI（L1-L2-L3，watch实时预览）
│   └─ 日常办公 → Anthropic pptx（7套配色，最稳定基础款）
│
├─ ▶ 要 HTML（设计感强）
│   ├─ 杂志/人文 → guizang 风格A（Noto Serif衬线+WebGL流体背景）
│   ├─ 科技/数据 → guizang 风格B（Inter无衬线+12列网格+IKB蓝）
│   └─ 模板化快速 → html-ppt（36主题+15模板+47动画+S演讲者模式）
│
├─ ▶ 要极速出稿（马上要）
│    → 百度AI PPT（45秒27页）或 AIPPT.cn（20秒15页）
│
├─ ▶ 要反复改稿
│    → open-slide（点批注AI改，React组件每页）
│
├─ ▶ 从 PDF/材料 转
│    → 路径C：SVG串行转原生PPTX（hugohe3/ppt-master）
│
├─ ▶ 要技术分享/演讲（带逐字稿）
│    → html-ppt presenter-mode-reveal（S键4磁卡：当前/下一页/逐字稿/计时器）
│
├─ ▶ 要操作已有PPT
│    → OfficeCLI（增删改查+watch浏览器实时预览）
│
└─ ▶ 团队协作/云端
     → Google Slides
```

### 路径说明

| 路径 | 适用场景 | 输出格式 | 典型复杂度 | 耗时估计 |
|------|---------|---------|-----------|---------|
| A: 风格勘探 | 用户说不清要什么 | HTML多页 | 中 | 2-5轮交互 |
| B: 竖屏影视风 | 朋友圈/小红书/短视频 | HTML单页→PNG | 低→中 | 1-2轮 |
| C: SVG串行转PPTX | PDF/材料转正式文件 | .pptx | 高 | 3-8轮 |
| MiniMax | 企业级PPTX量产 | .pptx | 中 | 1轮 |
| OfficeCLI | 操作已有PPTX | .pptx | 低 | 即时 |
| 百度AI | 极速出稿 | .pptx | 低 | 45秒 |

---

## 三、通用工作流

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Step 1       │ ──▶ │ Step 2       │ ──▶ │ Step 3       │ ──▶ │ Step 4       │
│ 需求对齐     │     │ 选路径+风格   │     │ 生成内容     │     │ QA + 交付     │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
```

### Step 1 · 需求对齐（3问必问）

1. **输出格式** — HTML（浏览器展示/设计感强） vs PPTX（可编辑/可发送） vs 海报（单页） vs 长图组合？
2. **内容准备状况** — 有大纲/文档/链接？还是只有一个模糊想法？（← ppt-skill 的「阶段0检测模式」）
3. **观众/场景** — 投屏演讲 / 微信发文件 / 朋友圈 / 小红书 / 内部汇报？

> 溯源：guizang-ppt 的7问澄清清单（风格/受众/时长/素材/图片/主题色/硬约束）中提炼出的核心3问。

### Step 2 · 选路径+风格

- 按「方案选择树」判断走哪条路径
- 从对应路径的风格预设里推荐2-3套让用户选
- **不动手抽象描述——直接出视觉预览**
- 如果路径A：先出3个不同风格预览，用户选一个再深入

### Step 3 · 生成内容

- 内容密度硬约束（← ppt-skill、guizang-ppt）：
  - 标题页 ≤ 2个核心元素
  - 内容页 ≤ 6个要点，每个 ≤ 2行
  - 代码页 ≤ 10行代码
- 内容全填充真实内容，不用 lorem ipsum
- 视口适配无滚动（HTML）或16:9标准尺寸（PPTX）

### Step 4 · QA + 交付

按 §六 QA检查清单 逐项检查后：
- HTML：`open index.html` 在浏览器看效果
- PPTX：`officecli validate deck.pptx` 验证schema
- 海报：截PNG检查零遮挡
- 报告输出路径和打开方式给用户

---

## 四、内置设计系统

### 4.1 竖屏影视风规范（9:16 · 朋友圈/海报）

**源起：** 短剧大师朋友圈海报经过6轮修改（字号太小→留白太多→absolute重叠→flex流动→字体放大→四周收窄），提炼出以下稳定体系。

#### 色彩系统

| 色名 | 色值 | 用途 | 设计理由 |
|------|------|------|---------|
| 黑底 | `#0A0A0A` | 背景 | 纯黑显高级，反白文字对比度极高 |
| 暖金 | `#C9A96E` | 主强调 | 电影海报经典金，低调不刺眼 |
| 暗金 | `#B89745` | 次级强调 | 比暖金深一档，适合小字/标签 |
| 暖白 | `#EDE8DC` | 正文/大标题 | 米白不刺眼，比纯白柔和 |
| 暗红 | `#8B1A1A` | 警示 | 只在需要强调「注意」时使用 |

#### 字体系统

| 层级 | 字体 | 字号(1080px宽画布) |
|------|------|-------------------|
| 标题 | Noto Serif SC / PingFang SC Semibold | 100-110px |
| 数据 | Noto Sans SC Bold | 80-90px |
| 卡片标题 | Noto Sans SC Medium | 26-30px |
| 正文 | Noto Sans SC Regular | 22-24px |
| 辅助 | Noto Sans SC Light | 18-20px |

#### 海报布局模板（5层结构）

```
┌─ █████████████████████████ ─┐
│  BRAND                       │  品牌区（标题+tagline+版本号）
│  短剧大师™ v5.0              │  padding-top: 30px
│  "从一句话→小云雀AI成片"      │
├─ █████████████████████████ ─┤
│  CASE HOOK                   │  案例区（核心数据——最大字号）
│  🔥 1,467万                  │  border-top+bottom 分隔
│  红果AI短剧最高热度           │
├─ █████████████████████████ ─┤
│  321  │  875  │  34          │  指标区（3列对称）
│ 剧本库│ 规则  │ 质量关卡      │
├─ █████████████████████████ ─┤
│  🎯 一句话·全自动成片         │  核心优势（5卡）
│  ⚡ 六维剧本升级引擎           │  border + 半透明背景
│  🛡️ 34道质量关卡              │  左右padding: 40px
│  🌐 三平台统一交付             │
│  📖 15个附录知识体系           │
├─ █████████████████████████ ─┤
│  ▸ 批量审查流水线             │  更多能力（5条亮点）
│  ▸ 7大高频陷阱库              │  dot前缀列表
│  ▸ 20维质量矩阵               │
├─ █████████████████████████ ─┤
│  GitHub · woqianfu/xxx        │  CTA区
│  软著·TM                      │  margin-top: auto
└─ █████████████████████████ ─┘
```

#### 排版规则（硬约束）

- `padding ≤ 40px`（四周留白过多→用户否定了3次才收敛到这个值）
- 所有元素用 flex flow 自然排列，**不用 absolute 定位**（absolute 导致重叠2次）
- 字号用**固定 px 单位**，不用 vw/clamp（手机上 vw 太小，用户否定了2次）
- 上下区块用 `border-top/bottom` 视觉分隔，不用间距（留白给内容）

> 以上所有规则都源自用户对同一张海报的6轮修正反馈。

### 4.2 横屏PPT规范（16:9 · 企业/演讲）

| 属性 | 值 | 来源 |
|------|-----|------|
| 尺寸 | 10" × 5.625" (LAYOUT_16x9) | ← MiniMax PptxGenJS 标准 |
| 颜色 | 6位hex无# | ← MiniMax 主题契约 |
| 英文 | Arial / Inter / Helvetica | ← MiniMax + guizang 瑞士风 |
| 中文 | 微软雅黑 / Noto Sans SC | ← MiniMax + html-ppt |

---

## 五、各生成路径详细规则

### 路径A：风格勘探（ppt-skill）
**来源：** xiongy26/ppt-skill · 核心理念「Show don't tell」
**流程：** 出3视觉预览 → 用户看图选 → 生成完整版
**9种风格预设：** Bold Signal / Dark Botanical / Notebook Tabs / Pastel Geometry / Neon Cyber / Swiss Modern / Paper & Ink / Electric Studio / Terminal Green
**内容密度硬约束：** 标题页≤2元素，内容页≤6要点，代码页≤10行

### 路径B：竖屏影视风（定制HTML）
**来源：** 用户6轮实测迭代
**使用：** 直接走 §4.1 设计系统 + 5层海报布局模板
**输出：** HTML → Chrome headless → PNG（1080×1920）→ 直接发朋友圈

### 路径C：SVG串行转原生PPTX（hugohe3/ppt-master）
**来源：** hugohe3/ppt-master（27k⭐）· 8步串行工作流
**流程：** Source→Project→Template→Strategist→SVG逐页手写→QC→Export→PPTX
**特点：** 质量最高但最慢，适合从PDF/材料转正式PPTX

### guizang（Claude-PPTX）
**来源：** op7418/guizang-ppt-skill（16k⭐）· 歸藏维护
**风格A · 电子杂志风：** 衬线(Noto Serif SC) + WebGL流体 + 暖色 · 适合人文/故事
**风格B · 瑞士国际主义：** 无衬线(Inter) + 12列网格 + IKB蓝/柠檬黄/柠檬绿/安全橙 · 适合科技/数据
**硬规则：** 类名必须模板有定义 / 中文标题≤5字 / 只从5套预设选色

### html-ppt（模板化HTML）
**来源：** lewislulu/html-ppt-skill（5.9k⭐）
**核心资产：** 36主题×15完整模板×31布局×47动画
**演讲者模式：** presenter-mode-reveal 模板，S键弹出4磁卡（当前页/下一页/逐字稿/计时器）
**创作规则：** 从布局开始 / 用CSS token / 演讲者文字在 `<div class="notes">`

### MiniMax PptxGenJS（企业级PPTX）
**来源：** MiniMax-AI/skills（12.6k⭐）
**技术栈：** Node.js PptxGenJS
**规格：** 10"×5.625"(16:9) / 6位hex无# / 英文Arial/中文微软雅黑
**主题契约：** `primary`(最暗) / `secondary`(暗强调) / `accent`(中调) / `light`(浅强调) / `bg`(背景)
**5种页类型：** Cover / TOC / Section Divider / Content / Summary
**7套配色：** Midnight Executive / Forest & Moss / Coral Energy / Warm Terracotta / Ocean Gradient / Charcoal Minimal / Teal Trust

### OfficeCLI（命令行PPT操作）
**来源：** iOfficeAI/OfficeCLI（7k⭐）
**三层架构：** L1(创建+读取) → L2(DOM操作set/add/remove) → L3(原始XML)
**关键命令：** `create` / `add slide` / `add shape` / `view outline` / `watch` / `set --find --replace`
**黄金法则：** 任何时候不确定属性名 → 先 `officecli help pptx <element>`

### 快捷方案

| 方案 | 来源 | 适用场景 | 时效 |
|------|------|---------|------|
| 百度AI PPT | 安装至本地 | 极速出稿（45秒27页） | 需BAIDU_API_KEY |
| AIPPT.cn | 在线工具 | 零门槛（20秒15页） | 浏览器打开即可 |
| open-slide | 1weiho（5.3k⭐） | 点批注AI改稿 | 适合反复修改 |
| huashu-design | alchaincyf（18.5k⭐） | 一套内容出4种格式(HTML+PPTX+视频+Dome) | 适合多格式输出 |

---

## 六、QA 检查清单

### 通用检查（所有路径）

- [ ] 方案选择正确（HTML vs PPTX vs 海报 vs 极速）
- [ ] 串行执行，不跳步
- [ ] Show Don't Tell — 先出预览
- [ ] 内容全填充，无占位lorem

### HTML类检查（路径A/B/guizang/html-ppt）

- [ ] 视口适配无滚动
- [ ] 内容密度符合限制（标题页≤2，内容页≤6）
- [ ] 风格统一（不混搭衬线/无衬线）
- [ ] 字体统一用CSS变量（token）
- [ ] 图片标准比例（16:9/16:10/4:3/3:2）
- [ ] 演讲者文字在 `<div class="notes">`，不在slide上
- [ ] 包含 `runtime.js`，支持键盘导航
- [ ] 零遮挡零溢出

### 竖屏海报专项检查（路径B）

- [ ] padding ≤ 40px
- [ ] 字号体系对齐9级规范（Hero 100px → Footer 18px）
- [ ] flex flow 布局，无 absolute 定位
- [ ] 5层结构（品牌→案例→数据→优势→更多能力）
- [ ] CTA和版权信息在底部可见
- [ ] TM商标标注（如适用）

### PPTX类检查（MiniMax/OfficeCLI）

- [ ] 尺寸16:9（10"×5.625"）
- [ ] 主题契约5个键齐全
- [ ] 页码徽章（封面外每页）
- [ ] `officecli validate` 通过
- [ ] 字体统一（英文Arial/中文微软雅黑）

---

## 七、方法论溯源暗线

本技能所有规则都有明确的来源。这里记录每条核心决策的**起因**，防止未来使用时丢失上下文。

### 7.1 为什么要有这个技能？

2026年6月14-15日，用户要求制作短剧大师PPT。经过：

1. **python-pptx** → 用户否定（设计感不够）
2. **pptxgenjs** → 用户否定
3. **Keynote AppleScript自动化** → 无GUI工具不可行
4. **HTML-PPT-Skill** → 模板化但不满足竖屏要求
5. **百度AI PPT** → 45秒出27页，用户认可速度但设计一般
6. **手动CSS竖屏HTML** → 经过6轮修改终于验收

**教训：** 做PPT不是写代码，是选方案。从零发明 python-pptx 永远做不出设计感。

### 7.2 竖屏规范的形成

每次用户否定后，规则被提炼：

| 轮次 | 用户反馈 | 新增规则 |
|------|---------|---------|
| 1 | "字太小" | 正文从1.6vw改为固定22-24px |
| 2 | "设计感不够" | 采用黑底金字影视风 |
| 3 | "只有一页" | 加 `@page` + `page-break-after` 分页 |
| 4 | "有重叠" | absolute定位→flex flow排列 |
| 5 | "留白太多" | padding从60px降到40px |
| 6 | "字体要大" | 品牌名放大到110px，正文到24px |

### 7.3 方案选择树的形成

| 用户场景 | 第一次用的方案 | 结果 | 最终确定的路径 |
|---------|--------------|------|-------------|
| 说不出风格 | 直接写HTML | 4轮改稿 | ppt-skill 出3预览 |
| 竖屏海报 | 绝对定位CSS | 重叠重做2次 | 5层flex模板 |
| 技术分享 | python-pptx | 设计不够 | guizang瑞士风 |
| 快速出稿 | 手写所有 | 慢 | 百度AI PPT |

### 7.4 引用来源清单

| 技能/工具 | GitHub Star | 核心贡献 |
|-----------|-----------|---------|
| guizang-ppt-skill (op7418) | 16k⭐ | 风格A&B双系统+7问澄清+22版式S01-S22 |
| html-ppt-skill (lewislulu) | 5.9k⭐ | 36主题+15模板+47动画+演讲者模式 |
| ppt-skill (xiongy26) | — | Show don't tell + 9风格 + 内容密度约束 |
| ppt-master (hugohe3) | 27k⭐ | SVG串行工作流→原生PPTX |
| MiniMax pptx-generator | 12.6k⭐ | PptxGenJS企业级5页类型+主题契约 |
| OfficeCLI (iOfficeAI) | 7k⭐ | L1-L2-L3命令行Office操作 |
| Anthropic pptx | 47.6K安装 | 7套配色最稳定 |
| frontend-slides | 21k⭐ | 先出3预览选风格 |
| huashu-design | 18.5k⭐ | 一套内容4格式输出 |
| open-slide | 5.3k⭐ | 点批注AI交互改稿 |
| html-anything | 6.6k⭐ | 75模板×9种输出形态 |

---

## 八、记忆要点（持久化）

### 用户偏好（每次使用自动加载）

- 竖屏 9:16 暗色影视风（黑底 #0A0A0A + 暖金 #C9A96E）
- 朋友圈海报固定5层结构：品牌→案例→数据→优势→更多能力
- 字号体系需要够大（手机阅读），四周留白要少（padding ≤ 40px）
- TM商标标注（商标注册申请中）
- 不要 python-pptx / pptxgenjs 做设计感PPT
- 先学开源再融合，不发明新方案

### 已记录的错误模式（下次避免）

| 错误 | 正确做法 | 来源轮次 |
|------|---------|---------|
| 海报用 absolute 定位 | 用 flex flow 自然排列 | 第4轮 |
| 字号用 vw/clamp | 固定 px，正文22-24px | 第1轮 |
| 四周 padding > 40px | padding ≤ 40px | 第5轮 |
| HTML打印只有1页 | 加 `@page` + `page-break-after: always` | 第3轮 |
| PDF尺寸默认A4 | 设 390×844（iPhone 14竖屏） | 第3轮 |
| 一次性堆22个技能名 | 按角色分类（视觉/生成/交互/素材） | 重构时 |
| 同一份skill名冲突「ppt-master」 | 本skill是调度器，hugohe3的是SVG转PPTX工具 | 重构时 |
