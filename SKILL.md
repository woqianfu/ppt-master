---
name: ppt-master
description: "PPT 大师 v1.2 —— 22大PPT技能/工具融合的统一方法论。不堆叠工具名，按角色分类（视觉引擎/生成引擎/交互引擎/素材引擎）。方案选择树→4步工作流→内置设计系统→QA清单→方法论溯源。输出HTML/PPTX/PNG/PDF。每次更新递增版本号。"
license: MIT
platforms: [macos, linux, windows]
tags: [ppt, presentation, slides, design, methodology]
---

# 🎯 PPT 大师 v1.2

> 融合 22 大技能后提炼的统一方法论。不是工具列表，是决策系统。
> 每次更新递增版本号，变更记录见 Changelog。

---

## 一、核心哲学（5条铁律）

| # | 铁律 | 来源 |
|---|------|------|
| 1 | **不要从零发明** — 好看靠模板/设计系统，不是坐标代码 | 短剧大师 PPT 4 次方案失败后总结 |
| 2 | **HTML > PPTX（设计感）** — 需要设计感走HTML，需编辑/发送走PPTX | guizang + html-ppt 实测 |
| 3 | **Show Don't Tell** — 先出预览让用户看图选 | xiongy26/ppt-skill |
| 4 | **串行不跳步** — 需求→选方案→生成→自检→交付 | hugohe3/ppt-master 工作流 |
| 5 | **量化而非感觉** — 字大→110px，留白少→40px | 6 轮反馈收敛 |

---

## 二、方案选择树

```
用户 需求
├── ▶ 说不出要什么风格 → A:风格勘探（ppt-skill 出3预览）
├── ▶ 竖屏 9:16 / 海报 → B:竖屏影视风（定制HTML→PNG）
├── ▶ 要 PPTX 文件
│   ├── 快速量产 → MiniMax PptxGenJS（5页类型+7配色+图表）
│   ├── 命令操作 → OfficeCLI（L1-L2-L3，watch预览）
│   └── 日常办公 → Anthropic pptx（7配色最稳定）
├── ▶ 要 HTML（设计感）
│   ├── 杂志/人文 → guizang 风格A（Noto Serif衬线+WebGL流体）
│   ├── 科技/数据 → guizang 风格B（无衬线+网格+IKB蓝）
│   └── 模板化快速 → html-ppt（36主题+15模板+47动画+S演讲者模式）
├── ▶ 极速出稿 → 百度AI PPT（45秒27页）
├── ▶ 要反复改 → open-slide（点批注AI改）
├── ▶ PDF/材料转 → SVG串行转原生PPTX（hugohe3/ppt-master）
├── ▶ 技术演讲带讲稿 → html-ppt presenter-mode-reveal（S键4磁卡+逐字稿）
├── ▶ 操作已有PPT → OfficeCLI（增删改查+watch）
└── ▶ 团队协作 → Google Slides
```

### 路径说明

| 路径 | 输出 | 耗时 | 设计感 | 编辑性 |
|------|------|:----:|:-----:|:-----:|
| A:风格勘探 | HTML | 2-5轮 | ★★★★ | ★★★ |
| B:竖屏影视 | PNG/HTML | 1-2轮 | ★★★★★ | ★★ |
| MiniMax | .pptx | 1轮 | ★★★ | ★★★★★ |
| guizang 风格A/B | HTML | 1轮 | ★★★★★ | ★★★ |
| html-ppt | HTML | 1轮 | ★★★★ | ★★★ |
| 百度AI | .pptx | 45秒 | ★★ | ★★★★ |
| OfficeCLI | .pptx | 即时 | ★★ | ★★★★★ |

---

## 三、通用工作流

```
Step 1 需求对齐 ─→ Step 2 选路径+风格 ─→ Step 3 生成 ─→ Step 4 QA+交付
```

### Step 1 · 需求对齐（3问）
1. 输出格式？HTML（设计感强）/ PPTX（可编辑）/ 海报（单页）
2. 内容准备？有大纲/文档还是只有一个主题？
3. 观众场景？投屏演讲 / 微信 / 小红书 / 内部汇报

### Step 2 · 选路径+风格
按方案选择树判定后，从预设推荐2-3套让用户选。**不出抽象描述，直接出视觉预览。**

### Step 3 · 生成
- 内容密度：标题页≤2元素，内容页≤6要点，代码页≤10行
- 内容全填充真实数据，无占位
- 视口适配无滚动（HTML）/ 16:9标准（PPTX）

### Step 4 · QA + 交付
按 QA检查清单 逐项过 → 报告输出路径 → open预览

---

## 四、内置设计系统

### 4.1 竖屏影视风（9:16 · 朋友圈/海报）

| 色名 | 色值 | 用途 |
|------|------|------|
| 黑底 | `#0A0A0A` | 背景 |
| 暖金 | `#C9A96E` | 主强调 |
| 暗金 | `#B89745` | 次级强调 |
| 暖白 | `#EDE8DC` | 正文 |
| 暗红 | `#8B1A1A` | 警示 |

**字体：** 标题=Noto Serif SC/PingFang SC Semibold · 正文=Noto Sans SC

**字号体系（1080px画布）：**
| 层级 | 字号 | 用途 |
|------|:----:|------|
| Hero | 100-110px | 品牌名 |
| Mega | 80-90px | 案例数字 |
| XL | 28-34px | 副标题 |
| L | 26-30px | 卡片标题 |
| M | 22-24px | 正文 |
| S | 18-20px | 辅助文字 |

**5层布局模板：**
```
品牌区 → 案例区 → 指标区 → 核心优势(5卡) → 更多能力(5条) → CTA区
```

**硬约束：** padding ≤ 40px · flex flow 不用 absolute · 字号固定 px · 上下区块用 border 分隔

### 4.2 横屏规范（16:9 · 企业/演讲）

| 属性 | 标准 | 来源 |
|------|------|------|
| 尺寸 | 10"×5.625" | MiniMax 标准 |
| 颜色 | 6位hex无# | MiniMax 主题契约 |
| 英文 | Arial/Inter/Helvetica | guizang+MiniMax |
| 中文 | 微软雅黑/Noto Sans SC | html-ppt |

**MiniMax 主题契约：** `primary`(最暗) / `secondary`(暗强调) / `accent`(中调) / `light`(浅强调) / `bg`(背景)

---

## 五、各方案速查

| 方案 | 一句话定位 | 关键命令/规则 |
|------|-----------|-------------|
| **guizang** | 杂志&瑞士双风格HTML | `npx skills add op7418/guizang-ppt-skill` · 类名必须模板有定义 |
| **html-ppt** | 36主题模板化HTML | S键演讲者模式·notes放逐字稿·始终包含runtime.js |
| **ppt-skill** | 出3预览选风格 | 9种风格·标题页≤2元素·内容页≤6要点 |
| **MiniMax** | 企业级PPTX生成 | `npm install -g pptxgenjs` · 5页类型·主题契约5键 |
| **OfficeCLI** | 命令行操作PPTX | `officecli add/create/set/view` · 先help后操作 |
| **百度AI** | 45秒极速出稿 | `BAIDU_API_KEY` · `X-Appbuilder-From: openclaw` |
| **open-slide** | 点批注AI改稿 | `npx @open-slide/cli init` |
| **Google Slides** | 云端协作 | `npx skills add googleworkspace/cli` |

---

## 六、QA 检查清单

### 通用
- [ ] 方案选择正确
- [ ] 串行执行不跳步
- [ ] Show Don't Tell
- [ ] 内容全填充，无占位

### HTML类
- [ ] 视口适配无滚动
- [ ] 风格统一（不混搭衬线/无衬线）
- [ ] CSS变量（token）管理颜色
- [ ] 图片标准比例
- [ ] 演讲者文字在 `<div class="notes">`
- [ ] 包含 runtime.js

### 竖屏海报专项
- [ ] padding ≤ 40px
- [ ] flex flow 布局
- [ ] 字号体系对齐9级
- [ ] 5层结构
- [ ] TM标注（如适用）

### PPTX类
- [ ] 16:9 (10"×5.625")
- [ ] 主题契约5键齐全
- [ ] 页码徽章（封面外每页）
- [ ] `officecli validate` 通过

---

## 七、方法论溯源暗线

| 规则 | 来源 | 形成原因 |
|------|------|---------|
| 不python-pptx做设计感 | 短剧大师海报4轮失败 | python-pptx→pptxgenjs→Keynote→百度AI→定制HTML才通过 |
| Show Don't Tell | xiongy26/ppt-skill | 「先出3预览」比抽象描述高效10倍 |
| HTML>PPTX设计感 | guizang+html-ppt实测 | 浏览器渲染远超PptxGenJS |
| 串行不跳步 | hugohe3/ppt-master | 跳过一步=返工 |
| 竖屏5层结构 | 6轮用户反馈 | 品牌→案例→数据→优势→更多能力 |
| 字号固定px | 第1轮反馈 | vw手机上太小 |
| padding≤40px | 第3轮反馈 | 60px留白太多 |
| flex flow不用absolute | 第2轮反馈 | 不同分辨率重叠 |

---

## 八、Changelog

```
v1.2 (当前)
  - 精炼各方案速查，去重「4种设计风格」等无效描述
  - 路径说明表增加设计感/编辑性星级评分
  - 主题契约MiniMax指南从正文移入速查表
  - 方法论溯源暗线从8条精简为8条，每条≤2行

v1.1
  - 合并 original-ppt-designer 到 ppt-master，消除同名冲突
  - 新增方法论溯源暗线章节
  - 新增错误模式记录
  - 删除「OfficeCLI 4种设计风格」错误描述

v1.0
  - 初始版：从 original-ppt-designer 22条重组为统一体系
  - 方案选择树 + 通用工作流 + 内置设计系统 + QA清单
```

---

## 九、引用来源（精简）

| 技能 | Star | 核心贡献 |
|------|:----:|---------|
| hugohe3/ppt-master | 27k⭐ | SVG串行→原生PPTX |
| guizang-ppt | 16k⭐ | 杂志&瑞士双风格 |
| MiniMax pptx-gen | 12.6k⭐ | 企业级PptxGenJS |
| OfficeCLI | 7k⭐ | 命令行Office |
| html-ppt | 5.9k⭐ | 36主题+演讲者模式 |
| html-anything | 6.6k⭐ | 75模板×9输出 |
| Anthropic pptx | 47.6K安装 | 日常办公最稳 |
| xiongy26/ppt-skill | — | Show Don't Tell |
