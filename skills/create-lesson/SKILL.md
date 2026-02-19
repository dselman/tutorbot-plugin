---
name: create-lesson
description: Create educational content (resources and courses) for the TutorBot SaaS application. Use when the user wants to create resources, courses, quizzes, or upload images for AI-powered voice delivery.
user_invocable: true
---

# Create Resource Skill

This skill helps you create educational resources for the TutorBot platform. Resources are the building blocks of your curriculum - each is a self-contained learning unit delivered by AI bots to students via voice conversation or presentation mode. Resources are grouped into courses.

## Instructions for Claude

When this skill is invoked, follow these steps:

1. **Gather Requirements**: Ask the user about:
   - Topic/subject for the resource
   - Target audience (age, skill level)
   - Delivery mode preference (conversation or presentation)
   - Desired length (default: 5-10 minutes)
   - Any specific learning objectives
   - Whether they want AI-generated images or have URLs to images

2. **Design the Resource**: Based on the guides, create a structure with:
   - Clear learning objectives
   - Logical sections with headings
   - Checkpoints for understanding (quizzes)
   - Appropriate media placement

3. **Create Content**: Draft the markdown content following best practices:
   - Write instructions for the bot, not a script
   - Use "the student" with they/them pronouns
   - Keep sections digestible

4. **Generate Media** (if needed): Use image generation tools to create:
   - Diagrams and illustrations
   - Educational visuals
   - Upload via `upload_image_from_url` (preferred) or `create_image`

5. **Execute Creation**: Use MCP tools to:
   - Create the resource via `create_resource`
   - Upload any media files via `upload_image_from_url` or `create_image`
   - Create quizzes via `create_quiz`
   - **CRITICAL**: Update resource content via `update_resource` to embed image and quiz references using the correct markdown syntax (see below)
   - Optionally create a course and add the resource to it

6. **Provide Testing Instructions**: Tell the user how to test their resource using the Test Resource button in the admin UI

## MCP Tools

Use the `tutorbot` MCP server tools:

### Available Tools

| Tool | Description |
|------|-------------|
| `list_resources` | List existing resources with optional tag filtering |
| `get_resource` | Fetch a resource by ID |
| `create_resource` | Create a new resource |
| `update_resource` | Update an existing resource |
| `create_image` | Upload an image (base64 data) to a resource |
| `upload_image_from_url` | Upload an image from a URL to a resource (preferred for remote use) |
| `create_quiz` | Create a quiz for a resource |
| `list_tags` | List available tags |
| `create_course` | Create a new course (collection of resources) |
| `list_courses` | List existing courses |
| `add_resource_to_course` | Add a resource to a course |

### Workflow

```
1. create_resource(name, content, tags, deliveryMode)
   → Returns resource with ID

2. upload_image_from_url(resourceId, url, name, description, question, answer, hint, botVisible)
   → Returns image with ID
   OR
   create_image(resourceId, name, mimeType, data, description, question, answer, hint, botVisible)
   → Returns image with ID

3. create_quiz(resourceId, question, questionType, answers, ...)
   → Returns quiz with ID

4. update_resource(id, content)
   → CRITICAL: Update content to include image and quiz references

5. (Optional) create_course(name, description, tags, progressionType)
   → Returns course with ID

6. (Optional) add_resource_to_course(courseId, resourceId, order)
   → Adds resource to the course
```

### Tool Parameters

**create_resource:**
- `name` (required): Display name for the resource
- `content` (required): Markdown content
- `tags` (optional): Array of tags for organization
- `deliveryMode` (optional): `"conversation"` or `"presentation"`

**upload_image_from_url** (preferred for remote use):
- `resourceId` (required): Resource to attach image to
- `url` (required): Public URL of the image to download
- `name` (required): Image filename
- `description` (optional): What the image shows (important for bot)
- `question` (optional): Question to ask about the image
- `answer` (optional): Expected answer
- `hint` (optional): Help for students
- `botVisible` (optional): If true, bot can see the image

**create_image:**
- `resourceId` (required): Resource to attach image to
- `name` (required): Image filename
- `mimeType` (required): e.g., `"image/png"`, `"image/jpeg"`
- `data` (required): Base64-encoded image data
- `description` (optional): What the image shows (important for bot)
- `question` (optional): Question to ask about the image
- `answer` (optional): Expected answer
- `hint` (optional): Help for students
- `botVisible` (optional): If true, bot can see the image

**create_quiz:**
- `resourceId` (required): Resource to attach quiz to
- `question` (required): Question text
- `questionType` (required): `"single"`, `"multiple"`, or `"freetext"`
- `answers` (for single/multiple): Array of `{id, text, isCorrect}`
- `expectedAnswer` (for freetext): Correct answer
- `inputRestriction` (for freetext): `"text"`, `"integer"`, or `"decimal"`
- `evaluationCriteria` (optional): AI grading guidelines
- `retryLimit` (optional): Max attempts
- `hint` (optional): Guidance for wrong answers
- `description` (optional): When the bot should present this quiz

**create_course:**
- `name` (required): Course name
- `description` (optional): Course description
- `tags` (optional): Array of tags
- `progressionType` (optional): `"flexible"`, `"sequential"`, or `"random"`

**add_resource_to_course:**
- `courseId` (required): Course ID
- `resourceId` (required): Resource ID to add
- `order` (optional): Position in the course

## CRITICAL: Embedding Media and Quizzes in Resource Content

After creating images and quizzes, you **MUST** update the resource content to include references to them. Without these references, the bot will NOT display the media or quizzes during delivery.

### Image Reference Syntax

```markdown
![IMAGE_ID](/api/v1/images/IMAGE_ID/data)
```

Example: If `create_image` returns `{ id: 156 }`, insert:
```markdown
![156](/api/v1/images/156/data)
```

### Quiz Reference Syntax

```markdown
::quiz{#QUIZ_ID}
```

Example: If `create_quiz` returns `{ id: 28 }`, insert:
```markdown
::quiz{#28}
```

### Complete Example

```
# Step 1: Create resource
create_resource(
  name: "Introduction to Photosynthesis",
  content: "# Learning Objectives\n\nPlaceholder content...",
  tags: ["science", "biology"],
  deliveryMode: "conversation"
)
# Response: { id: 42, ... }

# Step 2: Upload image from URL
upload_image_from_url(
  resourceId: 42,
  url: "https://example.com/plant-cell.png",
  name: "Plant Cell Diagram",
  description: "Diagram of a plant cell showing chloroplasts",
  question: "Where does photosynthesis occur?",
  answer: "In the chloroplasts",
  hint: "Look for the green organelles",
  botVisible: true
)
# Response: { id: 156, ... }

# Step 3: Create quiz
create_quiz(
  resourceId: 42,
  description: "Test understanding of photosynthesis location",
  question: "In which organelle does photosynthesis take place?",
  questionType: "single",
  answers: [
    { id: "a", text: "Mitochondria", isCorrect: false },
    { id: "b", text: "Chloroplast", isCorrect: true },
    { id: "c", text: "Nucleus", isCorrect: false }
  ],
  retryLimit: 2,
  hint: "It contains chlorophyll, which is green"
)
# Response: { id: 28, ... }

# Step 4: CRITICAL - Update resource with image and quiz references
update_resource(
  id: 42,
  content: "# Learning Objectives\n\nBy the end of this resource, the student should understand photosynthesis.\n\n## What is Photosynthesis?\n\nExplain that plants convert sunlight into energy. Show the diagram:\n\n![156](/api/v1/images/156/data)\n\nDiscuss the diagram with the student.\n\n## Check Understanding\n\nNow test the student's knowledge:\n\n::quiz{#28}\n\n## Summary\n\nReview the key points."
)
```

## Quiz Types

### Single Choice
```json
{
  "question": "What gas do plants absorb?",
  "questionType": "single",
  "answers": [
    { "id": "a", "text": "Oxygen", "isCorrect": false },
    { "id": "b", "text": "Carbon dioxide", "isCorrect": true }
  ],
  "hint": "Think about what humans breathe out"
}
```

### Multiple Choice
```json
{
  "question": "Select ALL ingredients for photosynthesis",
  "questionType": "multiple",
  "answers": [
    { "id": "a", "text": "Sunlight", "isCorrect": true },
    { "id": "b", "text": "Water", "isCorrect": true },
    { "id": "c", "text": "Oxygen", "isCorrect": false }
  ]
}
```

### Free Text
```json
{
  "question": "Calculate 15% of 80",
  "questionType": "freetext",
  "inputRestriction": "decimal",
  "expectedAnswer": "12",
  "evaluationCriteria": "Accept 12, 12.0, or 12.00"
}
```

## Generating Images with AI

For AI-generated images:

1. **Generate** with educational prompts like:
   - "A simple diagram showing [concept], suitable for [age] students"
   - "An illustration of [subject] with labeled parts"

2. **Host temporarily** - upload the generated image to an accessible URL or use base64

3. **Upload** with `upload_image_from_url` (preferred) providing complete metadata (description, question, answer, hint, botVisible)

## Best Practices

1. **Write for the bot, not the student** - The bot interprets your instructions and delivers them conversationally
2. **Use clear headings** - Structure content with `#`, `##`, `###` for pacing
3. **Keep resources short** - 5-10 minutes is ideal per resource; split longer content into multiple resources within a course
4. **Provide complete media metadata** - Description, question, answer, and hint for every image
5. **Place quizzes strategically** - After teaching the relevant content
6. **Enable botVisible for important images** - Let the bot see diagrams and charts
7. **Always embed references** - Images need `![ID](/api/v1/images/ID/data)` and quizzes need `::quiz{#ID}` in the content
8. **Design resources to be self-contained** - Each resource should make sense on its own and be reusable across courses
9. **Test your resources** - Use the Test Resource feature in the admin UI before assigning to students

## Additional Resources

- [resource-creation-guide.md](resource-creation-guide.md) - Detailed resource structuring guidance
- [teacher-guide.md](teacher-guide.md) - Teacher workflow and course management
