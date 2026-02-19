# Teacher Guide

This guide covers how to create resources, build courses, manage student enrollments, and monitor progress.

## Your Dashboard

Your teacher dashboard provides quick access to common tasks and recent activity.

### Quick Actions

The dashboard includes shortcuts to:
- **Create Resource**: Start building new learning content
- **Create Course**: Set up a new course structure
- **Invite Student**: Add a new student to the platform

### Recent Activity

Your dashboard displays:
- **Recently Updated Resources**: Your latest resource changes with tags and update times
- **Recently Updated Courses**: Your latest course changes with progression types
- **Recent Student Activity**: Student completions showing scores and timestamps

## Managing Resources

Resources are individual learning units that students complete. Navigate to **Teaching > Resources** to manage them.

### Creating a Resource

1. Click **New Resource**
2. Enter a **Name** for the resource
3. Select a **Delivery Mode**:
   - **Conversation**: Two-way voice interaction (requires student microphone)
   - **Presentation**: One-way narration (student clicks to advance)
4. Add **Content** using the rich text editor
5. Apply **Tags** to organize the resource
6. Click **Save**

### Choosing a Delivery Mode

**Conversation Mode** is best for:
- Interactive tutoring with Q&A
- Personalized learning experiences
- Building on student responses
- Lessons that benefit from discussion

**Presentation Mode** is best for:
- Lecture-style content delivery
- Students who can't use a microphone
- Information-heavy content
- Consistent delivery across all students

### Resource List Features

The resource list provides:
- **Search**: Find resources by name
- **Tag Filter**: Filter by one or more tags
- **Sorting**: Sort by name, update date, or other fields
- **Export**: Download the list as CSV or Excel

### Resource Actions

For each resource, you can:
- **Edit**: Click the resource name to modify it
- **Test Resource**: Preview the resource with an AI tutor before assigning
- **Assign to Student**: Quickly assign this resource to a specific student
- **Delete**: Remove the resource (use with caution)

### Testing a Resource

Before assigning a resource to students, you can test it to verify the AI tutor delivers the content correctly:

1. Open the resource editor
2. Click **Test Resource** in the toolbar
3. Select which **Bot** to use for testing (if your organization has multiple bots)
4. Optionally select a **Student** profile to simulate (defaults to yourself)
5. Click **Start Test** to open the player

During testing, you'll experience the lesson exactly as a student would - including voice interaction with the AI tutor. Test sessions are automatically marked as "tests" and won't appear in the student's activity log by default.

**What to check when testing:**
- Does the bot introduce the topic clearly?
- Are images displayed at the right moments?
- Are quizzes presented at appropriate points in the lesson?
- Does the bot ask appropriate questions?
- Is the difficulty level appropriate?
- Does the lesson flow naturally?

## Managing Courses

Courses are collections of resources organized for students to complete. Navigate to **Teaching > Courses**.

### Creating a Course

1. Click **New Course**
2. Enter a **Name** and **Description**
3. Select a default **Bot** for interactive lessons
4. Choose a **Progression Type**:
   - **Flexible**: Students complete resources in any order
   - **Sequential**: Students must follow your specified order
   - **Random**: The system selects the next resource
5. Apply **Tags** for organization
6. Click **Save**

### Adding Resources to a Course

1. Open the course details page
2. Click **Add Resource**
3. Select resources from your library
4. **Drag and drop** resources to set the order (important for sequential courses)

### Overriding the Bot for Specific Resources

By default, all resources in a course use the course's default bot. However, you can override the bot for individual resources if needed:

1. Open the course details page
2. In the **Resources** list, find the resource you want to modify
3. Use the **Bot dropdown** on the right side of the resource row
4. Select a specific bot, or choose "Course default" to use the course's bot

This is useful when:
- A specific resource topic requires a different AI persona
- You want to test content with different bots
- Certain resources benefit from a bot with specialized knowledge

### Open Enrollment Courses

Open enrollment allows students to self-enroll in courses without teacher intervention. This is ideal for self-paced learning, large-scale courses, or when you want students to browse and join courses independently.

#### Enabling Open Enrollment

1. Create or edit a course
2. Scroll to the **Open Enrollment** section
3. Toggle on **Enable Open Enrollment**
4. Select a **Default Teacher** (required) - this teacher will be assigned to all self-enrolled students
5. Optionally set **Maximum Enrollments** to limit capacity (leave empty for unlimited)
6. Save the course

#### How Open Enrollment Works

When open enrollment is enabled:
- The course appears in the **Course Catalog** on the student dashboard
- Students can click "Enroll Now" to join the course immediately
- The selected default teacher is automatically assigned to manage these enrollments
- You receive an email notification each time a student self-enrolls
- If a maximum enrollment limit is set, the course shows as "Full" when capacity is reached

#### Default Teacher Requirements

The default teacher field is required for open enrollment courses because:
- Self-enrolled students need a teacher contact for questions
- Someone needs to monitor progress and provide support
- Enrollment notifications are sent to this teacher

You can select yourself or another teacher in your organization as the default teacher.

#### Capacity Limits

If you set a maximum enrollment limit:
- Students can only enroll if spaces are available
- The Course Catalog shows remaining capacity (e.g., "8/10 enrolled")
- Once full, the "Enroll Now" button is disabled and shows "Course Full"
- You can increase the limit later to allow more enrollments

#### Managing Self-Enrolled Students

Self-enrolled students appear in your normal enrollment list. You can:
- View their progress in the course details
- Contact them through the platform
- Pause or remove their enrollment if needed
- Change their assigned teacher to a different person

#### Paid Courses

If your organization has Stripe Connect set up (see Admin Guide), you can create paid courses:

1. Enable **Open Enrollment** (required for paid courses)
2. Toggle on **Paid Course**
3. Select a **Currency** from the dropdown (GBP, USD, EUR, and others)
4. Enter the **Price** as a decimal amount (e.g., 29.99)
5. Save the course

Students will see the price with the appropriate currency symbol (£, $, €, etc.) in the Course Catalog. Clicking "Purchase Course" takes them through secure Stripe checkout, and they're automatically enrolled after payment.

**Note**: Paid course setup requires your organization to have completed Stripe Connect onboarding. Contact your administrator if the Paid Course option is disabled.

#### Teacher Preview Mode

Before releasing a course to students, you can enable **Teacher Preview Only** mode to test everything—including the purchase flow for paid courses—without students seeing the course in their catalog.

**Enabling Teacher Preview:**

1. Create or edit a course with Open Enrollment enabled
2. Toggle on **Teacher Preview Only**
3. Save the course

**How Teacher Preview Works:**

- The course only appears in the Course Catalog for users with the **teacher role**
- Students cannot see or enroll in the course
- A yellow "Teacher Preview" badge appears on the course card and in course lists
- Teachers can test the full enrollment process, including payment for paid courses
- Once testing is complete, toggle off Teacher Preview to release the course to students

**When to use Teacher Preview:**

- Testing a new course before public release
- Verifying paid course pricing and checkout flow
- Reviewing content organization and progression
- Training other teachers on course content before student rollout

**Tip:** Combine Teacher Preview with the Test Course feature to experience the course exactly as students will, while keeping it hidden from the student catalog.

### Managing Course Enrollments

In the course details, the **Enrollments** tab shows all enrolled students:
- Student name and email
- Assigned teacher
- Enrollment status
- Start and completion dates

For each enrollment, you can:
- **Change status**: Set to Active, Paused, or Completed
- **Play**: Open the enrollment in player mode (student view)
- **Test Course**: Open in test mode for verification
- **Copy URL**: Get the player URL for external sharing
- **Delete**: Remove the enrollment

### Testing a Course

You can test a course enrollment to experience it as a student would:

1. Go to the course details page
2. Open the **Enrollments** tab
3. Find the enrollment and click the actions menu (three dots)
4. Select **Test Course**

This opens the player in test mode where you can:
- Complete lessons and interact with the AI tutor
- See how resources flow in sequence (for sequential courses)
- Verify the overall learning experience

**Test mode differences:**
- Sessions are marked as "tests" in the activity log
- Progress doesn't affect the student's actual completion status
- Test sessions are hidden by default when viewing student activity
- Transcripts are still captured for review

**Tip:** Always test a course before sharing the enrollment URL with students to ensure the content flows correctly and the AI tutor behaves as expected.

## Managing Students

Navigate to **Teaching > Students** to view and manage your students.

### Inviting Students

1. Click **Invite Student**
2. Enter the student's email address
3. The system sends an invitation

Students appear with invitation status:
- **Pending**: Invitation sent, waiting for acceptance
- **Accepted**: Student has activated their account
- **Legacy**: Pre-existing user from before the invitation system

### Student Consent

If your organization has configured a consent form (e.g., for parental consent), you'll see a **Consent** column in the student list with these statuses:

| Status | Description |
|--------|-------------|
| **N/A** | Consent not required for this student |
| **Pending** | Student hasn't submitted the consent form yet |
| **Submitted** | Student has submitted the form, awaiting verification |
| **Verified** | Consent verified, student has full access |

**Managing consent:**

From the student list action menu (three dots), you can:

- **Verify Consent** (for Submitted students): After confirming you've received the consent form, verify the student. They'll receive a welcome email with a sign-in link.

- **Resend Welcome Email** (for Verified students): If a student didn't receive or lost their welcome email, resend it.

- **Revoke Consent** (for Submitted or Verified students): If consent needs to be withdrawn, this blocks the student's access until they re-submit and are verified again.

**Note**: Students cannot access their dashboard until their consent is verified. Contact your administrator if you need help with consent form configuration.

### Student Details

Click on a student to view their profile:
- Overall progress percentage
- Contact information and join date
- Enrollments with individual progress
- Progress and score charts by course
- Complete activity log

### Assigning Resources

You can assign resources to students in several ways:

**From the Resource List:**
1. Click the actions menu on a resource
2. Select **Assign to Student**
3. Choose the student, teacher, and bot
4. Click **Assign**

**From the Student Details:**
1. Open the student's profile
2. Use the enrollment options to add new courses or resources

## Managing Enrollments

Navigate to **Teaching > Enrollments** to view and manage all student enrollments across your courses.

### Enrollment List Features

The enrollments page provides a comprehensive view of all enrollments with:
- **Student Filter**: Find enrollments for a specific student
- **Teacher Filter**: Filter by assigned teacher
- **Status Filter**: Show only Active, Paused, or Completed enrollments
- **Quick Search**: Search across all fields
- **Export**: Download the list as CSV or Excel

### Enrollment Information

Each enrollment shows:
- **Course**: The course name (click to view course details)
- **Student**: Student name and email (click to view student profile)
- **Teacher**: The assigned teacher
- **Status**: Active, Paused, or Completed
- **Started**: When the enrollment began
- **Updated**: Last activity date

### Enrollment Actions

Use the actions menu (three dots) on each enrollment to:
- **View Student**: Open the student's profile page
- **View Course**: Open the course details page
- **Pause**: Temporarily pause an active enrollment (student cannot continue until resumed)
- **Resume**: Reactivate a paused enrollment
- **Delete**: Permanently remove the enrollment (use with caution)

### Common Use Cases

**Finding a student's enrollments:**
1. Use the Student filter dropdown
2. Select the student's name
3. View all their enrollments across courses

**Managing paused enrollments:**
1. Set Status filter to "Paused"
2. Review which students are paused
3. Use Resume action to reactivate as needed

**Checking enrollment status for a course:**
1. Navigate to the course details page, or
2. Use the Enrollments page and filter by searching the course name

## Monitoring Progress

### Activity Feed

Your dashboard shows recent student activity including:
- Student name
- Course and resource completed
- Score achieved (color-coded by performance)
- Completion timestamp

### Student Progress

In student details, you can see:
- Per-course progress breakdown
- Individual resource completion status
- Attempt counts and scores
- Completion dates

### Enrollment Details

Expand an enrollment row to see per-resource information:
- Which resources are completed, in progress, or locked
- Number of attempts on each resource
- Latest scores
- Completion timestamps

### Session Transcripts

Every conversation between a student and the AI tutor is automatically transcribed and saved. This gives you valuable insight into how students engage with your content and how the AI delivers your lessons.

**What is transcription?**

During a lesson, both the student and AI tutor communicate via voice. The platform uses speech recognition to convert these spoken conversations into text, creating a complete written record of the session. This transcript is saved alongside other session data like scores and summaries.

**Why transcripts are valuable:**

- **Understand student struggles**: See exactly where students had difficulty or asked for clarification
- **Evaluate AI delivery**: Review how the bot presented your content and whether it stayed on topic
- **Identify content improvements**: Spot areas where your resource content could be clearer
- **Support student follow-up**: Reference specific moments when discussing progress with students
- **Quality assurance**: Verify that the AI tutor is behaving appropriately

**Viewing Transcripts:**

1. Navigate to a student's profile page
2. Scroll to the **Activity Log** section
3. Look for the chat icon in the **Transcript** column
4. Click the icon to open the transcript viewer

**Transcript Contents:**

The transcript viewer displays the conversation in a chat-style format:
- **Student messages** (right side): What the student said, transcribed from their speech
- **Bot messages** (left side): What the AI tutor said, transcribed from its speech
- **Images shown** (center): Thumbnails of images displayed during the lesson with timestamps

Each message shows the timestamp so you can follow the conversation flow.

**Filtering the Activity Log:**

- Use the **Hide tests** toggle to exclude test sessions (on by default)
- Test sessions are marked with a blue "Test" badge when visible
- Only sessions with meaningful data (score, summary, or transcript) are shown

**Note:** Transcripts are only visible to teachers and administrators, not to students.

## Working with Bots

Bots are AI tutors that guide students through interactive lessons. Only administrators can create and configure bots.

When assigning resources or creating enrollments:
1. Choose a bot whose teaching style matches your content
2. Consider the bot's subject matter expertise
3. Ask your admin about available bots and their specializations

Contact your admin if you need a new bot created for specific content.

For details on how bots deliver lessons and how to write effective content for AI delivery, see the **Resource Guide**.

## Working with Images in Resources

**Every resource should include at least 1-2 images.** Images are essential for engagement — they break up text, illustrate concepts, and give the bot concrete material to discuss with the student. A resource with no images will feel text-heavy and lecture-like, even with great written content.

When creating resources, you can add images to enhance learning. By default, the AI bot relies on text descriptions you provide for each image.

### Bot Vision Feature

For images where visual details matter, you can enable **"Bot can see this image"** in the image settings panel. This sends the actual image to the AI when it's displayed to the student, allowing the bot to see and discuss what's in the image.

**Best practices:**
- Enable Bot Vision for diagrams, charts, and complex visuals
- Leave it off for decorative images or simple visuals with good descriptions
- Always provide text descriptions even with Bot Vision enabled
- Note: Bot Vision only works for images, not videos

For comprehensive guidance on writing effective content and working with media, see the **Resource Guide**.

## Working with Quizzes in Resources

**Quizzes are essential for interactive, engaging lessons.** Aim for **at least 2-3 quizzes per resource**, placed after each major concept. Quizzes keep students actively thinking and participating — without them, lessons feel passive and text-heavy. Use a variety of quiz types (single choice, multiple choice, free text, fraction) to keep things interesting.

The platform supports three question types: single choice, multiple choice, and free text.

### Quiz Question Types

**Single Choice**: Student selects one answer from a list
- Best for clear-cut facts with one correct answer

**Multiple Choice**: Student selects all correct answers from a list
- Best for "select all that apply" questions

**Free Text**: Student types their answer, evaluated by AI
- Best for numerical answers, calculations, fractions, or short written responses
- Supports input restrictions: Text, Integer, Decimal, or Fraction
- Numeric types (Integer, Decimal, Fraction) show an on-screen keypad instead of the native keyboard
- Fraction input shows a visual numerator/denominator entry
- Optional min/max range and allow-negative constraints for numeric types

### How Quizzes Work

When the AI tutor displays a quiz during a lesson:
1. The student sees the question (with options or a text input)
2. The student selects their answer(s) or types their response
3. The system checks correctness (AI evaluates free text answers)
4. The bot receives feedback about whether the student answered correctly
5. If incorrect and retries are allowed, the bot can encourage another attempt using the hint you provided

### Creating Quizzes

1. Open a resource in the editor
2. Click the **Quiz** button in the toolbar
3. Fill in the quiz details:
   - **Description**: Tells the bot when to use this quiz
   - **Question**: The question text shown to students
   - **Question Type**: Single choice, Multiple choice, or Free text
   - **Answers**: The answer options with correct answers marked (choice questions)
   - **Expected Answer**: The correct answer to evaluate against (free text)
   - **Input Restriction**: Text, Integer, Decimal, or Fraction (free text)
   - **Min/Max Value**: Optional range constraints for numeric types (free text)
   - **Allow Negative**: Whether negative values are accepted (free text, numeric types)
   - **Evaluation Criteria**: Optional guidance for AI grading (free text)
   - **Retry Limit**: How many attempts students get (leave empty for unlimited)
   - **Hint**: Guidance for the bot to help struggling students
4. Click **Save**

### Quiz vs. Conversational Questions

Use **quizzes** when you want:
- Structured assessment with automatic correctness checking
- Retry attempts with hints
- Clear right/wrong feedback
- Numerical, calculation-based, or fraction questions (free text)

Use **conversational questions** (in your content) when you want:
- Open-ended discussion
- The bot to evaluate complex free-form responses
- More natural dialogue flow

### Viewing Quiz Results

Quiz responses are captured in session transcripts. When viewing a transcript:
- Quiz displays show when the bot presented each quiz
- Quiz responses show what the student selected/typed and whether it was correct
- Free text responses include the AI's feedback and score
- You can see how many attempts were needed

For comprehensive guidance on creating effective quizzes, see the **Resource Guide**.

## Tips for Effective Teaching

1. **Use clear resource names** that describe what students will learn
2. **Apply tags consistently** to make resources easy to find
3. **Choose the right delivery mode** - conversation for interactive lessons, presentation for lecture-style content
4. **Choose the right progression type** - sequential for prerequisite content, flexible for independent topics
5. **Include plenty of quizzes** - aim for at least 2-3 per resource. Quizzes are the primary way students actively engage with content. Lessons without enough quizzes feel passive and text-heavy.
6. **Include images in every resource** - aim for at least 1-2 images. Visuals break up text, illustrate concepts, and keep students interested. A text-only resource is almost always too dry.
7. **Avoid text-heavy sections** - if any section is more than a few sentences without a quiz or image, add interactivity
8. **Mix quiz types for variety** - use single choice for quick checks, multiple choice for "select all", free text for calculations, and fraction for math. Variety keeps students engaged.
9. **Monitor the activity feed** to identify students who may need help
10. **Test resources and courses** before assigning to students to verify the AI delivers content correctly
11. **Review session transcripts** periodically to understand how students interact with your content
12. **Enable Bot Vision** for images where the AI needs to see visual details
13. **Provide helpful quiz hints** that guide students without giving away the answer
