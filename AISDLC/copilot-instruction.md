# AI-SDLC WORKFLOW — AUTHORITATIVE CONTROL FILE

**Override Instructions**

**WHEN USER REQUESTS SOFTWARE DEVELOPMENT, ALWAYS FOLLOW THIS FILE FIRST**

Always follow this workflow. Never skip it.

---

## Primary Objectives

- **Correctness**
- Zero hallucination
- Zero assumption
- Zero unintended behavior change

**Clarity > Speed**

**Correctness > Completion**

---

## Initial Setup (MANDATORY FOR NEW WORK)

1. Create directory `aidlc-docs/`
2. Convert feature name to kebab-case
3. Create `aidlc-docs/audit.md` for approval logging
4. Create `story/story-development-guide.md`
5. Explain AI-SDLC process to the user
6. Create `aidlc-docs/aidlc-state.md` with:
   - all phases
   - all steps
   - checkboxes for progress tracking

**Do NOT proceed until setup is complete.**

---

## AI-SDLC PROCESS OVERVIEW (PRESENT TO USER)

Requirements Assessment → Story Planning → Story Development → Architecture Decision → Design → Code

### Collaboration Model
- Every clarification must present clearly labeled options (Option A, Option B, Option C, …) including “Other”.
- Users must respond strictly using [Answer]: <Option Letter> or [Answer]: <custom input>.
- If any clarification question remains unanswered, phase approval is invalid, the user must either respond using [Answer]: or explicitly delegate resolution before proceeding.
- Each phase requires explicit approval.
- User edits reopen clarification.
- Nothing proceeds silently.

---

## SESSION CONTINUITY (MANDATORY)

When `aidlc-state.md` exists:

1. Read it first
2. Identify current phase and next step
3. Present continuity prompt
4. Log prompt in `audit.md`
5. Wait for confirmation before proceeding

---

## PHASE 1 — REQUIREMENTS ASSESSMENT

(Assume the role of Product Owner)

### 1. Input Analysis

Analyze all provided input:

- intent statements
- existing documents
- pasted content
- referenced files

---

### 2. Preserve Original Intent (MANDATORY)

Create: `aidlc-docs/requirements/original-fsd-intent.md`

**Rules:**

- Preserve exact user input
- No rewriting
- No interpretation
- This file is immutable

---

### 2.1 BUSINESS CCR PRE-CHECK (MANDATORY, NON-INTRUSIVE)

**Purpose**

Validate requirements against existing system invariants WITHOUT altering clarification behavior.

**Steps**

1. Identify impacted module(s) using `module-context-summary.md`
2. Load ONLY Business CCR for those modules
3. Use Business CCR STRICTLY to:
   - detect conflicts with stated requirements
   - surface mandatory business constraints
   - eliminate forbidden options

**Business CCR MUST NOT**

- infer intent
- fill missing requirements
- skip clarification
- approve requirements
- trigger implementation

**If a CCR conflict is detected**

- Convert it into a clarification question
- Ask explicitly using `[Answer]:`
- Continue clarification loop

CCR is a constraint validator, not a control gate.

---

### 3. Completeness Check

Evaluate if requirements are sufficient.

- If sufficient → proceed
- If insufficient → generate clarification questions

---

### 4. Clarification Question Loop (STRICT)

1. Create: `aidlc-docs/requirements/requirement-verification-questions.md`
2. Ask 3–7 focused questions using `[Answer]:`
3. Wait for user responses
4. Re-evaluate answers for:
   - ambiguity
   - partial decisions
   - CCR conflicts
   - new gaps

**If ANY ambiguity remains:**

- Ask follow-up questions
- Continue loop

User edits ALWAYS reopen clarification.

---

### 5. Generate Requirements Document

Create or update: `aidlc-docs/requirements/requirements.md`

**Rules:**

- Derived from original intent + clarified answers
- Include functional + non-functional requirements
- No assumptions

---

### 6. Approval Gate — Phase 1

1. Log approval prompt in `audit.md`
2. Wait for explicit approval
3. Record response
4. Mark Phase 1 complete in `aidlc-state.md`

---

## PHASE 2 — STORY PLANNING

### 1. Create Story Plan

Create: `aidlc-docs/plans/story-generation-plan.md`

**Contents:**

- Step-by-step checklist
- Checkboxes [ ]
- Feature breakdown
- Domain objectives
- Story decomposition approaches

---

### 2. Embed Story Clarification Questions

- Reference:
  - `original-fsd-intent.md`
  - `requirements.md`
- Use `[Answer]:` tags
- Mark unknowns as `[CLARIFICATION NEEDED]`

---

### 3. Collect & Analyze Answers

Check for:

- vague answers
- incomplete information
- contradictions

---

### 4. Create Stories

Generate detailed user stories based on clarified requirements.

---

### 5. Story Refinement

For each story:

- Validate completeness
- Ensure clarity
- Confirm alignment with requirements

---

### 6. Approval Gate — Phase 2

1. Log approval prompt
2. Wait for explicit approval
3. Record response
4. Mark Phase 2 complete

---

## PHASE 3 — STORY DEVELOPMENT

### 1. Preparation

- Read `story/story-development-guide.md`
- Review all requirements and stories
- Identify dependencies

---

### 2. Implementation Planning

- Break down stories into tasks
- Identify technical dependencies
- Create implementation checklist

---

### 3. Development Execution

- Follow story development guide
- Update progress in checkboxes
- Document decisions

---

### 4. Approval Gate — Phase 3

1. Log approval
2. Wait for confirmation
3. Record response
4. Mark Phase 3 complete

---

## PHASE 4 — ARCHITECTURE DECISION

1. Present monolith vs microservices trade-offs
2. Ask architecture questions
3. Log prompts + responses
4. Create: `aidlc-docs/design-artifacts/architectural-decisions.md`
5. Update `aidlc-state.md`

---

## CHECKPOINT TRACKING RULES

- NEVER complete work without updating checkboxes
- Update plan checkboxes immediately
- Update phase checkbox only after approval
- Same interaction rule applies

**No exceptions.**

---

## UNANSWERED QUESTIONS TRACKING

**Create:** `aidlc-docs/research/unanswered-questions.md`

**Track:**

- context
- impact
- status
- final answer

**Review at every phase boundary.**

---

## AUDIT & LOGGING RULES

- Log approval prompts BEFORE asking
- Log responses AFTER receiving
- ISO-8601 timestamps
- Chronological order only

---

## DIRECTORY STRUCTURE (FINAL)

```
aidlc-docs/
├── audit.md
├── aidlc-state.md
├── requirements/
│   ├── original-fsd-intent.md
│   ├── requirement-verification-questions.md
│   └── requirement-verificaion-follow-up-01.md
│   └── requirements.md
├── plans/
│   └── story-generation-plan.md
├── design-artifacts/
│   └── architectural-decisions.md
└── research/
    └── unanswered-questions.md
```

---

## FINAL PRINCIPLES

- Never assume
- Never skip clarification
- Never implement early
- CCR constrains, not controls
- User intent is supreme
- Phase progression is invalid if any clarification remains unresolved or undelegated.

---

**END OF FILE**

