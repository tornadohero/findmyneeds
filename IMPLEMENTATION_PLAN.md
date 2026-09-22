# IMPLEMENTATION_PLAN.md

## Execution Rule

严格按顺序执行。每个 Task 独立、可测试、可回滚。

---

## EPIC-00 Foundation

### TASK-001 Repository bootstrap
- 初始化 pnpm workspace
- TypeScript
- lint
- format
- commit hooks
- README
Acceptance:
- install/build/lint/typecheck pass

### TASK-002 Backend skeleton
- NestJS
- health endpoint
- config module
- error handling
Acceptance:
GET /health = 200

### TASK-003 Database
- PostgreSQL
- Prisma
- initial migration
- User model
Acceptance:
migration and seed pass

### TASK-004 Redis
- Redis module
- health check
Acceptance:
connection test pass

### TASK-005 CI
- lint
- typecheck
- test
- build

---

## EPIC-01 Identity

### TASK-010 WeChat auth abstraction
不要先绑定具体生产凭证。
建立 WeChatAuthProvider interface + mock provider。

### TASK-011 Auth session
JWT/refresh/session implementation.

### TASK-012 User profile

### TASK-013 RBAC

### TASK-014 Audit log

---

## EPIC-02 Recruitment

### TASK-020 Job domain

### TASK-021 Job repository

### TASK-022 Job CRUD API

### TASK-023 Job list/search/filter

### TASK-024 Job detail

### TASK-025 Job application

### TASK-026 Favorite

### TASK-027 Job moderation

---

## EPIC-03 Tutoring

### TASK-030 Teacher profile

### TASK-031 Teacher verification

### TASK-032 Tutor requirement

### TASK-033 Tutor search/filter

### TASK-034 Tutor application

### TASK-035 Matching v1

### TASK-036 Review/report

---

## EPIC-04 AI Foundation

### TASK-040 AI Gateway interface

### TASK-041 Provider adapter

### TASK-042 Model router

### TASK-043 Prompt registry

### TASK-044 AI usage logging

### TASK-045 AI rate limit

### TASK-046 Structured output validation

---

## EPIC-05 Career

### TASK-050 Career profile

### TASK-051 Career analysis

### TASK-052 Career plan

### TASK-053 Career roadmap UI

---

## EPIC-06 Resume

### TASK-060 File upload

### TASK-061 Document extraction

### TASK-062 Resume parser

### TASK-063 Resume analysis

### TASK-064 Resume optimization

### TASK-065 Resume versioning

### TASK-066 Resume export

---

## EPIC-07 Interview

### TASK-070 Interview session

### TASK-071 Question generation

### TASK-072 Answer evaluation

### TASK-073 Follow-up question

### TASK-074 Interview report

---

## EPIC-08 Project

### TASK-080 Project model

### TASK-081 Project list/detail

### TASK-082 Enrollment

### TASK-083 Submission

### TASK-084 AI project mentor

---

## EPIC-09 Mini Program

### TASK-090 Mini program shell

### TASK-091 Home

### TASK-092 Jobs UI

### TASK-093 Tutors UI

### TASK-094 Career UI

### TASK-095 Profile UI

### TASK-096 Error/loading/empty states

---

## EPIC-10 Admin

### TASK-100 Admin shell

### TASK-101 User management

### TASK-102 Job moderation

### TASK-103 Tutor verification

### TASK-104 Report handling

### TASK-105 AI usage dashboard

---

## EPIC-11 Testing

### TASK-110 Domain tests

### TASK-111 API integration tests

### TASK-112 Critical E2E

### TASK-113 AI evaluation harness

### TASK-114 Security tests

---

## EPIC-12 Deployment

### TASK-120 Docker

### TASK-121 staging

### TASK-122 production configuration

### TASK-123 monitoring

### TASK-124 backup

---

## MVP Exit Criteria

必须通过：
1. Student job application E2E
2. Parent tutor requirement E2E
3. Resume AI E2E
4. Career plan E2E
5. Admin moderation E2E
6. CI green
7. No critical security issue
