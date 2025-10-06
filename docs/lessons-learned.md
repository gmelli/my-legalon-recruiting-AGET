# Lessons Learned - Recruiting Agent Setup

## Session: 2025-10-06 - Initial Framework Setup

### Context
Built evaluation framework from scratch for GM-LEGALON recruiting operations across Japan and USA regions.

---

## Decisions Made

### 1. Region-Based Organization
**Decision**: Organize candidates by region (`data/candidates/japan/`, `data/candidates/usa/`)

**Rationale**:
- Matches business structure (two separate regions)
- Simplifies batch processing per region
- Clear separation for location-specific hiring

**Alternative considered**: Organize by role first, then region
- Rejected: More complex navigation, batch processing harder

---

### 2. Separate Level Requirements by Track
**Decision**: Two level requirement docs (`engineering-levels.md`, `data-science-levels.md`)

**Rationale**:
- Engineering and DS have different career progressions
- DS roles focus on business impact, engineering on technical scope
- Clearer evaluation criteria per track

**Alternative considered**: Single unified level doc
- Rejected: Would force artificial alignment between different career paths

---

### 3. Comprehensive Evaluation Template
**Decision**: Single detailed template covering initial assessment + interview integration

**Rationale**:
- Supports both batch mode and deep dive mode
- Avoids multiple template versions
- Interview sections can remain blank initially

**Trade-off**: Template is lengthy but comprehensive
- Mitigated: Clear section headers, easy to scan

---

### 4. Input Location External to Repo
**Decision**: Resumes stored in `~/Downloads/resumes-JP/` and `resumes-US/`

**Rationale**:
- PII never enters git repo directory tree
- User controls deletion timing
- No accidental commits of candidate data

**Alternative considered**: Store in `data/candidates/` directly
- Rejected: Higher risk of accidental git add despite .gitignore

---

### 5. JD Templates Over Full Specs
**Decision**: Created generic JD templates, not fully detailed specs

**Rationale**:
- User hasn't provided specific requirements yet
- Standard breadth covers most scenarios
- Easy to customize when needed

**Next step**: User will fill in team context, specific requirements, location details

---

## Process Insights

### What Worked Well
1. **Privacy-first design**: .gitignore verification before any candidate processing
2. **Framework separation**: Job descriptions and level requirements as committed, reusable artifacts
3. **Template-driven**: Evaluation template ensures consistency across batches
4. **Clear directory structure**: Intuitive organization (data/, workspace/, products/, docs/)

### What Could Improve
1. **Example evaluation**: Consider adding a sanitized example evaluation to docs/
2. **JD customization guide**: Step-by-step for filling in template sections
3. **Comparison format**: No template yet for comparative analysis across candidates
4. **Automation**: Could script batch processing from directory scan

---

## Technical Notes

### Privacy Controls Verified
- `data/candidates/` - gitignored (line 63)
- `workspace/evaluations/*_evaluation_*.md` - gitignored (line 69)
- Session notes use anonymized IDs per AGENTS.md protocol

### File Naming Convention
- Evaluations: `{region}_{candidate-id}_evaluation_{YYYY-MM-DD}.md`
- Anonymized IDs: "JPN-001", "USA-005", "Candidate A", etc.
- Avoids real names in filesystem

### Git Commits
- Setup framework: 882a33d (6 files, 532 insertions)
- Workflow docs: 2125f47 (1 file, 154 insertions)

---

## Recommendations for Next Cycle

### Before First Batch
1. Customize JDs with specific requirements
2. Test with 1-2 sample resumes to validate workflow
3. Create example evaluation for reference
4. Document comparison report format

### During Batch Processing
1. Process candidates sequentially, not parallel (avoid confusion)
2. Mark todos for each candidate to track progress
3. Generate summary report after batch completes
4. Archive raw materials after hiring decision

### After Hiring Round
1. Clean up `data/candidates/{region}/` for completed roles
2. Archive evaluations or delete per privacy policy
3. Review lessons learned, update framework
4. Commit any JD/template improvements

---

## Open Questions

1. **Comparison reports**: What format for comparing 3-5 candidates side-by-side?
2. **Interview feedback structure**: Freeform text or structured fields?
3. **Ranking criteria**: What weights for level fit vs skills match vs culture fit?
4. **Archive strategy**: How long to retain evaluations after hiring decision?

---

## Framework Maturity

**Current state**: v1.0 - Initial setup complete
- ✅ Directory structure
- ✅ Job descriptions (templates)
- ✅ Level requirements (L3-L6, DS1-DS4)
- ✅ Evaluation template
- ✅ Privacy controls
- ✅ Workflow documentation

**Next maturity milestone**: v1.1 - After first batch
- Process 5-10 real candidates
- Refine templates based on actual data
- Add comparison report format
- Create example evaluations

---

*Documented: 2025-10-06*
*Agent: my-legalon-recruiting-AGET v2.5.1*
