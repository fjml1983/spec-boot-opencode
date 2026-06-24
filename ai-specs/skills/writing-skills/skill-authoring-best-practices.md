# Skill Authoring Best Practices

This guide provides OpenCode-first patterns for writing effective skills that agents can discover and apply reliably.

## Core Principles

### Be concise

A skill shares context budget with:
- System instructions
- Conversation history
- Other skill metadata
- The current user request

Keep SKILL.md focused on what is needed to execute the workflow correctly.

### Use progressive disclosure

Keep SKILL.md as the execution guide, then reference additional files only when needed:
- Reference docs (APIs, schemas, command catalogs)
- Large examples
- Reusable scripts

### Match constraint level to task risk

- High freedom: when multiple approaches are valid (exploration, review)
- Medium freedom: when a preferred pattern exists (templates, pseudocode)
- Low freedom: when operations are fragile (migrations, destructive changes)

### Test across your actual environments

Validate skills in the environments and agent setups your team actually uses.

## Frontmatter Quality

Use clear metadata:
- name: short, specific, searchable
- description: starts with "Use when..." and focuses on trigger conditions

Good description traits:
- Mentions symptoms and contexts
- Includes domain keywords users will naturally use
- Avoids workflow summary that could bypass the SKILL.md body

## Discovery Optimization

### Use trigger-rich descriptions

Include terms agents can match:
- Symptoms: flaky, hanging, race condition, rollback needed
- Artifacts: tasks.md, spec.md, migration, report
- Actions: verify, audit, sync, archive

### Name skills for intent

Prefer explicit names that indicate action and scope.

### Add keyword coverage in body text

Use common synonyms and tool names so matching remains robust.

## Structure Recommendations

Suggested layout:
1. Overview
2. When to Use
3. Workflow
4. Guardrails
5. Output Contract
6. Examples

Keep examples realistic and short.

## Reliability Patterns

### Plan-validate-execute loop

1. Plan steps
2. Validate assumptions and dependencies
3. Execute incrementally
4. Re-validate outcomes

### Prefer deterministic scripts for fragile tasks

If a workflow is repeatable and sensitive, provide a script instead of free-form instructions.

### Make failure handling explicit

For each critical step, define:
- Expected outcome
- Failure signal
- Recovery action

## Common Mistakes

- Vague description fields (poor auto-discovery)
- Overlong SKILL.md with duplicated explanations
- Hidden assumptions about tools or environment
- No explicit completion criteria
- No anti-shortcut guardrails for demo/show requests

## Review Checklist

- [ ] Description starts with "Use when..."
- [ ] Trigger conditions are concrete and searchable
- [ ] Workflow is explicit and sequential
- [ ] Guardrails prevent common failure modes
- [ ] Output format is specified
- [ ] References are one level deep from SKILL.md
- [ ] Examples are short and executable
