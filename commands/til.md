---
description: Save a TIL (Today I Learned) note to Obsidian knowledge base
allowed-tools: Write, Read, Glob, Skill
argument-hint: [topic]
---

Save a knowledge note to the TIL vault at the path specified by the `TIL_VAULT_PATH` environment variable. If not set, default to `~/Github/til`.

## Instructions

### Step 1 — Identify the knowledge point

Review the current conversation to identify the knowledge point to save. If the user provides a topic via `$1`, focus on that topic. Otherwise, identify the most recent technical Q&A in the conversation.

### Step 2 — Determine the note type (Diataxis)

Based on the conversation content, classify the note into one of these types:

| User signal in conversation | Note type | Writing style |
|---|---|---|
| "Why..." / "internals" / "how does X work" / understanding principles | **explanation** | Focus on *why* and *how it works internally*. Structure: Context → Core concept → Trade-offs. Use diagrams/tables to illustrate. |
| "How to..." / "configure" / solving a specific problem | **how-to** | Focus on *steps to solve*. Structure: Goal → Prerequisites → Numbered steps → Expected result. Skip conceptual background. |
| "Parameters" / "API" / "options" / looking up specific facts | **reference** | Focus on *facts*. Structure: Consistent format per entry (name → type → default → description → example). Terse, scannable. |
| "Teach me..." / "walk me through" / learning something new | **tutorial** | Focus on *learning by doing*. Structure: Goal → Step-by-step with verifiable results. Minimise explanation, maximise doing. |

### Step 3 — Determine the category folder

Choose the best folder:
- `typescript/` - Type system, generics, compiler
- `node-js/` - Runtime, modules, performance, npm packages (BullMQ, ioredis, etc.)
- `fastify/` - Routes, plugins, lifecycle
- `react/` - Components, hooks, state management
- `claude-sdk/` - Agent SDK, MCP, tool calls
- `e2b/` - Sandbox, filesystem, runtime
- `multiplayer/` - MQTT, real-time communication, sync
- `architecture/` - Design patterns, system design
- `devops/` - K8s, Docker, CI/CD
- `redis/` - Redis data structures, commands, patterns
- If none fit, create a new category folder

### Step 4 — Check for duplicates

Use Glob to search for existing notes on the same topic. If one exists, update it instead of creating a duplicate.

### Step 5 — Write the note

Write a markdown file with this structure:

```markdown
---
type: explanation | how-to | reference | tutorial
tags: [category, specific-tech, ...]
created: YYYY-MM-DD
---

# Title

Content here...

## Related
- [[other-note-name]] - brief description (if relevant notes exist)
```

**Writing rules:**
- Filename: kebab-case summary (e.g., `bullmq-internals.md`)
- One concept per note
- Use tables, code blocks, and lists for clarity
- Write in the same language the user used in the conversation
- Follow the writing style for the note type (Step 2)
- Add `[[wiki links]]` to related existing notes when applicable — use Glob to find them
- Validation: apply the Diataxis check for the note type:
  - **explanation**: Does the reader understand the *why*, not just the *what*?
  - **how-to**: Can an experienced user complete the task without confusion?
  - **reference**: Can the user find a specific fact in under 30 seconds?
  - **tutorial**: Can a beginner complete it end-to-end?

### Step 6 — Generate visual diagram

If the note involves processes, flows, state machines, or system architecture, generate a visual diagram to accompany the note. Choose the best format:

| Content type | Skill to use | Best for |
|---|---|---|
| Flowcharts, state machines, sequences, system flows | `obsidian-visual-skills:mermaid-visualizer` | Process flows, lifecycle diagrams, request sequences |
| Hand-drawn style diagrams, architectural overviews | `obsidian-visual-skills:excalidraw-diagram` | Architecture diagrams, concept maps, free-form explanations |
| Mind maps, spatial knowledge organization | `obsidian-visual-skills:obsidian-canvas-creator` | Topic overviews, knowledge maps with multiple connected concepts |

**Rules:**
- Save the diagram in the same category folder as the note
- Use a matching filename with a suffix (e.g., `bullmq-internals-flow.md` for a mermaid diagram alongside `bullmq-internals.md`)
- Link the diagram from the note using `[[wiki links]]`
- Skip diagram generation if the note is a simple reference or how-to with no meaningful flow to visualize

### Step 7 — Confirm

Tell the user: the file path, the note type, any diagrams generated, and any related notes that were linked.
