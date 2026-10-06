# Engineering workflow experiment

This policy governs the Matt Pocock engineering experiment, not F-AI-R scientific
architecture or validation requirements. Keep the configured domain documentation
layout and glossary vocabulary.

## Current tracker and publication gate

GitHub Issues in `DataScienceINT/FAIR` is the active tracker. GitHub CLI access was
verified as `michael-liem` on 2026-10-06; Issues are enabled for the repository.
Read `docs/agents/issue-tracker.md` for operations, readiness vocabulary, blockers,
and closure rules. The initial local tracker is superseded; `.scratch/` is not a
fallback for this experiment.

The required `ready-for-agent` label was created with explicit human authorization
and verified on 2026-10-06. Its availability gate is resolved; the human review and
execution requirements below still apply. See
`docs/experiments/matt-pocock-full-workflow.md` for the setup history and access
verification. Documentation setup does not authorize issue publication or
implementation.

## Initial execution policy

1. Clarify intent with `grill-with-docs`, using `grilling` and `domain-modeling`.
   Use `prototype` only to settle a design question requiring runnable evidence;
   use `handoff` when moving into or out of a separate prototype session.
2. Use `to-spec` to synthesize the agreed plan and testing seams. Obtain human
   review of the spec before ticket generation.
3. Use `to-tickets` to propose self-contained vertical slices. Each issue must
   have acceptance criteria and identify its parent spec and blockers. Publish
   GitHub implementation issues only after the human approves the breakdown.
4. Run `implement` for exactly one named, open implementation issue per
   invocation. Start only when its blockers are closed and its scope and testing
   seams are agreed. Use `tdd` at those seams and run feature-appropriate checks.
   Start a fresh implementation context for each ticket, carrying pointers to
   its issue, parent spec, glossary, ADRs, and relevant commits.
5. Run `code-review` against a stated comparison point and the originating
   issue/spec. Address findings and present the acceptance-criteria evidence and
   review results to the human. A ticket is complete only after code review and
   human acceptance; then record the outcome and close that issue. Keep the
   parent spec open until all its implementation issues have been accepted.
6. Repeat for the next unblocked issue. Run `retro` before clearing the relevant
   session, or provide its session log, to propose improvements to the agent's
   environment using `writing-for-agents`.

## Autonomous implementation

`implement-spec` is installed for later evaluation but is disabled for execution
by this repository policy. Do not invoke it until the single-ticket workflow has
been demonstrated reliable and the human explicitly enables its evaluation.
Its upstream files remain unchanged and Codex may still list it as enabled;
this is an execution policy, not a Codex runtime configuration toggle.
