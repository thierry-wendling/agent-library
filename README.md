# agent-primitives

A curated library of reusable agent tooling—rules, skills, agents, commands, MCP servers, hooks, and related assets—scoped to specific domains. It is designed for use with AI agents and tools like Claude and Cursor.

This repository follows the same component model as [Cursor plugins](https://cursor.com/docs/plugins): distributable bundles can include rules, skills, agents, commands, MCP servers, and hooks. Here those primitives live in one place for versioning, reuse, and packaging into plugins or local workflows.

| Component | Role |
| :--- | :--- |
| **Rules** | Persistent AI guidance and coding standards (e.g. `.mdc` under `rules/`) |
| **Skills** | Specialized agent capabilities for complex tasks (e.g. `skills/*/SKILL.md`; see `skills/engineering-performance-review/`) |
| **Agents** | Custom agent configurations and prompts |
| **Commands** | Agent-executable command files (e.g. `commands/`) |
| **MCP servers** | Model Context Protocol integrations (config and server definitions as added) |
| **Hooks** | Automation scripts triggered by events (as added) |

See the [Plugins](https://cursor.com/docs/plugins) and [Plugins reference](https://cursor.com/docs/reference/plugins) docs for manifest layout (`.cursor-plugin/plugin.json`), testing locally under `~/.cursor/plugins/local`, and marketplace submission.
