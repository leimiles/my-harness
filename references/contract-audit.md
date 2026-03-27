# Contract Audit

Use this mode to evaluate whether a repository's AI collaboration contract is clear, convergent, executable, non-redundant, and unambiguous.

## Goal

A strong contract should make it easy to answer:

- what the authoritative rule source is
- what is allowed and forbidden
- when coding is allowed
- what the current task and next step are
- what happens after failure
- how ambiguity and override are handled

## Quick Failure Signals

If any of the following is present, the contract cannot be rated above `Usable` without strong counter-evidence:

1. No unique formal entry contract
2. Phase or execution boundary cannot be uniquely determined
3. Development preconditions cannot be uniquely determined
4. Current task or next step cannot be uniquely determined
5. Failure has no stop, rollback, or recovery entry
6. Non-formal documents carry formal rules
7. The same rule is repeated in multiple places with inconsistent wording

## Scoring Dimensions

Score each dimension from `0-10`.

### 1. Clarity

Check:

- clear distinction between allowed, forbidden, required, and exceptions
- clear distinction between design work and development work
- clear handling of rule violations
- explicit response or output requirements when relevant

### 2. Convergence

Check:

- existence of a unique formal entry
- whether rule sources are separated by responsibility
- whether templates, examples, or notes are prevented from becoming de facto rules
- whether the same question has one authoritative answer

### 3. Executability

Check:

- explicit startup or self-check steps
- explicit development preconditions
- explicit execution order where needed
- explicit rollback and recovery entry after failure
- explicit prohibition on claiming completion before gates pass

### 4. Redundancy Control

Check:

- repeated expansion of the same gate or phase rule
- repeated definitions of phase, task, version, or override rules
- explanatory sections that add no new constraint
- opportunities to replace repetition with reference

### 5. Unambiguity

Check:

- unique phase determination
- unique task determination
- unique version-selection rule
- bounded exception paths
- fixed override format or override constraints

## Strength Protection

A better contract is shorter and sharper without becoming weaker.

During review, ensure that any proposed simplification:

- reduces duplication without reducing gate strength
- preserves execution boundaries
- keeps exceptions explicit and narrow
- preserves the repository's formal authority structure

## Rating Bands

- `Weak`: major ambiguity or multi-source drift
- `Usable`: workable, but still exposed to split interpretation
- `Strong`: clear and mostly convergent, with limited ambiguity
- `Robust`: highly clear, highly convergent, minimal redundancy, directly executable

## Output Requirements

Always provide:

1. Audit Scope
2. Evidence Basis
3. Scoring
4. Conclusion
5. High-Risk Findings
6. Recommendations
7. Uncertainties

Recommendations should focus on:

- collapsing duplicate rule text
- restoring a single authority source
- tightening ambiguous preconditions
- making rollback and completion conditions explicit
