# TEST_SPEC.md

## 1. Test Pyramid

Unit > Integration > E2E

AI 另建 Evaluation Pyramid：
offline dataset → regression → online metrics

## 2. Unit

必须测试：
- domain invariants
- matching rules
- authorization policies
- validation
- career plan schema
- resume transformations

## 3. Integration

必须测试：
- auth
- user profile
- job CRUD
- job application
- tutor requirement
- tutor application
- resume upload
- AI Gateway
- admin moderation

## 4. E2E

### E2E-001 Student
login
→ profile
→ jobs
→ detail
→ apply

### E2E-002 Parent
login
→ requirement
→ tutor search
→ tutor detail
→ application/contact request

### E2E-003 Resume
login
→ upload
→ parse
→ analyze
→ optimize
→ save version

### E2E-004 Career
profile
→ target role
→ analysis
→ plan
→ roadmap

### E2E-005 Moderation
admin
→ pending content
→ review
→ approve/reject

## 5. Authorization Tests

- Student cannot edit another student's profile.
- Parent cannot approve teacher verification.
- Normal user cannot access admin APIs.
- Blocked user cannot create application.
- Unverified teacher cannot claim verified status.

## 6. Security Tests

- malformed upload
- oversized upload
- malicious filename
- XSS payload
- SQL injection payload
- rate limit
- object-level authorization
- token reuse
- prompt injection in uploaded document

## 7. AI Evaluation

Metrics:
- factuality
- relevance
- completeness
- safety
- structured output validity
- latency
- cost

Regression:
任何 Prompt 或 Model 版本变化必须跑 regression dataset。

## 8. Acceptance

测试必须证明用户闭环，而不是只证明函数存在。
