# DOMAIN_MODEL.md

## 1. Bounded Context

Identity
Recruitment
Tutoring
Career
Project
AI
Content
Trust
Notification

## 2. Aggregate Roots

### Identity
User

### Recruitment
Job
JobApplication

### Tutoring
TeacherProfile
TutorRequirement
TutorApplication

### Career
Resume
CareerPlan
InterviewSession

### Project
Project
ProjectEnrollment
ProjectSubmission

### Trust
Verification
Report
Review

## 3. User

Fields:
- id
- openid
- unionid optional
- role
- nickname
- avatarUrl
- phone
- status
- createdAt
- updatedAt

Roles:
student
parent
enterprise
admin

## 4. StudentProfile

- id
- userId
- realName
- university
- college
- major
- education
- grade
- city
- skills
- subjects
- certificates
- teachingExperience
- internshipExperience
- careerTarget
- expectedSalary
- availableTime
- verified

## 5. Job

- id
- title
- category
- description
- companyName
- location
- remote
- salaryMin
- salaryMax
- salaryUnit
- requiredSkills
- requiredEducation
- requiredMajor
- deadline
- status
- createdAt
- updatedAt

Categories:
part_time
internship
project
research
campus

Statuses:
draft
pending_review
published
closed
rejected

## 6. JobApplication

- id
- jobId
- studentId
- resumeId
- message
- status
- createdAt

Statuses:
submitted
viewed
interview
accepted
rejected

Unique:
(jobId, studentId)

## 7. TeacherProfile

- id
- studentId
- displayName
- university
- education
- major
- grade
- subjects
- teachingGrades
- teachingMode
- teachingCities
- hourlyRate
- introduction
- teachingExperience
- achievements
- verified
- verificationStatus
- rating
- reviewCount

## 8. TutorRequirement

- id
- parentId
- subject
- studentGrade
- teachingMode
- city
- district
- frequency
- duration
- expectedRate
- requirements
- status

## 9. TutorApplication

- id
- requirementId
- teacherId
- message
- status
- createdAt

Unique:
(requirementId, teacherId)

## 10. Resume

- id
- studentId
- basicInfo
- education
- experience
- projects
- skills
- certificates
- awards
- createdAt
- updatedAt

ResumeVersion:
- id
- resumeId
- version
- targetJob
- content
- aiGenerated
- createdAt

## 11. CareerPlan

- id
- studentId
- targetRole
- targetIndustry
- targetCity
- currentLevel
- skillGap
- roadmap
- generatedByAI
- createdAt
- updatedAt

## 12. InterviewSession

- id
- studentId
- targetRole
- targetCompany
- status
- overallScore
- feedback
- createdAt

InterviewQuestion:
- id
- sessionId
- question
- category
- answer
- score
- feedback
- followUpQuestions

## 13. Project

- id
- title
- category
- description
- difficulty
- requirements
- deliverables
- evaluationCriteria
- status

ProjectEnrollment:
- id
- projectId
- studentId
- status

ProjectSubmission:
- id
- enrollmentId
- artifactUrl
- reportUrl
- feedback
- score
- submittedAt

## 14. Trust

Verification:
- id
- userId
- type
- evidenceUrl
- status
- reviewerId
- reviewedAt

Report:
- id
- reporterId
- targetType
- targetId
- reason
- description
- status
- resolution

Review:
- id
- reviewerId
- targetType
- targetId
- rating
- content

## 15. Relationships

User 1—1 StudentProfile
User 1—1 ParentProfile
StudentProfile 1—0..1 TeacherProfile
Student 1—N JobApplication
Job 1—N JobApplication
Parent 1—N TutorRequirement
Teacher 1—N TutorApplication
TutorRequirement 1—N TutorApplication
Student 1—N Resume
Student 1—N CareerPlan
Student 1—N InterviewSession
Student 1—N ProjectEnrollment

## 16. Invariants

1. blocked user cannot create new application.
2. only verified teacher can be marked as verified teacher.
3. only published job can receive applications.
4. only published tutor requirement can receive applications.
5. application cannot be duplicated.
6. users cannot review themselves.
7. admin-only operations are server-side enforced.
8. AI cannot mutate verified identity facts.
