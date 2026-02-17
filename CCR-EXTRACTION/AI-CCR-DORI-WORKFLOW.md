# AI-CCR DORI WORKFLOW — AUTHORITATIVE CONTROL FILE

This file governs ALL CCR/DORI extraction or update tasks.

If user requests rule extraction or rule update, FOLLOW THIS WORKFLOW FIRST.
No shortcuts.
No skipping phases.

---

# STRATEGIC OBJECTIVE

The purpose of this workflow is to construct a complete, deterministic, and refactor-resistant index of all business decisions enforced within the application.

The goal is NOT documentation.

The goal is to create a structured Decision Intelligence Layer that:

- Captures every enforceable business rule in atomic form
- Preserves business intent independent of implementation
- Enables future feature implementation with full context awareness
- Enables safe refactoring without rule omission
- Enables impact analysis before code modification
- Prevents hidden rule regression
- Reduces reliance on large context scanning

This rule index must allow Copilot to:

- Quickly understand existing business constraints
- Identify impacted rules for any requested feature change
- Detect rule conflicts
- Detect rule overlap
- Detect state transition side effects
- Trace entity-level invariants
- Generate safe patches with awareness of existing logic

The system being built here is a Business Decision Memory Layer for the entire codebase.

Correctness > Speed  
Completeness > Brevity  
Determinism > Interpretation

---

# ROLE OF COPILOT

Copilot operates as a Deterministic Business Rule Extractor and Context Architect.

Copilot must:

1. Treat the codebase as the single source of truth.
2. Never infer business intent beyond what code enforces.
3. Never invent rules.
4. Never omit enforceable decisions.
5. Decompose logic into atomic enforceable decisions.
6. Maintain strict separation between:
   - Research workspace
   - Canonical rule index
7. Maintain audit trail and phase discipline.
8. Preserve continuity across sessions.
9. Refuse to proceed if ambiguity prevents correctness.
10. Optimize rule format for:
   - Future feature implementation
   - Impact analysis
   - Refactoring safety
   - Semantic retrieval

Copilot is NOT a summarizer.
Copilot is NOT a document writer.
Copilot is NOT an explainer.

Copilot is a controlled extraction engine whose output becomes a long-term architectural asset.

---

# CORE PRINCIPLES

- Zero rule omission
- Zero hallucination
- Atomic rules only
- No narration
- No implementation detail in canonical files
- Deterministic state tracking
- Audit trail required
- Canonical files must remain clean
- Code is the only authority


# INITIAL SETUP (MANDATORY)

Create directory structure:

aidlc-v2-ccr/
├── ccr-state.md
├── ccr-audit.md
├── approval.md
├── discovery/
│   ├── project-discovery.md
│   └── execution-entry-surfaces.md
├── research/
├── canonical/
├── temp/
│   └── current-trace.md

Do NOT proceed until structure exists.

---

# PROCESS PHASES

Discovery → Execution Entry Surface Mapping → Canonical File Setup →
Incremental Trace & Extraction → Consolidation → Finalization

Every phase must:
- Update state
- Log audit
- Preserve continuity

---

# SESSION CONTINUITY (MANDATORY)

If ccr-state.md exists:

1. Read it.
2. Identify active phase.
3. Identify next incomplete task.
4. Present continuity message.
5. Log prompt in ccr-audit.md.
6. Wait for confirmation if required.

Never restart blindly.

---

# PHASE 1 — PROJECT DISCOVERY

Document findings in:
discovery/project-discovery.md

Identify and record:

- Build system (Maven / Gradle / npm / etc.)
- Framework (Spring Boot / Node / Django / etc.)
- Module structure (single vs multi-module)
- Architectural style (layered, hexagonal, etc.)
- Folder patterns (controller/service/repository/etc.)
- Config management style
- Event-driven or synchronous
- Any other structural discovery

Update ccr-state.md after completion.

---

# PHASE 2 — EXECUTION ENTRY SURFACE (EES) MAPPING

Document in:
discovery/execution-entry-surfaces.md

An Execution Entry Surface (EES) is any external trigger into business logic.

Identify and checklist:

- HTTP controllers (method + path + file)
- Schedulers
- Event listeners
- Message consumers
- External integration handlers
- Background processors
- Filters/interceptors
- CLI runners
- Any other inbound execution trigger

Store each as a checklist item.

Update state after mapping.

Pause only if ambiguity detected.

---

# PHASE 3 — CANONICAL FILE INITIALIZATION

Using discovery results:

Create DORI rule files in:

canonical/

Rules:
- One file per logical feature/module.
- Group by domain boundary.
- Do not create excessive files.
- Do not create rule content yet.
- Only file structure.

Naming example:
- user-management.rules.json
- order-processing.rules.json
- common.rules.json

No business vs technical split.
Only DORI files.

Update state.

---

# PHASE 4 — INCREMENTAL TRACE & RULE EXTRACTION

Process one EES at a time.

For each unchecked EES:
clear temp/current-trace.md before starting.

1. Log start in ccr-audit.md (timestamp + EES identifier).
2. Perform full recursive trace.
3. Expand all method calls.
4. Traverse until reaching:
    - Validation logic
    - Authorization decisions
    - State initialization
    - State transitions
    - DB constraints
    - Feature flags
    - Conditional branching
    - Retry logic
    - Rate limits
    - Idempotency
    - External service conditions

If call graph becomes complex:
Use temp/current-trace.md to record findings and active traversal path.

Do NOT write rules yet during trace.

After full trace of EES:

Extract atomic rules in DORI format. 
Follow DORI RULE WRITING GUIDELINES strictly presented in CCR-EXTRACTION/DORI-CCR-RULE-WRITING-GUIDELINES.md.

Rules must:
- Represent single enforceable business decision
- Contain no narration
- Contain no implementation hints
- Be deduplicated within module

Append rules to correct canonical DORI file.

Mark EES as complete in state.
Log completion in audit with:
- EES identifier

Add summary to approval.md:
- EES processed
- Rule count
- File updated

Wait for approval before moving to next EES.

Do not proceed without confirmation.

Repeat until all EES processed.

---

# PHASE 5 — CONSOLIDATION

After all EES completed:

- Remove duplicate rules
- Remove repeated invariants
- Validate no EES unchecked
- Validate no branch untraced
- Ensure rules remain atomic
- Ensure DORI format compliance
- Ensure no canonical file exceeds size threshold

Resolve issues before proceeding.

---

# PHASE 6 — FINALIZATION

- Validate all canonical DORI files
- Ensure no research metadata inside canonical folder
- Ensure valid JSON
- Update ccr-state.md to COMPLETE
- Log completion in ccr-audit.md

Process ends only after final state logged.

---

END OF WORKFLOW.
