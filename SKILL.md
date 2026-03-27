---
name: ai-harness-auditor
description: Use when auditing an AI collaboration contract, checking whether a repository is ready for AI coding, verifying an AI harness through real execution, or reviewing rule clarity, convergence, redundancy, and execution safety. Produces audits with scores, conclusions, risks, and prioritized recommendations.
---

# AI Harness Auditor

This skill audits a repository's AI collaboration system in one of three modes:

- `contract`: audit rule clarity, convergence, ambiguity, and redundancy
- `readiness`: audit whether the repository is structurally ready for safe AI coding
- `verification`: audit whether the claimed workflow has been proven by real execution

## Boundaries

- This skill audits repository rules; it does not define repository rules.
- If this skill conflicts with the audited repository's formal contract, the repository contract wins.
- Do not invent missing project facts.
- Do not use this skill as the authority source for the target repository.
- When evidence is missing, downgrade the conclusion and report the gap explicitly.
- Do not convert repository-specific facts into generic assumptions.
- Do not treat templates, examples, or convenience notes as formal contract unless the repository explicitly does so.

## Mode Selection

Choose exactly one mode.

Use `contract` when the user asks whether rules are clear, convergent, non-redundant, or unambiguous.

Use `readiness` when the user asks whether a repository is operationally ready for safe AI coding.

Use `verification` when the user asks whether the workflow has been truly exercised and evidenced through real execution.

If the user does not specify a mode, infer the closest one from the request and state which mode you chose.

## Required Inputs

Read the repository's formal entry contract and only the documents needed for the selected mode.

Typical sources may include:

- top-level AI contract
- phase rules
- issue / PR rules
- progress rules
- plan documents
- CI or verification documents

If the repository lacks a unique formal entry, report that as a finding rather than compensating for it.

## Workflow

1. Identify the audit mode.
2. Read the formal repository documents relevant to that mode.
3. Load the matching reference:
   - `references/contract-audit.md`
   - `references/readiness-audit.md`
   - `references/verification-audit.md`
4. Audit the repository against that framework.
5. Produce:
   - audit scope
   - evidence basis
   - scoring
   - conclusion
   - high-risk findings
   - prioritized recommendations
   - uncertainties

## Output Contract

Always structure the result as:

1. Audit Scope
2. Evidence Basis
3. Scoring
4. Conclusion
5. High-Risk Findings
6. Recommendations
7. Uncertainties

Rules:

- Give one primary conclusion only.
- Separate confirmed findings from uncertainties.
- Do not hide missing evidence inside recommendations.
- Prefer high-signal findings over exhaustive restatement.
- When a conclusion depends on inference, mark it clearly as an inference.
- When repository materials conflict, describe the conflict before scoring downstream impact.

## References

- For `contract` mode, read `references/contract-audit.md`
- For `readiness` mode, read `references/readiness-audit.md`
- For `verification` mode, read `references/verification-audit.md`
- For scoring format and result layout, read `references/output-templates.md`
