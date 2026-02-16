# AIUP Marketplace

A collection of plugins that bring the [AI Unified Process](https://aiup.dev) methodology directly into Claude Code.

## What is AIUP?

The AI Unified Process (AIUP) is a methodology that keeps requirements at the center of your development process. It
provides a structured workflow from vision to implementation, ensuring consistency and traceability throughout your
project.

## Architecture

The marketplace is organized in two layers:

- **aiup-core** — Stack-agnostic methodology (requirements, entity model, use cases). Works with any tech stack.
- **aiup-vaadin-jooq** — Stack-specific implementation and testing for the Vaadin + jOOQ technology stack.

Commands follow the [AIUP phases](https://aiup.dev) (based on the Rational Unified Process):

|                      | Inception       | Elaboration                            | Construction                                                                | Transition |
|----------------------|-----------------|----------------------------------------|-----------------------------------------------------------------------------|------------|
| **aiup-core**        | `/requirements` | `/entity_model`<br>`/use_case_diagram` | `/use_case_spec`                                                            |            |
| **aiup-vaadin-jooq** |                 |                                        | `/flyway_migration`<br>`/implement`<br>`/karibu_test`<br>`/playwright_test` |            |

## Installation

```
/plugin marketplace add martinellich/aiup-marketplace
/plugin enable aiup-core
/plugin enable aiup-vaadin-jooq
```

## Key Concepts

### Marketplace

A **marketplace** is a curated repository that hosts and distributes multiple Claude Code plugins. It acts as a central
hub where plugins can be discovered, installed, and managed. When you add a marketplace to Claude Code, you gain access
to all the plugins it contains. Marketplaces make it easy to share and distribute collections of related plugins.

### Plugin

A **plugin** is a self-contained extension that adds new capabilities to Claude Code. Each plugin can include:

- **Commands** - Slash commands that trigger specific workflows
- **Agents** - Specialized subagents for complex tasks
- **Skills** - Behaviors that Claude can invoke autonomously
- **Hooks** - Event handlers that respond to Claude Code events
- **MCP Servers** - External tools and documentation sources

Plugins are technology-specific and encapsulate everything needed to work with a particular tech stack or methodology.
When enabled, a plugin's components become available in your Claude Code session.

### Command

A **command** is a slash-invoked instruction (e.g., `/my-command`) defined in a Markdown file. Commands contain prompts
that guide Claude through specific tasks, specifying what to do, what context to consider, and what output to produce.
Commands can accept arguments and be chained together to form complete workflows.

### Agent

An **agent** (or subagent) is a specialized AI assistant designed for specific task types. Each agent operates in its
own context window, separate from the main conversation, which preserves context and allows focused expertise. Claude
can delegate tasks to agents automatically, or users can invoke them explicitly. Agents can have restricted tool access
and custom system prompts tailored to their specialty.

### Skill

A **skill** is a specialized behavior that Claude invokes autonomously when it recognizes a matching task. Unlike
commands which require explicit user invocation, skills are triggered by Claude based on task context. Each skill is
defined in a `SKILL.md` file and can include supporting scripts and resources.

### Hook

A **hook** is an event handler that executes automatically in response to Claude Code events. Hooks can respond to
events like tool usage, permission requests, prompt submissions, and session lifecycle events. They enable automation,
validation, and custom workflows triggered by specific actions.

### MCP Server

An **MCP (Model Context Protocol) Server** is an external service that provides Claude with access to specialized tools,
documentation, and capabilities. MCP servers extend what Claude can do by connecting it to external resources like
documentation databases, APIs, browser automation, and other integrations. They start automatically when the plugin is
enabled.

## Available Plugins

### aiup-core

Stack-agnostic core methodology plugin. Use this for any project, regardless of technology stack.

#### Commands

| Command             | Description                                  |
|---------------------|----------------------------------------------|
| `/requirements`     | Generate requirements from vision document   |
| `/entity_model`     | Create entity model with Mermaid ER diagrams |
| `/use_case_diagram` | Generate PlantUML use case diagrams          |
| `/use_case_spec`    | Write detailed use case specifications       |

#### Skills

| Skill                             | Description                                                                  |
|-----------------------------------|------------------------------------------------------------------------------|
| **requirements-engineer**         | Creates requirements catalogs                                                |
| **data-modeler**                  | Creates entity models with Mermaid.js ER diagrams and attribute tables       |
| **use-case-specification-writer** | Creates use case specifications with structured scenarios and business rules |

#### MCP Servers

| Server         | Description                          |
|----------------|--------------------------------------|
| **context7**   | General library documentation lookup |
| **Playwright** | Browser automation for testing       |

### aiup-vaadin-jooq

Stack-specific plugin for Java web application development using the Vaadin + jOOQ technology stack.
Requires **aiup-core** for the methodology commands.

#### Commands

| Command             | Description                               |
|---------------------|-------------------------------------------|
| `/flyway_migration` | Create Flyway database migrations         |
| `/implement`        | Implement use cases using Vaadin and jOOQ |
| `/karibu_test`      | Create Karibu unit tests                  |
| `/playwright_test`  | Create Playwright integration tests       |

#### Skills

| Skill                 | Description                                           |
|-----------------------|-------------------------------------------------------|
| **karibu-tester**     | Creates Karibu unit tests for Vaadin views            |
| **playwright-tester** | Creates Playwright integration tests for Vaadin views |

#### MCP Servers

| Server            | Description                            |
|-------------------|----------------------------------------|
| **Vaadin**        | Access to Vaadin documentation         |
| **KaribuTesting** | Karibu testing framework documentation |
| **jOOQ**          | jOOQ documentation                     |
| **JavaDocs**      | Java API documentation                 |

## Learn More

Visit [aiup.dev](https://aiup.dev) to learn more about the AI Unified Process methodology.
