# AI产品技术学习资料索引

## 说明

这份索引只收录 **一手或官方资料**，优先用于支撑知识库里的技术判断。

文档分成两层：

1. 能直接拿来学和上手的官方文档
2. 能帮助你纠偏的关键判断

对于用户研究、沟通、PRD、B 端经验这类能力，本仓库更适合沉淀你自己的方法论与案例，而不是机械罗列外部链接。

## 一、Prompt 与模型使用

### 1. OpenAI Prompt Engineering

- 链接：https://platform.openai.com/docs/guides/prompt-engineering
- 用途：建立提示词的基本写法与常见优化思路
- 为什么重要：Prompt 仍然是最低成本的效果优化手段

### 2. OpenAI Reasoning Best Practices

- 链接：https://developers.openai.com/api/docs/guides/reasoning-best-practices
- 用途：理解 reasoning 模型与普通 GPT 模型在提示方式上的差异
- 关键结论：
  - reasoning 模型适合复杂、多步、模糊问题
  - GPT 模型更适合明确、低成本、高速度执行
  - 不要机械套用“think step by step”
  - 应先 zero-shot，再决定是否补 few-shot

### 3. OpenAI Model Optimization

- 链接：https://developers.openai.com/api/docs/guides/model-optimization
- 用途：理解 Prompt、eval、fine-tuning 的关系
- 关键结论：
  - 先建立评测，再优化 Prompt
  - Prompt 可能已经足够解决问题
  - Fine-tuning 适合格式稳定、场景稳定、规模足够大的任务

## 二、Agent 与工作流平台

### 1. Coze Agent

- 链接：https://docs.coze.cn/develop/agent
- 用途：学习扣子里 Bot / Agent 的构建方式
- 适合阶段：入门无代码 Agent

### 2. Coze Workflow

- 链接：https://docs.coze.cn/develop/workflow
- 用途：学习扣子工作流的节点编排思路
- 适合阶段：从单 Bot 进入结构化流程

### 3. Dify Workflow & Chatflow

- 链接：https://docs.dify.ai/en/use-dify/build/workflow-chatflow
- 用途：理解 Workflow 与 Chatflow 的区别
- 关键结论：
  - Workflow 适合一次性、结构化任务
  - Chatflow 适合对话式交互，但底层仍然是流程

### 4. Dify Agent

- 链接：https://docs.dify.ai/en/use-dify/build/agent
- 用途：理解 Agent 如何自主选择工具、管理记忆、控制迭代次数
- 关键结论：
  - Prompt 不只是说明任务，还决定工具使用方式
  - 最大迭代次数、知识库、工具权限都属于产品设计的一部分

### 5. Langflow Overview

- 链接：https://docs.langflow.org/
- 用途：理解 Langflow 作为低代码 AI 流程构建器的定位
- 关键结论：
  - Langflow 重点是可视化创建、测试、运行和服务化 flow
  - 它更适合原型和流程实验，不只是“拖拖拽拽”

### 6. Langflow Agents

- 链接：https://docs.langflow.org/agents
- 用途：理解 Agent 在 flow 中如何通过工具完成任务
- 关键结论：
  - Agent 的本质是 LLM + Tool 注册 + 执行动作
  - 是否真的要用 Agent，应取决于任务复杂度，而不是“听起来更高级”

### 7. OpenAI Agent Builder

- 链接：https://developers.openai.com/api/docs/guides/agent-builder
- 用途：从更平台化的视角理解 agent workflow
- 关键结论：
  - workflow = agent + tools + control flow
  - 构建流程时需要同时考虑预览、部署、安全和评测

## 三、API 调用与模型接入

### 1. OpenAI GPT-4.1 模型页

- 链接：https://developers.openai.com/api/docs/models/gpt-4.1
- 用途：理解当前模型能力面板、支持的接口和工具
- 关键结论：
  - 当前主流能力围绕 Responses API、function calling、structured outputs、tools 展开

### 2. OpenAI Embeddings

- 链接：https://developers.openai.com/api/docs/models/text-embedding-3-large
- 用途：理解 embedding 的实际用途
- 关键结论：
  - embedding 主要用于检索、聚类、推荐、分类、相关性判断

### 3. Kimi API 主要概念

- 链接：https://platform.moonshot.cn/docs/intro
- 用途：了解 Kimi API 的模型谱系、速率限制和调用方式
- 关键结论：
  - 当前文档明确给出了模型列表与上下文规格
  - 速率限制和成本是产品设计时必须考虑的约束

### 4. Kimi K2.5 快速开始

- 链接：https://platform.moonshot.cn/docs/guide/kimi-k2-5-quickstart
- 用途：上手 Kimi 当前主力模型的调用
- 关键结论：
  - Kimi API 兼容 OpenAI SDK 形式
  - k2.5 支持多模态、思考/非思考模式和 Agent 任务

### 5. 阿里云百炼 completions 接口

- 链接：https://help.aliyun.com/zh/model-studio/completions
- 用途：理解通义千问在代码补全和文本补全场景下的 API 调用方式
- 关键结论：
  - 需要把 OpenAI 兼容调用和百炼原生接口区分开

### 6. 阿里云百炼向量化

- 链接：https://help.aliyun.com/zh/dashscope/developer-reference/text-embedding-quick-start
- 用途：理解通义侧 embedding 的规格、维度、成本与语言支持
- 关键结论：
  - embedding 不是抽象概念，而是会直接影响检索质量和成本的工程参数

## 四、评测、优化与迭代

### 1. OpenAI Model Optimization

- 链接：https://developers.openai.com/api/docs/guides/model-optimization
- 用途：把“Prompt / Fine-tuning / Evals”放进一个统一优化循环
- 适用问题：
  - 什么时候继续改 Prompt
  - 什么时候需要引入 eval
  - 什么时候才值得做 fine-tuning

### 2. Dify Run History

- 链接：https://docs.dify.ai/en/use-dify/debug/history-and-logs
- 用途：理解工作流日志、Tracing 和节点级历史
- 对产品经理的意义：
  - Badcase 机制不能只靠主观记录，必须能回到执行链路看输入、输出和节点耗时

## 五、你现在最值得先看的资料顺序

如果你现在时间有限，建议按这个顺序读：

1. OpenAI Prompt Engineering
2. OpenAI Reasoning Best Practices
3. Coze Agent
4. Coze Workflow
5. Dify Workflow & Chatflow
6. Dify Agent
7. Langflow Overview
8. Kimi K2.5 快速开始
9. 阿里云百炼 completions / embedding
10. OpenAI Model Optimization

## 六、从资料到作品的最小闭环

不要只停留在“看文档”，至少把文档转成这 4 类产物：

1. 一张 Prompt 模板卡
2. 一个 Coze 或 Dify 工作流 demo
3. 一个 API 调用 demo
4. 一份 Badcase 与评测表

只有这样，这些资料才会从“知道”变成“可展示的能力”。
