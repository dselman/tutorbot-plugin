# Pedagogy Reference Guide

Research-backed frameworks for interpreting student performance data. Use this guide when analyzing data collected by the evaluate-student skill.

---

## 1. Mastery Learning (Bloom, 1968)

**Core principle**: Most students can achieve mastery if given sufficient time and appropriate instruction.

### Mastery Threshold: 80%

| Score | Classification | Implication |
|-------|---------------|-------------|
| ≥80% | **Mastery achieved** | Student is ready to advance to new material |
| 70-79% | **Approaching mastery** | Needs targeted review of specific gaps before advancing |
| <70% | **Not yet mastered** | Needs corrective instruction with a *different* approach (not just repetition) |

### Key Metrics
- **Mastery rate**: % of resources where student scored ≥80%
- **Attempts to mastery**: How many tries before reaching 80% — lower is better, but more attempts ≠ failure (persistence is positive)
- **Corrective effectiveness**: After a low score, did the next attempt improve? If not, the corrective strategy needs to change

### Application
When a student scores below 80%:
1. Do NOT simply repeat the same content
2. Recommend a different instructional approach (different examples, different modality, prerequisite review)
3. Track whether the alternative approach produces improvement

---

## 2. Zone of Proximal Development (Vygotsky, 1978)

**Core principle**: Learning happens best when material is challenging but achievable with support.

### ZPD Score Boundaries

| Score Range | Zone | What It Means | Recommended Action |
|-------------|------|---------------|-------------------|
| 0-35% | **Frustration Zone** | Material is too far beyond current ability | Step back to prerequisite content; reduce complexity |
| 36-69% | **Zone of Proximal Development** | Productive struggle — learning is happening | Maintain scaffolding; this is the sweet spot |
| 70-100% | **Comfort Zone** | Student can handle this independently | Gradually fade scaffolds; increase challenge level |

### Scaffolding Indicators (from transcript data)
- **High scaffolding need**: Multiple retries on quizzes, requests for hints, short responses, bot does most of the talking
- **Moderate scaffolding**: Occasional retries, engages with hints productively, growing independence
- **Independent**: First-attempt success on quizzes, asks own questions, extends concepts

### Application
- If a student is consistently in the Frustration Zone across resources → the course difficulty is mismatched, not a student effort problem
- If a student is consistently in the Comfort Zone → they need more challenging material to continue growing
- The goal is to keep students in the ZPD as much as possible

---

## 3. Bloom's Taxonomy — Quiz Type Mapping

Map quiz types to cognitive levels to assess the depth of understanding being tested:

| Quiz Type | Typical Cognitive Level | What It Tests |
|-----------|----------------------|---------------|
| Single choice (recall) | **Remember** | Can the student recognize the correct answer? |
| Single choice (application) | **Apply** | Can the student apply a concept to a new situation? |
| Multiple choice | **Understand/Analyze** | Can the student identify all relevant factors? |
| Freetext (short answer) | **Understand** | Can the student explain in their own words? |
| Freetext (calculation) | **Apply** | Can the student execute a procedure? |
| Freetext (open-ended) | **Analyze/Evaluate** | Can the student reason about the concept? |

### Application
- A student who masters Remember-level quizzes but struggles with Apply-level quizzes needs more practice with application, not more memorization
- If a course only has Remember-level quizzes, performance data may overestimate true understanding
- Note the cognitive level mix when reporting — "85% accuracy on recall questions, 60% on application questions" is more useful than just "72% average"

---

## 4. Key Performance Metrics

### Primary Metrics

| Metric | How to Calculate | What It Indicates |
|--------|-----------------|-------------------|
| **Accuracy Rate** | Total correct / Total attempted | Overall performance level |
| **Mastery Rate** | Resources ≥80% / Total resources | Proportion of content mastered |
| **Improvement Trend** | Compare scores across sequential sessions | Whether the student is progressing |
| **Attempts to Mastery** | Avg attempts before ≥80% score | Learning efficiency (lower = faster acquisition) |
| **Completion Rate** | Completed resources / Total assigned | Engagement and persistence |
| **Engagement Score** | Composite of message count, word count, questions asked | Quality of participation |

### Derived Insights

- **Mastery rate high + Attempts high** = Student perseveres and eventually succeeds (positive trait, may need efficiency support)
- **Mastery rate low + Attempts low** = Student may be disengaged or giving up early (intervention needed)
- **Mastery rate low + Attempts high** = Student is trying but current approach isn't working (change instructional strategy)
- **Accuracy declining over time** = Possible burnout, increasing difficulty without readiness, or external factors

---

## 5. Early Warning Signs

Flag students who exhibit any of these patterns:

| Warning Sign | Threshold | Severity | Recommended Response |
|-------------|-----------|----------|---------------------|
| Score consistently below 35% | 2+ resources | 🔴 Urgent | Step back to prerequisites; check course-student match |
| Declining score trend | 3+ consecutive sessions | 🔴 Urgent | Investigate cause; possible burnout or difficulty spike |
| No activity | 7+ days since last session | 🟡 Warning | Reach out to student/parent; check for barriers |
| Very short responses | Avg <5 words per message | 🟡 Warning | May indicate low engagement; try different delivery mode |
| Never asks questions | 0 questions across 3+ sessions | 🟡 Warning | Model question-asking; check comprehension |
| Repeated failure without mastery | 3+ attempts on same resource, still <80% | 🟡 Warning | Change instructional approach; different resource |
| Very fast completion | Session <2 minutes | 🟡 Warning | May be rushing; check if scores reflect understanding |
| High mastery + high engagement | Consistent ≥80% with good interaction | 🟢 Positive | Recognize achievement; offer enrichment |
| Improving trend | 3+ sessions with rising scores | 🟢 Positive | Acknowledge growth; current approach is working |
| Asks questions independently | Regular "?" in messages | 🟢 Positive | Encourage curiosity; provide extension activities |

---

## 6. Intervention Recommendations

| Condition | Intervention | Rationale |
|-----------|-------------|-----------|
| Score <35% consistently | Assign prerequisite resources; reduce course difficulty | Student is in frustration zone — material is too advanced |
| Score 36-69%, not improving | Try different delivery mode (conversation ↔ presentation); provide additional scaffolding resources | Student is in ZPD but current approach isn't working |
| Score 36-69%, improving | Continue current approach; acknowledge progress | Student is in ZPD and making gains — don't change what's working |
| Score 70-79% | Targeted review of specific weak areas; then reassess | Close to mastery — focused review can close the gap |
| High attempts, eventual mastery | Praise persistence; consider breaking content into smaller chunks | Student succeeds but needs more scaffolding steps |
| Fast completion, low scores | Check for rushing; consider adding more formative checks | Student may not be engaging deeply with content |
| No activity 7+ days | Personal outreach; check for barriers (access, motivation, life circumstances) | Disengagement needs human connection, not more content |
| Low engagement in transcripts | Switch delivery mode; try more interactive content with images and varied quiz types | Passive learning isn't working for this student |
| Consistently high performance | Offer enrichment; increase challenge; consider peer tutoring role | Student needs continued growth, not just maintenance |

---

## 7. Report Audience Adaptation

### For Teachers
- Use pedagogical terminology (ZPD, scaffolding, mastery, formative assessment)
- Include specific data points and percentages
- Reference specific resources and quiz questions
- Provide actionable next steps tied to the platform (assign resource X, switch to conversation mode, etc.)

### For Parents
- Use accessible language — avoid jargon
- Focus on growth trajectory, not absolute scores
- Frame challenges as "next steps" not "problems"
- Highlight positive behaviors (persistence, curiosity, improvement)
- Keep it concise — key takeaways and 2-3 action items

### For Students
- Lead with achievements and progress
- Use encouraging, goal-focused language
- Set concrete, achievable next goals
- Acknowledge effort, not just results
- Keep it brief and forward-looking
