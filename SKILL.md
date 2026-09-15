---
name: ai-latest-news
description: 自动抓取并汇总 12+ 家顶尖 AI 实验室、开源生态与硬核技术博客的最新更新，生成结构化的中文 AI 动态周报与日报。
---

# AI 前沿动态技能 (`ai-latest-news`)

当用户需要了解近期 AI 领域最新动态、查看顶尖实验室或技术博客的更新、生成 AI 周报/日报，或者询问“近期 AI 有什么新进展？”时使用此技能。

---

## 监测源注册表 (Target Sources Registry)

本技能覆盖 3 大核心分类共 12+ 高信任度权威信息源：

### 1. 头部大模型实验室 (Base Models)
*关注重点：底层模型发布、安全对齐、架构风向标。*
- **OpenAI**：官方动态（`https://openai.com/news`）、前沿研究（`https://openai.com/index/research`）
- **Google DeepMind**：官方博客（`https://deepmind.google/discover/blog`）
- **Meta AI (FAIR)**：官方博客（`https://ai.meta.com/blog`）
- **Mistral AI**：官方动态（`https://mistral.ai/news`）
- **Anthropic**：官方动态（`https://www.anthropic.com/news`）、Claude 博客（`https://claude.com/blog`）

### 2. 开源生态与应用工程 (Open Source & Infra)
*关注重点：Agent 架构、RAG 实战、工具调用、模型微调与量化落地。*
- **Hugging Face**：技术博客（`https://huggingface.co/blog`）、每日精选论文（`https://huggingface.co/papers`）
- **LangChain**：官方博客（`https://blog.langchain.dev`）
- **LlamaIndex**：官方博客（`https://www.llamaindex.ai/blog`）

### 3. 独立技术博客与深度硬核分析 (Tech Blogs & Deep Dives)
*关注重点：技术综述拆解、算力集群硬件（GPU/算力成本）、生态格局分析。*
- **Lil'Log (Lilian Weng)**：博客主页（`https://lilianweng.github.io`）
- **Interconnects (Nathan Lambert)**：博客主页（`https://www.interconnects.ai`）
- **Latent Space**：博客主页（`https://www.latent.space`）
- **SemiAnalysis**：博客主页（`https://www.semianalysis.com`）

---

## 执行流程协议 (Execution Protocol)

触发本技能后，Agent 必须严格执行以下多阶段工作流：

### 阶段 1：解析时间范围与用户需求
1. 检查用户提示词中指定的时间窗口（如“过去24小时”、“近3天”、“本周”等）。
2. 若用户未指定时间范围，默认使用 **最近 7 天**。

### 阶段 2：并行/批量数据抓取
1. 针对各个分类，优先使用 `read_url_content` 或 RSS/Atom 订阅 Endpoint（如 `https://lilianweng.github.io/feed.xml`、`https://www.interconnects.ai/feed`、`https://blog.langchain.dev/rss/` 等）获取最新文章列表。
2. 从返回的 HTML 或 Markdown 内容中提取最新的文章条目（包含：文章标题、发布日期、原文链接、内容摘要）。
3. 若某网站访问受限或解析失败，退回尝试读取其 RSS 源，或通过 `search_web` 执行搜索（如 `site:<domain> 2026`），或调用浏览器子 agent 渲染页面。

### 阶段 3：日期与关联度过滤
1. 对比当前系统时间（`2026-09-15`）计算内容新鲜度。
2. 仅保留在指定时间窗口内发布的文章。
3. **降级策略**：若目标源缺失明确发布日期，则默认选取其首页/列表顶部的最新 2 篇文章。

### 阶段 4：综合汇总与周报生成
按照下方指定的结构化模板，直接在对话框中输出排版精美的中文 AI 动态报告。

---

## 输出格式模板 (Output Format Template)

```markdown
# 🤖 AI 前沿动态周报 (AI Latest News Digest)

> **统计周期**：[YYYY-MM-DD 至 YYYY-MM-DD] | **监测源**：12 大核心实验室与技术博客

---

## 🏛️ 头部大模型实验室 (Base Models)

### 1. [文章/公告标题](源链接)
- **来源**：[OpenAI / DeepMind / Anthropic / Meta AI / Mistral AI] | **发布日期**：YYYY-MM-DD
- **核心要点**：
  - 重点 1：简明阐述核心技术、模型发布或重大更新。
  - 重点 2：对产业或研究方向的影响。

---

## 🛠️ 开源生态与应用工程 (Open Source & Infra)

### 1. [文章/项目标题](源链接)
- **来源**：[Hugging Face / LangChain / LlamaIndex] | **发布日期**：YYYY-MM-DD
- **核心要点**：
  - 重点 1：Agent / RAG / 工具链关键改进。
  - 重点 2：实践落地方案与开发者价值。

---

## 🔬 深度技术博客与硬核分析 (Tech Blogs & Deep Dives)

### 1. [文章标题](源链接)
- **来源**：[Lil'Log / Interconnects / Latent Space / SemiAnalysis] | **发布日期**：YYYY-MM-DD
- **核心要点**：
  - 重点 1：深度拆解核心观点或算力/架构分析。
  - 重点 2：行业洞察与趋势研判。

---

## 💡 总结与趋势研判
- **本周热点趋势**：[1-2 句高屋建瓴的趋势总结]
- **最值得关注的突破**：[突出 1-2 项最重磅进展]
```
