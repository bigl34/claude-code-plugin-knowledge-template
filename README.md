# Claude Code Plugin: Knowledge Base Template

A Claude Code plugin template for creating business knowledge bases. Use this to give Claude Code access to your company's products, processes, policies, and troubleshooting information.

## Features

- **Knowledge Files**: Structured markdown files with your business information
- **Self-Correction Workflow**: Agent logs corrections to PENDING.md for user review
- **Confidence Levels**: Agent expresses certainty based on documentation coverage
- **Boundary Awareness**: Knows when to defer to other agents for live data

## Installation

### 1. Clone the Template

```bash
git clone https://github.com/bigl34/claude-code-plugin-knowledge-template.git \
  ~/.claude/plugins/local-marketplace/my-company-knowledge
```

### 2. Customize for Your Business

1. **Rename the plugin**: Update `.claude-plugin/plugin.json` with your business name
2. **Edit the agent**: Update `agents/business-knowledge.md` with your context
3. **Add your knowledge**: Replace example content in `knowledge/` files

### 3. Register with Claude Code

```bash
/plugins install my-company-knowledge
```

## Directory Structure

```
.
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── agents/
│   ├── business-knowledge.md # Agent definition
│   ├── LEARNINGS.md          # Applied corrections
│   └── PENDING.md            # Corrections awaiting review
└── knowledge/
    ├── index.md              # Coverage tracker
    ├── products.md           # Product information
    └── operations.md         # Business processes
```

## Knowledge File Format

Each knowledge file follows a consistent structure:

```markdown
# Topic Title

> Last verified: YYYY-MM-DD

## Overview
Brief summary of the topic.

## Key Facts
- Important point 1
- Important point 2

## Details
Detailed information organized by subtopic.

## Common Questions
Q: Frequently asked question?
A: Clear answer.

## Related
- Links to other knowledge files
- References to agents for live data
```

## Self-Correction Workflow

When the agent receives a correction:

1. **Acknowledges** the correction
2. **Uses correct info** for the rest of the conversation
3. **Logs to PENDING.md** for user review
4. **User approves** corrections, then applies to knowledge files and LEARNINGS.md

This prevents hallucinations from being persisted while ensuring corrections are captured.

## Customization Guide

### Adding New Topics

1. Create a new `.md` file in `knowledge/`
2. Use the standard format (see above)
3. Update `knowledge/index.md` with coverage status

### Integrating with Other Agents

Add deferral rules to the agent definition:

```markdown
## When to Defer to Other Agents

| Question Type | Defer To |
|---------------|----------|
| "What's the status of order #1234?" | shopify-order-manager |
| "How many widgets in stock?" | inflow-inventory-manager |
```

### Knowledge Categories to Consider

- **Products**: Specs, features, pricing, troubleshooting
- **Operations**: Fulfillment, shipping, returns, support
- **Policies**: Warranty, refunds, terms of service
- **Technical**: Integration docs, API references
- **Brand**: Voice, guidelines, messaging

## Example Usage

Once installed, invoke the agent:

```
User: What products do we sell?
Claude: [Reads knowledge/products.md and provides answer]

User: Actually, we discontinued the Widget Pro last month.
Claude: Thank you for the correction. I'll use this information and log it to PENDING.md for review.
```

## License

MIT
