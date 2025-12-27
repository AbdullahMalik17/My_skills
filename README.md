# My Skills - Reusable Claude Code Skills Library

A curated collection of 50+ battle-tested skills that extend Claude Code's capabilities across software engineering domains. Each skill encodes production knowledge, domain expertise, and proven workflows for AI-assisted development.

## Quick Start

### Using Skills with Claude Code

Skills automatically trigger when Claude Code detects relevant tasks. No manual activation required.

```bash
# Clone the repository
git clone <your-repo-url>
cd My_skills

# Browse available skills
cat .claude/skills/SKILLS-INDEX.md

# Claude Code will automatically load and use skills when appropriate
```

### Example Usage

When you ask Claude to perform tasks, skills trigger automatically:

```
"Build a Next.js app with authentication"
→ Triggers: building-nextjs-apps, configuring-better-auth

"Deploy this app to Kubernetes"
→ Triggers: containerizing-applications, deploying-cloud-k8s

"Help me debug this test failure"
→ Triggers: systematic-debugging
```

## Available Skills

This repository contains **50+ skills** across 8 categories:

| Category | Count | Examples |
|----------|-------|----------|
| **MCP-Backed** | 3 | browsing-with-playwright, fetching-library-docs |
| **Infrastructure** | 3 | containerizing-applications, deploying-cloud-k8s |
| **Application** | 4 | building-nextjs-apps, scaffolding-fastapi-dapr |
| **UI/Frontend** | 4 | building-chat-interfaces, styling-with-shadcn |
| **Development** | 2 | systematic-debugging, operating-production-services |
| **Documents** | 2 | working-with-spreadsheets, working-with-documents |
| **Meta** | 2 | creating-skills, skill-creator |
| **Integration** | 2 | building-mcp-servers, internal-comms |

**Full catalog**: See [.claude/skills/SKILLS-INDEX.md](.claude/skills/SKILLS-INDEX.md)

## Creating New Skills

### Prerequisites

Skills should encode knowledge Claude doesn't already possess:

- ✅ Production gotchas that broke your system
- ✅ Domain expert patterns not in documentation
- ✅ Complex tool integrations you've debugged
- ❌ Standard library usage
- ❌ Well-documented public patterns

### Creation Workflow

1. **Initialize skill structure**
   ```bash
   python3 .claude/skills/creating-skills/scripts/init_skill.py my-new-skill
   ```

2. **Implement skill components**
   ```
   my-new-skill/
   ├── SKILL.md          # Frontmatter + instructions
   ├── scripts/          # Automation scripts
   ├── references/       # Deep-dive documentation
   └── assets/           # Output templates
   ```

3. **Package and verify**
   ```bash
   python3 .claude/skills/creating-skills/scripts/package_skill.py my-new-skill
   ```

**Detailed guide**: See [creating-skills](.claude/skills/creating-skills/SKILL.md)

## Skill Anatomy

### SKILL.md Structure

```yaml
---
name: skill-name
description: |
  Use when [triggering conditions].
  NOT when [exclusions].
---

# Skill Title

Instructions for Claude to follow...
```

### Key Principles

1. **Concise**: Under 500 lines per SKILL.md
2. **Triggered**: Clear "Use when..." conditions in description
3. **Verified**: Each skill includes verification script
4. **Battle-tested**: Production knowledge, not theory

## Repository Structure

```
My_skills/
├── README.md                    # This file
├── CLAUDE.md                    # Detailed documentation
└── .claude/
    └── skills/
        ├── SKILLS-INDEX.md      # Complete catalog
        └── [skill-name]/
            ├── SKILL.md         # Skill definition
            ├── scripts/         # Executable automation
            │   └── verify.py    # Validation script
            ├── references/      # Documentation
            └── assets/          # Templates/resources
```

## Verification

### Verify all skills
```bash
for skill in .claude/skills/*/; do
  python3 "$skill/scripts/verify.py" 2>/dev/null || echo "FAIL: $skill"
done
```

### Verify specific skill
```bash
python3 .claude/skills/creating-skills/scripts/verify.py /path/to/skill --verbose
```

## Quality Standards

Every skill must meet these criteria:

- **Clear trigger**: "Use when..." in description
- **Concise**: <500 lines, <5000 tokens
- **Verified**: Includes passing verify.py script
- **Battle-tested**: Contains production gotchas
- **Structured**: References one level deep only

## Common Tasks

### Browse Skills by Category
```bash
# View complete skills index
cat .claude/skills/SKILLS-INDEX.md

# List all skill names
ls -1 .claude/skills/
```

### Use a Specific Skill
Skills trigger automatically based on your requests to Claude Code. Reference the skill name explicitly if needed:

```
"Use the systematic-debugging skill to help me fix this test"
"Apply the building-nextjs-apps patterns here"
```

### Contribute a New Skill

1. Review [CLAUDE.md](CLAUDE.md) for contribution guidelines
2. Use [creating-skills](.claude/skills/creating-skills/SKILL.md) for the creation process
3. Ensure skill passes verification
4. Submit with clear, atomic commits

## Documentation

- **Quick Reference**: This README
- **Comprehensive Guide**: [CLAUDE.md](CLAUDE.md)
- **Skills Catalog**: [.claude/skills/SKILLS-INDEX.md](.claude/skills/SKILLS-INDEX.md)
- **Creation Guide**: [.claude/skills/creating-skills/SKILL.md](.claude/skills/creating-skills/SKILL.md)

## Professional Standards

This repository follows professional development practices:

- **Atomic commits**: One logical change per commit
- **Conventional commits**: `type: description` format
- **Verification required**: All skills must pass verify.py
- **No unnecessary files**: Only essential artifacts
- **Evidence-based**: Decisions backed by testing

## What Makes a Good Skill?

Ask yourself:

1. **Would you recreate this if deleted?** (If no → not a skill)
2. **Did this cause production issues?** (If yes → high priority)
3. **Would a domain expert recreate it?** (If yes → medium priority)
4. **Does Claude already know this?** (If yes → not a skill)

## Future Skill Ideas

Areas needing skills:
- Database migrations at scale (Alembic, Drizzle)
- Feature flags and gradual rollouts
- Incident response playbooks
- Observability instrumentation (OpenTelemetry)
- GraphQL federation patterns
- WebSocket scaling patterns

## Contributing

1. Fork the repository
2. Create your skill following quality standards
3. Verify your skill passes validation
4. Submit with descriptive commit message
5. Reference relevant documentation

## License

See individual skill LICENSE.txt files where applicable.

## Support

For issues or questions:
- Review [CLAUDE.md](CLAUDE.md) for detailed documentation
- Check [SKILLS-INDEX.md](.claude/skills/SKILLS-INDEX.md) for skill-specific guidance
- Examine existing skills for examples

---

**Purpose**: Provide reusable, battle-tested skills encoding domain expertise for AI-assisted software engineering.

**Philosophy**: Quality over quantity. Every skill must justify its existence.