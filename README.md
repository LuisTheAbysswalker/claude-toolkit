# Claude Toolkit

General-purpose development skills and commands for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## Skills

| Skill | Description |
|-------|-------------|
| **documentation** | Technical documentation following the Diataxis framework (tutorials, how-to guides, reference, explanation) |
| **fastify-best-practices** | Fastify server development: routes, plugins, validation, hooks, security, deployment |
| **node-best-practices** | Node.js with TypeScript: type stripping, async patterns, error handling, streams, testing, performance |
| **typescript-magician** | Advanced TypeScript: generics, conditional types, type guards, utility types, error diagnosis |
| **code-review-expert** | Expert code review of git changes: SOLID violations, security risks, actionable improvements |
| **excalidraw-diagram** | Generate Excalidraw diagrams: flowcharts, mind maps, timelines, with Obsidian/standard/animated modes |
| **mermaid-visualizer** | Transform text into Mermaid diagrams: process flows, sequences, state diagrams, with syntax error prevention |
| **obsidian-canvas-creator** | Create Obsidian Canvas files with MindMap or freeform layouts |

## Commands

| Command | Description |
|---------|-------------|
| `/til [topic]` | Save a TIL (Today I Learned) note to Obsidian knowledge base with Diataxis classification |

## Installation

```
/plugin marketplace add LuisTheAbysswalker/claude-toolkit
/plugin install claude-toolkit
```

Then restart Claude Code to load the skills.

## File Structure

```
claude-toolkit/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── til.md
├── skills/
│   ├── code-review-expert/
│   ├── documentation/
│   ├── excalidraw-diagram/
│   ├── fastify-best-practices/
│   ├── mermaid-visualizer/
│   ├── node-best-practices/
│   ├── obsidian-canvas-creator/
│   └── typescript-magician/
└── README.md
```

## Credits

- Skills `documentation`, `fastify-best-practices`, `node-best-practices`, `typescript-magician` are from [mcollina/skills](https://github.com/mcollina/skills)
- Skills `excalidraw-diagram`, `mermaid-visualizer`, `obsidian-canvas-creator` are from [axtonliu/axton-obsidian-visual-skills](https://github.com/axtonliu/axton-obsidian-visual-skills)
- Skill `code-review-expert` from [sanyuan0704/code-review-expert](https://github.com/sanyuan0704/code-review-expert)

## License

MIT
