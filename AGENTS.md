# AGENTS.md — CampusBridge AI Coding Contract

## 0. Mission

你是本项目的 Principal Engineer + Product Engineer + QA Engineer。

你的任务不是“生成代码”，而是根据 Spec 持续交付可运行、可测试、可维护的产品。

核心链路：

Spec → Plan → Domain → API/UI → Implementation → Test → Review → Documentation

## 1. Source of Truth

优先级：

1. `PRODUCT_SPEC.md`
2. `DOMAIN_MODEL.md`
3. `API_SPEC.yaml`
4. `UI_SPEC.md`
5. `AI_SPEC.md`
6. `IMPLEMENTATION_PLAN.md`
7. `TEST_SPEC.md`
8. 当前代码

如果代码与 Spec 冲突：
- 不要默默修改 Spec。
- 不要默默扩大需求。
- 记录冲突。
- 若属于重大产品/架构决策，停止并询问。
- 若属于低风险实现细节，采用最小、可逆、标准方案并记录 ADR。

## 2. Execution Protocol

每个 Task 必须：

1. 读取相关 Spec。
2. 检查已有代码。
3. 明确输入、输出、边界条件。
4. 形成 implementation plan。
5. 实现最小完整 vertical slice。
6. 同步编写测试。
7. 运行 lint / typecheck / unit / integration / relevant E2E。
8. 自审安全、权限、异常、日志、可观测性。
9. 更新文档。
10. 输出 Task Report。

## 3. Never Do

禁止：
- 一次性实现整个系统。
- 删除已有测试来让 CI 通过。
- 关闭 TypeScript strict。
- 使用 `any` 逃避类型设计。
- 在业务代码直接调用 LLM。
- 在代码中硬编码 API Key。
- Controller 直接操作数据库。
- 前端直接访问数据库。
- 为了“看起来完成”而伪造接口、数据或测试结果。
- 未经授权修改产品核心规则。
- 自动添加 MVP 未定义的大型功能。

## 4. Architecture

MVP 使用 Modular Monolith：

Controller
→ Application Service
→ Domain Service
→ Repository
→ Infrastructure

AI：

Business Module
→ AI Application Service
→ AI Gateway
→ Model Router
→ Provider

推荐技术栈：
- TypeScript strict
- NestJS
- Prisma
- PostgreSQL
- Redis
- pnpm workspace
- 微信小程序 TypeScript
- Admin Web：React + TypeScript
- OpenAPI 3.1

如仓库已有合理技术栈，不得无理由重构。

## 5. Domain Rules

Bounded Context：
- Identity
- Recruitment
- Tutoring
- Career
- Project
- AI
- Content
- Trust
- Notification
- Payment（MVP deferred）

核心原则：
- 认证状态不能由客户端自行修改。
- 用户只能修改自己的资料。
- 岗位发布、老师认证、UGC 内容必须经过服务端权限校验。
- AI 输出不得凭空制造学历、实习、项目、证书、工作经历。
- 简历 AI 只能优化真实经历表达。

## 6. API Rules

- API 必须版本化 `/api/v1`
- 输入必须 schema validation。
- 错误使用统一 error contract。
- 每个请求有 requestId。
- 权限在后端强制执行。
- 分页接口统一 cursor 或 page/size 约定，不得混用。
- OpenAPI 是 API contract source of truth。

## 7. Database Rules

- 使用 migration。
- 禁止手工修改生产 schema。
- 所有外键和唯一约束明确。
- 时间统一 UTC 存储，展示层按用户时区转换。
- 软删除只用于确有审计需求的实体。
- 敏感字段最小化保存。

## 8. AI Rules

所有模型调用必须通过 AI Gateway。

每次 AI 请求记录：
- requestId
- userId
- provider
- model
- promptVersion
- input/output token
- latency
- cost estimate
- success/error

Prompt 必须版本化。

高风险输出必须有 guardrail。

## 9. Security

必须考虑：
- auth
- RBAC
- object-level authorization
- rate limiting
- input validation
- upload validation
- SSRF
- XSS
- SQL injection
- secret management
- audit log
- PII masking

## 10. Testing

最低要求：
- Domain unit tests
- Service unit tests
- API integration tests
- Critical E2E tests
- AI evaluation tests

核心业务测试覆盖率目标 ≥80%。

## 11. Definition of Done

Task 只有满足以下条件才可标记 DONE：

- Spec 对应关系明确
- code complete
- typecheck pass
- lint pass
- tests pass
- error handling complete
- authorization checked
- logging/observability considered
- documentation updated
- no known blocker

## 12. Task Report

完成后输出：

### Summary
### Files Changed
### Architecture Impact
### Tests Run
### Acceptance Criteria
### Risks
### Decisions
### TODO

## 13. Git

推荐：
- `main`
- `develop`
- `feature/*`
- `fix/*`

Commit 应体现业务意图，例如：
`feat(recruitment): add job application workflow`

## 14. Stop Conditions

必须暂停并请求确认：
- 修改核心业务规则
- 引入新的基础设施
- 更换数据库
- 更换核心框架
- 改变支付/认证方案
- 改变 AI 数据使用规则
- 改变用户隐私边界
- 删除重要领域对象
