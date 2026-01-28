# OpenCode Configuration Learning Project

### Version 1.0

Welcome to the OpenCode Configuration Learning Project! This repository contains comprehensive examples and documentation for learning how to customize OpenCode using **custom agents**, **custom commands**, and **agent skills**.

## 📚 Table of Contents

- [What You'll Learn](#what-youll-learn)
- [Quick Start](#quick-start)
- [Documentation Guides](#documentation-guides)
- [Example Structure](#example-structure)
- [How to Use This Repository](#how-to-use-this-repository)
- [Key Concepts](#key-concepts)
- [Additional Resources](#additional-resources)

---

## 🎯 What You'll Learn

By working through this project, you'll understand:

### **Custom Agents**
- How to create specialized AI agents for different tasks
- Difference between primary agents and subagents
- Configuring tools, permissions, and models per agent
- JSON vs Markdown configuration formats
- Agent-specific skill permissions

### **Custom Commands**
- Creating shortcuts for repetitive tasks
- Using arguments and shell command integration
- File references with the `@` syntax
- When to use commands vs agents
- Command templates and descriptions

### **Agent Skills**
- Creating reusable, on-demand instructions
- Skill discovery and loading mechanisms
- Frontmatter requirements and naming rules
- Permission-based skill access control
- When to use skills vs AGENTS.md instructions

### **Integration Patterns**
- Combining agents, commands, and skills
- Designing cohesive workflow systems
- Real-world examples and best practices

---

## 🚀 Quick Start

### 1. Understand the Basics

Start by reading the core documentation guides in order:

1. **[agents-guide.md](./agents-guide.md)** - Comprehensive guide to custom agents
2. **[commands-guide.md](./commands-guide.md)** - Complete commands documentation
3. **[skills-guide.md](./skills-guide.md)** - Skills system explained

Note: This repository stores examples under `agents/`, `commands/`, and `skills/` for learning. To use them in a real project, copy them into `.opencode/agents/`, `.opencode/commands/`, and `.opencode/skills/`.

### 2. Explore Examples by Difficulty

Navigate to the examples directories based on your experience level:

#### Beginner
- `agents/beginner/` - Simple agent configurations
- `commands/beginner/` - Basic command examples
- `skills/beginner/` - Fundamental skills

#### Intermediate
- `agents/intermediate/` - More complex agent setups
- `commands/intermediate/` - Commands with arguments and shell integration
- `skills/intermediate/` - Skills with metadata and workflows

#### Advanced
- `agents/advanced/` - Complex multi-agent systems
- `commands/advanced/` - Full-featured command automation
- `skills/advanced/` - Advanced skills with permissions

### 3. Study Integration Patterns

Once comfortable with individual concepts, explore:

- **[integration-patterns.md](./examples/integration-patterns.md)** - Design patterns
- **[real-world-workflows.md](./examples/real-world-workflows.md)** - Practical examples
- **[skill-permission-examples.md](./examples/skill-permission-examples.md)** - Permission patterns

---

## 📖 Documentation Guides

### Core Guides

| Guide | Description | Topics Covered |
|-------|-------------|----------------|
| [**agents-guide.md**](./agents-guide.md) | Complete agents documentation | Types, configuration, tools, permissions, models, skill integration |
| [**commands-guide.md**](./commands-guide.md) | Complete commands documentation | Templates, arguments, shell output, file references, options |
| [**skills-guide.md**](./skills-guide.md) | Complete skills documentation | Discovery, SKILL.md format, frontmatter, permissions, naming rules |

### Integration & Patterns

| Guide | Description |
|-------|-------------|
| [**integration-patterns.md**](./examples/integration-patterns.md) | Combining agents, commands & skills effectively |
| [**real-world-workflows.md**](./examples/real-world-workflows.md) | Practical workflow examples |
| [**skill-permission-examples.md**](./examples/skill-permission-examples.md) | Skill permission configurations |

---

## 📂 Example Structure

```
opencode_config/
├── README.md                              # This file
├── agents-guide.md                        # Agents documentation
├── commands-guide.md                      # Commands documentation
├── skills-guide.md                        # Skills documentation
│
├── agents/                                # Agent examples
│   ├── beginner/                          # Simple configurations
│   │   ├── readonly-reviewer.md
│   │   ├── docs-writer.md
│   │   └── simple-config.json
│   ├── intermediate/                      # More complex setups
│   │   ├── test-runner.md
│   │   ├── git-helper.md
│   │   ├── debug-analyzer.md
│   │   └── intermediate-config.json
│   └── advanced/                          # Advanced configurations
│       ├── security-auditor.md
│       ├── multi-model-orchestrator.md
│       ├── task-delegator.md
│       ├── skill-aware-agent.md
│       └── advanced-config.json
│
├── commands/                              # Command examples
│   ├── beginner/                          # Basic commands
│   │   ├── test.md
│   │   ├── format.md
│   │   └── simple-commands.json
│   ├── intermediate/                      # Commands with features
│   │   ├── component-creator.md
│   │   ├── git-review.md
│   │   ├── coverage-analyzer.md
│   │   └── intermediate-commands.json
│   └── advanced/                          # Complex automation
│       ├── pr-workflow.md
│       ├── refactor-assistant.md
│       ├── context-aware-test.md
│       └── advanced-commands.json
│
├── skills/                                # Skill examples
│   ├── beginner/                          # Basic skills
│   │   ├── code-style/SKILL.md
│   │   ├── commit-format/SKILL.md
│   │   └── README.md
│   ├── intermediate/                      # Skills with workflows
│   │   ├── git-release/SKILL.md
│   │   ├── pr-review/SKILL.md
│   │   ├── testing-strategy/SKILL.md
│   │   └── README.md
│   └── advanced/                          # Advanced skills
│       ├── security-audit/SKILL.md
│       ├── performance-optimization/SKILL.md
│       ├── architecture-review/SKILL.md
│       ├── permission-examples/
│       └── README.md
│
└── examples/                              # Integration examples
    ├── real-world-workflows.md
    ├── integration-patterns.md
    └── skill-permission-examples.md
```

---

## 🎓 How to Use This Repository

### For Complete Beginners

1. **Read the guides first**: Start with `agents-guide.md`, then `commands-guide.md`, then `skills-guide.md`
2. **Try beginner examples**: Copy examples from `*/beginner/` directories
3. **Experiment locally**: Modify examples and test in your OpenCode setup
4. **Progress gradually**: Move to intermediate examples when comfortable

### For Intermediate Users

1. **Review specific topics**: Jump to relevant sections in the guides
2. **Study intermediate examples**: See realistic configurations
3. **Combine features**: Try mixing agents, commands, and skills
4. **Check integration patterns**: Learn best practices

### For Advanced Users

1. **Explore advanced examples**: Complex multi-agent systems and workflows
2. **Study permission patterns**: Fine-grained access control
3. **Design workflows**: Use integration-patterns.md as reference
4. **Customize extensively**: Adapt examples to your needs

### Copying Examples to Your Project

To use these examples in your actual OpenCode projects:

#### For Project-Local Configuration
```bash
# Copy to your project's .opencode directory
cp agents/beginner/readonly-reviewer.md /path/to/your-project/.opencode/agents/
cp commands/beginner/test.md /path/to/your-project/.opencode/commands/
cp -r skills/beginner/code-style /path/to/your-project/.opencode/skills/
```

#### Testing Examples
You can test examples directly in this repository by:
1. Running `opencode` from this directory
2. Agents/commands/skills will be discovered if properly placed in `.opencode/`
3. Use `/your-command` or `@your-agent` to test

---

## 💡 Key Concepts

### When to Use What?

#### **AGENTS.md / Instructions**
- ✅ Project-wide context that's always needed
- ✅ Coding standards, architecture overview
- ✅ Conventions that apply to all work
- ❌ NOT for task-specific workflows

#### **Skills**
- ✅ Reusable, on-demand task instructions
- ✅ Specific workflows (releases, reviews, audits)
- ✅ Shareable across projects and teams
- ✅ Can be permission-controlled per agent
- ❌ NOT for always-needed context

#### **Commands**
- ✅ Frequently-run specific tasks
- ✅ Tasks needing arguments or shell integration
- ✅ Quick shortcuts for common operations
- ❌ NOT for complex multi-step workflows requiring back-and-forth

#### **Agents**
- ✅ Specialized personas with specific capabilities
- ✅ Different behavior modes (build vs plan vs review)
- ✅ Task delegation and orchestration
- ✅ Custom tool/permission configurations
- ❌ NOT for one-off commands

### Configuration Precedence

OpenCode loads configuration from multiple locations with this precedence order:

1. **Remote config** (from `.well-known/opencode`) - organizational defaults
2. **Global config** (`~/.config/opencode/opencode.json`) - user preferences
3. **Custom config** (`OPENCODE_CONFIG` env var) - custom overrides
4. **Project config** (`opencode.json` in project) - project-specific settings
5. **`.opencode` directories** - agents, commands, plugins, skills
6. **Inline config** (`OPENCODE_CONFIG_CONTENT` env var) - runtime overrides

This repository focuses on **project-local** configurations (`.opencode/` directories).

---

## 🔗 Additional Resources

### Official Documentation
- [OpenCode Documentation](https://opencode.ai/docs)
- [Configuration Guide](https://opencode.ai/docs/config/)
- [Agents Documentation](https://opencode.ai/docs/agents/)
- [Commands Documentation](https://opencode.ai/docs/commands/)
- [Skills Documentation](https://opencode.ai/docs/skills/)

### Community
- [GitHub Repository](https://github.com/anomalyco/opencode)
- [Discord Community](https://opencode.ai/discord)
- [Report Issues](https://github.com/anomalyco/opencode/issues)

---

## 📝 Contributing to This Learning Project

This is a learning project! Feel free to:
- Add your own example configurations
- Improve documentation with clarifications
- Share interesting patterns you discover
- Create real-world examples from your workflows

---

## 🎉 Getting Started

Ready to start learning? 

1. **Begin with**: [agents-guide.md](./agents-guide.md)
2. **Then explore**: Examples in `agents/beginner/`, `commands/beginner/`, `skills/beginner/`
3. **Practice**: Copy examples and modify them
4. **Advance**: Move to intermediate and advanced examples

Happy learning! 🚀

---

**Last Updated**: January 28, 2026
