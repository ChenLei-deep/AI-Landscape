# 🤖 AI 全景图

一个单文件、零依赖的纯静态网页，一页纵览 AI 世界：大模型 · AI 产品 · 模型榜单 · AI 坟场。

> 线上访问：**https://chenlei-deep.github.io/AI-Landscape/ai-landscape.html**

---

## ✨ 功能概览

整个网站是一个独立的 `ai-landscape.html` 文件（HTML + CSS + 内联 JS，无后端、无打包步骤），打开即用。

### 🧠 大模型全览
- 收录 **41 个大模型**，覆盖 **20 个系列**（GPT / Claude / Gemini / Qwen / DeepSeek / Doubao 等）
- 每个卡片是一个**独立模型**，同系列挂系列标签、按公司标注国别（🇨🇳中国 / 🇺🇸美国 / 🇫🇷法国 / 🇬🇧英国 / 🇨🇦加拿大）
- 顶部统计条：已收录数 · 当前筛选展示数 · 系列数（实时联动）
- **三维度筛选**：地区（中国/美国/欧洲）· 开源类型（开源/闭源）· 模型系列
- **搜索框**：模糊匹配名称、英文代号、所属公司
- **查看详情**：弹窗展示模型概述、核心优势、典型应用场景、产品定位
- **加入对比**：选 2–4 个模型，一键对比开源状态、参数规模、上下文窗口、定价、国别、核心特征

### 🛠️ AI 产品
三大子板块一键切换：
- **产品矩阵**：50 个还在运营的 AI 产品（编程 / 陪伴 / 生图 / 视频 / 音乐 / 搜索 / **办公** / 其他），左侧类型筛选带数量徽标，支持搜索与国别标签
- **产品热度榜**：下载量 · Token 消耗量 双指标 Top 30 现象级应用，可切换查看
- **产品 & 模型图谱**：揭示现象级应用底层的技术选型栈（自研底座 / 接入第三方大模型 / 多模型聚合）

### 🏆 模型榜单
- 9 大权威榜单：Chatbot Arena、SWE-bench、HLE、MMLU、生图 Arena、视频 Arena、SuperCLUE、OpenCompass、LiveCodeBench
- **可折叠榜单**：默认收起，点击展开，一屏纵览；分类单选切换，无需下滑翻找
- 一键折叠/展开全部

### 🪦 AI 坟场
- 收录 **100 个**已停运 AI 产品（国内 + 国际）
- 每张卡片含：产品类型、功能介绍、停运原因、生命跨度（发行时间 → 停运时间，带可视化进度条与存活时长）
- **三维度筛选**：时间（停运年份）· 行业 · 死亡原因（已关停🔴 / 已出售🟢 / 大幅收缩🟡，卡片标签按此着色）
- **停运数量柱状图**：按行业分布，随筛选实时联动
- 置顶「AI 坟场洞察」：基于本页 100 条数据的真实统计（重灾区 Top3、死亡结局结构、四大失败主因、核心启示）

---

## 🚀 本地预览

直接用浏览器打开 `ai-landscape.html` 即可。或本地起服务：

```bash
python3 -m http.server 8000
# 访问 http://localhost:8000/ai-landscape.html
```

---

## 📦 数据维护

所有数据均为页面内 JS 数组，集中在 `<script>` 中，按需增改即可：

| 模块 | 数据变量 | 说明 |
|------|----------|------|
| 大模型 | `MODELS` | 每模型含 series / country / params / context / pricing / overview / strengths / useCases / positioning |
| AI 产品 | `PRODUCTS` | 每产品含 cat / region / company / features / url |
| 产品国别 | `PRODUCT_COUNTRY` | 非美国公司单独标注，默认美国 |
| 热度榜 | `HEAT_DATA` | downloads（百万下载）/ tokens（十亿tokens/日） |
| 产品&模型图谱 | `GRAPH_DATA` | 每产品底层所用大模型，self=true 表示自研底座 |
| AI 坟场 | `GRAVE_DATA` | 每停运产品含 type / status / func / born / dead / reason |
| 死亡原因归并 | `CAUSE_GROUPS` | status → 已关停/已出售/大幅收缩 三大类 |

新增数据时注意：
- 坟场 `status` 取值限于现有集合，`type` 限于 `companion/writing/image/video/chatbot/hardware/search/tool/ent`
- 产品 `cat` 可取 `coding/companion/image/video/music/search/office/other`

---

## 🔄 月度自动更新

已配置定时任务：**每月 1 日 10:00（北京时间）** 自动联网抓取最新 AI 动态，更新模型榜单排名、热度榜数据，增量补充新 AI 产品与停运产品，并推送上线，线上自动刷新。

> 运行前提：每月 1 日执行时电脑开机、CodeFuse 应用打开。

---

## 🌐 部署方式

采用 **GitHub Pages** 部署，零成本、永久在线：

1. 仓库 `main` 分支存放 `ai-landscape.html`
2. GitHub 仓库 Settings → Pages → Source 选 `main / (root)`
3. 访问 `https://chenlei-deep.github.io/AI-Landscape/ai-landscape.html`

更新流程：

```bash
git add ai-landscape.html
git commit -m "更新说明"
git push origin main
# 约 1 分钟后线上自动刷新
```

---

## 📝 数据来源

模型榜单：Arena.ai · SuperCLUE · SWE-bench · Artificial Analysis · Vellum · LLM Stats · OpenCompass · LiveCodeBench
AI 坟场：本页整理 + [AI Graveyard by DANG!](https://dang.ai/ai-graveyard)（全网收录 1289+ 项目）

数据更新于 2026 年 7 月，仅供学习参考，不保证完全准确。

---

## 🛡️ 技术栈

- 纯 HTML5 + CSS3 + 原生 JavaScript（无框架、无构建工具）
- 单文件交付，所有逻辑与数据内联
- 响应式布局，适配桌面与移动端