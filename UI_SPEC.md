# UI_SPEC.md

## 1. Navigation

TabBar:
- Home
- Jobs
- Tutors
- Career
- Me

## 2. Page Inventory

### Home
- HOME-001 首页
- HOME-002 搜索结果
- HOME-003 Banner落地页

### Jobs
- JOB-001 岗位列表
- JOB-002 岗位详情
- JOB-003 发布岗位
- JOB-004 我的申请

### Tutors
- TUTOR-001 老师列表
- TUTOR-002 老师详情
- TUTOR-003 发布家教需求
- TUTOR-004 需求详情
- TUTOR-005 我的老师资料

### Career
- CAREER-001 求职首页
- CAREER-002 AI职业规划
- CAREER-003 简历上传
- CAREER-004 简历诊断
- CAREER-005 简历优化结果
- CAREER-006 AI模拟面试
- CAREER-007 面试反馈
- CAREER-008 实战项目列表
- CAREER-009 项目详情

### Me
- ME-001 我的
- ME-002 学生资料
- ME-003 我的收藏
- ME-004 设置

## 3. UX Rules

- 首屏任务导向。
- 关键 CTA 明确。
- 表单尽量分步。
- 认证状态明显。
- 不把内部匹配分数直接作为“成功概率”。
- AI 结果必须说明“建议/分析”，不能伪装为事实。
- 空状态必须给出下一步行动。
- 加载、错误、权限不足必须有明确状态。

## 4. Job List

Card：
- title
- category
- company
- city
- remote
- salary
- skill tags
- publish time

Actions：
- view
- favorite
- apply

## 5. Tutor Card

Card：
- displayName
- university
- education
- major
- subjects
- teaching mode
- city
- hourlyRate
- verification badge
- rating/review count

## 6. Career Home

四个核心入口：
- AI职业规划
- AI简历
- AI模拟面试
- 实战项目

## 7. AI UX

AI 生成内容必须：
- 显示生成中
- 支持失败重试
- 显示生成结果
- 允许用户修改
- 对重要事实提供来源/用户原始输入依据
- 不允许 AI 静默修改用户身份信息

## 8. Accessibility

- 可读字号
- 足够点击区域
- 表单错误可理解
- 不只依赖颜色表达状态

## 9. Admin UI

桌面端：
- Dashboard
- Users
- Jobs
- Tutors
- Reports
- Verification
- AI Usage
- Content
