# DORI RULE WRITING GUIDELINES (EES-BASED)

This file defines how CCR rules must be written using the DORI (Decision-Only Rule Index) model.

Canonical files must strictly follow this specification.

---

# PURPOSE

DORI stores atomic business decisions enforced within the application in a deterministic, refactor-resistant format.

The objective is to:

- Preserve business intent independent of implementation
- Enable safe feature implementation
- Enable impact analysis before code changes
- Prevent rule regression
- Provide structured context to Copilot
- Avoid full codebase rescanning for every change

DORI is not documentation.
DORI is not explanation.
DORI is a Business Decision Index.

---

# CORE PRINCIPLES

- Code is the only source of truth.
- Rules represent enforceable decisions, not implementation.
- One rule = one atomic business decision.
- No narration.
- No examples.
- No technical commentary.
- No duplication.
- No implementation hints.
- Rules must survive refactoring.

---

# WHAT IS AN EXECUTION ENTRY SURFACE (EES)

An Execution Entry Surface (EES) is any external trigger that initiates business logic.

Examples:

- HTTP endpoint
- Scheduler
- Event listener
- Message consumer
- CLI command
- Background job
- Integration handler
- Interceptor/filter with business impact

Rules are scoped to an EES.

A rule must always specify the EES in which it is enforced.

---

# WHAT QUALIFIES AS A RULE

A rule is a SINGLE enforceable business decision including:

- Field validation
- Field length constraint
- Required constraint
- Uniqueness constraint
- Authorization requirement
- Conditional gating
- Feature flag dependency
- State initialization
- State transition condition
- Retry policy
- Rate limit
- Idempotency enforcement
- DB-level constraint
- External dependency condition

If multiple decisions exist → split into multiple rules.

Never merge decisions.

---

# DORI FORMAT (MANDATORY)

{
"meta": {
"service": "<SERVICE_NAME>",
"version": "1.0"
},
"entities": {
"<EntityName>": ["field1", "field2"]
},
"rules": [
{
"id": "BR-<SERVICE>-001",
"entry": "<EES_IDENTIFIER>",
"entity": "<EntityName>",
"field": "<FieldName or null>",
"type": "<RULE_TYPE>",
"decision": "<Short semantic sentence>"
}
]
}

---

# RULE FIELD DEFINITIONS

id:
Format → BR-<SERVICE>-<3_DIGIT_SEQUENCE>
Sequential and deterministic within service.

entry:
Execution Entry Surface identifier.

Examples:
- "HTTP POST /users"
- "SCHEDULER DailyUserSyncJob"
- "CONSUMER UserCreatedEvent"
- "LISTENER PaymentSuccessHandler"
- "CLI RebuildIndexCommand"

entity:
Business entity impacted.

field:
Specific field affected.
Use null if rule applies to entire entity.

type:
Must be one of:

- VALIDATION
- UNIQUE
- REQUIRED
- AUTHORIZATION
- STATE_INIT
- STATE_TRANSITION
- FEATURE_FLAG
- RATE_LIMIT
- IDEMPOTENCY
- EXTERNAL_CONDITION
- CONDITIONAL_FLOW
- RETRY_POLICY
- DB_CONSTRAINT

decision:
Single sentence.
Maximum ~20 words.
Vector-search friendly.
No implementation detail.

Correct:
"Email must be unique across all users."

Incorrect:
"Repository checks database to validate uniqueness."

---

# ATOMICITY CHECK

Before finalizing a rule, verify:

- Does it represent one enforceable decision?
- Can it be split further?
- Is it free from implementation detail?
- Is it deterministic?
- Is it independent of narration?

If unclear → split.

---

# DEDUPLICATION RULE

Two rules are duplicates if they share:

- Same entity
- Same field
- Same decision meaning
- Same Execution Entry Surface

Keep only one.

---

# WHAT MUST NEVER APPEAR IN CANONICAL FILES

- File names
- Class names
- Method names
- Line numbers
- Error codes
- Stack traces
- Narration
- Technical commentary
- Research notes
- TODO markers
- Internal component references
- Cross-service references

Canonical files must contain only valid DORI JSON.

---

# SCALE PRINCIPLES

- One DORI file per logical module.
- Avoid excessive file splitting.
- Keep JSON flat.
- No nested rule structures.
- No cross-service coupling.
- Deterministic rule ordering.
- Keep decisions concise.

DORI must remain small and query-efficient.

---

# FINAL VALIDATION CHECKLIST

Before marking complete:

- All Execution Entry Surfaces processed
- No unchecked traversal paths
- All rules atomic
- No duplicates
- Valid JSON
- No metadata leakage
- Rule IDs sequential
- All decisions implementation-free
- Each rule mapped to a valid EES

Only then finalize.

---

END OF GUIDELINES
