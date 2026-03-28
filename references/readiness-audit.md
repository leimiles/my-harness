# Readiness Audit

Use this mode to determine whether a repository is operationally ready for safe, controlled AI coding.

## Boundaries

- The agent executing this audit must not be the same agent session that defined or optimized the rules being audited in the current engagement. If it is, the audit conclusion lacks independence and a new session must be used.
- This skill audits whether structural prerequisites exist; it does not audit rule quality (contract mode) or execution evidence (verification mode).

## Goal

A ready repository should let AI reliably determine:

- whether it may change code
- what task it is executing
- what plan governs the task
- what validation gates must pass
- what review and remote validation rules apply
- what to do after failure
- how to recover context in a new session

## Hard Gates

If any gate is missing, the repository cannot be rated `Ready`. A missing gate caps the corresponding dimension at 4/10, regardless of how many gates within that dimension are missing. Two or more missing gates cap the overall rating at `Not Ready`; one missing gate caps it at `Partially Ready`. Dimension 6 (Context Recovery And Evolution) has no hard gate; a low score there affects the overall band through the dimension scoring rules only.

| Gate | Governing Dimension |
|---|---|
| 1. Unique rule entry | 1. Entry And Execution Boundaries |
| 2. Explicit phase or execution boundary | 1. Entry And Execution Boundaries |
| 3. Explicit task or plan mechanism | 2. Task And Plan System |
| 4. Explicit progress determination | 3. Progress And Traceability |
| 5. Explicit local gate | 4. Local Validation And Completion Definition |
| 6. Explicit task tracking and review rules | 5. Review And Remote Validation Loop |
| 7. Explicit remote validation path and failure loop | 5. Review And Remote Validation Loop |
| 8. Explicit AI coding boundary | 1. Entry And Execution Boundaries |
| 9. Explicit stop or rollback after failure | 4. Local Validation And Completion Definition |
| 10. Explicit completion backfill or delivery artifacts | 3. Progress And Traceability |

**Gate 8 — Explicit AI coding boundary:** The repository must have an explicit rule stating when AI may and may not modify code. A broad statement such as "follow the process" does not satisfy this gate. The boundary must be stated as a condition, not implied by convention.

## High-Risk Signals

Any of the following should materially downgrade the result:

- AI can bypass task or plan and change code directly
- AI can bypass validation and still claim completion
- AI can bypass review or remote checks
- AI cannot read or use failure results for repair
- AI can continue downstream work after a failed node
- temporary paths can bypass the main flow
- a new session cannot recover version, phase, task, and next step
- non-formal materials can override formal rules

## Scoring Dimensions

Score each dimension from `0-10`.

### 1. Entry And Execution Boundaries

Check:

- unique rule entry
- coding allowed or forbidden boundary
- destructive or high-risk action boundary

### 2. Task And Plan System

Check:

- task carrier exists
- plan carrier exists
- status model exists
- current task and next step can be uniquely determined

### 3. Progress And Traceability

Check:

- progress rule exists
- completion definition exists
- failure traces exist
- temporary or exception work has a bounded tracking path

### 4. Local Validation And Completion Definition

Check:

- local gates are defined
- validation commands are concrete
- completion claims require validation
- environment-related inability to validate has a required risk report
- evidence is expected, not implied

### 5. Review And Remote Validation Loop

Check:

- issue or ticket and review carrier binding
- remote validation must-pass definition
- local and remote validation relationship
- failure result reading entry
- repair and re-validation path
- prohibition on claiming completion before checks pass

### 6. Context Recovery And Evolution

Check:

- new sessions can recover phase, task, next step, and version
- rules do not depend on chat history
- versioned evolution path is explicit
- mutable vs immutable documents are distinguishable

## Rating Bands

- `Not Ready`
- `Partially Ready`
- `Ready`
- `Strongly Ready`

## Output Requirements

Always provide:

1. Audit Scope
2. Evidence Basis
3. Scoring
4. Conclusion
5. High-Risk Findings
6. Recommendations
7. Uncertainties

Recommendations should prioritize the smallest changes that restore a stable AI coding loop.
