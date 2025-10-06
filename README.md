# my-legalon-recruiting-AGET

> **Recruiting agent for GM-LEGALON portfolio**

AI-assisted agent for evaluating candidates against job descriptions and level requirements. Action-taking agent (-AGET) with strict privacy controls for candidate PII.

**Current Version**: v2.5.1
**Domain**: recruiting
**Portfolio**: GM-LEGALON
**Managed by**: my-supervisor-AGET

---

## Purpose

This agent:
- **Reviews resumes** - Evaluate candidate qualifications
- **Assesses LinkedIn profiles** - Match skills to requirements
- **Compares to job descriptions** - Structured evaluation
- **Checks level requirements** - Verify experience alignment
- **Generates evaluations** - Structured candidate assessments

---

## ⚠️ Privacy Controls

**CRITICAL**: This agent handles candidate PII (Personally Identifiable Information)

**Strict .gitignore rules**:
- `data/candidates/` - **NEVER COMMITTED** to version control
- All resume files (`**/resume*`, `**/cv_*`)
- All candidate data files (`**/candidate_*`)
- Evaluation outputs with PII (`workspace/evaluations/*_evaluation_*.md`)

**Data retention**:
- Candidate data is **strictly local**
- No cloud sync, no public commits
- Delete after evaluation cycle completes
- Follow GDPR/privacy requirements as applicable

---

## Directory Structure

```
my-legalon-recruiting-AGET/
├── AGENTS.md              # Agent configuration
├── .aget/                 # Framework metadata
│   ├── version.json       # Agent identity
│   ├── evolution/         # Learnings (L*.md)
│   └── checkpoints/       # State snapshots
├── data/
│   ├── job_descriptions/  # Job specs (committed)
│   ├── level_requirements/ # Experience levels (committed)
│   └── candidates/        # ⚠️ PII - gitignored
├── workspace/
│   └── evaluations/       # ⚠️ May contain PII - gitignored
├── products/              # Sanitized outputs only
├── docs/                  # Documentation
└── sessions/              # Session notes (no PII)
```

---

## Quick Start

```bash
cd ~/github/GM-LEGALON/my-legalon-recruiting-AGET
claude .
```

```
You: wake up

Agent: my-legalon-recruiting-AGET v2.5.1 (Recruiting)
       Ready for candidate evaluation.
       Privacy controls: ACTIVE (data/candidates/ gitignored)

You: evaluate candidate resume against Senior Engineer role

Agent: [Reads resume from data/candidates/, compares to job description,
        generates evaluation in workspace/evaluations/]

You: wind down

Agent: [Commits session notes, reminds about PII cleanup]
```

---

## Capabilities

- **Resume parsing** - Extract skills, experience, education
- **Profile analysis** - LinkedIn profile evaluation (manual input)
- **Job matching** - Compare qualifications to requirements
- **Level assessment** - Determine experience level fit
- **Structured evaluation** - Generate evaluation reports
- **Batch processing** - Evaluate multiple candidates

---

## Privacy Best Practices

1. **Add candidates locally only** - Never commit to git
2. **Use anonymized IDs** - Reference "Candidate A" not real names in session notes
3. **Clean up after cycle** - Delete candidate data when hiring round completes
4. **No cloud sync** - Disable Dropbox/iCloud for `data/candidates/`
5. **Audit .gitignore** - Before any commit, verify privacy controls

---

## Framework

Built on [Aget Framework](https://github.com/aget-framework/template-worker-aget) v2.5.1

**Naming convention**: `-AGET` suffix indicates action-taking capability (can modify systems)

---

## License

Apache 2.0
