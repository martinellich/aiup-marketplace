# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

AIUP Marketplace is a collection of plugins for Claude Code that implement the AI Unified Process (AIUP) methodology.
The repository is structured as a marketplace with a two-layer architecture: a stack-agnostic core and technology-specific plugins.

## Repository Structure

```
aiup-marketplace/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace metadata listing all plugins
├── aiup-core/                    # Stack-agnostic core methodology
│   ├── .claude-plugin/
│   │   └── plugin.json
│   ├── .mcp.json                 # context7, Playwright
│   ├── commands/                 # requirements, entity model, use cases
│   └── skills/                   # requirements-engineer, data-modeler, use-case-specification-writer
├── aiup-vaadin-jooq/             # Vaadin + jOOQ technology stack plugin
│   ├── .claude-plugin/
│   │   └── plugin.json
│   ├── .mcp.json                 # Vaadin, KaribuTesting, jOOQ, JavaDocs
│   ├── commands/                 # database migration, implement, karibu test, playwright test
│   └── skills/                   # karibu-tester, playwright-tester
└── README.md
```

## Plugin Architecture

### Two-Layer Design

- **aiup-core** — Stack-agnostic methodology: from vision to use case specification. Works with any tech stack.
- **aiup-vaadin-jooq** — Stack-specific: implementation and testing for the Vaadin + jOOQ stack. Requires aiup-core.

### Marketplace Configuration

- `marketplace.json` defines the marketplace with owner info and an array of plugins
- Each plugin entry has `name`, `source` (path), and `description`

### Plugin Structure

Each plugin contains:

- `.claude-plugin/plugin.json` - Plugin metadata (name, version, author)
- `.mcp.json` - MCP server configurations for external tools
- `commands/` - Slash command files that define workflow steps
- `skills/` - Auto-activated skills with SKILL.md definitions

## AIUP Workflow

### Core (stack-agnostic)

- **requirements.md** - Generate requirements from vision document
- **entity_model.md** - Create entity model with Mermaid ER diagrams
- **use_case_diagram.md** - Generate PlantUML use case diagrams
- **use_case_spec.md** - Write detailed use case specifications

### Vaadin/jOOQ (stack-specific)

- **flyway_migration.md** - Create Flyway migrations
- **implement.md** - Implement use cases using Vaadin and jOOQ
- **karibu_test.md** - Create Karibu unit tests
- **playwright_test.md** - Create Playwright integration tests
