# AI_SPEC.md

## 1. Architecture

Business
→ AI Application Service
→ AI Gateway
→ Model Router
→ Provider

## 2. AI Gateway

统一接口：

```ts
chat(request): Promise<ChatResponse>
embedding(request): Promise<EmbeddingResponse>
```

请求必须包含：
- requestId
- userId
- useCase
- promptVersion
- modelPolicy

## 3. AI Use Cases

- career.analyze
- career.plan
- resume.parse
- resume.analyze
- resume.optimize
- interview.generate
- interview.evaluate
- matching.explain
- content.generate

## 4. Model Routing

初始策略：
- 高质量推理任务：高能力模型
- 分类/抽取：低成本模型
- Embedding：专用 embedding model

模型名称通过环境配置，不写死在业务代码。

## 5. Prompt Versioning

目录：

prompts/
career/
resume/
interview/
matching/
content/

每个 Prompt：
- version
- input schema
- output schema
- system instruction
- evaluation dataset

## 6. Structured Output

AI 服务优先使用 JSON Schema structured output。

禁止业务层依赖自由文本正则解析关键字段。

## 7. Resume Guardrail

AI 可以：
- 改写表达
- 量化已有事实
- 重组结构
- 提取技能

AI 不可以：
- 编造公司
- 编造项目
- 编造学历
- 编造证书
- 编造业绩

## 8. Career Plan

输入：
- profile
- targetRole
- targetIndustry
- targetCity

输出：
- profileSummary
- recommendedDirections
- skillGaps
- roadmap
- projectSuggestions
- resumeSuggestions

## 9. Interview

状态机：

created
→ question_ready
→ answering
→ evaluating
→ follow_up
→ completed

AI 必须基于目标岗位和用户简历生成问题。

## 10. RAG

知识库：
- career
- skills
- interview
- resume
- projects

流程：
ingest → chunk → embedding → retrieve → rerank → generate

## 11. AI Safety

- PII 最小化发送给模型
- 对上传文档进行恶意内容检测
- 防止 prompt injection
- 不执行文档中的工具调用指令
- 工具调用采用 allowlist
- 高成本请求限流

## 12. AI Evaluation

每个重要 AI use case 至少建立：
- 100 个离线测试样本
- golden output / rubric
- factuality
- relevance
- completeness
- safety
- latency
- cost

## 13. Observability

ai_requests：
- id
- requestId
- userId
- useCase
- provider
- model
- promptVersion
- inputTokens
- outputTokens
- latencyMs
- cost
- status
- errorCode

## 14. Agent

MVP 先实现 workflow，不实现开放式 autonomous agent。

后续 Agent：
- Career Agent
- Resume Agent
- Interview Agent
- Project Mentor Agent

所有 Agent Tool 必须 allowlist。
