# CampusBridge AI-SSD Specification

本仓库是一套可直接交给 Codex / Claude Code / CodeBuddy 使用的 Spec-Driven Development（AI-SSD）工程规范。

## 文档
- `AGENTS.md`：AI Coding Agent 总规则
- `PRODUCT_SPEC.md`：产品规格
- `DOMAIN_MODEL.md`：领域模型与数据模型
- `API_SPEC.yaml`：OpenAPI 3.1 API Contract
- `UI_SPEC.md`：微信小程序 UI / 页面规格
- `AI_SPEC.md`：AI Gateway / Agent / RAG / Evaluation 规格
- `IMPLEMENTATION_PLAN.md`：Epic → Feature → Task 执行计划
- `TEST_SPEC.md`：测试与验收规格
- `DECISIONS.md`：架构决策记录

## 推荐执行方式

1. 将整个目录放到代码仓库根目录。
2. 将 `AGENTS.md` 作为 Codex / Claude Code / CodeBuddy 的最高级项目规则。
3. 首次只执行 `TASK-001`。
4. 每个 Task 都必须先读取相关 Spec，再实现，再测试。
5. AI 不得一次性生成整个项目。
6. 当 Spec 与代码冲突时，优先保护 Spec；重大冲突必须暂停并请求确认。
