---
name: evaluate-student
description: Evaluate student performance by analyzing course progress, quiz scores, and conversation transcripts. Generates evidence-based reports with pedagogical analysis and intervention recommendations for teachers.
user_invocable: true
---

# Evaluate Student Skill

This skill helps teachers evaluate student performance on the TutorBot platform. It analyzes course progress, quiz scores, activity patterns, and conversation transcripts to produce structured, evidence-based reports with actionable recommendations.

## Instructions for Claude

When this skill is invoked, follow these steps:

### 1. Determine Report Type

Ask the user which type of report they need:

| Report Type | Purpose | Best For |
|-------------|---------|----------|
| **Individual Student Report** | Deep dive on one student's performance | Parent meetings, 1:1 check-ins, IEP reviews |
| **Course Performance Report** | Class-wide analysis of a specific course | Curriculum review, identifying struggling students |
| **Intervention Alerts** | Quick scan for students needing attention | Weekly check-ins, early warning detection |

### 2. Gather Context

Based on the report type, ask the user:
- **Individual**: Which student? (name or let them pick from a list)
- **Course**: Which course? (name or let them pick from a list)
- **Intervention**: Which courses or all active enrollments?

### 3. Collect Data Using MCP Tools

Follow the data collection flows below for each report type.

### 4. Analyze Using Pedagogy Framework

Apply the frameworks from [pedagogy-guide.md](pedagogy-guide.md) to interpret the data:
- Classify students into ZPD zones based on scores
- Identify mastery vs. non-mastery using the 80% threshold
- Map quiz types to Bloom's taxonomy levels
- Check for early warning signs
- Calculate engagement metrics from transcripts

### 5. Generate Structured Report

Use the report templates below to produce the final output.

---

## MCP Tools Reference

Use the `tutorbot` MCP server tools for data collection:

| Tool | Description | Use When |
|------|-------------|----------|
| `list_users` | List students/teachers with tag filtering | Finding students by name or tag |
| `get_user` | Get full student profile (learning goals, challenges) | Individual student deep dive |
| `list_courses` | List available courses | Course selection |
| `list_enrollments` | List enrollments with filtering by course/student/teacher/status | Finding enrollments to analyze |
| `get_enrollment_progress` | Per-resource scores, completion, attempts for an enrollment | Core performance data |
| `get_student_stats` | 30-day averages, streak, all-time totals | Quick performance overview |
| `get_student_activity` | Paginated activity log with scores and summaries | Recent session history |
| `get_transcript` | Full conversation transcript with quiz responses | Deep engagement analysis |

---

## Data Collection Flows

### Individual Student Report

```
1. list_users → identify the student (search by name or browse)
2. get_user(id) → full profile including learning goals, challenges, interests
3. list_enrollments(student=studentId) → all their enrollments
4. For each active enrollment:
   get_enrollment_progress(enrollmentId) → per-resource scores and completion
5. get_student_stats(studentId) → 30-day overview, streak, totals
6. get_student_activity(studentId, limit=20) → recent sessions
7. For 2-3 key sessions (lowest scores or most recent):
   get_transcript(progressId) → deep analysis of interaction quality
```

### Course Performance Report

```
1. list_courses → identify the course
2. list_enrollments(course=courseId) → all enrolled students
3. For each enrollment:
   get_enrollment_progress(enrollmentId) → per-resource scores
4. For flagged students (score <70% or high attempts):
   get_student_activity(studentId, limit=5) → recent sessions
   get_transcript(progressId) → selective deep dive (1-2 sessions max)
```

### Intervention Alerts

```
1. list_enrollments(status=active) → all active enrollments
   (or filter by teacher if the user wants only their students)
2. For each enrollment:
   get_enrollment_progress(enrollmentId) → check for warning signs
3. For flagged students:
   get_student_stats(studentId) → confirm patterns
   get_student_activity(studentId, limit=5) → recent history
```

**Important token management**: Never fetch all transcripts at once. Transcripts are large (JSONB). Only fetch them for 2-3 key sessions per student, selected based on the quantitative data.

---

## Report Templates

### Individual Student Report

```markdown
# Student Performance Report: [Student Name]

**Date**: [Date]
**Report Period**: [Date range or "All time"]

## Student Profile
- **Learning Goals**: [From profile]
- **Learning Challenges**: [From profile]
- **Interests**: [From profile]

## Performance Summary

| Metric | Value | Assessment |
|--------|-------|------------|
| Mastery Rate (≥80%) | X/Y resources (Z%) | [Strong/Developing/Needs Support] |
| 30-Day Average Score | X% | [ZPD classification] |
| Current Streak | X days | [Engagement level] |
| Course Completion | X/Y courses | [Progress assessment] |
| Avg Attempts to Mastery | X.X | [Efficiency assessment] |

## Course-by-Course Analysis

### [Course Name] — [Status]
- **Progress**: X/Y resources completed (Z%)
- **Average Score**: X%
- **Strengths**: [Specific resources/topics mastered]
- **Growth Areas**: [Resources with low scores or high attempts]
- **Notable Patterns**: [From transcript analysis]

[Repeat for each enrolled course]

## Transcript Insights

Based on analysis of [N] lesson sessions:

- **Engagement Quality**: [High/Medium/Low] — [evidence: avg word count, questions asked, self-corrections]
- **Quiz Performance**: [First-attempt accuracy X%, common error patterns]
- **Scaffolding Dependency**: [Independent/Moderate/High] — [evidence: retry patterns, hint usage]
- **Misconceptions Identified**: [List any recurring wrong answers or misunderstandings]

## ZPD Classification

[Based on scores and patterns, classify where the student is operating:]
- Below 35%: Material is too challenging — recommend stepping back
- 36-69%: Productive struggle zone — maintain scaffolding
- 70%+: Ready to advance — fade scaffolds, increase challenge

**Current Zone**: [Classification with evidence]

## Recommendations

1. [Specific, actionable recommendation based on evidence]
2. [Another recommendation]
3. [Another recommendation]

## Early Warnings

[List any triggered warning indicators, or "No warnings at this time"]
- ⚠️ [Warning with evidence and recommended action]
```

### Course Performance Report

```markdown
# Course Performance Report: [Course Name]

**Date**: [Date]
**Enrolled Students**: [N]
**Course Type**: [Progression type]

## Class Overview

| Metric | Value |
|--------|-------|
| Average Score | X% |
| Completion Rate | X% |
| Students at Mastery (≥80%) | X/Y (Z%) |
| Students Needing Support (<70%) | X/Y (Z%) |

## Score Distribution

| Range | Count | Students | Recommended Action |
|-------|-------|----------|--------------------|
| 90-100% | X | [Names] | Recognition; extend with enrichment |
| 80-89% | X | [Names] | On track; maintain current approach |
| 70-79% | X | [Names] | Monitor; may need targeted support |
| 36-69% | X | [Names] | Active scaffolding; check understanding |
| 0-35% | X | [Names] | Urgent: reassess difficulty level |

## Per-Resource Analysis

| Resource | Avg Score | Completion | Avg Attempts | Problem Areas |
|----------|-----------|------------|-------------|---------------|
| [Name] | X% | X/Y | X.X | [Issues noted] |

[Flag resources where average score <70% — may indicate content issues rather than student issues]

## Students Needing Attention

### [Student Name] — [Score]%
- **Pattern**: [Brief description]
- **Recommended Action**: [Specific intervention]

## Course-Level Recommendations

1. [Recommendation about content/pacing/structure]
2. [Recommendation about specific resources]
3. [Recommendation about student grouping or differentiation]
```

### Intervention Alerts

```markdown
# Intervention Alerts

**Date**: [Date]
**Scanned**: [N] active enrollments across [M] courses

## 🔴 URGENT — Immediate Action Needed

### [Student Name] — [Course Name]
- **Evidence**: [Specific data points]
- **Recommended Action**: [What to do]

## 🟡 WARNING — Monitor Closely

### [Student Name] — [Course Name]
- **Evidence**: [Specific data points]
- **Recommended Action**: [What to do]

## 🟢 POSITIVE — Recognition Opportunity

### [Student Name] — [Course Name]
- **Achievement**: [What they did well]
- **Recommended Action**: [How to reinforce]
```

---

## Transcript Analysis Guide

When analyzing transcripts from `get_transcript`, look for these specific patterns:

### Quiz Performance
- Extract entries with type `quiz_response`, `freetext_response`, or `ordered_list_response`
- Calculate **first-attempt accuracy**: correct on first try vs. needed retries
- Note **wrong answer patterns**: do multiple students choose the same wrong answer? (indicates confusing question or common misconception)
- Track **score progression**: are scores improving across the session?

### Engagement Quality
- **Student message count**: How many messages did the student send?
- **Average word count**: Longer responses generally indicate deeper engagement
- **Questions asked**: Look for "?" in student messages — asking questions shows active learning
- **Self-corrections**: Student correcting their own answers shows metacognition

### Scaffolding Dependency
- **Retry count on quizzes**: Multiple attempts with hints = high scaffolding need
- **Hint usage**: Did the student need hints to succeed?
- **Independence trajectory**: Are retries decreasing across the session?

### Session Patterns
- **Session duration**: Time from first to last transcript entry
- **Message ratio**: Student messages vs. assistant messages (very low student ratio = passive)
- **Drop-off point**: Did the student stop engaging partway through?

---

## Tone Guidelines

When writing reports:

- **Lead with strengths**: Always start with what the student is doing well
- **Use growth-oriented language**: "developing" not "failing", "growth area" not "weakness"
- **Be evidence-based**: Every claim should reference specific data (scores, dates, transcript excerpts)
- **Make recommendations actionable**: "Try resource X next" not "needs improvement"
- **Match the audience**:
  - For teachers: Specific, data-rich, include pedagogical terminology
  - If asked for parent-friendly version: Accessible language, focus on growth trajectory, avoid jargon
  - If asked for student-friendly version: Encouraging, goal-focused, celebrate progress

---

## Additional Resources

- [pedagogy-guide.md](pedagogy-guide.md) - Research-backed framework for interpreting student data
