# DECISIONS.md

## ADR-001 Modular Monolith

Decision:
MVP 使用 Modular Monolith。

Reason:
团队规模和产品阶段不需要微服务复杂度。

## ADR-002 AI Gateway

Decision:
所有模型调用统一经过 AI Gateway。

Reason:
模型可替换、成本可控、统一日志和安全策略。

## ADR-003 WeChat Mini Program

Decision:
核心交易/服务体验优先小程序。

Reason:
微信生态降低用户进入门槛。

## ADR-004 Official Account

Decision:
公众号负责内容和获客，不承载核心领域逻辑。

## ADR-005 Matching

Decision:
MVP 使用 rule-based + keyword + embedding，不做复杂 ML 推荐。

## ADR-006 Autonomous Agent

Decision:
MVP 使用确定性 workflow，暂不使用开放式 autonomous agent。

Reason:
可控、可测试、成本低。

## ADR-007 Payments

Decision:
MVP 延后支付。

Reason:
先验证撮合和 AI 服务需求。

## ADR-008 Sensitive Data

Decision:
个人敏感信息最小化采集和存储。
