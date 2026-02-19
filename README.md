# TutorBot Plugin for Claude Code

A Claude Code plugin for creating educational resources on the [TutorBot](https://tornadolabs.net) platform. This plugin gives Claude the knowledge and tools to author resources, upload images, create quizzes, and organize courses - all delivered by AI bots to students via voice.

## What This Plugin Provides

- **MCP Server Connection**: Connects to the TutorBot API for resource management (create/update resources, upload images, create quizzes, manage courses)
- **Authoring Skill**: The `create-resource` skill teaches Claude how to structure educational resources with proper markdown syntax for embedding images and quizzes

## Installation

### Via Marketplace URL

In Claude Code:
```
/plugin marketplace add dselman/tutorbot-plugin
/plugin install tutorbot@tutorbot-marketplace
```

### Via Direct Install

```
/plugin install dselman/tutorbot-plugin
```

## Usage

Once installed, invoke the skill:
```
/tutorbot:create-resource
```

Claude will guide you through creating a resource by asking about the topic, audience, delivery mode, and learning objectives. It then uses the MCP tools to create the resource, upload images, create quizzes, and embed everything into the content.

## Key Concepts

- **Resource**: A self-contained learning unit with markdown content, images, and quizzes
- **Course**: A collection of resources organized for students to complete
- **Delivery Mode**: How the resource is presented - `conversation` (two-way voice) or `presentation` (one-way narration)
- **Quiz**: Structured assessment with single choice, multiple choice, or free text questions

## MCP Tools Available

| Tool | Description |
|------|-------------|
| `list_resources` | List resources with optional tag filtering |
| `get_resource` | Fetch a resource by ID |
| `create_resource` | Create a new resource |
| `update_resource` | Update an existing resource |
| `create_image` | Upload an image (base64) to a resource |
| `upload_image_from_url` | Upload an image from URL to a resource |
| `create_quiz` | Create a quiz for a resource |
| `list_tags` | List available tags |
| `create_course` | Create a course |
| `list_courses` | List courses |
| `add_resource_to_course` | Add a resource to a course |

## Authentication

The MCP server uses OAuth 2.1 with Auth0. When you first use a tool, you'll be prompted to authenticate with your TutorBot account.

## License

MIT
