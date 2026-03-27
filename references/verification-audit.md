# Verification Audit

Use this mode to determine whether a repository's claimed AI workflow has been demonstrated through real execution rather than documentation alone.

## Preconditions

This mode should only be used when the repository appears mature enough to verify.

Expected preconditions:

1. The repository has a formal rule entry
2. The workflow is sufficiently specified to run
3. A minimal task sample exists
4. A local gate or CI path exists

If these are not met, report that verification is premature and downgrade accordingly.

## Goal

Verification answers three questions:

1. What was tested
2. How it was tested
3. What happens with the result

If these cannot be answered uniquely, the workflow cannot be considered verified.

## Required Coverage

A full verification should cover all of the following:

1. New-session context recovery
2. One minimal task sample
3. At least one real local gate or CI run
4. At least one real failure path with stop, repair, and re-validation
5. One real closure or traceability step

## Minimal Task Sample Requirements

The sample should be:

- small enough to complete in one verification cycle
- bounded in scope
- objectively checkable
- validatable through gate or CI
- free of large refactors or broad migrations

Avoid samples that are:

- broad refactors
- multi-module feature programs
- purely exploratory tasks
- tasks without a real validation path

## Verification Procedure

1. Read the formal entry and governing documents
2. Determine current phase, task, and next step
3. Select a minimal task sample
4. Execute according to repository rules
5. Run local gate or CI
6. If failure occurs, read the result and repair
7. Re-run verification
8. Perform closure and traceability steps
9. Produce a verification conclusion

## Anti-False-Positive Checks

Downgrade the result if any of the following occurs:

- only static reading, no real execution
- oversized task sample that hides workflow defects
- gate or CI claimed but not actually run
- failure output exists but is not used
- downstream work continues after failure
- closure is skipped while success is claimed
- conclusion lacks evidence

## Evidence Requirements

A strong result should include evidence for:

1. phase, task, and next-step determination
2. task sample definition
3. real gate or CI execution result
4. at least one failure and repair record
5. re-validation result
6. closure or traceability result

## Scoring Dimensions

Score each dimension from `0-10`.

- scope completeness
- execution realism
- failure-loop integrity
- evidence completeness
- repeatability

## Rating Bands

- `Unverified`
- `Partially Verified`
- `Verified`
- `Battle-Tested`

## Output Requirements

Always provide:

1. Audit Scope
2. Evidence Basis
3. Scoring
4. Conclusion
5. High-Risk Findings
6. Recommendations
7. Uncertainties

Recommendations should explicitly say whether the next action is:

- improve contract
- improve readiness
- repair environment
- re-select a smaller sample
- re-run verification
