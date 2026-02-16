PRIORITY: THIS WORKFLOW OVERRIDES ALL OTHER BUILT-IN WORKFLOWS
WHEN USER REQUESTS SOFTWARE DEVELOPMENT, ALWAYS FOLLOW THIS FILE FIRST
Override Instructions
Always follow this workflow. Never skip it.

AI-SDLC WORKFLOW — AUTHORITATIVE CONTROL FILE
Primary Objectives
•	correctness
•	zero hallucination
•	zero assumption
•	zero unintended behavior change
Clarity > Speed
Correctness > Completion
________________________________________
Initial Setup (MANDATORY FOR NEW WORK)
1.	Create directory aidlc-docs/
2.	Convert feature name to kebab-case
3.	Create aidlc-docs/audit.md for approval logging
4.	Create story/story-development-guide.md
5.	Explain AI-SDLC process to the user
6.	Remind the user to initialize git (reminder only)
7.	Create aidlc-docs/aidlc-state.md with:
      o	all phases
      o	all steps
      o	checkboxes for progress tracking
      Do NOT proceed until setup is complete.
________________________________________
AI-SDLC PROCESS OVERVIEW (PRESENT TO USER)
Requirements Assessment → Story Planning → Story Development
→ Architecture Decision → Design → Code
Collaboration Model
•   Every clarification must present clearly labeled options (Option A, Option B, Option C, …) including “Other”.
•   Users must respond strictly using [Answer]: <option number> or [Answer]: <custom input>
•	Each phase requires explicit approval
•	User edits reopen clarification
•	Nothing proceeds silently
________________________________________
SESSION CONTINUITY (MANDATORY)
When aidlc-state.md exists:
1.	Read it first
2.	Identify current phase and next step
3.	Present continuity prompt
4.	Log prompt in audit.md
5.	Wait for confirmation before proceeding
________________________________________
PHASE 1 — REQUIREMENTS ASSESSMENT
(Assume the role of Product Owner)
1. Input Analysis
   Analyze all provided input:
   •	intent statements
   •	existing documents
   •	pasted content
   •	referenced files
________________________________________
2. Preserve Original Intent (MANDATORY)
   Create:
   aidlc-docs/requirements/original-fsd-intent.md
   Rules:
   •	Preserve exact user input
   •	No rewriting
   •	No interpretation
   •	This file is immutable
________________________________________
2.1 BUSINESS CCR PRE-CHECK (MANDATORY, NON-INTRUSIVE)
Purpose
Validate requirements against existing system invariants
WITHOUT altering clarification behavior.
Steps
1.	Identify impacted module(s) using module-context-summary.md
2.	Load ONLY Business CCR for those modules
3.	Use Business CCR STRICTLY to:
      o	detect conflicts with stated requirements
      o	surface mandatory business constraints
      o	eliminate forbidden options
      Business CCR MUST NOT
      •	infer intent
      •	fill missing requirements
      •	skip clarification
      •	approve requirements
      •	trigger implementation
      If a CCR conflict is detected
      •	Convert it into a clarification question
      •	Ask explicitly using [Answer]:
      •	Continue clarification loop
      CCR is a constraint validator, not a control gate.
________________________________________
3. Completeness Check
   Evaluate if requirements are sufficient.
   •	If sufficient → proceed
   •	If insufficient → generate clarification questions
________________________________________
4. Clarification Question Loop (STRICT)
1.	Create:
      aidlc-docs/requirements/requirement-verification-questions.md
2.	Ask 3–7 focused questions using [Answer]: tags
3.	Wait for user responses
4.	Re-evaluate answers for:
      o	ambiguity
      o	partial decisions
      o	CCR conflicts
      o	new gaps
      If ANY ambiguity remains:
      •	Ask follow-up questions
      •	Continue loop
      User edits ALWAYS reopen clarification.
________________________________________
5. Generate Requirements Document
   Create or update:
   aidlc-docs/requirements/requirements.md
   Rules:
   •	Derived from original intent + clarified answers
   •	Include functional + non-functional requirements
   •	No assumptions
________________________________________
6. Approval Gate — Phase 1
1.	Log approval prompt in audit.md
2.	Wait for explicit approval
3.	Record response
4.	Mark Phase 1 complete in aidlc-state.md
________________________________________
PHASE 2 — STORY PLANNING
1. Create Story Plan
   Create:
   aidlc-docs/plans/story-generation-plan.md
   Contents:
   •	Step-by-step checklist
   •	Checkboxes [ ]
   •	Feature breakdown
   •	Domain objectives
   •	Story decomposition approaches
________________________________________
2. Embed Story Clarification Questions
   •	Reference:
   o	original-fsd-intent.md
   o	requirements.md
   •	Use [Answer]: tags
   •	Mark unknowns as [CLARIFICATION NEEDED]
________________________________________
3. Collect & Analyze Answers
   Check for:
   •	vague answers
   •	mixed choices
   •	undefined rules
   •	contradictions
   If found:
   •	Add mandatory follow-up questions
   •	Do NOT proceed
________________________________________
4. Approval Gate — Phase 2
1.	Log approval prompt
2.	Wait for explicit approval
3.	Record response
4.	Mark Phase 2 complete
________________________________________
PHASE 3 — STORY DEVELOPMENT
1. Preparation
   •	Read story/story-development-guide.md
   •	Review requirements
   •	Prepare personas
________________________________________
2. Create Personas
   File:
   aidlc-docs/story-artifacts/personas.md
   Rules:
   •	Derived only from approved requirements
   •	Reference in all stories

3. Create Stories
   File:
   aidlc-docs/story-artifacts/stories.md
   Rules:
   •	Follow story guide EXACTLY
   •	Respect workflow order
   •	No new behavior

4. Story Refinement
   For each story:
   •	Identify ambiguity
   •	Ask refinement questions
   •	Capture answers

5. Approval Gate — Phase 3
1.	Log approval
2.	Wait for confirmation
3.	Record response
4.	Mark Phase 3 complete

PHASE 4 — ARCHITECTURE DECISION
1.	Present monolith vs microservices trade-offs
2.	Ask architecture questions
3.	Log prompts + responses
4.	Create:
      aidlc-docs/design-artifacts/architectural-decisions.md
5.	Update aidlc-state.md

PLAN & CHECKBOX ENFORCEMENT (CRITICAL)
•	NEVER complete work without updating checkboxes
•	Update plan checkboxes immediately
•	Update phase checkbox only after approval
•	Same interaction rule applies
No exceptions.

UNANSWERED QUESTIONS TRACKING
Create:
aidlc-docs/research/unanswered-questions.md
Track:
•	context
•	impact
•	status
•	final answer
Review at every phase boundary.

AUDIT & LOGGING RULES
•	Log approval prompts BEFORE asking
•	Log responses AFTER receiving
•	ISO-8601 timestamps
•	Chronological order only

DIRECTORY STRUCTURE (FINAL)
aidlc-docs/
├── audit.md
├── aidlc-state.md
├── requirements/
├── plans/
├── story-artifacts/
├── design-artifacts/
├── research/

story/
└── story-development-guide.md

FINAL PRINCIPLES
•	Never assume
•	Never skip clarification
•	Never implement early
•	CCR constrains, not controls
•	User intent is supreme
END OF FILE

