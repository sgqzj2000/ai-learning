# AI Engineer 12 周学习路线

> 面向具备 **Python、SQL、Spark、Airflow、Databricks** 经验的数据工程师，目标是从「会用 API」到「能交付可运维的 Data Platform Copilot」。
>
> **主线能力：** 生成式 AI 基础 → RAG 与评估 → 向量库工程化 →（原理与部署）→ 企业级 RAG → Agent / LangGraph → MCP → 综合项目

## 目录

- [先决条件与环境](#先决条件与环境)
- [三阶段路线图](#三阶段路线图)
- [学习目标与节奏](#学习目标与节奏)
- [12 周总览](#12-周总览)
- [路径设计说明](#路径设计说明)
- [分周计划（Week 1–12）](#week-1生成式-ai-与-prompt-engineering)
- [毕业项目与周交付映射](#毕业项目与周交付映射)
- [学习优先级与时间分配](#学习优先级与时间分配)
- [每周复盘模板](#每周复盘模板)
- [官方资源收藏](#官方资源收藏)
- [职业能力路径](#职业能力路径)

---

## 先决条件与环境

### 技能先决条件

| 领域 | 期望水平 |
|---|---|
| Python | 能写模块、依赖管理、简单 async |
| SQL | 复杂查询、只读分析场景 |
| 数据平台 | 接触过 Airflow / Spark / 仓库表结构 / Runbook |
| Git | 分支、PR、`.env` 不入库 |
| 容器 | 能跑 `docker compose` |

### 环境清单（Week 1 前完成）

- Python 3.11+，推荐 `uv` 或 `poetry` 管理虚拟环境
- Docker Desktop（Week 4 起 Qdrant；Week 12 Compose 全栈）
- 至少一种 LLM 访问方式：**OpenAI / Azure OpenAI API**，或本机 **Ollama**（Week 7 前备好）
- 可选 GPU：Week 6 微调、Week 7 vLLM；无 GPU 可走文档中的**选修路径**
- 本仓库约定：每周代码放在 `weekNN-<topic>/`，根目录不放密钥

### 与现有工作的衔接

每周尽量用**真实但脱敏**的材料练手（Airflow 文档、内部规范摘要、表结构样例、故障 Runbook），这样 Week 8 与 Week 12 不是从零造场景，而是**把前几周作业升格为产品化**。

---

## 三阶段路线图

```mermaid
flowchart LR
  subgraph P1["阶段一：能用模型（W1–2）"]
    A1[Prompt 与 API]
    A2[Embedding 与 RAG 原型]
  end
  subgraph P2["阶段二：能建系统（W3–8）"]
    B1[LangChain 流水线]
    B2[Qdrant 生产化]
    B3[原理 / 微调 / 部署]
    B4[企业 RAG + 评估]
  end
  subgraph P3["阶段三：能连平台（W9–12）"]
    C1[Tool Agent]
    C2[LangGraph 多角色]
    C3[MCP]
    C4[Copilot 毕业项目]
  end
  P1 --> P2 --> P3
```

| 阶段 | 周次 | 结束时你能演示什么 |
|---|---|---|
| 一 | 1–2 | 3 个 Prompt 小工具 + 带引用的 PDF/文档问答 |
| 二 | 3–8 | Qdrant 上 1k+ 切片、可评估的企业知识库 API（Copilot V1） |
| 三 | 9–12 | 多工具 Agent、审批流、MCP 接 GitHub/文件/数据平台、Compose 一键启动 |

---

## 学习目标与节奏

完成本计划后，应具备：

- 使用云端或本地大模型开发生成式 AI 应用
- 理解 Prompt、Token、Embedding、Transformer 与 Attention（能讲清 RAG 里每一环在干什么）
- 独立构建**可评估**、带来源引用的 RAG 知识库（含 Hybrid / Rerank / 拒答）
- 使用 **Qdrant** 做语义检索、Payload 过滤与混合检索
- 使用 **Ollama** 或 **vLLM** 提供推理服务，并做基础压测
- 理解 SFT、LoRA、QLoRA（至少完成一次小规模实验或读懂训练配置）
- 使用 **LangGraph** 组织 Agent 与多 Agent 工作流（AutoGen / CrewAI 作对比阅读）
- 使用 **MCP** 连接文件系统、GitHub 与数据平台类工具
- 交付一个可部署的 **Data Engineer Copilot**（含日志与测试）

### 建议投入

| 时间 | 建议 |
|---|---:|
| 工作日 | 每天 1–1.5 小时 |
| 周末 | 4–6 小时 |
| 每周 | **10–15 小时**（低于 8 小时请优先「必做」） |
| 总周期 | 12 周（约 **120–180** 小时） |

### 每周固定动作

1. 阅读当周**必做**课程（选做留到有余力或第二遍）
2. 跑通官方示例 → 改成本周作业目录下的代码
3. 写清 `weekNN-*/README.md`：怎么跑、依赖、已知问题
4. 用当周**验收标准**自测；RAG 相关周更新测试问题集
5. Git 提交到对应周目录（不提交密钥与原始敏感数据）

---

## 12 周总览

| 周 | 阶段 | 主题 | 必做交付 | 学时（参考） |
|---:|---|---|---|---:|
| 1 | 一 | LLM 与 Prompt | API 客户端 + 3 个助手 | 10–12 |
| 2 | 一 | Embedding 与 RAG 入门 | 多格式 RAG + Chunk 实验 | 12–15 |
| 3 | 二 | LangChain 与 RAG 工程化 | Airflow 文档助手（**接 Qdrant**） | 12–15 |
| 4 | 二 | Qdrant 向量库 | 1k+ Chunks、Filter、Hybrid | 10–12 |
| 5 | 二 | Transformer 原理 | 架构图 + Attention 代码 | 8–10 |
| 6 | 二 | LoRA 微调 | SQL 微调对比（**无 GPU 可选修**） | 10–15 |
| 7 | 二 | 模型部署 | Ollama / vLLM + 压测 | 10–12 |
| 8 | 二 | 企业级 RAG | Copilot V1 + Ragas 评估 | 15–18 |
| 9 | 三 | Agent 基础 | 多工具 + 护栏 | 12–14 |
| 10 | 三 | LangGraph | Data Engineer 多节点图 | 14–16 |
| 11 | 三 | MCP | 自定义 Data Platform MCP | 12–14 |
| 12 | 三 | 毕业项目 | Data Engineer Copilot | 18–24 |

**核心课程来源（按周查阅详情）：** Microsoft GenAI / OpenAI Cookbook → LangChain + LLM Zoomcamp → Qdrant → LLM Course → LLaMA-Factory → Ollama/vLLM → LlamaIndex/Ragas → Microsoft AI Agents → LangGraph → MCP 官方文档。

---

## 路径设计说明

以下调整用于**减少返工、对齐数据工程场景**，周次编号不变，便于目录与习惯一致。

1. **Week 3 起向量库统一为 Qdrant**  
   不要在 Week 3 用临时内存向量库再在 Week 4 重写。直接复用 `week04-qdrant/docker-compose.yml`（可在 Week 3 先建目录与 compose），索引与检索 API 从 Week 3 就针对 Qdrant。

2. **Week 5 可与 Week 3–4 并行阅读**  
   不必等 Week 5 才做 RAG。最低要求：Week 2 后读 [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) 前半；Week 5 集中补 Attention 实现与笔记。Week 6 微调前需理解「下一 Token 预测」即可。

3. **评估从 Week 3 开始线程化**  
   Week 3 建立 `evaluation_questions.json`（≥20 题）；Week 8 扩展到 ≥30 题并接入 **Ragas**（或先手写「来源是否命中」规则）。避免 Week 8 才第一次测质量。

4. **Week 6 微调为选修加深**  
   时间紧或无机：精读 PEFT 文档 + 完成 `train_config.yaml` 与数据格式，用**已有 LoRA 权重**或云端 Notebook 跑 1 次短训练；必做项改为「前后对比表 + 能解释 rank/alpha」。

5. **Week 8 是 Week 3–4 的产品化，不是第二个 science project**  
    ingestion / retrieval 模块从周作业**迁移+加固**（增量、Hybrid、Rerank、拒答、API），不要另起一套目录结构。

6. **Agent 栈以 LangGraph 为主**  
   Week 9 理解 Tool / Memory / Agentic RAG；Week 10 用 LangGraph 实现审批与路由。AutoGen、CrewAI 各选 1 个官方 Quickstart 对比即可。

7. **可选：Databricks 对齐（与 NIKE/EDA 栈一致）**  
   - RAG 文档源：Unity Catalog 表说明、Job 说明、内部 Markdown  
   - 评估与追踪：MLflow Tracing / GenAI Evaluate（有 workspace 时替代部分手写评估表）  
   - MCP：表搜索、Job 运行状态、血缘查询与 Week 11 作业对齐  

---

## Week 1：生成式 AI 与 Prompt Engineering

**本周投入：** 10–12h · **必做：** 课程 00–05 + 3 个助手 · **选做：** 06–07 多模态章节

### 学习目标

- 理解 LLM、Token、上下文窗口和常用生成参数
- 掌握 Zero-shot、Few-shot、Role Prompt 和结构化输出
- 能通过 Python SDK 调用大模型

### 课程与章节

- [Generative AI for Beginners](https://microsoft.github.io/generative-ai-for-beginners/) · [GitHub](https://github.com/microsoft/generative-ai-for-beginners)
- [00 - Course Setup](https://github.com/microsoft/generative-ai-for-beginners/tree/main/00-course-setup) · [01 - Introduction](https://github.com/microsoft/generative-ai-for-beginners/tree/main/01-introduction-to-genai) · [02 - Comparing LLMs](https://github.com/microsoft/generative-ai-for-beginners/tree/main/02-exploring-and-comparing-different-llms) · [03 - Responsible AI](https://github.com/microsoft/generative-ai-for-beginners/tree/main/03-using-generative-ai-responsibly) · [04 - Prompt Fundamentals](https://github.com/microsoft/generative-ai-for-beginners/tree/main/04-prompt-engineering-fundamentals) · [05 - Advanced Prompts](https://github.com/microsoft/generative-ai-for-beginners/tree/main/05-advanced-prompts)

### 作业

1. 编写模型 API 客户端：System Prompt、用户输入、**耗时与 Token 统计**、可选流式。
2. 实现邮件润色、工作日报、**SQL 生成**三个助手（SQL 助手为全课程红线场景，后续周会复用）。
3. 整理 ≥10 个可复用 Prompt（SQL、PySpark、Airflow、文档总结、故障分析等），写入 `prompt_templates.md`。

### 交付物

- `week01-genai-basics/chat_client.py`
- `week01-genai-basics/prompt_templates.md`
- `week01-genai-basics/README.md`

### 验收标准

- [ ] 能解释 Token、上下文窗口、Temperature、Top-p
- [ ] 能区分 Zero-shot 与 Few-shot
- [ ] 能拿到**结构化 JSON**输出（`response_format` 或等价约束）
- [ ] 完成 3 个 Prompt 应用

---

## Week 2：Embedding、搜索与 RAG 入门

**本周投入：** 12–15h · **必做：** RAG 端到端 + Chunk 实验 · **选做：** OpenAI Cookbook 其他 vector 示例

### 学习目标

- 理解 Embedding、余弦相似度与 RAG 全流程
- 加载并切分 PDF、Markdown、TXT，保留元数据
- 完成带引用来源的文档问答

### 课程与章节

- [08 - Building Search Applications](https://github.com/microsoft/generative-ai-for-beginners/tree/main/08-building-search-applications) · [15 - RAG and Vector Databases](https://github.com/microsoft/generative-ai-for-beginners/tree/main/15-rag-and-vector-databases)
- [OpenAI Cookbook](https://github.com/openai/openai-cookbook) · [Vector DB Examples](https://github.com/openai/openai-cookbook/tree/main/examples/vector_databases)
- 选读：[11 - Function Calling](https://github.com/microsoft/generative-ai-for-beginners/tree/main/11-integrating-with-function-calling)（Week 9 会再用）

### RAG 流程

```text
Document → Loader → Splitter → Chunks → Embeddings → Vector Store
         → Retriever → Context + Question → LLM → Answer + Sources
```

### 作业

1. 支持 PDF / MD / TXT，元数据含文档名、页码或段落、Chunk ID。
2. PDF 问答：上传、索引、检索、回答、**来源引用**。
3. 对比 Chunk Size `300/500/800`、Overlap `0/50/100`、Top-K `3/5/10`，结论写入 `chunk_experiment.md`（选 1 组作为 Week 3 默认）。

### 交付物

- `week02-rag-basics/document_loader.py`
- `week02-rag-basics/index_documents.py`
- `week02-rag-basics/rag_chat.py`
- `week02-rag-basics/chunk_experiment.md`

### 验收标准

- [ ] 能解释 Embedding 与余弦相似度
- [ ] ≥3 种文档格式
- [ ] 回答含来源位置
- [ ] 完成 Chunk 参数实验并有**明确推荐默认值**

---

## Week 3：LangChain 与 RAG 工程化

**本周投入：** 12–15h · **必做：** 流水线拆分 + Qdrant + 20 题评测集 · **选做：** LLM Zoomcamp 额外模块

### 学习目标

- LangChain（或同构抽象）的加载、切分、索引、检索、生成
- **索引与问答解耦**，可增量更新
- 建立可持续扩展的评测问题集

### 课程与章节

- [LangChain Overview](https://docs.langchain.com/oss/python/langchain/overview) · [Retrieval](https://docs.langchain.com/oss/python/langchain/retrieval) · [GitHub](https://github.com/langchain-ai/langchain)
- [LLM Zoomcamp](https://github.com/DataTalksClub/llm-zoomcamp)

### 作业

1. 语料：Airflow 官方文档 + 脱敏 Runbook（与 Week 8 同源，避免重复收集）。
2. **使用 Qdrant**（compose 可与 `week04-qdrant` 共享）：增量索引、Top-K、Metadata Filter、来源引用、**检索日志**（打了哪些 chunk）。
3. `evaluation_questions.json` ≥20 题：预期答案要点、预期来源、实际召回、是否通过。

### 交付物

- `week03-airflow-rag/ingestion_pipeline.py`
- `week03-airflow-rag/retrieval_pipeline.py`
- `week03-airflow-rag/evaluation_questions.json`

### 验收标准

- [ ] 索引与问答逻辑分离
- [ ] 支持增量导入与 Metadata Filter
- [ ] 可查看实际召回 Chunks
- [ ] ≥20 题评测集且每周可重跑

---

## Week 4：Qdrant 向量数据库

**本周投入：** 10–12h · **必做：** 持久化 + 1k Chunks + Hybrid · **选做：** 多 Collection 与备份策略

### 学习目标

- Docker 部署 Qdrant，理解 Collection / Point / Payload / Filter
- Dense、Sparse 与 Hybrid Search 的差异与适用场景

### 课程与章节

- [Qdrant Documentation](https://qdrant.tech/documentation/) · [Quickstart](https://qdrant.tech/documentation/quickstart/) · [Collections](https://qdrant.tech/documentation/concepts/collections/) · [Search](https://qdrant.tech/documentation/concepts/search/) · [Filtering](https://qdrant.tech/documentation/concepts/filtering/) · [Hybrid Queries](https://qdrant.tech/documentation/concepts/hybrid-queries/)

### 作业

1. `docker-compose.yml` 持久化卷；重启后数据仍在。
2. 导入 **≥1,000** Chunks（可合并 Week 3 语料），Payload：文档 ID、类型、来源、更新时间等。
3. 语义检索、Filter、Top-K、Hybrid；`benchmark.md` 记录写入/查询耗时与 2–3 个召回样例。

### 交付物

- `week04-qdrant/docker-compose.yml`
- `week04-qdrant/create_collection.py`
- `week04-qdrant/load_vectors.py`
- `week04-qdrant/search_vectors.py`
- `week04-qdrant/benchmark.md`

### 验收标准

- [ ] 重启不丢数据
- [ ] ≥1,000 Chunks
- [ ] Payload 更新/删除与 Filter
- [ ] 有 Hybrid 或明确说明为何仅用 Dense

---

## Week 5：Transformer 与 LLM 原理

**本周投入：** 8–10h · **可与 W3–4 并行** · **必做：** Illustrated Transformer + Attention 代码

### 学习目标

- Tokenization、Embedding、Attention、Decoder-only、下一 Token 预测
- 能向同事解释「RAG 检索」与「生成」在模型里分别对应什么

### 课程与章节

- [LLM Course](https://github.com/mlabonne/llm-course)（README：Fundamentals、Architecture、Tokenization、Attention、Sampling）
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)
- 选读：[LLMs from Scratch](https://github.com/rasbt/LLMs-from-scratch) · [nanoGPT](https://github.com/karpathy/nanoGPT)

### 作业

1. 架构图：Tokenizer → Embedding → Attention → FFN → Residual → LayerNorm → 输出。
2. ~1,000 字原理总结（`transformer-summary.md`）。
3. NumPy 或 PyTorch 实现 Scaled Dot-Product Attention。

### 交付物

- `week05-transformer/transformer-architecture.md`
- `week05-transformer/attention_demo.py`
- `week05-transformer/transformer-summary.md`

### 验收标准

- [ ] 能解释 Q/K/V、Self-Attention、Causal Mask
- [ ] 能解释 GPT 下一 Token 预测
- [ ] Attention 最小实现可运行

---

## Week 6：SFT、LoRA 与 QLoRA

**本周投入：** 10–15h（**无 GPU：8h 理论+配置选修**）

### 学习目标

- Pre-training、SFT、Instruction Tuning；LoRA / QLoRA 原理
- 完成小规模 **SQL 生成**微调或等价实验记录

### 课程与章节

- [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory) · [Docs](https://llamafactory.readthedocs.io/)
- [Hugging Face PEFT](https://huggingface.co/docs/peft/index)

### 作业

1. ≥100 条脱敏 SQL 指令数据（与 Week 1 SQL 助手同风格）。
2. 记录模型、batch、lr、epoch、LoRA rank/alpha、耗时、显存。
3. ≥20 题对比微调前后正确性与风格；`before_after_comparison.md`。

### 交付物

- `week06-finetuning/sql_instruction_dataset.json`
- `week06-finetuning/train_config.yaml`
- `week06-finetuning/evaluation_questions.json`
- `week06-finetuning/before_after_comparison.md`

### 验收标准

- [ ] 能解释 SFT、LoRA、QLoRA
- [ ] 至少一次训练实验 **或** 完整复现配置+他人权重推理对比
- [ ] 数据集无企业敏感信息

---

## Week 7：本地模型与推理服务部署

**本周投入：** 10–12h · **必做：** Ollama + 压测 · **有 GPU：** vLLM OpenAI 兼容 API

### 学习目标

- Ollama 本地推理与流式；vLLM 服务化概念
- TTFT、吞吐、成功率基础指标

### 课程与章节

- [Ollama](https://github.com/ollama/ollama) · [API](https://github.com/ollama/ollama/blob/main/docs/api.md)
- [vLLM](https://docs.vllm.ai/) · [OpenAI-Compatible Server](https://docs.vllm.ai/en/latest/serving/openai_compatible_server.html)

### 作业

1. Ollama 跑适合本机规模的模型，API + 流式。
2. 有 GPU 部署 vLLM；无 GPU 在 `README` 写清 vLLM 步骤并用 Ollama 完成压测。
3. ≥20 次请求：`benchmark-results.md` 含 TTFT、总时延、tokens/s、成功率。

### 交付物

- `week07-model-serving/ollama_client.py`
- `week07-model-serving/openai_compatible_client.py`
- `week07-model-serving/benchmark.py`
- `week07-model-serving/benchmark-results.md`

### 验收标准

- [ ] API 调通本地模型与流式
- [ ] 能说明量化 / GGUF / OpenAI 兼容端点
- [ ] 有可复现压测数字

---

## Week 8：企业级 RAG

**本周投入：** 15–18h · **阶段二里程碑**

### 学习目标

- 在 Week 3–4 基础上：**Hybrid、Rerank、拒答、增量、评估**
- 交付 **Data Platform Copilot V1**（API 优先，UI 可极简）

### 课程与章节

- [LangChain Retrieval](https://docs.langchain.com/oss/python/langchain/retrieval) · [LlamaIndex Starter](https://docs.llamaindex.ai/en/stable/getting_started/starter_example/) · [Ragas](https://docs.ragas.io/)

### 作业

1. 知识库：Airflow、Databricks、Spark、规范、脱敏 Runbook（与前几周语料合并治理）。
2. Dense + Filter + Hybrid + Rerank + 引用 + **无资料拒答**。
3. 评测 ≥30 题：来源命中、忠实度、相关性（Ragas 或规则表）；结果存档 `evaluation/`。

### 交付物

- `week08-enterprise-rag/ingestion/` · `retrieval/` · `evaluation/` · `api/`
- `week08-enterprise-rag/ui/`（可选 Streamlit）
- `week08-enterprise-rag/docker-compose.yml`

### 验收标准

- [ ] 增量、Filter、Hybrid、Rerank 至少各 1 处落地
- [ ] 有引用；无资料不编造
- [ ] ≥30 题评估可重复运行

---

## Week 9：AI Agent 基础

**本周投入：** 12–14h · **必做：** 3 工具 + 护栏 · **选做：** Agentic RAG 与 Week 8 联调

### 学习目标

- Agent、Tool Calling、Memory、Agentic RAG
- 安全的多工具 Agent（只读 SQL、审计日志）

### 课程与章节

- [AI Agents for Beginners](https://microsoft.github.io/ai-agents-for-beginners/) · 01–07（Setup 至 Planning）

### 作业

1. 工具：时间查询、文档搜索（接 Week 8 检索）、SQLite **只读**。
2. Memory：最近对话、会话摘要、清除；可选用户偏好。
3. 护栏：参数校验、SQL 只读、超时重试、高风险拒绝、**工具调用审计日志**。

### 交付物

- `week09-agent-basics/agent.py` · `tools/` · `memory/` · `guardrails/`

### 验收标准

- [ ] 路由到正确工具
- [ ] Tool Schema 清晰
- [ ] SQL 仅 SELECT
- [ ] 每次工具调用有日志

---

## Week 10：LangGraph 与 Multi-Agent

**本周投入：** 14–16h · **必做：** LangGraph · **选做：** AutoGen/CrewAI 各 1 个 demo

### 学习目标

- 状态图、条件路由、持久化、Human-in-the-loop
- Data Engineer 多角色：分析 → 生成 → 审查 → 安全

### 课程与章节

- [LangGraph Overview](https://docs.langchain.com/oss/python/langgraph/overview) · [Quickstart](https://docs.langchain.com/oss/python/langgraph/quickstart) · [Workflows and Agents](https://docs.langchain.com/oss/python/langgraph/workflows-agents)

### 作业

1. 节点：SQL / PySpark / Airflow DAG 生成（复用 Week 1 Prompt 与 Week 8 上下文）。
2. 流程：Requirement → Generator → Reviewer → Security Checker。
3. 写 SQL、改文件、改 DAG、调外部 API 前 **人工审批**。

### 交付物

- `week10-langgraph-agent/graph.py` · `state.py` · `nodes/` · `tools/` · `reviewers/`

### 验收标准

- [ ] ≥4 节点 + 1 条条件边
- [ ] 审查与安全检查
- [ ] 高风险需批准；失败可重试或降级

---

## Week 11：Model Context Protocol

**本周投入：** 12–14h

### 学习目标

- MCP Host / Client / Server；Tool vs Resource
- 自定义 **Data Platform MCP**（表、Schema、血缘、DAG/Job 状态）

### 课程与章节

- [MCP 文档](https://modelcontextprotocol.io/) · [Architecture](https://modelcontextprotocol.io/docs/learn/architecture) · [Build Server](https://modelcontextprotocol.io/docs/develop/build-server) · [Official Servers](https://github.com/modelcontextprotocol/servers)

### 作业

1. Filesystem MCP（限制根目录）+ GitHub MCP（仓库/Issue/PR）。
2. 自研 MCP：`表搜索`、`Schema`、`血缘`、`DAG/运行状态`（可读 mock 或只读 API）。
3. `security-design.md`：允许名单、只读、超时、审计、凭据走环境变量。

### 交付物

- `week11-mcp/mcp_server.py` · `mcp_client.py` · `tools/` · `resources/` · `security-design.md`

### 验收标准

- [ ] 说清 Tool 与 Resource
- [ ] 跑通 1 个官方 Server + 1 个自研 Server
- [ ] 范围限制与密钥不入库

---

## Week 12：毕业项目 Data Engineer Copilot

**本周投入：** 18–24h · **整合，避免新造轮子**

### 项目目标

把 Week 8 API、Week 10 图、Week 11 MCP **合并**为可 Compose 启动的 Copilot，并补齐可观测性与测试。

### 推荐架构

```text
Web UI (Streamlit / 可选 Next.js)
  ↓
FastAPI
  ↓
LangGraph Agent
  ├── RAG (Week 8)
  ├── SQL / PySpark / Airflow Generators
  ├── Reviewer + Security
  └── MCP Client (Week 11)
  ↓
Cloud LLM or Ollama/vLLM (Week 7)
  ↓
Qdrant (Week 4)
```

### 功能要求（摘要）

| 模块 | 要求 |
|---|---|
| RAG | 增删改索引、Hybrid、Rerank、引用、拒答 |
| SQL | NL→SQL、方言、格式化与风险提示；**不执行写操作** |
| PySpark | DataFrame API；提示 Join/Collect/分区风险 |
| Airflow | DAG/Schedule/Retry/Callback；检查 catchup/并发 |
| 工作流 | 意图路由 → 生成 → 审查 → 安全 → **人工批准** → 响应 |
| 可观测性 | Request ID、路由、工具调用、检索片段、Token、延迟、错误状态 |

### 推荐技术栈

Python · FastAPI · LangGraph · LangChain 或 LlamaIndex · Qdrant · OpenAI/Ollama · MCP SDK · Docker Compose · pytest · Ruff

### 建议仓库结构

```text
data-engineer-copilot/
├── README.md · .env.example · docker-compose.yml · pyproject.toml
├── app/{api,agent,rag,tools,mcp,prompts,ui}
├── ingestion/ · evaluation/ · tests/ · scripts/ · docs/
```

### 最终验收标准

- [ ] `docker compose up` 可启动核心路径
- [ ] RAG 有引用；无资料拒答
- [ ] Agent 路由与工具失败可处理
- [ ] 高风险需人工批准；SQL/文件默认只读或受限
- [ ] 环境变量配置；含测试、架构说明、部署步骤

---

## 毕业项目与周交付映射

| 毕业项目模块 | 主要来源周 | 迁移时注意 |
|---|---|---|
| `app/rag/*` | 3, 4, 8 | 勿复制粘贴第三套 ingestion |
| `app/api` + Compose | 7, 8 | 模型端点环境变量化 |
| `app/agent/graph` | 9, 10 | 审批节点与 Week 10 一致 |
| `app/mcp/*` | 11 | 安全设计文档进 `docs/` |
| SQL 风格与评测 | 1, 6 | Prompt + 可选 LoRA |
| `evaluation/*` | 3, 8 | 问题集合并去重 |
| 压测与 SLO 参考 | 7 | 写入 `docs/performance.md` |

---

## 学习优先级与时间分配

时间不够时按此砍 **选做**，保留 **必做** 与阶段里程碑（Week 8、Week 12）。

| 方向 | 建议占比 | 优先级 |
|---|---:|---|
| 企业级 RAG + 评估 | 35% | 最高 |
| Agent 与 LangGraph | 25% | 最高 |
| MCP 与工具集成 | 15% | 高 |
| 模型部署 | 10% | 中高 |
| Prompt Engineering | 5% | 中 |
| Transformer 原理 | 5% | 中 |
| LoRA 微调 | 5% | 中低（可选修） |

**固定主栈：**

```text
Python + FastAPI + LangChain + LangGraph + Qdrant + OpenAI/Ollama + MCP + Docker Compose
```

### 常见误区

- 每周换一套向量库实现 → **从 Week 3 起锁定 Qdrant**
- 只做 Demo 不做评测集 → **Week 3 起维护 `evaluation_questions.json`**
- 毕业周重写 RAG → **在 Week 8 目录上演进**
- Agent 无护栏直接连生产库 → **只读 + 审批 + 审计**

---

## 每周复盘模板

```markdown
## Week X 学习复盘

### 本周目标（必做 / 选做）

- 必做：
- 选做：

### 课程进度

- [ ] 
- [ ] 

### 作业与交付物

- [ ] 
- GitHub 路径：

### 三个核心概念（用自己的话）

1. 
2. 
3. 

### 阻塞与解决

1. 

### 评测 / 指标（RAG 周填写）

- 题数：  通过率：  主要失败类型：

### 自评（/10）

理论 · 实践 · 排错 · 工程 · 文档

### 下周一条改进

- 
```

---

## 官方资源收藏

| 类别 | 资源 |
|---|---|
| 生成式 AI | [Microsoft Generative AI for Beginners](https://microsoft.github.io/generative-ai-for-beginners/) |
| AI Agent | [Microsoft AI Agents for Beginners](https://microsoft.github.io/ai-agents-for-beginners/) |
| LLM 路线 | [LLM Course](https://github.com/mlabonne/llm-course) |
| RAG 课程 | [LLM Zoomcamp](https://github.com/DataTalksClub/llm-zoomcamp) |
| LangChain / LangGraph | [LangChain Docs](https://docs.langchain.com/) · [LangGraph](https://docs.langchain.com/oss/python/langgraph/overview) |
| LlamaIndex / Ragas | [LlamaIndex](https://docs.llamaindex.ai/) · [Ragas](https://docs.ragas.io/) |
| 向量库 | [Qdrant](https://qdrant.tech/documentation/) |
| 微调 | [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory) · [PEFT](https://huggingface.co/docs/peft/index) |
| 推理 | [Ollama](https://github.com/ollama/ollama) · [vLLM](https://docs.vllm.ai/) |
| 多 Agent 对比 | [AutoGen](https://microsoft.github.io/autogen/) · [CrewAI](https://docs.crewai.com/) |
| MCP | [modelcontextprotocol.io](https://modelcontextprotocol.io/) · [Official Servers](https://github.com/modelcontextprotocol/servers) |

---

## 职业能力路径

```text
Senior Data Engineer
        ↓
AI Application Engineer（应用与 API）
        ↓
RAG Engineer（检索、评估、知识库运维）
        ↓
AI Agent Engineer（工作流、工具、安全）
        ↓
Data Platform AI Engineer（MCP + 平台元数据 + 生产规范）
```

**优先落地场景（与 12 周作业对齐）：**

1. Data Platform Knowledge Copilot（Week 8 / 12）
2. Airflow Operations Assistant（Week 3 RAG 语料）
3. Databricks / Spark 文档助手（Week 8 知识库）
4. SQL 生成与审查 Agent（Week 1 + 6 + 10）
5. PySpark Code Review Agent（Week 10）
6. 数据质量 / 故障 Runbook Agent（Week 2–3 语料）
7. 元数据与血缘 MCP（Week 11）
8. GitHub 代码检索（Week 11 MCP）
9. 可观测性：请求链路日志（Week 12）
10. 评估回归：发版前跑评测集（Week 3 起）
