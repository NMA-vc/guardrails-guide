# GUARDRAILS.md Protocol

The safety protocol for autonomous AI coding agents. Persistent constraints that prevent catastrophic failures.

🌐 **Live Site:** [guardrails.md](https://guardrails.md)

## About

GUARDRAILS.md is a file-based protocol for creating persistent safety constraints in agentic development loops. It solves the fundamental problem of agents having no memory across sessions by externalizing learned constraints into a file that must be read at initialization.

Essential for [Claude Code](https://code.anthropic.com/), [Google Antigravity](https://antigravity.google/), and any autonomous coding system.

## The Problem It Solves

Autonomous agents fail stochastically—the same task might succeed nine times and fail catastrophically on the tenth. Without persistent memory, agents repeat the same mistakes across sessions. GUARDRAILS.md provides:

- **Persistent State** - Lessons learned survive context resets
- **"Signs" Architecture** - Discrete units of learned safety constraints
- **Context Pollution Prevention** - Escape mechanism for "Gutter" states
- **Audit Trail** - Human-readable record of failures and fixes

## What's Inside

### The Problem
Deep dive into "The Gutter" - the failure mode where agents enter recursive loops of repeated mistakes due to context pollution.

### The Protocol
How GUARDRAILS.md works architecturally: persistent storage, force-read on initialization, append-only learning, human-readable format.

### Signs Architecture
The anatomy of effective safety constraints: Trigger → Instruction → Reason → Provenance. Learn what makes a good Sign vs a bad one.

### Universal Patterns
Proven safety mechanisms:
- **Artifact Verification** - Human review before destructive operations
- **Context Rotation** - Periodic resets to prevent pollution
- **Privilege Boundaries** - Explicit access controls
- **Rate Limiting** - Preventing runaway loops

### Implementation Guides
Platform-specific instructions for:
- Claude Code
- Google Antigravity
- Ralph Loop
- Custom agents

### Case Studies
Real disasters and how guardrails prevented recurrence:
- The database migration disaster (4-hour downtime)
- The infinite API loop ($200 in unexpected costs)
- The credential leak (emergency key rotation)

## Quick Start

### For Claude Code Users
1. Create `GUARDRAILS.md` in your project root
2. Claude Code automatically reads it
3. Optionally reference it in `.claude/instructions.md`

### For Antigravity Users
1. Create `GUARDRAILS.md` in project root
2. Reference it in `AGENTS.md` or `GEMINI.md`
3. Configure approval workflows for violations

### Example GUARDRAILS.md

```markdown
# GUARDRAILS.md
# Persistent safety constraints

## SIGN #1
**Trigger:** Modifying database schema
**Instruction:** ALWAYS create migration file. Never use direct schema changes.
**Reason:** Direct changes caused data loss in staging
**Provenance:** Manual intervention, 2026-01-27

## SIGN #2
**Trigger:** External API calls
**Instruction:** Wrap ALL calls in try-catch with exponential backoff
**Reason:** Stripe timeout caused 2-hour outage
**Provenance:** Iteration 12 failure
```

## Key Concepts

### "The Gutter"
When an agent's context window fills with error logs and failed attempts, it prioritizes recent failures over original instructions, entering a recursive loop of repeated mistakes. GUARDRAILS.md prevents this by providing persistent memory that survives context resets.

### Signs
Discrete units of learned safety. Each Sign captures a specific failure pattern and the constraint that prevents it from recurring.

### Context Rotation
When context pollution reaches a threshold, save state to files, reset the context window, and re-inject only essential information (including GUARDRAILS.md).

## Related Resources

- [antigravity.md](https://antigravity.md) - Google Antigravity IDE guide
- [Claude Code](https://code.anthropic.com/) - Anthropic's agentic coding tool
- [AGENTS.md Spec](https://agents.md/) - Universal agent instructions
- [Ralph Loop](https://github.com/agrimsingh/ralph-wiggum-cursor) - Implementation reference
- [OWASP LLM Top 10](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

## Contributing

We welcome:
- Real-world failure case studies
- New safety patterns
- Platform-specific implementations
- Improved Sign examples

Please maintain the practical, startup-friendly tone.

## License

MIT - use freely, share learnings widely.

---

Maintained by [nma.vc](https://nma.vc)
