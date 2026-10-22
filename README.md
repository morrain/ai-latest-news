# AI 前沿技术与工程动态 (`ai-latest-news`)

`ai-latest-news` 是一个严谨且硬核的 AI 技术情报架构师 Agent 技能。它的核心任务是访问并抓取指定技术来源在过去 24 小时（1天）内的最新发布内容，剔除营销噪音，提炼出高信息密度的技术简报。

---

## 📡 允许抓取的唯一目标列表 (Exclusive Sources)

本技能严格排他，**仅且必须**在以下 11 个指定数据源 URL 中提取内容，严禁抓取或引入列表之外的任何第三方网站：

### 1. 头部大模型实验室 (Base Models)
- **OpenAI 官方动态**: `https://openai.com/news/` 及 `https://openai.com/index/`（含中文镜像 `https://openai.com/zh-Hans-CN/news/`）
- **Google DeepMind 官方博客**: `https://deepmind.google/discover/blog/`
- **Google 官方 AI 动态 (The Keyword)**: `https://blog.google/technology/ai/`
- **Meta AI (FAIR) 官方博客**: `https://ai.meta.com/blog/`
- **Anthropic 官方动态**: `https://www.anthropic.com/news/`
- **Claude 官方博客**: `https://claude.com/resources/articles/`

### 2. 开源生态与应用工程 (Open Source & Infra)
- **Hugging Face 技术博客**: `https://huggingface.co/blog/`
- **Hugging Face 每日精选论文**: `https://huggingface.co/papers/`
- **NVIDIA 开发者技术博客**: `https://developer.nvidia.com/blog/`

### 3. 独立技术博客与深度硬核分析 (Tech Blogs & Deep Dives)
- **Lil'Log (Lilian Weng)**: `https://lilianweng.github.io/`
- **SemiAnalysis**: `https://semianalysis.com/` 及 `https://newsletter.semianalysis.com/`

---

## ⚙️ 严格执行规则 (Strict Rules)

1. **绝对排他与事实落地**：仅基于从上述具体 URL 获取到的实际文本进行分析与总结。绝对禁止通过自身历史参数臆测，若某个站点在过去 24 小时内没有新文章发布，直接忽略或归入“暂无更新”，严禁编造虚假新闻。
2. **硬核去噪与全面覆盖**：
   - 剔除纯商业宣发、峰会致辞、无实测数据的营销合作软文。
   - 重点保留架构创新、模型参数、算力成本、底层硬件（GPU 规格/液冷/BOM/网络拓扑）、Agent 编排机制、MCP 协议、RAG 演进、以及企业工程落地与前沿工程实践（如 Forward Deployed Engineering, Evals 评测体系）等实质性工程细节。
3. **严格深层链接（Deep Link）**：必须提取并输出每篇文章的具体真实叶子链接（如 `https://openai.com/index/what-fde-means-at-openai/`、`https://newsletter.semianalysis.com/p/huawei-deepseek`），严禁使用顶级域名充当文章链接。
4. **输出规范**：使用简体中文输出，专业术语（如 FDE, MCP Server, Dify, RAG, KV Cache, SWC, TTFT）保留英文原文。

---

## 📋 输出格式模板 (Output Format Template)

```markdown
# 🤖 AI 前沿技术与工程动态简报 [YYYY-MM-DD]

## 1. 头部大模型实验室 (Base Models)
> 重点关注：底座模型迭代、安全对齐、架构创新

### [站点名称]：[文章标题](原文具体子链接)
* **发布日期**：YYYY-MM-DD
* **核心更新**：[一句话说明核心发布，如模型规格、关键指标、研究突破]
* **技术/架构细节**：[关键技术改进，如训练机制、注意力优化、上下文管理等]
* **工程影响**：[对下游调用、推理成本或行业生态的具体影响]

*(若本模块对应 URL 均无更新，请注明：本分类过去 24 小时内暂无更新)*

---

## 2. 开源生态与应用工程 (Open Source & Infra)
> 重点关注：Agent 架构、RAG 实战、工具调用规范、模型微调与量化部署、算力硬件与加速优化

### [站点名称]：[文章标题](原文具体子链接)
* **发布日期**：YYYY-MM-DD
* **核心更新**：[工具链/框架/开源模型/硬件加速更新内容]
* **核心机制**：[关键代码变更、协议标准（如 MCP）实现、检索策略演进、计算内核优化]
* **落地建议**：[在生产环境或实际业务流编排中的落地注意点]

*(若本模块对应 URL 均无更新，请注明：本分类过去 24 小时内暂无更新)*

---

## 3. 独立技术博客与深度硬核分析 (Tech Blogs & Deep Dives)
> 重点关注：技术综述拆解、算力集群硬件（GPU/算力成本/BOM）、生态格局分析

### [站点名称/作者]：[文章标题](原文具体子链接)
* **发布日期**：YYYY-MM-DD
* **核心论点**：[作者的核心论点与推演逻辑]
* **硬核数据/论据**：[提及的硬件参数、网络拓扑、成本模型拆解或实测数据]
* **架构启示**：[对长期架构选型、算力基建规划的参考价值]

*(若本模块对应 URL 均无更新，请注明：本分类过去 24 小时内暂无更新)*

---

## 💡 今日技术风向标 (Key Takeaways)
* [浓缩 1~2 条本日最具价值的技术演进或工程趋势结论]
```

---

## 📁 目录结构 (Repository Structure)

- `SKILL.md`: 技能定义与 Agent 执行 Protocol。
- `README.md`: 仓库说明与规范文档。
- `.gitignore`: Git 忽略配置。
