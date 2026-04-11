# GitHub 爆款项目口播文案生成器

自动发现 GitHub 爆款项目，智能评估爆款潜力，生成适合多平台的高转化口播脚本。

## 核心功能

- 🔍 **自动发现爆款** — 从 GitHub Trending/Hacker News/Product Hunt 获取热门项目
- 📊 **爆款潜力评分** — 100分制评分模型，筛选最具传播潜力的项目
- 🏷️ **智能分类** — 自动识别 8 大爆款类型（AI工具/终端神器/效率工具/替代方案等）
- 📝 **多平台文案** — 针对抖音/小红书/B站/视频号生成差异化爆款文案
- 🎯 **平台适配** — 按项目类型匹配最佳文案模板和发布策略
- 💾 **自动保存** — 每次分析自动保存报告到 `~/demo/hot/` 目录
- 🎬 **视频生成** — 自动生成60秒抖音竖屏宣传视频（Beta）

## 使用方法

### 模式一：自动发现爆款（推荐）

```bash
# 自动发现今日爆款项目并生成文案
/github-kol-script --discover

# 发现 AI 类爆款项目
/github-kol-script --discover --category ai

# 发现开发工具类，生成抖音专用文案
/github-kol-script --discover --category devtools --platform 抖音

# 批量生成 5 个爆款项目文案
/github-kol-script --batch 5

# 分析本周 Trending
/github-kol-script --trending weekly
```

### 模式二：分析指定项目

```bash
# 使用完整 GitHub URL
/github-kol-script https://github.com/vercel/next.js

# 使用 owner/repo 格式
/github-kol-script vercel/next.js

# 指定平台和风格
/github-kol-script https://github.com/anthropics/claude-code --platform 抖音 --style 硬核技术
```

## 爆款评分模型

每个项目按以下维度计算「爆款潜力分」（满分 100）：

### 基础分（40分）
- Stars 增速（15分）— 今日新增 Stars 数量
- 项目热度（10分）— 总 Stars 数
- 活跃度（10分）— 最近更新时间
- 易用性（5分）— 安装使用难度

### 内容分（35分）
- 视觉可展示（12分）— 能否录屏展示效果
- 痛点明确度（10分）— 解决的问题是否普遍
- 情绪价值（8分）— 是否能引发"用了回不去"
- 故事性（5分）— 是否有大厂背书/创始人故事

### 时机分（25分）
- 话题热度（15分）— AI/热门技术栈等
- 新鲜度（10分）— 发布时间/版本更新

## 爆款项目分类

| 分类 | 爆款公式 | 适合平台 |
|------|----------|----------|
| **AI编程工具** | "AI自动生成+效率翻倍" | 抖音/B站 |
| **终端神器** | "程序员必备+装逼神器" | 抖音/小红书 |
| **效率工具** | "省时间+告别繁琐" | 小红书/视频号 |
| **替代方案** | "免费替代+放弃XX" | 抖音/B站 |
| **新版本发布** | "重大更新+5个新功能" | 全平台 |
| **视觉工具** | "效果惊艳+前后对比" | 小红书/抖音 |
| **学习资源** | "自学神器+少走弯路" | 小红书/B站 |
| **基础设施** | "大厂都在用+性能炸裂" | B站/视频号 |

## 输出内容

1. **TOP 5 爆款项目列表** — 潜力分、Stars增速、推荐理由
2. **爆款要素分析** — 各维度得分及说明
3. **多平台口播文案** — 抖音/小红书/B站/视频号四个版本
4. **发布优化建议** — 标题、封面、标签、最佳发布时间
5. **自动保存报告** — 完整 Markdown 报告保存到 `~/demo/hot/`

### 报告保存规则

- **保存路径**: `~/demo/hot/`
- **文件命名**:
  - 自动发现模式：`github-hot-YYYYMMDD-HHMMSS.md`
  - 指定项目模式：`github-[owner]-[repo]-YYYYMMDD-HHMMSS.md`
- **示例**: `~/demo/hot/github-hot-20260411-143022.md`

## 爆款文案结构

### 抖音版（45-60秒）
```
黄金3秒钩子 → 痛点共鸣 → 解决方案演示 → 效果对比
→ 技术背书 → 行动号召
```

### 小红书版（60-90秒）
```
种草标题 → 个人体验 → 功能亮点(emoji列表) → 使用教程
→ 效果对比 → 互动引导
```

### B站版（2-5分钟）
```
开场介绍 → 背景分析 → 原理解析 → 代码演示
→ 对比分析 → 总结推荐
```

### 视频号版（60-120秒）
```
专业开场 → 价值分析 → 案例说明 → 适用人群
→ 行动建议
```

## 爆款项目案例库

### AI 编程工具（爆款指数 ⭐⭐⭐⭐⭐）
- anthropic/claude-code — AI 编程助手
- continue-dev/continue — 开源 AI 代码补全
- aider-ai/aider — AI 结对编程

### 终端神器（爆款指数 ⭐⭐⭐⭐⭐）
- warpdotcom/Warp — 现代终端
- starship/starship — 终端提示符美化
- junegunn/fzf — 模糊查找神器

### 效率工具（爆款指数 ⭐⭐⭐⭐）
- jesseduffield/lazygit — TUI 版 Git
- BurntSushi/ripgrep — 极速文本搜索
- sharkdp/fd — 人性化 find 替代

### 替代方案（爆款指数 ⭐⭐⭐⭐⭐）
- brunolemos/bruno — Postman 开源替代
- AppFlowy-IO/AppFlowy — Notion 开源替代
- nocodb/nocodb — Airtable 开源替代

## 数据来源

- GitHub Trending — https://github.com/trending
- Hacker News — https://news.ycombinator.com/show
- Product Hunt — https://www.producthunt.com
- 大厂开源动态 — vercel/meta/google/microsoft 等

## 视频生成功能（Beta）

自动为分析的 GitHub 项目生成 60 秒抖音竖屏宣传视频。

### 使用方法

```bash
# 发现项目并生成视频
/github-kol-script --discover --generate-video

# 为指定项目生成视频
/github-kol-script owner/repo --generate-video

# 或者直接运行生成脚本
node ~/.claude/skills/github-kol-script/generate-video.js <owner> <repo> [name] [description]
```

### 视频特点

- **格式**: 抖音竖屏 9:16 (1080x1920)
- **时长**: 60 秒，30fps
- **结构**: 6 场景叙事流程
  1. **钩子** (0-3s): 吸引注意力的开场
  2. **痛点** (3-8s): 展示用户遇到的问题
  3. **方案** (8-12s): 项目介绍和核心价值
  4. **演示** (12-35s): 核心功能展示（带智能缩放）
  5. **爆点** (35-45s): 核心亮点总结
  6. **CTA** (45-60s): 行动号召和 GitHub 链接

### 技术实现

- 基于 **Remotion** 框架（React 视频生成）
- 使用现有的 `~/demo/markitdown-video` 项目作为模板
- 动态替换场景内容，无需重新安装依赖
- **SmoothZoom** 组件实现多点平滑缩放，清晰展示重点

### 依赖要求

- Node.js 18+
- `~/demo/markitdown-video` 项目已初始化并安装依赖

**首次使用检查**:
```bash
# 检查视频模板是否存在
if [ ! -d "$HOME/demo/markitdown-video/node_modules" ]; then
  echo "首次使用，安装依赖..."
  cd ~/demo/markitdown-video && npm install
fi
```

### 输出位置

视频输出到 `~/demo/videos/` 目录，文件名为 `[owner]-[repo]-YYYY-MM-DD.mp4`

---

## 注意事项

1. Trending 数据变化快，建议发现后立即制作
2. 避免夸大宣传，技术效果要基于项目实际能力
3. 替代方案类避免直接贬低商业软件
4. 不确定的数据标注「约」或「据」
5. 视频渲染约需 2-5 分钟（取决于机器性能）

## 更新日志

- **v3.0.0** (2026-04-11): 新增视频自动生成功能 (Beta)
  - 基于 Remotion 自动生成 60 秒抖音竖屏视频
  - 6 场景结构：钩子 → 痛点 → 方案 → 演示 → 爆点 → CTA
  - SmoothZoom 组件实现智能缩放，聚焦重点内容
  - 复用 `~/demo/markitdown-video` 项目，无需重复安装依赖
  - 视频输出到 `~/demo/videos/` 目录

- **v2.1.0** (2026-04-11): 新增报告自动保存功能
  - 自动保存到 `~/demo/hot/` 目录
  - 智能文件命名（含时间戳和项目名称）
  - 执行完成显示保存路径

- **v2.0.0** (2026-04-11): 新增爆款自动发现功能
  - 自动从多数据源获取热门项目
  - 爆款潜力评分模型
  - 8大项目分类标签
  - 分类专属文案模板

- **v1.0.0** (2026-04-11): 初始版本
  - 支持指定项目分析
  - 四平台口播文案生成
