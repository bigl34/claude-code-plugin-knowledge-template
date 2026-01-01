# Knowledge Base Index

> Last updated: YYYY-MM-DD

This file tracks what's documented in the knowledge base and identifies gaps.

## Current Coverage

| Topic | File | Status | Notes |
|-------|------|--------|-------|
| Product catalog | `products.md` | Documented | Basic specs included |
| Order fulfillment | `operations.md` | Documented | High-level process |
| Shipping process | `operations.md` | Documented | High-level process |
| Troubleshooting | - | Gap | Add as issues arise |
| Warranty policy | - | Gap | Add when needed |
| Return policy | - | Gap | Add when needed |

## File Organization

Currently using single files. Split into directories when content grows:
- `products.md` -> `products/` directory with per-category files
- `operations.md` -> `operations/` directory with per-process files

## Adding New Knowledge

When documenting new topics:
1. Create file in `knowledge/` directory
2. Use consistent format (see template below)
3. Update this index with coverage status

## Knowledge File Template

```markdown
# [Topic Title]

> Last verified: YYYY-MM-DD

## Overview
Brief summary.

## Key Facts
- Fact 1
- Fact 2

## Details
Detailed information.

## Common Questions
Q: Question?
A: Answer.

## Related
- Other knowledge files
- Agents for live data
```
