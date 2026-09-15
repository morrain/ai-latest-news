# AI Latest News (`ai-latest-news`)

`ai-latest-news` 是一个用于追踪、抓取与汇总 AI 前沿动态的 Agent Skill 仓库。它自动监测 12+ 家顶尖 AI 实验室、开源生态与深度技术博客的最新更新，并生成结构化的中文 AI 动态周报/日报。

---

## 📡 监测源列表 (Monitored Sources)

### 1. 头部大模型实验室 (Base Models)
* **OpenAI**
  * 官方动态: `https://openai.com/news`
  * 前沿研究: `https://openai.com/index/research`
* **Google DeepMind**
  * 官方博客: `https://deepmind.google/discover/blog`
* **Meta AI (FAIR)**
  * 官方博客: `https://ai.meta.com/blog`
* **Mistral AI**
  * 官方动态: `https://mistral.ai/news`
* **Anthropic**
  * 官方动态: `https://www.anthropic.com/news`
  * 技术博客: `https://claude.com/blog`

### 2. 开源生态与应用工程 (Open Source & Infra)
* **Hugging Face**
  * 技术博客: `https://huggingface.co/blog`
  * 每日精选论文: `https://huggingface.co/papers`
* **LangChain**
  * 官方博客: `https://blog.langchain.dev`
* **LlamaIndex**
  * 官方博客: `https://www.llamaindex.ai/blog`

### 3. 独立技术博客与深度硬核分析 (Tech Blogs & Deep Dives)
* **Lil'Log (Lilian Weng)**: `https://lilianweng.github.io`
* **Interconnects (Nathan Lambert)**: `https://www.interconnects.ai`
* **Latent Space**: `https://www.latent.space`
* **SemiAnalysis**: `https://www.semianalysis.com`

---

## 🚀 使用方式 (Usage)

在 Agent 交互界面中直接通过如下指令触发：

- `"帮我总结一下最近一周的 AI 动态"`
- `"抓取 AI 前沿博客的最新更新"`
- `"运行 ai-latest-news 技能"`

Agent 将直接使用原生网页抓取与解析能力，对上述源进行时间窗口过滤（默认最近 7 天），并在对话框中输出排版精美的中文报告。

---

## 📁 目录结构 (Repository Structure)

- `SKILL.md`: 技能定义与 Agent 执行 Protocol。
- `.gitignore`: 常用 Git 忽略配置。