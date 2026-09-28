# AI Engineer 12 周学习路线

> 面向具备 Python、SQL、Spark、Airflow、Databricks 等经验的数据工程师。
>
> 核心路线：`生成式 AI 基础 → RAG → 向量数据库 → Transformer → 微调 → 模型部署 → 企业级 RAG → Agent → Multi-Agent → MCP → 综合项目`

## 学习目标

完成本计划后，应具备以下能力：

- 使用云端或本地大模型开发生成式 AI 应用
- 理解 Prompt、Token、Embedding、Transformer 和 Attention
- 独立构建带来源引用的 RAG 知识库
- 使用 Qdrant 完成语义检索、过滤和混合检索
- 使用 Ollama 或 vLLM 部署开源模型
- 理解 SFT、LoRA 和 QLoRA
- 使用 LangGraph 构建 Agent 与多 Agent 工作流
- 使用 MCP 连接文件系统、GitHub 和数据平台工具
- 完成一个可部署的 Data Engineer Copilot

## 学习节奏

| 时间 | 建议投入 |
|---|---:|
| 工作日 | 每天 1 至 1.5 小时 |
| 周末 | 4 至 6 小时 |
| 每周 | 10 至 15 小时 |
| 总周期 | 12 周 |
| 总投入 | 约 120 至 180 小时 |

每周执行流程：

1. 阅读指定课程章节
2. 运行官方示例
3. 独立完成作业
4. 补充 README 和学习笔记
5. 按验收标准自测
6. 将代码提交到对应周目录

## 12 周总览

| 周次 | 主题 | 核心课程 | 作业 | 交付物 |
|---:|---|---|---|---|
| 1 | LLM 与 Prompt | Microsoft Generative AI for Beginners | 3 个 Prompt 助手 | API Demo |
| 2 | Embedding 与 RAG | Microsoft GenAI、OpenAI Cookbook | PDF 问答机器人 | RAG Demo |
| 3 | LangChain 与 RAG 工程化 | LangChain、LLM Zoomcamp | Airflow 文档助手 | Airflow RAG |
| 4 | 向量数据库 | Qdrant | 导入 1,000+ Chunks | Qdrant 服务 |
| 5 | Transformer | LLM Course、Illustrated Transformer | Attention 实验 | 原理笔记 |
| 6 | LoRA 微调 | LLaMA-Factory、PEFT | SQL 模型微调 | LoRA Adapter |
| 7 | 模型部署 | Ollama、vLLM | 本地推理 API | 模型服务 |
| 8 | 企业级 RAG | LangChain、LlamaIndex、Ragas | Data Platform Copilot V1 | 企业 RAG |
| 9 | Agent 基础 | Microsoft AI Agents for Beginners | 多工具 Agent | Tool Agent |
| 10 | LangGraph 与 Multi-Agent | LangGraph、AutoGen、CrewAI | Data Engineer Agent | Agent Graph |
| 11 | MCP | MCP 官方课程 | Data Platform MCP | MCP Server |
| 12 | 综合项目 | 前 11 周内容 | Data Engineer Copilot | 完整项目 |

---

## Week 1：生成式 AI 与 Prompt Engineering

### 学习目标

- 理解 LLM、Token、上下文窗口和常用生成参数
- 掌握 Zero-shot、Few-shot、Role Prompt 和结构化输出
- 能通过 Python SDK 调用大模型

### 课程与章节

- [课程主页：Generative AI for Beginners](https://microsoft.github.io/generative-ai-for-beginners/)
- [GitHub 仓库](https://github.com/microsoft/generative-ai-for-beginners)
- [00 - Course Setup](https://github.com/microsoft/generative-ai-for-beginners/tree/main/00-course-setup)
- [01 - Introduction to Generative AI](https://github.com/microsoft/generative-ai-for-beginners/tree/main/01-introduction-to-genai)
- [02 - Exploring and Comparing Different LLMs](https://github.com/microsoft/generative-ai-for-beginners/tree/main/02-exploring-and-comparing-different-llms)
- [03 - Using Generative AI Responsibly](https://github.com/microsoft/generative-ai-for-beginners/tree/main/03-using-generative-ai-responsibly)
- [04 - Prompt Engineering Fundamentals](https://github.com/microsoft/generative-ai-for-beginners/tree/main/04-prompt-engineering-fundamentals)
- [05 - Advanced Prompts](https://github.com/microsoft/generative-ai-for-beginners/tree/main/05-advanced-prompts)

### 作业

1. 编写一个模型 API 客户端，支持 System Prompt、用户输入、响应耗时与 Token 记录。
2. 实现邮件润色助手、工作日报助手和 SQL 生成助手。
3. 整理至少 10 个可复用 Prompt，覆盖 SQL、PySpark、Airflow、文档总结、故障分析等场景。

### 交付物

- `week01-genai-basics/chat_client.py`
- `week01-genai-basics/prompt_templates.md`
- `week01-genai-basics/README.md`

### 验收标准

- [ ] 能解释 Token、上下文窗口、Temperature 和 Top-p
- [ ] 能区分 Zero-shot 与 Few-shot
- [ ] 能调用一个大模型并获得结构化 JSON 输出
- [ ] 完成至少 3 个 Prompt 应用

---

## Week 2：Embedding、搜索与 RAG 入门

### 学习目标

- 理解 Embedding、余弦相似度和 RAG 流程
- 能加载并切分 PDF、Markdown 和 TXT
- 完成带引用来源的文档问答应用

### 课程与章节

- [08 - Building Search Applications](https://github.com/microsoft/generative-ai-for-beginners/tree/main/08-building-search-applications)
- [11 - Integrating with Function Calling](https://github.com/microsoft/generative-ai-for-beginners/tree/main/11-integrating-with-function-calling)
- [15 - RAG and Vector Databases](https://github.com/microsoft/generative-ai-for-beginners/tree/main/15-rag-and-vector-databases)
- [OpenAI Cookbook](https://github.com/openai/openai-cookbook)
- [OpenAI Cookbook Examples](https://github.com/openai/openai-cookbook/tree/main/examples)
- [Vector Database Examples](https://github.com/openai/openai-cookbook/tree/main/examples/vector_databases)

### RAG 流程

```text
Document → Loader → Splitter → Chunks → Embeddings → Vector DB
         → Retriever → Context + Question → LLM → Answer + Sources
```

### 作业

1. 支持 PDF、Markdown、TXT 文档加载与切分，并保留文档名、页码、Chunk ID 等元数据。
2. 完成 PDF 问答机器人，支持上传、索引、检索、回答和来源引用。
3. 对 Chunk Size `300/500/800`、Overlap `0/50/100`、Top-K `3/5/10` 做对比实验。

### 交付物

- `week02-rag-basics/document_loader.py`
- `week02-rag-basics/index_documents.py`
- `week02-rag-basics/rag_chat.py`
- `week02-rag-basics/chunk_experiment.md`

### 验收标准

- [ ] 能解释 Embedding 与余弦相似度
- [ ] 支持至少 3 种文档格式
- [ ] 回答包含来源位置
- [ ] 完成 Chunk 参数对比实验

---

## Week 3：LangChain 与 RAG 工程化

### 学习目标

- 掌握 LangChain 的加载、切分、索引、检索和生成组件
- 构建 Airflow 文档助手
- 建立基础的 RAG 测试问题集

### 课程与章节

- [LangChain 文档](https://docs.langchain.com/)
- [LangChain Python Overview](https://docs.langchain.com/oss/python/langchain/overview)
- [LangChain Retrieval](https://docs.langchain.com/oss/python/langchain/retrieval)
- [LangChain GitHub](https://github.com/langchain-ai/langchain)
- [LLM Zoomcamp](https://github.com/DataTalksClub/llm-zoomcamp)

### 作业

1. 准备 Airflow 官方文档与脱敏 Runbook。
2. 实现文档导入、增量索引、Top-K、Metadata Filter、来源引用和检索日志。
3. 建立至少 20 个测试问题，记录预期答案、预期来源、实际召回和是否通过。

### 交付物

- `week03-airflow-rag/ingestion_pipeline.py`
- `week03-airflow-rag/retrieval_pipeline.py`
- `week03-airflow-rag/evaluation_questions.json`

### 验收标准

- [ ] 索引与问答逻辑分离
- [ ] 支持增量导入和 Metadata Filter
- [ ] 可查看实际召回的 Chunks
- [ ] 完成至少 20 个测试问题

---

## Week 4：Qdrant 向量数据库

### 学习目标

- 使用 Docker 部署 Qdrant
- 掌握 Collection、Point、Payload、Filter 和 Search
- 理解 Dense、Sparse 与 Hybrid Search

### 课程与章节

- [Qdrant Documentation](https://qdrant.tech/documentation/)
- [Quickstart](https://qdrant.tech/documentation/quickstart/)
- [Collections](https://qdrant.tech/documentation/concepts/collections/)
- [Points](https://qdrant.tech/documentation/concepts/points/)
- [Search](https://qdrant.tech/documentation/concepts/search/)
- [Filtering](https://qdrant.tech/documentation/concepts/filtering/)
- [Payload](https://qdrant.tech/documentation/concepts/payload/)
- [Hybrid Queries](https://qdrant.tech/documentation/concepts/hybrid-queries/)
- [Qdrant GitHub](https://github.com/qdrant/qdrant)

### 作业

1. 使用 Docker Compose 部署 Qdrant，并配置数据持久化。
2. 导入至少 1,000 个 Chunks，保存文档 ID、Chunk ID、类型、来源、更新时间等 Payload。
3. 完成语义检索、Metadata Filter、Top-K 和 Hybrid Search。
4. 记录平均写入耗时、查询耗时和召回示例。

### 交付物

- `week04-qdrant/docker-compose.yml`
- `week04-qdrant/create_collection.py`
- `week04-qdrant/load_vectors.py`
- `week04-qdrant/search_vectors.py`
- `week04-qdrant/benchmark.md`

### 验收标准

- [ ] 容器重启后数据不丢失
- [ ] 已导入 1,000+ Chunks
- [ ] 支持 Payload Filter、更新和删除
- [ ] 完成查询延迟记录

---

## Week 5：Transformer 与 LLM 原理

### 学习目标

- 理解 Tokenization、Embedding、Attention 和生成过程
- 理解 Decoder-only LLM
- 能用自己的语言解释 GPT 如何预测下一个 Token

### 课程与章节

- [LLM Course](https://github.com/mlabonne/llm-course)
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)
- [LLMs from Scratch](https://github.com/rasbt/LLMs-from-scratch)
- [nanoGPT](https://github.com/karpathy/nanoGPT)

重点阅读 LLM Course README 中的：

- LLM Fundamentals
- LLM Architecture
- Tokenization
- Attention Mechanisms
- Sampling Techniques
- LLM Scientist Roadmap
- LLM Engineer Roadmap

### 作业

1. 绘制包含 Tokenizer、Embedding、Attention、FFN、Residual、LayerNorm、Softmax 的架构图。
2. 编写约 1,000 字的 Transformer 原理总结。
3. 使用 NumPy 或 PyTorch 实现 Scaled Dot-Product Attention。

### 交付物

- `week05-transformer/transformer-architecture.md`
- `week05-transformer/attention_demo.py`
- `week05-transformer/transformer-summary.md`

### 验收标准

- [ ] 能解释 Query、Key、Value
- [ ] 能解释 Self-Attention 和 Causal Mask
- [ ] 能解释 GPT 的下一 Token 预测
- [ ] 完成最小 Attention 代码

---

## Week 6：SFT、LoRA 与 QLoRA

### 学习目标

- 理解 Pre-training、SFT、Instruction Tuning
- 理解 LoRA 与 QLoRA
- 完成小规模 SQL 生成模型微调实验

### 课程与章节

- [LLaMA-Factory GitHub](https://github.com/hiyouga/LLaMA-Factory)
- [LLaMA-Factory Documentation](https://llamafactory.readthedocs.io/)
- [Installation](https://llamafactory.readthedocs.io/en/latest/getting_started/installation.html)
- [Quickstart](https://llamafactory.readthedocs.io/en/latest/getting_started/quickstart.html)
- [Data Preparation](https://llamafactory.readthedocs.io/en/latest/getting_started/data_preparation.html)
- [Hugging Face PEFT](https://huggingface.co/docs/peft/index)
- [PEFT GitHub](https://github.com/huggingface/peft)

### 作业

1. 准备至少 100 条脱敏 SQL 指令数据。
2. 记录模型、Batch Size、Learning Rate、Epoch、LoRA Rank、Alpha、耗时和显存。
3. 使用至少 20 个问题对比微调前后的 SQL 正确性与风格一致性。

### 交付物

- `week06-finetuning/sql_instruction_dataset.json`
- `week06-finetuning/train_config.yaml`
- `week06-finetuning/evaluation_questions.json`
- `week06-finetuning/before_after_comparison.md`

### 验收标准

- [ ] 能解释 SFT、LoRA 和 QLoRA
- [ ] 完成至少一次微调实验
- [ ] 完成前后效果对比
- [ ] 数据集不包含企业敏感信息

---

## Week 7：本地模型与推理服务部署

### 学习目标

- 使用 Ollama 运行本地模型
- 使用 vLLM 提供 OpenAI-Compatible API
- 对比模型的延迟与吞吐量

### 课程与章节

- [Ollama GitHub](https://github.com/ollama/ollama)
- [Ollama Model Library](https://ollama.com/library)
- [Ollama API](https://github.com/ollama/ollama/blob/main/docs/api.md)
- [vLLM Documentation](https://docs.vllm.ai/)
- [vLLM GitHub](https://github.com/vllm-project/vllm)
- [OpenAI-Compatible Server](https://docs.vllm.ai/en/latest/serving/openai_compatible_server.html)

### 作业

1. 使用 Ollama 运行一个适合本机资源的模型，支持 API 与流式输出。
2. 有 GPU 时部署 vLLM；无 GPU 时整理部署步骤并用 Ollama 完成核心实验。
3. 测试至少 20 次请求，记录 TTFT、总响应时间、Tokens/s 和成功率。

### 交付物

- `week07-model-serving/ollama_client.py`
- `week07-model-serving/openai_compatible_client.py`
- `week07-model-serving/benchmark.py`
- `week07-model-serving/benchmark-results.md`

### 验收标准

- [ ] 能通过 API 调用本地模型
- [ ] 支持流式输出
- [ ] 能解释 GGUF、量化和 OpenAI-Compatible API
- [ ] 完成基础性能测试

---

## Week 8：企业级 RAG

### 学习目标

- 整合前几周内容构建企业知识库
- 增加 Hybrid Search、Reranking、评估和增量更新
- 完成 Data Platform Copilot V1

### 课程与章节

- [LangChain Retrieval](https://docs.langchain.com/oss/python/langchain/retrieval)
- [LlamaIndex Documentation](https://docs.llamaindex.ai/)
- [LlamaIndex Starter Tutorial](https://docs.llamaindex.ai/en/stable/getting_started/starter_example/)
- [LlamaIndex GitHub](https://github.com/run-llama/llama_index)
- [Ragas Documentation](https://docs.ragas.io/)
- [Ragas GitHub](https://github.com/explodinggradients/ragas)

### 作业

1. 使用 Airflow、Databricks、Spark、开发规范和脱敏 Runbook 构建知识库。
2. 实现 Dense Search、Metadata Filter、Hybrid Search、Reranking、引用和无答案拒绝。
3. 准备至少 30 个测试问题，评估来源命中、忠实度和回答相关性。

### 交付物

- `week08-enterprise-rag/ingestion/`
- `week08-enterprise-rag/retrieval/`
- `week08-enterprise-rag/evaluation/`
- `week08-enterprise-rag/api/`
- `week08-enterprise-rag/ui/`
- `week08-enterprise-rag/docker-compose.yml`

### 验收标准

- [ ] 支持增量更新、Metadata Filter、Hybrid Search 和 Reranking
- [ ] 回答包含来源
- [ ] 无资料时拒绝编造
- [ ] 完成至少 30 个问题评估

---

## Week 9：AI Agent 基础

### 学习目标

- 理解 Agent、Tool Calling、Planning、Memory 和 Agentic RAG
- 构建一个安全的多工具 Agent

### 课程与章节

- [AI Agents for Beginners 课程主页](https://microsoft.github.io/ai-agents-for-beginners/)
- [GitHub 仓库](https://github.com/microsoft/ai-agents-for-beginners)
- [00 - Course Setup](https://github.com/microsoft/ai-agents-for-beginners/tree/main/00-course-setup)
- [01 - Introduction to AI Agents](https://github.com/microsoft/ai-agents-for-beginners/tree/main/01-intro-to-ai-agents)
- [02 - Explore Agentic Frameworks](https://github.com/microsoft/ai-agents-for-beginners/tree/main/02-explore-agentic-frameworks)
- [03 - Agentic Design Patterns](https://github.com/microsoft/ai-agents-for-beginners/tree/main/03-agentic-design-patterns)
- [04 - Tool Use](https://github.com/microsoft/ai-agents-for-beginners/tree/main/04-tool-use)
- [05 - Agentic RAG](https://github.com/microsoft/ai-agents-for-beginners/tree/main/05-agentic-rag)
- [06 - Building Trustworthy Agents](https://github.com/microsoft/ai-agents-for-beginners/tree/main/06-building-trustworthy-agents)
- [07 - Planning Design](https://github.com/microsoft/ai-agents-for-beginners/tree/main/07-planning-design)

### 作业

1. 实现时间查询、文档搜索、SQLite 只读查询三个工具。
2. 增加最近对话、用户偏好、会话摘要和清除记忆功能。
3. 增加参数校验、SQL 只读限制、超时、重试、高风险拒绝和审计日志。

### 交付物

- `week09-agent-basics/agent.py`
- `week09-agent-basics/tools/`
- `week09-agent-basics/memory/`
- `week09-agent-basics/guardrails/`

### 验收标准

- [ ] Agent 能选择正确工具
- [ ] Tool Schema 定义清晰
- [ ] SQL 工具仅允许只读查询
- [ ] 所有工具调用有日志

---

## Week 10：LangGraph 与 Multi-Agent

### 学习目标

- 使用状态图组织 Agent 工作流
- 掌握条件路由、持久化和 Human in the Loop
- 构建 Data Engineer Agent

### 课程与章节

- [LangGraph Overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [LangGraph Quickstart](https://docs.langchain.com/oss/python/langgraph/quickstart)
- [Workflows and Agents](https://docs.langchain.com/oss/python/langgraph/workflows-agents)
- [LangGraph GitHub](https://github.com/langchain-ai/langgraph)
- [AutoGen](https://microsoft.github.io/autogen/)
- [AutoGen GitHub](https://github.com/microsoft/autogen)
- [CrewAI Documentation](https://docs.crewai.com/)
- [CrewAI GitHub](https://github.com/crewAIInc/crewAI)

### 作业

1. 实现 SQL Generator、PySpark Generator 和 Airflow DAG Generator。
2. 建立 Requirement Analyzer、Generator、Reviewer、Security Checker 流程。
3. 在执行 SQL、覆盖文件、修改 DAG、调用外部 API 前加入人工审批。

### 交付物

- `week10-langgraph-agent/graph.py`
- `week10-langgraph-agent/state.py`
- `week10-langgraph-agent/nodes/`
- `week10-langgraph-agent/tools/`
- `week10-langgraph-agent/reviewers/`

### 验收标准

- [ ] 至少包含 4 个节点和 1 个条件路由
- [ ] 包含代码审核和安全检查
- [ ] 高风险操作需要人工批准
- [ ] 工作流支持错误处理和重试

---

## Week 11：Model Context Protocol

### 学习目标

- 理解 MCP Host、Client、Server、Tool、Resource 和 Prompt
- 运行现有 MCP Server
- 开发自定义 Data Platform MCP Server

### 课程与章节

- [MCP 官方网站](https://modelcontextprotocol.io/)
- [Introduction](https://modelcontextprotocol.io/docs/getting-started/intro)
- [Architecture](https://modelcontextprotocol.io/docs/learn/architecture)
- [Build an MCP Server](https://modelcontextprotocol.io/docs/develop/build-server)
- [Build an MCP Client](https://modelcontextprotocol.io/docs/develop/build-client)
- [MCP GitHub](https://github.com/modelcontextprotocol)
- [MCP Servers](https://github.com/modelcontextprotocol/servers)
- [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers)

### 作业

1. 运行 Filesystem MCP Server，限制允许访问的根目录。
2. 连接 GitHub MCP，查询仓库、代码、Issue、Pull Request 和文件。
3. 开发 Data Platform MCP Server，提供表搜索、Schema、血缘、DAG 和运行状态工具。
4. 增加允许名单、参数校验、只读模式、超时、审计日志和环境变量凭据管理。

### 交付物

- `week11-mcp/mcp_server.py`
- `week11-mcp/mcp_client.py`
- `week11-mcp/tools/`
- `week11-mcp/resources/`
- `week11-mcp/security-design.md`

### 验收标准

- [ ] 能解释 Tool 与 Resource 的区别
- [ ] 成功运行至少一个现有 MCP Server
- [ ] 完成一个自定义 MCP Server
- [ ] 实现访问范围限制
- [ ] 敏感凭据未提交到 GitHub

---

## Week 12：毕业项目 Data Engineer Copilot

### 项目目标

整合前 11 周成果，构建一个面向数据工程场景的 AI Copilot。

### 推荐架构

```text
Web UI
  ↓
FastAPI
  ↓
LangGraph Agent
  ├── RAG Retriever
  ├── SQL Generator
  ├── PySpark Generator
  ├── Airflow DAG Generator
  ├── Code Reviewer
  └── MCP Client
        ├── Filesystem MCP
        ├── GitHub MCP
        └── Data Platform MCP
  ↓
Cloud LLM or Local Model
  ↓
Qdrant
```

### 功能要求

#### 企业知识库 RAG

- 文档上传、更新和删除
- 增量索引
- Metadata Filter
- Hybrid Search
- Reranking
- 来源引用
- 无答案拒绝

#### SQL Copilot

- 自然语言生成 SQL
- 读取表结构
- 支持 SQL 方言
- SQL 格式化、风险检查和优化建议
- 禁止直接执行写操作 SQL

#### PySpark Copilot

- 生成 DataFrame API 代码
- 检查大表 Join、Collect、分区和缓存问题
- 输出必要注释与测试建议

#### Airflow Copilot

- 生成 DAG、Schedule、Retry、Timeout 和 Failure Callback
- 输出依赖关系
- 检查 Catchup 与并发配置
- 生成基础测试

#### Agent Workflow

```text
Requirement Analyzer
  ↓
Intent Router
  ├── RAG Search
  ├── SQL Generator
  ├── PySpark Generator
  ├── Airflow Generator
  └── MCP Tool
  ↓
Code Reviewer
  ↓
Security Checker
  ↓
Human Approval
  ↓
Final Response
```

#### 可观测性

记录 Request ID、Query、Agent Route、Tool Calls、Retrieval Results、Token、模型延迟、工具延迟、错误与最终状态。

### 推荐技术栈

| 模块 | 推荐技术 |
|---|---|
| 前端 | Streamlit 或 Next.js |
| API | FastAPI |
| Agent | LangGraph |
| RAG | LangChain 或 LlamaIndex |
| 向量数据库 | Qdrant |
| 云端模型 | OpenAI 或 Azure OpenAI |
| 本地模型 | Ollama 或 vLLM |
| MCP | Model Context Protocol SDK |
| 数据库 | PostgreSQL 或 SQLite |
| 容器化 | Docker Compose |
| 测试 | pytest |
| 代码质量 | Ruff、Black、MyPy |
| CI/CD | GitHub Actions |

### 建议仓库结构

```text
data-engineer-copilot/
├── README.md
├── LICENSE
├── .env.example
├── .gitignore
├── docker-compose.yml
├── pyproject.toml
├── docs/
├── app/
│   ├── api/
│   ├── agent/
│   ├── rag/
│   ├── tools/
│   ├── mcp/
│   ├── models/
│   ├── prompts/
│   └── ui/
├── ingestion/
├── evaluation/
├── tests/
└── scripts/
```

### 最终验收标准

- [ ] 可以通过 Docker Compose 启动
- [ ] RAG 回答包含引用且无资料时拒绝编造
- [ ] Agent 能正确路由并处理工具失败
- [ ] 高风险操作需要人工批准
- [ ] SQL 与文件工具默认只读或限制范围
- [ ] 配置通过环境变量管理
- [ ] 包含测试、日志、架构图和部署说明

---

## 学习优先级

| 方向 | 建议占比 | 优先级 |
|---|---:|---|
| 企业级 RAG | 35% | 最高 |
| Agent 与 LangGraph | 25% | 最高 |
| MCP 与工具集成 | 15% | 高 |
| 模型部署 | 10% | 中高 |
| Prompt Engineering | 5% | 中 |
| Transformer 原理 | 5% | 中 |
| LoRA 微调 | 5% | 中低 |

建议主技术栈固定为：

```text
Python + FastAPI + LangChain + LangGraph + Qdrant + Ollama/OpenAI + MCP + Docker Compose
```

## 每周复盘模板

```markdown
## Week X 学习复盘

### 本周目标

- 

### 已完成课程

- [ ] 
- [ ] 

### 已完成作业

- [ ] 
- [ ] 

### 核心知识点

1. 
2. 
3. 

### 遇到的问题与解决方案

1. 
2. 

### 本周交付物

- GitHub：
- Demo：
- 文档：

### 自我评分

- 理论理解：/10
- 动手实践：/10
- 独立排错：/10
- 工程质量：/10
- 文档质量：/10

### 下周改进项

- 
```

## 官方资源收藏

| 类别 | 资源 |
|---|---|
| 生成式 AI | [Microsoft Generative AI for Beginners](https://microsoft.github.io/generative-ai-for-beginners/) |
| AI Agent | [Microsoft AI Agents for Beginners](https://microsoft.github.io/ai-agents-for-beginners/) |
| LLM 路线 | [LLM Course](https://github.com/mlabonne/llm-course) |
| LLM 原理 | [LLMs from Scratch](https://github.com/rasbt/LLMs-from-scratch) |
| RAG 课程 | [LLM Zoomcamp](https://github.com/DataTalksClub/llm-zoomcamp) |
| LangChain | [LangChain Documentation](https://docs.langchain.com/) |
| LangGraph | [LangGraph Documentation](https://docs.langchain.com/oss/python/langgraph/overview) |
| LlamaIndex | [LlamaIndex Documentation](https://docs.llamaindex.ai/) |
| 向量数据库 | [Qdrant Documentation](https://qdrant.tech/documentation/) |
| 微调 | [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory) |
| PEFT | [Hugging Face PEFT](https://huggingface.co/docs/peft/index) |
| 本地模型 | [Ollama](https://github.com/ollama/ollama) |
| 模型服务 | [vLLM](https://docs.vllm.ai/) |
| RAG 评估 | [Ragas](https://docs.ragas.io/) |
| AutoGen | [AutoGen](https://microsoft.github.io/autogen/) |
| CrewAI | [CrewAI](https://docs.crewai.com/) |
| MCP | [Model Context Protocol](https://modelcontextprotocol.io/) |
| MCP Servers | [Official MCP Servers](https://github.com/modelcontextprotocol/servers) |

## 职业能力路径

```text
Senior Data Engineer
        ↓
AI Application Engineer
        ↓
RAG Engineer
        ↓
AI Agent Engineer
        ↓
Data Platform AI Engineer
```

优先落地场景：

1. Data Platform Knowledge Copilot
2. Airflow Operations Assistant
3. Databricks Documentation Assistant
4. SQL Generation and Review Agent
5. PySpark Code Review Agent
6. Data Quality Troubleshooting Agent
7. Metadata and Data Lineage Agent
8. Runbook Automation Agent
9. GitHub Code Search Agent
10. MCP-Based Data Platform Assistant
