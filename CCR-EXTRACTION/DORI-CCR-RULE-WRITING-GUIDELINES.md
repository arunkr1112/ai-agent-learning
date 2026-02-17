# DORI RULE WRITING GUIDELINES — DOMAIN INVARIANT MODEL

This file defines how DORI rules must be written.

DORI captures DOMAIN INVARIANTS only.

Not implementation.
Not mechanics.
Not enforcement noise.

---

# PURPOSE

DORI stores business invariants and state machines in a compressed, refactor-resistant format.

It enables:

- Feature impact analysis
- Safe refactoring
- Behavior regression detection
- Business-aware code generation

It does NOT capture low-level validations.

---

# WHAT QUALIFIES AS A RULE

A rule must satisfy:

If removed, domain behavior changes.

Valid examples:

- Email must be globally unique.
- Tenant must verify email and phone before activation.
- Account transitions from PENDING to ACTIVE after verification.
- Payment must be successful before order confirmation.
- Subscription cannot renew if status is CANCELLED.

Invalid examples (do NOT capture):

- Email trimmed before save.
- OTP hashed before storage.
- ID generated as 6-digit numeric string.
- Validation runs before transaction.
- Password hashed before persist.

Those are implementation mechanics.

---

# DORI FORMAT (SIMPLIFIED)

{
"meta": {
"service": "<SERVICE_NAME>",
"version": "2.0"
},
"rules": [
{
"id": "BR-<SERVICE>-001",
"entry": "<EES_IDENTIFIER>",
"entity": "<EntityName>",
"type": "<INVARIANT_TYPE>",
"decision": "<Short domain-level invariant sentence>"
}
]
}

EXAMPLE RULE:
{
"id": "BR-TENANT-005",
"entity": "TenantRootAccount",
"type": "STATE_MACHINE",
"decision": "Root account initial state is ACTIVE with unverified email and phone."
}
---

# RULE FIELD DEFINITIONS

id:
BR-<SERVICE>-<3_DIGIT_SEQUENCE>

entry:
Execution Entry Surface.

entity:
Primary business entity affected.

type:
Must be one of:

- INVARIANT
- STATE_MACHINE
- STATE_TRANSITION
- ACTIVATION_CONDITION
- CROSS_ENTITY_CONSTRAINT
- ELIGIBILITY_RULE

decision:
Single short domain-level statement.
Max ~20 words.
No implementation detail.
No technical wording.

---

# ATOMICITY RULE

One invariant per rule.

Example:

Wrong:
"Email and phone must be unique and verified before activation."

Correct:
1. Email must be unique.
2. Phone must be unique.
3. Email and phone must be verified before activation.

---

# DEDUPLICATION RULE

If invariant applies across multiple entry surfaces,
store it once per domain module, not per EES.

DORI represents domain truth,
not per-endpoint duplication.

---

# WHAT MUST NEVER APPEAR

- File names
- Class names
- Method names
- DB field normalization details
- Hashing details
- Transaction mechanics
- Internal sequencing
- DTO mappings
- Implementation steps

---

# SCALE PRINCIPLE

DORI must remain small.

If rule file grows large,
mechanical noise is being included.

Domain invariants are always fewer than mechanical validations.

---

# FINAL VALIDATION CHECK

Before finalize:

- Does every rule represent domain truth?
- Would removing it change business behavior?
- Is state machine fully represented?
- Is duplication removed?
- Is JSON minimal?

Only then finalize.

---

END OF GUIDELINES
