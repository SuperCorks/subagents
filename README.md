# Subagents

Specialized AI agent definitions for multi-agent workflows. Each `.agent.md` file defines an agent with specific responsibilities, capabilities, and instructions.

## Installation

Use the `@supercorks/skills-installer` CLI:

Installer repository: [supercorks/agent-skills-installer](https://github.com/supercorks/agent-skills-installer)

```bash
npx @supercorks/skills-installer
```

Select the subagents you want to install. They will be placed in your chosen directory (e.g., `.github/agents/` or `.claude/agents/`).

## Available Agents

### Workflow Agents

| Agent | Description |
|-------|-------------|
| **Orchestrator** | Coordinates multi-agent workflows, enforces quality gates, and ensures agents run in the correct sequence |
| **Architect** | Designs implementation plans and technical architecture before any code is written |
| **Developer** | Implements solutions defined by the Architect while adhering to project standards |
| **Tester** | Ensures correctness and reliability by designing, reviewing, and executing tests |
| **Code Quality** | Reviews implementation for maintainability, consistency, and standards compliance |
| **Documentation** | Updates README, changelogs, and feature documentation |
| **Git** | Manages branch state, validates repositories, and creates pull requests |

### Specialist Agents

| Agent | Description |
|-------|-------------|
| **Code Simplifier** | Refactoring specialist that reduces complexity while preserving functionality |
| **Codebase Explorer** | Read-only analyst that maps architecture and traces execution paths |
| **Security Auditor** | Red team agent that identifies vulnerabilities using OWASP patterns |
| **UX Reviewer** | Design-focused QA for aesthetics, usability, and accessibility |

## Standard Workflow

The recommended workflow orchestrated by the **Orchestrator** agent:

```
Architect → Git (pre) → Developer → Tester → Code Quality → Docs → Git (post)
```

### Workflow Stages

1. **Architect** - Produces implementation plan, presents to user for approval
2. **Git (pre)** - Validates branch state, ensures feature branches are ready
3. **Developer** - Implements the approved plan, runs lint and tests
4. **Tester** - Verifies test coverage, all tests must pass
5. **Code Quality** - Reviews for maintainability, zero errors/warnings required
6. **Documentation** - Updates relevant docs to reflect changes
7. **Git (post)** - Creates PRs for affected repositories

### Quality Gates

The workflow enforces gates between stages:
- **Architecture Gate**: Plan must be approved by user before development
- **Git Gate (Pre)**: Must be on correct feature branch, up-to-date with develop
- **Implementation Gate**: Code compiles, linting passes, tests run
- **Testing Gate**: All tests must pass (zero tolerance policy)
- **Code Quality Gate**: Zero errors and zero warnings
- **Documentation Gate**: User-facing changes documented
- **Git Gate (Post)**: PRs created with semantic commit titles

## Agent File Format

Each agent uses the `.agent.md` format with YAML frontmatter:

```markdown
```chatagent
---
name: Agent Name
description: Brief description of the agent's purpose
tools: ['tool1', 'tool2', 'tool3']
---
```

## Instructions

Agent-specific instructions here...
```

### Frontmatter Properties

| Property | Description |
|----------|-------------|
| `name` | Display name of the agent |
| `description` | Brief summary shown in agent selection |
| `tools` | Array of tool capabilities the agent can use |

## License

MIT
