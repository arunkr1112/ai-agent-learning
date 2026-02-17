# AI-CCR DORI WORKFLOW — DOMAIN INVARIANT MODEL

This file governs ALL CCR/DORI extraction or update tasks.

If user requests rule extraction or update, FOLLOW THIS WORKFLOW FIRST.

No shortcuts.
No skipping phases.

---

# STRATEGIC OBJECTIVE

The purpose of this workflow is to construct a refactor-resistant Business Invariant Index for the application.

This is NOT a code decision mirror.
This is NOT an enforcement log.
This is NOT low-level validation capture.

This system must capture ONLY:

- Domain invariants
- State machines
- Cross-entity constraints
- Cross-flow dependencies
- Activation/eligibility conditions

The objective is to:

- Preserve business behavior independent of implementation
- Reduce feature-implementation context overload
- Enable deterministic impact analysis
- Prevent invariant regression
- Allow Copilot to reason about business behavior without scanning entire codebase

We are building a Business Decision Memory Layer.

Correctness > Speed  
Signal > Noise  
Domain > Mechanics

---

# ROLE OF COPILOT

Copilot operates as a Domain Invariant Extractor.

Copilot must:

1. Treat code as source of truth.
2. Extract ONLY domain-level invariants.
3. Ignore mechanical enforcement details.
4. Ignore normalization, trimming, hashing, formatting.
5. Ignore internal sequencing mechanics.
6. Capture state transitions and invariant rules.
7. Preserve strict atomicity at invariant level.
8. Avoid implementation-level duplication.
9. Maintain audit and phase discipline.

Copilot is NOT extracting all enforceable decisions.
Copilot is extracting domain behavior.

---

# WHAT MUST NOT BE CAPTURED

Do NOT extract:

- String trimming
- Lowercasing
- Hashing
- ID generation format
- Transaction start order
- Validation-before-transaction mechanics
- DTO mapping details
- Internal ordering steps

If removing the rule does NOT break domain behavior,
it does NOT belong in DORI.

---

# INITIAL SETUP

aidlc-v3-ccr/
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

---

# PROCESS PHASES

Discovery  
→ Execution Entry Surface Mapping  
→ Canonical File Setup  
→ Domain Invariant Extraction  
→ Consolidation  
→ Finalization

Every phase updates state and audit.

---

# PHASE 1 — PROJECT DISCOVERY

Same as before.
Structural understanding only.

---

# PHASE 2 — EXECUTION ENTRY SURFACE (EES) MAPPING

Identify all business entry triggers:

- HTTP endpoints
- Schedulers
- Consumers
- Listeners
- CLI
- Integrations

Checklist only.
No rule extraction here.

---

# PHASE 3 — CANONICAL FILE INITIALIZATION

Create DORI files grouped by domain modules.

Example:
- onboarding.rules.json
- user-management.rules.json
- billing.rules.json

No rule content yet.

---

# PHASE 4 — DOMAIN INVARIANT EXTRACTION

Process one EES at a time.

For each EES:

1. Perform full trace.
2. Identify domain behavior.
3. Identify invariants.
4. Identify state transitions.
5. Identify cross-entity coupling.
6. Identify activation conditions.
7. Identify uniqueness invariants.
8. Identify cross-flow dependencies.

Extract ONLY:

- Invariants that define domain behavior
- Rules whose removal changes business outcome
- State machine definitions
- Activation requirements

Ignore mechanical details.

Append to canonical file.

Wait for approval before next EES.

---

# PHASE 5 — CONSOLIDATION

After all EES:

- Merge duplicate invariants
- Merge repeated state transitions
- Merge cross-flow rules
- Ensure no invariant repetition
- Ensure rules remain domain-level

---

# PHASE 6 — FINALIZATION

- Validate invariant coverage
- Validate state machines complete
- Validate JSON correctness
- Update state COMPLETE
- Log audit

Process ends.

---

END OF WORKFLOW
