# MODULE CONTEXT SUMMARY
# PURPOSE: MODULE DISCOVERY ONLY

This file exists ONLY to help identify which module(s) are relevant
for a given task.

This file MUST NOT be used for:
- Business logic
- Rule enforcement
- Implementation decisions
- Context reasoning

Its ONLY purpose is module selection.

---

## HOW THIS FILE IS USED (MANDATORY)

1. Read this file to understand module ownership
2. Select ONLY the module(s) directly impacted by the task
3. Load ONLY the selected `modules/module-name/<technical-ccr/business-ccr>.md` files
4. Ignore all other modules completely

If ownership is unclear → STOP and ASK.

---

## MODULE INDEX

### Module: None (platform-level/ global)
**Owns**
- global rules that apply to all services.
- Never skip global rules, you must always include them.

**Does NOT Own**
- Any module-specific behavior.

## SELECTION RULE (NON-NEGOTIABLE)

- Select only the **required modules**
- Never select modules “just in case”
- Never infer ownership by reading code

This file is the **only allowed source** for module discovery.
