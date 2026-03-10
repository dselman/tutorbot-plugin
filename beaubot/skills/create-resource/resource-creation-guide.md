# Resource Guide

This guide explains how to create effective resources for delivery by AI bots. Understanding how the bot interprets your content is essential for creating engaging, educational lessons.

## Understanding the Delivery Model

When you create a resource, you're writing instructions for an AI bot that will deliver the lesson on your behalf. The bot reads your content and uses it to guide a conversation with the student.

### Key Terms

- **Student**: The person taking the lesson
- **Teacher**: You, the person creating the resource
- **Bot**: The AI that delivers your lesson to students
- **Resource**: A single learning unit containing content for the bot to deliver
- **Course**: A collection of resources organized for students to complete
- **Quiz**: A structured question with automatic correctness checking (supports single choice, multiple choice, open answer, and ordered list)
- **Assessment**: The AI-generated summary and grading of a completed resource
- **Delivery Mode**: How the resource is presented - either as a two-way voice conversation or a one-way presentation

### Resources and Courses

Resources are the building blocks of your curriculum. Each resource is a self-contained learning unit focused on a specific topic or skill.

**Courses** group related resources together:
- A course can contain multiple resources
- Resources can be reused across different courses
- Course progression can be flexible (any order), sequential (fixed order), or random
- Students are enrolled in courses, which gives them access to all resources in that course

When creating resources, design them to be:
- **Self-contained**: Each resource should make sense on its own
- **Focused**: Cover one topic or concept per resource
- **Reusable**: Write content that could fit into multiple courses if needed

### Delivery Modes

Resources can be delivered in two modes, which you select when creating the resource:

**Conversation Mode** (default):
- Two-way voice interaction between the student and AI tutor
- The student speaks to the bot and receives spoken responses
- Requires microphone access
- Ideal for: Interactive lessons, Q&A, discussion-based learning, personalized tutoring

**Presentation Mode**:
- One-way narration where the AI reads your content aloud
- No microphone required from the student
- Students click "Next" to advance through sections
- Ideal for: Lecture-style content, information delivery, accessibility (students who can't use a microphone), passive learning

When writing content for presentation mode:
- Organize content into clear sections using headings
- Each heading becomes a "slide" that the student advances through
- The bot narrates the content under each heading
- Quizzes pause the presentation until the student answers
- Keep each section concise for better pacing

### How the Bot Works

When a student starts a resource, the bot receives context that helps it personalize the delivery:

| Context | Source | Purpose |
|---------|--------|---------|
| **Bot description** | System prompt configured by admin | Defines the bot's personality, teaching style, and expertise |
| **Teacher description** | Your user profile | Allows the bot to represent you and your teaching approach |
| **Student description** | Student's user profile | Helps the bot personalize explanations to the student |
| **Resource content** | The document you create | The actual lesson material to deliver |

**Important**: Because the bot uses these descriptions to personalize delivery, it's essential that profile information is accurate and complete:
- Ensure your teacher profile describes your teaching style and expertise
- When adding students, include relevant information about their background and learning needs
- Work with your admin to select bots whose descriptions match your content

**Example teacher profile:**
```
Mrs Johnson is a professional and kind teacher. She has a
degree in education and is an expert primary school teacher.
She lives in Boston, Massachusetts.

If the pupil disengages or interacts in an unsafe or confused
manner please say, "If you do not engage with the lesson I
will contact Mrs Johnson."
```

Notice how this profile includes:
- Professional background and qualifications
- Teaching style (professional, kind)
- Location context
- Instructions for handling difficult situations

**Example student profile:**
```
Lily is 11 years old. She loves dinosaurs, swimming and
drawing. She has a pet hamster named Biscuit.
```

Student profiles help the bot personalize examples and make connections to the student's interests during lessons.

The bot combines all of this context to deliver a personalized lesson. This means:

- **Write for the bot, not to the student**: The bot will adapt your instructions based on who the student is
- **Don't repeat bot personality**: The bot already knows its teaching style from its system prompt
- **Focus on content**: Your resource should contain the learning material and objectives, not delivery instructions that duplicate the bot's configuration
- **Trust the personalization**: The bot will adjust its language and pace based on the student

The bot is knowledgeable and can draw on general knowledge to support your lesson. However, it follows your resource content as the primary guide. Your job is to:

1. Define what the student should learn
2. Structure the lesson into logical steps
3. Provide guidance on how to assess understanding
4. Add media with clear descriptions and questions

## Writing for AI Delivery

### Perspective and Tone

Write your content as instructions for the bot, not as a script to read verbatim. The bot will interpret your guidance and deliver it conversationally.

**Good approach:**
```
Explain the concept of photosynthesis to the student.
Make sure they understand that plants convert sunlight
into energy. Ask them to describe what would happen
if a plant received no sunlight.
```

**Avoid:**
```
Hello! Today we're going to learn about photosynthesis.
Photosynthesis is how plants make food...
```

### Language Guidelines

- Refer to "the student" and use they/them pronouns
- Keep sentences clear and concise
- Be specific about what the student should learn
- Avoid ambiguous instructions
- The bot is knowledgeable, so keep guidance high-level

### Explicit Learning Objectives

Start each resource with clear objectives so the bot understands the goal:

```
# Learning Objectives

By the end of this lesson, the student should be able to:
- Explain the basic process of photosynthesis
- Identify the inputs and outputs of photosynthesis
- Describe why photosynthesis is important for life on Earth
```

## Structuring Your Lesson

### Using Headings

Use markdown headings (#, ##, ###) to organize your content into steps. The bot uses these to pace the lesson appropriately.

```
# Introduction

Introduce the topic of photosynthesis and why it matters.
Show the diagram of a plant in sunlight:

![156](/api/v1/images/156/data)

## Step 1: What is Photosynthesis?

Explain that photosynthesis is the process plants use to
convert sunlight into food. Check that the student
understands this basic definition before moving on.

::quiz{#28}

## Step 2: The Ingredients

Show the diagram of the photosynthesis inputs:

![157](/api/v1/images/157/data)

Discuss the inputs: sunlight, water, and carbon dioxide.

::quiz{#29}

## Step 3: The Products

Explain that plants produce glucose and oxygen.

::quiz{#30}

# Summary

Review the key points and congratulate the student
on completing the lesson.
```

Notice how this example includes an image or quiz (or both) in **every section**. This is essential for keeping students engaged. A section that is only text with no interactivity will feel like a lecture.

### Lesson Flow

A well-structured lesson typically includes:

1. **Introduction**: Engage the student with a visual and preview what they'll learn
2. **Content Steps**: Break the material into digestible sections, **each with at least a quiz or image**
3. **Check Points**: Include quizzes to verify understanding — aim for **at least 2-3 quizzes per resource**
4. **Summary**: Recap key takeaways

### Keeping Lessons Interactive

**The most common mistake is creating text-heavy resources with too few quizzes and images.** Resources that are mostly text feel passive and lecture-like, even when delivered by an engaging AI tutor.

Follow these density guidelines:

| Element | Minimum per resource | Purpose |
|---------|---------------------|---------|
| **Quizzes** | 2-3 | Check understanding, keep students actively thinking |
| **Images** | 1-2 | Illustrate concepts, break up text, give the bot material to discuss |

**Signs your resource is too text-heavy:**
- A section has more than 3-4 sentences with no quiz or image
- The resource has fewer than 2 quizzes total
- The resource has no images at all
- The student would spend most of the lesson just listening

**How to fix text-heavy content:**
- Add a quick quiz after each concept to check understanding
- Add an image or diagram to illustrate the key idea in each section
- Split long explanatory sections into shorter ones with interactivity between them
- Use a variety of quiz types (single choice for quick checks, open answer for calculations, fraction for math, ordered list for sequencing) to keep things fresh

### Recommended Length

Keep lessons short and focused. **5-10 minutes is ideal** for maintaining student engagement. If you have more content, consider splitting it into multiple resources within a course.

## Working with Images

Images enhance your lessons. By default, the bot relies on the metadata you provide (description, question, answer, hint). However, you can enable **Bot Vision** on individual images to let the bot actually see the image content.

### How Image Metadata Works

When you add an image, you must fill in four fields:

| Field | Purpose |
|-------|---------|
| **Description** | Tells the bot what the image shows |
| **Question** | What the bot should ask about the image |
| **Answer** | The expected correct response |
| **Hint** | Help for students who are struggling |

### Adding an Image

Click the image button in the toolbar to open the media dialog. You have three ways to add images:

**Upload File** (first tab):
1. Click **Choose Image, Video, or PDF**
2. Select a file — **PNG** and **JPEG** images (max 5 MB), videos (max 100 MB), or PDFs (max 20 MB)
3. The file is uploaded and inserted into your content

**AI Image** (second tab):
1. Enter a text prompt describing the image you want (e.g. "A simple diagram showing the water cycle, suitable for primary school students")
2. Click **Generate** — the image is created using AI and inserted into your content
3. This uses your organization's OpenAI API key
4. Best for: custom illustrations, diagrams, educational scenes

**Word Image** (third tab):
1. Enter a word or phrase (e.g. "Photosynthesis", "3/4 + 1/2")
2. Optionally pick a font color
3. Click **Create** — a clean text image is generated instantly and inserted into your content
4. Supports multi-line text (use Shift+Enter for new lines)
5. Best for: vocabulary cards, sight words, math expressions, labels, flash cards

After inserting any image:
1. Click the image in the editor to open the settings panel
2. Fill in all four metadata fields (description, question, answer, hint)
3. Click **Save** to store the metadata

### Writing Effective Image Metadata

**Description**: Be specific about what the image contains. The bot will describe this to the student or reference it during discussion.

```
Description: A diagram showing a plant cell with labeled
chloroplasts. Arrows indicate sunlight entering the leaf
and oxygen being released.
```

**Question**: Write a clear question that tests understanding of what the image shows.

```
Question: Looking at the diagram, where does
photosynthesis take place within the plant cell?
```

**Answer**: Provide the expected response. Be specific enough that the bot can assess correctness, but allow for reasonable variations.

```
Answer: Photosynthesis takes place in the chloroplasts.
The student might also mention that chloroplasts contain
chlorophyll, which captures sunlight.
```

**Hint**: Guide students toward the answer without giving it away.

```
Hint: Look for the green structures inside the cell.
What are they called?
```

### Bot Vision: Letting the Bot See Images

By default, the bot relies entirely on your text descriptions. However, you can optionally enable **Bot Vision** for individual images, which sends the actual image data to the AI when it's displayed to the student.

**To enable Bot Vision:**
1. Click an image to open the settings panel
2. Toggle on **"Bot can see this image"**
3. Save the image settings

**When to enable Bot Vision:**
- **Diagrams and charts** where details matter
- **Photos** the bot should describe or discuss in detail
- **Complex visuals** where your text description might miss nuances

**When to leave it off:**
- **Decorative images** that don't need discussion
- **Simple visuals** where your description is sufficient
- **When lesson speed matters** (sending images adds processing time)

**Note**: Bot Vision only works for images, not videos or PDFs. Videos and PDFs always rely on your text descriptions.

Even with Bot Vision enabled, you should still provide a good description, question, answer, and hint. The text metadata helps structure the conversation, while the actual image allows the bot to notice and discuss details you might not have described.

### Image Best Practices

- **Include at least 1-2 images per resource** — every resource should have visuals. Text-only resources feel dry and lecture-like.
- **Use the right tool for the job**: Use **Word Image** for vocabulary and labels (instant, no API key needed). Use **AI Image** for custom illustrations and diagrams. Use **Upload** for existing files.
- **Use clear, simple images** that focus on one concept
- **Write detailed descriptions** even if Bot Vision is enabled
- **Enable Bot Vision** for images where visual details matter
- **Make questions specific** to what the image shows
- **Provide helpful hints** that scaffold learning
- **Test your lesson** to ensure the image discussion flows naturally
- **Don't skip images** — even if the topic seems abstract, a diagram, chart, or illustration almost always helps

## Working with Videos

Videos work similarly to images: **the bot cannot watch videos**. It relies entirely on your metadata.

### Adding a Video

1. Click the image button in the toolbar (videos use the same upload flow)
2. Select a video file (maximum 100 MB)
3. A video thumbnail appears in your content (with a blue border)
4. Click the thumbnail to open the settings panel
5. Fill in the description, question, answer, and hint
6. Click **Save**

### Video Metadata Strategy

Since the bot cannot watch the video, your description must capture everything the student sees:

```
Description: A 2-minute video showing the process of
photosynthesis. The animation shows sunlight hitting a leaf,
water traveling up from roots, and CO2 entering through
stomata. It then shows glucose molecules being created
inside chloroplasts and oxygen being released.
```

**Question** should relate to specific content in the video:

```
Question: According to the video, what three things
does a plant need for photosynthesis?
```

### When to Use Video

Videos are most effective when:
- Showing processes or animations
- Demonstrating real-world examples
- Providing visual context for complex concepts

Remember that you must describe everything important in the video's description field for the bot to discuss it meaningfully.

## Working with PDFs

PDFs allow you to attach downloadable documents to your lessons — worksheets, reference materials, supplementary reading, or any document the student may need.

### How to Upload

Upload PDFs through the media dialog (same as images and videos):

1. Click the image button in the toolbar, then use the **Upload** tab
2. Select a PDF file (maximum 20 MB)
3. The PDF will appear in the editor with a distinctive red border and PDF icon
4. Click on it to open the side panel and configure metadata

### Metadata Guidance

Since the bot **cannot read PDFs**, the **Description** field is critical. Without a description, the bot has no idea what the PDF contains and cannot discuss it with the student.

Write a thorough description that covers:
- What the document is (worksheet, reference sheet, reading passage, etc.)
- Key content or topics covered
- How the student should use it

```
Description: A two-page worksheet on long division with 10
practice problems. Problems start with simple single-digit
divisors and progress to two-digit divisors. An answer key
is included on the second page.
```

The **Question**, **Answer**, and **Hint** fields work the same as for images — use them to have the bot discuss or quiz the student about the PDF content.

### Student Experience

When the bot displays a PDF during a lesson, the student sees a download card with the filename and a download button. Clicking the button saves the PDF to their device. The bot will briefly describe what the PDF contains and encourage the student to download it.

### When to Use PDFs

PDFs are most effective for:
- Worksheets and practice exercises
- Reference materials and cheat sheets
- Supplementary reading passages
- Printed activities to complete offline

## Working with Quizzes

Quizzes provide structured assessment with automatic correctness checking. The platform supports four question types: single choice, multiple choice, open answer, and ordered list.

### When to Use Quizzes

**Use quizzes liberally.** Quizzes are the primary way students actively engage with the material. A resource without enough quizzes feels passive and lecture-like. Aim for **at least 2-3 quizzes per resource**, and consider adding more for longer or more complex topics.

**Use quizzes for:**
- Testing specific factual knowledge
- Checking understanding **after every major concept** before moving to the next topic
- Providing structured practice with clear feedback
- Assessments where you want consistent, objective evaluation
- Keeping the student actively thinking and participating (not just listening)
- Breaking up text-heavy sections with interactive checkpoints

**Use conversational questions for:**
- Open-ended discussion and exploration
- Questions with many valid answers
- Building on student responses dynamically
- More natural dialogue flow

**Tip:** When in doubt, add a quiz. It's better to have slightly too many interactive checkpoints than to have a passive, text-heavy lesson.

### Quiz Question Types

**Single Choice**: One correct answer from a list of options
- Best for: Clear-cut facts, definitions, identifying correct statements
- Example: "What is the capital of France?" (Paris)

**Multiple Choice**: Students select all correct answers from a list
- Best for: "Select all that apply" questions, identifying multiple correct items
- Example: "Which are prime numbers?" (2, 3, 5, 7)

**Open Answer**: Students type their answer, which is evaluated by AI
- Best for: Numerical answers, short written responses, calculations
- The AI compares the student's answer against your expected answer
- Provides intelligent feedback even for partially correct answers

**Ordered List**: Students drag and drop items into the correct sequence
- Best for: Ordering events, ranking items, sequencing steps, comparing values
- Example: "Put these in order from smallest to largest: 3/5, 0.55, 62%, 1/2"
- Items are shuffled for the student; they must arrange them in the correct order
- Partial credit: score based on how many items are in the correct position

### Adding a Quiz

1. Position your cursor where you want the quiz in the lesson flow
2. Click the **Quiz** button in the toolbar
3. Fill in the quiz fields:
   - **Description**: When the bot should use this quiz
   - **Question**: The question text shown to students
   - **Question Type**: Single choice, Multiple choice, Open answer, or Ordered list
   - **Answers** (for choice questions): The answer options
   - **Expected Answer** (for open answer): The correct answer to evaluate against
   - **Input Restriction** (for open answer): Text, Integer, Decimal, or Fraction
   - **Min/Max Value** (for numeric types): Optional range constraints
   - **Allow Negative** (for numeric types): Whether negative values are accepted
   - **Evaluation Criteria** (for open answer): Optional guidance for AI grading
   - **Retry Limit**: Number of attempts allowed
   - **Hint**: Guidance for incorrect attempts
4. Click **Save**

The quiz appears as a directive in your content (e.g., `::quiz{#123}`). Don't edit this text directly.

### Quiz Fields Explained

| Field | Purpose |
|-------|---------|
| **Description** | Tells the bot when and why to present this quiz. The bot uses this to decide the right moment. |
| **Question** | The actual question text the student sees. Keep it clear and unambiguous. |
| **Question Type** | "Single" for one answer, "Multiple" for selecting all correct answers, "Open answer" for typed responses, "Ordered list" for drag-and-drop sequencing. |
| **Answers** | List of options with correct answers marked. (Single/Multiple choice only) |
| **Expected Answer** | The correct answer the AI evaluates against. (Open answer only) |
| **Input Restriction** | What type of input is allowed: "Text" (any text), "Integer" (whole numbers), "Decimal" (numbers with decimals), or "Fraction" (e.g. 1/3). (Open answer only) |
| **Min/Max Value** | Optional range constraints for numeric input types (Integer, Decimal, Fraction). For fractions, the range applies to the evaluated decimal value. (Open answer only) |
| **Allow Negative** | Whether negative values are accepted. Default: yes. (Open answer with numeric input types only) |
| **Evaluation Criteria** | Optional guidance for the AI on how strictly to evaluate answers. (Open answer only) |
| **Retry Limit** | How many attempts before moving on. Leave empty for unlimited retries. |
| **Hint** | What the bot tells students after an incorrect answer to guide them. |

### Open Answer Input Restrictions

When creating open answer questions, choose the appropriate input restriction:

| Restriction | Use Case | Examples |
|-------------|----------|----------|
| **Text** | Written answers, explanations, names | "photosynthesis", "The mitochondria" |
| **Integer** | Whole number calculations, counts | "42", "100", "-5" |
| **Decimal** | Calculations with decimals, measurements | "3.14", "98.6", "0.5" |
| **Fraction** | Fraction answers, ratios, proportions | "1/3", "2/5", "-3/4" |

The input restriction affects:
- What the student can type (numbers only for Integer/Decimal, fraction format for Fraction)
- How the AI evaluates the answer (fractions are checked for equivalence, e.g. 2/6 = 1/3)
- The placeholder text shown to students
- Whether an on-screen keypad or fraction input is displayed

For numeric types (Integer, Decimal, Fraction), you can also set:
- **Min/Max Value**: Constrain the acceptable range. For fractions, this applies to the evaluated decimal value (e.g. min=0, max=1 means 1/3 is valid but 5/3 is not)
- **Allow Negative**: Toggle whether negative values are accepted (default: yes)

### Open Answer Evaluation

For open answer questions, an AI evaluates student responses by comparing them to your expected answer. The AI:
- Understands equivalent answers (e.g., "8" and "eight" can both be correct)
- Provides a correctness score (0-100%)
- Generates brief, encouraging feedback
- Considers your evaluation criteria if provided

**Evaluation Criteria Examples:**

For exact matches:
```
Accept only the exact numerical value. No units required.
```

For flexible answers:
```
Accept any response that mentions both chloroplasts and sunlight.
Allow for spelling variations.
```

For calculations:
```
Accept answers within 0.1 of the correct value.
The student should show their work is correct even if rounding differs.
```

### Writing Effective Quiz Questions

**Good single/multiple choice question:**
```
Question: What are the three inputs needed for photosynthesis?
Type: Multiple choice
Answers:
  ✓ Sunlight
  ✓ Water
  ✓ Carbon dioxide
  ✗ Oxygen
  ✗ Glucose
```

**Good open answer question (decimal):**
```
Question: Calculate 15% of 80.
Type: Open answer
Input Restriction: Decimal
Expected Answer: 12
Evaluation Criteria: Accept 12, 12.0, or 12.00
```

**Good open answer question (fraction):**
```
Question: What is 1/2 + 1/6?
Type: Open answer
Input Restriction: Fraction
Expected Answer: 2/3
Min Value: 0
Max Value: 1
Allow Negative: No
Evaluation Criteria: Accept equivalent fractions (e.g. 4/6, 8/12)
```

**Tips for choice questions:**
- Be specific and unambiguous
- Avoid "all of the above" or "none of the above"
- Make incorrect options plausible but clearly wrong
- Test understanding, not trick questions

**Tips for open answer questions:**
- Use Integer restriction for whole number answers
- Use Decimal restriction for calculations that may have decimals
- Use Fraction restriction for fraction answers (e.g. 1/3, 2/5) - the system checks equivalence automatically
- Set Min/Max values to constrain numeric ranges when appropriate
- Disable "Allow Negative" for questions where negative answers don't make sense
- Write expected answers that capture the core correct response
- Use evaluation criteria to specify acceptable variations

### Writing Good Descriptions

The description tells the bot when to use the quiz. Be specific:

**Good description:**
```
Use this quiz after explaining the three inputs of photosynthesis
to verify the student can identify them.
```

**Weak description:**
```
Quiz about photosynthesis.
```

### Setting Retry Limits

- **No limit (empty)**: Good for practice and learning
- **1 attempt**: Good for final assessments
- **2-3 attempts**: Balanced approach - allows learning from mistakes

### Writing Helpful Hints

Hints should guide students toward the correct answer without giving it away:

**Good hint:**
```
Think about what the plant needs from its environment.
What does it get from the sun, the soil, and the air?
```

**Poor hint (gives away answer):**
```
The answers are sunlight, water, and carbon dioxide.
```

### Quiz Flow in Lessons

When the bot displays a quiz:

1. The quiz UI appears with the question and answer options
2. The student selects their answer(s) and clicks Submit
3. The system checks correctness automatically
4. The bot receives the result and responds:
   - If correct: Congratulates the student and continues
   - If incorrect with retries left: Uses your hint to encourage another try
   - If incorrect with no retries: Acknowledges and moves on

### Quiz Best Practices

- **Include quizzes generously** — aim for at least 2-3 per resource, one after each major concept
- **Place quizzes after teaching** the relevant content, not before
- **Start with easier questions** and progress to harder ones
- **Vary quiz types** for engagement — mix single choice, multiple choice, open answer, fraction, and ordered list questions
- **Provide meaningful hints** that teach, not just hint
- **Test your quizzes** to ensure the flow feels natural
- **Match question type to content** — use single choice for quick fact checks, open answer for calculations, fraction for math, ordered list for sequencing

## Assessment and Questions

### Crafting Good Questions

Questions help the bot assess understanding. Write questions that:
- Test comprehension, not just recall
- Have clear, unambiguous answers
- Build on the content just covered

**Good question:**
```
Why is photosynthesis important for animals,
even though animals don't perform photosynthesis?
```

**Weaker question:**
```
What is photosynthesis?
```

### Using Hints Effectively

Hints should guide thinking without revealing answers:

**Good hint:**
```
Think about what plants produce that animals need to survive.
```

**Poor hint (gives away answer):**
```
Animals breathe oxygen, which plants produce.
```

### Answer Flexibility

Write answers that allow for reasonable variations in student responses:

```
Answer: Animals depend on photosynthesis because plants
produce oxygen that animals breathe, and plants are the
base of the food chain. Accept any response that mentions
oxygen production or food/energy from plants.
```

## Testing Your Resources

Always test your resources before assigning them to real students. Testing lets you experience the lesson exactly as a student would.

### Quick Test (Direct)

The fastest way to test a resource:

1. Open the resource in the editor
2. Click **Test Resource** in the toolbar (right panel)
3. Select which **Bot** to use (if your organization has multiple bots)
4. Optionally select a **Student** profile to simulate (if not selected, you act as the student)
5. Click **Start Test** to open the player

This opens the lesson in a new tab where you can interact with the AI tutor via voice. Direct tests are lightweight and don't create any courses or enrollments.

**Note:** Direct tests don't save transcripts or progress. Use this for quick content verification.

### Test with Transcript Capture

If you want to review the full transcript of your test session:

1. Create an enrollment by assigning the resource to yourself as a student
2. Go to the course and open the **Enrollments** tab
3. Click the actions menu and select **Test Course**
4. Complete the lesson - the transcript will be saved
5. View the transcript in the student's Activity Log

Test sessions created this way are marked with a "Test" badge and hidden by default in the activity log (use "Hide tests" toggle to show them).

### What to Check

When testing, verify that:

- **The bot introduces the topic clearly** and engages the student
- **Images are displayed at the right moments** in the lesson flow
- **The bot asks appropriate questions** based on your content
- **Questions flow naturally** after each section
- **The difficulty level is appropriate** for your target audience
- **The lesson length** is appropriate (5-10 minutes)
- **Transitions between sections** are smooth

### Common Issues to Fix

- **Image/video descriptions** need more detail for the bot to discuss them effectively
- **Questions** don't make sense in context - reword or reposition them
- **Hints** give away the answer - make them more subtle
- **Sections are too long** - break them into smaller steps
- **Learning objectives** aren't being met - restructure the content

## Exporting and Importing Resources

Resources can be exported as self-contained ZIP files and imported to create new resources. This enables sharing between organizations, backing up content, and migrating resources between environments.

### What's in the ZIP

An exported ZIP contains everything needed to recreate the resource:
- `manifest.json` — resource metadata (name, tags, delivery mode) and media/quiz mappings
- `content.md` — the markdown content with portable placeholder tokens
- `media/` — all image, video, and PDF files
- `quizzes/` — all quiz definitions as JSON files

### Portable Tokens

During export, database-specific IDs are replaced with portable tokens:
- Image references like `![42](/api/v1/images/42/data)` become `![media-001](media://media-001)`
- Quiz references like `::quiz{#28}` become `::quiz{#quiz-001}`

During import, these tokens are mapped to newly created database IDs.

### How to Export

**From the resource editor:** Click **Download ZIP** in the right panel.

**From the resource list:** Click the actions menu and select **Download ZIP**.

**Via MCP:** Use the `export_resource` tool with the resource ID. Returns a base64-encoded ZIP.

### How to Import

**From the resource list:** Click **Import Resource** and select a `.zip` file.

**Via MCP:** Use the `import_resource` tool with base64-encoded ZIP data.

### Cross-Organization Portability

Exported ZIPs are fully self-contained. Videos are stored as binary files in the ZIP and re-uploaded to the target organization's cloud storage on import. Image and quiz references are remapped to new IDs, so the imported resource is completely independent of the original.

## Quick Reference

### Resource Checklist

- [ ] Clear learning objectives stated
- [ ] Content organized with headings
- [ ] Steps are digestible (not too long)
- [ ] **At least 2-3 quizzes** included (one after each major concept)
- [ ] **At least 1-2 images** included (no text-only resources)
- [ ] No section is more than a few sentences without a quiz or image
- [ ] All images have complete metadata
- [ ] All videos have complete metadata
- [ ] Quizzes placed at appropriate checkpoints
- [ ] Questions test understanding
- [ ] Hints guide without revealing answers
- [ ] Total length is 5-10 minutes
- [ ] Tested using the **Test Resource** button

### Media Metadata Checklist

For each image or video:
- [ ] Description explains what it shows
- [ ] Question relates to the visual content
- [ ] Answer is specific but allows variation
- [ ] Hint scaffolds without revealing
- [ ] "Bot can see this image" enabled for complex visuals (images only)

### Quiz Checklist

For each quiz:
- [ ] Description tells bot when to use it
- [ ] Question is clear and unambiguous
- [ ] Question type matches the content (single, multiple, open answer, or ordered list)

For choice questions:
- [ ] Correct answer(s) marked appropriately
- [ ] Wrong answers are plausible but clearly incorrect

For open answer questions:
- [ ] Expected answer captures the correct response
- [ ] Input restriction matches the expected answer type (text/integer/decimal/fraction)
- [ ] Min/Max values set if a numeric range is appropriate
- [ ] Allow Negative set correctly for numeric types
- [ ] Evaluation criteria added if flexibility is needed

For all quizzes:
- [ ] Retry limit set appropriately for the context
- [ ] Hint guides without revealing the answer

### Writing Style Checklist

- [ ] Instructions for the bot, not a script
- [ ] "The student" with they/them pronouns
- [ ] Clear, concise sentences
- [ ] Explicit about what to teach
- [ ] High-level guidance (bot is knowledgeable)
