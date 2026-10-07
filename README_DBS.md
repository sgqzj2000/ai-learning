# Databricks Certified Data Engineer Professional 备考指南

> 面向已在 Databricks 上做过生产级数据管道、并希望系统备考 **Data Engineer Professional** 的学习者。  
> **权威来源：** [官方认证页](https://www.databricks.com/learn/certification/data-engineer-professional) · [Exam Guide PDF (Oct 2026)](https://www.databricks.com/sites/default/files/2026-09/databricks-certified-data-engineer-professional-exam-guide-oct-2026.pdf)

## 目录

- [考试概览](#考试概览)
- [考纲版本（重要）](#考纲版本重要)
- [官方推荐学习路径](#官方推荐学习路径)
- [GitHub 备考资源](#github-备考资源)
- [10 域大纲与权重](#10-域大纲与权重)
- [建议复习顺序](#建议复习顺序)
- [高频考点速查](#高频考点速查)
- [与本仓库 12 周路线的衔接](#与本仓库-12-周路线的衔接)

---

## 考试概览

| 项目 | 说明 |
|------|------|
| **认证名称** | Databricks Certified Data Engineer Professional |
| **费用** | 约 **$200 USD**（以官网为准） |
| **时长** | **120 分钟** |
| **题型** | 选择题（可能含未计分题，不影响通过/不通过结果） |
| **语言** | English；Japanese；Portuguese (BR)；Korean |
| **代码语言** | 题干中可能出现 **Python** 与 **SQL** |
| **经验建议** | **1 年+** 在 Databricks 上构建生产数据管道（强烈推荐） |
| **有效期** | **2 年**，到期需按当时 live 版本重考 |
| **交付方式** | 在线监考或测试中心 |
| **结果** | Pass / Fail（以当期 Exam Guide 为准） |

**能力定位（摘要）：** 在 Databricks 上设计、优化并运维生产级数据工程方案——Delta Lake、Unity Catalog、Auto Loader、Lakeflow Declarative Pipelines、Lakeflow Jobs、Medallion、流式与批处理、安全与治理、性能与成本、CI/CD 与 Asset Bundles 等。

---

## 考纲版本（重要）

官方 **Oct 2026** 考纲同时描述两版考试，**按你预约的考试日期**选择复习内容：

| 考试日期 | 计分题数 | 复习材料 |
|----------|----------|----------|
| **2026-10-08 及之前** | 59 道计分题 | Exam Guide 中的 **Current Exam** 大纲 |
| **2026-10-09 及之后** | 60 道计分题 | Exam Guide 中的 **New Exam** 大纲 |

- 考前约 **2 周** 再次打开官网考纲 PDF，确认未发生微调。  
- 社区 GitHub 资料多对齐 **2025-11-30** 十域结构；若与 New Exam 有差异，以 **官方 PDF + Databricks 文档** 为准。

---

## 官方推荐学习路径

以下在 Exam Guide 中列为推荐准备（主要在 **Databricks Academy**，非单一 GitHub 仓库）：

| 类型 | 课程 / 资源 |
|------|-------------|
| 讲师带课 | Advanced Data Engineering with Databricks |
| 自学 | Advanced Techniques with Apache Spark™ Declarative Pipeline |
| 自学 | Databricks Data Privacy |
| 自学 | Databricks Performance Optimization |
| 自学 | Automated Deployment with Declarative Automation Bundles |
| 文档 | [Databricks Documentation](https://docs.databricks.com/)（备考时以文档为准，避免过时 API） |
| AI 辅助 | 考纲中的 **AI Prep Guide**（用官方考纲约束对话，并配合动手练习） |

**说明：** Databricks **没有**一个公开 GitHub 仓库包含上述四门自学课的完整 lab 镜像；动手部分需结合 Academy、Free Edition workspace 与下方官方示例仓库。

---

## GitHub 备考资源

### 主推荐：结构化自学与刷题

**[kengio/databricks-certification-study-guide](https://github.com/kengio/databricks-certification-study-guide)**

| 资源 | 路径 / 说明 |
|------|-------------|
| Professional 总览 | [certifications/data-engineer-professional/README.md](https://github.com/kengio/databricks-certification-study-guide/blob/main/certifications/data-engineer-professional/README.md) |
| 10 域 topic 文件夹 | 与官方十域 1:1，每域 `README.md` 为精读入口 |
| 分域练习题（73 题） | `certifications/data-engineer-professional/resources/practice-questions/` |
| 模拟卷 ×2 | `resources/mock-exam-1/`、`mock-exam-2/`（见 [practice/README.md](https://github.com/kengio/databricks-certification-study-guide/blob/main/practice/README.md)） |
| 可运行 Lab | [labs/README.md](https://github.com/kengio/databricks-certification-study-guide/blob/main/labs/README.md) |
| 续证 / 术语变更 | [shared/appendix/renewal-guide.md](https://github.com/kengio/databricks-certification-study-guide/blob/main/shared/appendix/renewal-guide.md) |

**Lab 与 Professional 强相关：**

| Lab | 内容 | 对应能力 |
|:---:|------|----------|
| 01 | Medallion ingestion | Bronze/Silver/Gold、Delta、MERGE、OPTIMIZE |
| 02 | Unity Catalog setup | Catalog/Schema/Volume、GRANT、行过滤、列掩码 |
| 03 | Lakeflow Declarative Pipelines | `@dlt.table`、expectations、`APPLY CHANGES INTO`、event log |

社区仓库内常见 **8 周**复习节奏：前 4 周按域精读 topic → 第 5–6 周 cheat sheet + 分域刷题 → 第 7 周薄弱域 → 第 8 周限时 mock。

### Databricks 官方公开示例（动手补充）

| 主题 | 仓库 | 用途 |
|------|------|------|
| LDP / 流式管道示例 | [databricks/delta-live-tables-notebooks](https://github.com/databricks/delta-live-tables-notebooks) | Declarative Pipelines、流式场景 |
| Asset Bundles / 部署 | [databricks/bundle-examples](https://github.com/databricks/bundle-examples) | CI/CD、多环境部署 |
| Delta 生态 | [delta-io/delta](https://github.com/delta-io/delta) | Delta 语义与参考实现 |

社区讨论参考：[GitHub repo for 4 modules in DE Professional](https://community.databricks.com/t5/certifications/github-repo-for-4-modules-in-the-data-engineering-professional/td-p/118783)（性能优化、数据隐私等更依赖 Academy + 文档）。

### 刷题补充（需自行核对考纲）

**[Amrit-Hub/Databricks-Certified-Data-Engineer-Professional-Questions](https://github.com/Amrit-Hub/Databricks-Certified-Data-Engineer-Professional-Questions)**

- 考点回忆与外链（CDF、DLT、UC 权限、OPTIMIZE、流式失败、widgets 等）。  
- **仅作查漏**；错题务必回到官方文档与 kengio 对应域核对。

---

## 10 域大纲与权重

以下权重来自社区指南对齐的 **2025-11-30** Professional 蓝图；若 New Exam（2026-10-09+）域权有变，以 PDF 为准。

| # | 域 | 权重 | 重点（摘要） |
|---:|---|:---:|---|
| 01 | Developing Code for Data Processing | 22% | 批/流代码、Delta、LDP、Lakeflow Jobs、测试 |
| 02 | Cost & Performance Optimization | 13% | 文件大小、Z-ORDER / liquid clustering、Spark 调优、Photon、算力选型 |
| 03 | Data Transformation, Cleansing, and Quality | 10% | SQL/PySpark 变换、隔离坏数据、质量规则 |
| 04 | Monitoring and Alerting | 10% | 作业监控、告警、可观测 |
| 05 | Ensuring Data Security and Compliance | 10% | 密钥、网络、合规、脱敏 |
| 06 | Debugging and Deploying | 10% | Asset Bundles、CI/CD、Git folders、单测、Spark UI、CLI、REST API |
| 07 | Data Ingestion & Acquisition | 7% | Auto Loader、多格式摄取 |
| 08 | Data Governance | 7% | Unity Catalog、UC Volumes vs DBFS |
| 09 | Data Modelling | 6% | Medallion、Delta 基础、Schema、SCD |
| 10 | Data Sharing and Federation | 5% | Delta Sharing、Lakehouse Federation |

### 产品术语对照（续考 / 旧资料常见）

| 旧称 | 现行名称 |
|------|----------|
| Delta Live Tables (DLT) | **Lakeflow Declarative Pipelines** |
| Databricks Workflows | **Lakeflow Jobs** |
| Databricks Asset Bundles (DAB) | **Declarative Automation Bundles**（考纲表述以 PDF 为准） |

---

## 建议复习顺序

```text
1. 确认考试日期 → 选定 Current / New Exam 大纲（PDF）
2. kengio：按域 01→10 阅读 README + 完成该域 practice questions
3. labs：01 Medallion → 02 Unity Catalog → 03 LDP（Professional 核心）
4. 官方 repo：bundle-examples + delta-live-tables-notebooks
5. 限时完成 mock exam 1、2（120 min）→ 错题映射回域文件夹
6. 有权限时完成 Academy 四门自学课 + 通读相关官方文档章节
7. 考前 2 周：复查官网考纲 + 术语表（Lakeflow / UC / Bundles）
```

**通过线策略（社区实践，非官方承诺）：** 分域练习稳定 **70%+** 后再做整套 mock；mock 全程计时，模拟无资料查阅（正式考试不允许辅助材料）。

---

## 高频考点速查

备考时建议能**解释场景选型**，而非只背 API 名称：

- **Lakeflow Declarative Pipelines**：streaming table vs materialized view、`APPLY CHANGES` / AUTO CDC、expectations、quarantine 坏数据  
- **摄取**：Auto Loader、多格式（Delta/Parquet/JSON/CSV 等）、append-only 批流统一  
- **Delta Lake**：MERGE、CDF、OPTIMIZE、liquid clustering / Z-ORDER、约束与分区策略  
- **Lakeflow Jobs**：任务类型、重试、依赖、参数（widgets / job parameters）、失败排查  
- **Unity Catalog**：权限模型、Volumes、行/列级安全、血缘与治理  
- **部署**：Asset Bundles、Git 集成、环境分离、CI/CD 基本流程  
- **流式**：Structured Streaming vs LDP 选型、checkpoint、流式作业失败处理  
- **共享**：Delta Sharing（D2D / D2O）、Lakehouse Federation  
- **成本与性能**：文件大小、shuffle、缓存误用、集群/Serverless 选型  

---

## 与本仓库 12 周路线的衔接

主路线见 [README.md](./README.md)。与 **DE Professional** 重叠度较高的周次：

| 本仓库周次 | 考证可复用点 |
|------------|--------------|
| Week 4–4 | Qdrant 为本仓库主栈；考证侧对应 **Delta + 向量/检索在 Databricks 上** 以 Vector Search 文档为准 |
| Week 6 | AI Data Pipeline ↔ **摄取、CDC、质量、幂等、对账**（域 01、03、07） |
| Week 7 | Model Serving / Databricks AI ↔ **托管推理、UC、MLflow**（与域 05、08 部分重叠） |
| Week 8 | 企业 RAG + 评估 ↔ **监控、质量门禁**（域 04、03） |
| Week 11 | MCP + **AI 数据治理** ↔ **UC、权限、生命周期、审计**（域 08、05） |

**并行建议：** 工作日跟 [README.md](./README.md) 做 AI 平台作品；周末用 **kengio 一个域 + 一个 lab** 推进考证，避免两套完全独立的假项目。

---

## 维护说明

| 字段 | 值 |
|------|-----|
| 整理日期 | 2026-10 |
| 主要参考考纲 | Databricks Exam Guide Oct 2026 PDF |
| 社区指南版本 | kengio 对齐 2025-11-30 Professional 蓝图 |

发现考纲或仓库链接变更时：更新本文件「考纲版本」与「10 域权重」表，并在 [README.md](./README.md) 对标维护表中追加一行（若纳入主路线）。
