# Full Matt Pocock workflow preparation

Initially prepared on 2026-10-06, with repository-local GitHub tracker activation
completed after authentication on the same day. The readiness label was later
created with explicit human authorization and verified. This is engineering
tooling setup, not an adopted F-AI-R scientific architecture. All setup changes
remain uncommitted for human review.

## Starting state and history

- Host: `fairworkspace4.ombion.src.surf-hosted.nl`; user: `mliem2`.
- Repository: `/home/mliem2/FAIR`; remote: `DataScienceINT/FAIR`.
- Clean starting branch: `experiment/matt-pocock-skills` at
  `d27d9ba8ba612568b7bf8daa484a5ed309f1035a`.
- Created `experiment/matt-pocock-full-workflow` from that commit; the original
  branch remains unchanged.
- The [initial experiment](matt-pocock-skills-setup.md) used local markdown.
  Initial full-workflow preparation paused the tracker switch because `gh` was
  missing. GitHub Issues is now active in the local configuration; the original
  local tracker has been explicitly superseded. Domain configuration is unchanged.

## Upstream and installation

Rechecked upstream `main` with `git ls-remote` and read the current README and
relevant skill manifests at revision
`4588b32ecab9ecc9fc8cc6b6c5e7d675b6004b0d`. It is unchanged from the audit.

Used the canonical upstream installer, resolved as `skills@1.7.0`:

```bash
npx --yes skills@latest add mattpocock/skills --agent codex --skill to-tickets implement implement-spec code-review retro tdd writing-for-agents --yes
```

Added `to-tickets`, `implement`, `implement-spec`, `code-review`, and `retro`.
Added their supporting skills `tdd` and `writing-for-agents`, including bundled
reference files. Installation is Codex-only and project-local under
`.agents/skills/`; `skills-lock.json` records the additions. Upstream skill files
were not edited.

`triage` is optional for incoming requests and unnecessary for human-approved
planned work. `ask-matt` is an optional workflow router. Neither was installed.
`codebase-design` is a conditional TDD dependency when the module interface or
testing seam is itself uncertain; it was not installed for the minimum setup.
If that condition arises, install that reference before following that TDD branch.
This does not prevent TDD at already agreed seams.

Sources: [installation](https://github.com/mattpocock/skills/blob/4588b32ecab9ecc9fc8cc6b6c5e7d675b6004b0d/README.md),
[workflow guide](https://github.com/mattpocock/skills/blob/4588b32ecab9ecc9fc8cc6b6c5e7d675b6004b0d/skills/engineering/ask-matt/SKILL.md),
[TDD](https://github.com/mattpocock/skills/blob/4588b32ecab9ecc9fc8cc6b6c5e7d675b6004b0d/skills/engineering/tdd/SKILL.md).

## Intended workflow and execution policy

`grill-with-docs -> optional prototype -> to-spec -> to-tickets -> GitHub Issues -> implement one issue -> code-review -> human acceptance -> repeat -> retro`

The active execution policy is
[`docs/agents/workflow-experiment.md`](../agents/workflow-experiment.md), linked
from `AGENTS.md`. `implement-spec` is installed but held out of execution until
the single-ticket experiment is proven reliable and the human enables evaluation.
No workflow stage was executed by this setup task.

## History: GitHub readiness initially blocked

`gh --version` and `gh auth status` both reported `gh: command not found`.
Authentication and repository permissions were therefore unverified. No
credentials were requested or inspected. Under the user's explicit stop rule,
the GitHub configuration portion stopped; no tracker switch or remote writes
were performed. Spec/ticket creation and implementation were paused, with no local
markdown fallback.

The next required steps were to install `gh`, complete interactive authentication,
verify repository access, and inspect labels before activating the configuration.

## GitHub tracker activation (2026-10-06)

`gh` is now installed user-locally at `/home/mliem2/.local/bin/gh`, version
`2.102.0` (2026-09-30). Browser/device authentication was completed interactively.
`gh auth status` succeeds as `michael-liem`; the Git protocol is HTTPS.
`gh repo view DataScienceINT/FAIR` succeeds. Structured repository metadata
confirms Issues are enabled and the current account has admin access. No write
operations were used to test access, and no credentials are recorded here.

The authoritative, active configuration is now
[`docs/agents/issue-tracker.md`](../agents/issue-tracker.md), linked from
`AGENTS.md`. It documents GitHub issue reading, publication, body updates,
comments, native blockers with a textual fallback, readiness, and human-reviewed
completion. It replaces the earlier draft and local tracker; `.scratch/` is not
a fallback. Historical setup descriptions above and in the initial report are
preserved. The single-issue execution policy and `implement-spec` execution ban
remain in [`docs/agents/workflow-experiment.md`](../agents/workflow-experiment.md).

The label list was fetched read-only with `gh api --method GET --paginate`.
At activation, the repository had its nine default labels, and
**`ready-for-agent` was absent**. It is required by unmodified `to-spec` and is the
retained default for `to-tickets`; its mapping and purpose were documented in the
active tracker configuration.
No other workflow labels or triage automation are proposed. Remote label creation
required explicit human authorization; none was created during activation.
Spec and ticket publication was blocked until the label became available.

Rechecked upstream `main` at
`4588b32ecab9ecc9fc8cc6b6c5e7d675b6004b0d`; it is unchanged. Current `to-spec` and
`to-tickets` files still match upstream byte for byte. Dependency endpoint shapes
were checked against [GitHub's issue dependency API](https://docs.github.com/en/rest/issues/issue-dependencies).
Actual issue publication, comment writes, dependency writes, closure, and all
implementation stages remain untested; this task performed local configuration only.

Comment editing and completion flags were checked against the official
[comment](https://cli.github.com/manual/gh_issue_comment) and
[close](https://cli.github.com/manual/gh_issue_close) command documentation.

## Discovery, verification, and untested stages

- `npx skills@latest list --agent codex --json` reports all 14 skills as
  project-local Codex installations.
- Codex CLI `0.160.1` app-server `skills/list`, queried for `/home/mliem2/FAIR`
  with `forceReload: true`, discovers all 14 repository skills, enabled, with no
  project loading errors. Only initialization and discovery were requested;
  no agent thread, turn, or workflow skill was invoked.
- Discovery is verified; end-to-end execution is separate. Previous setup and
  first-grill glossary capture are evidenced by the original report and commit
  `d27d9ba`. Prototype, spec publication, ticket publication, implementation,
  review, retrospective, and autonomous orchestration remain untested.
- Implementation still needs a real reviewed issue, agreed test seams, and
  feature-appropriate check commands. No application test/typecheck pipeline was
  introduced by this setup. Review needs a comparison point and issue/spec.
- `retro` is available for an explicitly requested session retrospective; it
  does not depend on GitHub activation. `implement-spec` remains disabled for
  execution by policy even though its discovery metadata says enabled.
- Initial preparation verification included upstream byte comparisons, lock/manifest
  consistency, Git diff review including untracked additions, whitespace checks,
  and unchanged-byte checks for `surf/fair-hello-world.yml`, `GLOSSARY.md`, the
  original skills, and the tracker/domain files.
- At initial preparation, all 40 installed skill files matched upstream byte for
  byte. The seven original lock entries and 27 protected files are unchanged.
  Tracked diff: three files, 58 added lines. There are 19 untracked files:
  17 skill files and two workflow documents. Whitespace checks passed for both
  tracked changes and untracked additions; secret-pattern scans found no matches.
- Initial preparation created no real GitHub issues, labels, specifications,
  implementation tickets, commits, pushes, scientific functionality, or secrets,
  and executed no workflow stages or autonomous implementation.

## Readiness label and development guide (2026-10-06)

The user separately authorized creation of exactly one label. `ready-for-agent`
was absent before that action and was created in `DataScienceINT/FAIR` with
description "Ready for the next agent step" and color `0e8a16`. GitHub access and
the resulting label were verified. No issues, other labels, local files, commits,
or pushes were created by that label task.

The subsequent documentation-only task rechecked runtime versions and label
availability, added a reproducible development guide to [README.md](../../README.md),
and synchronized the active tracker/policy and experiment reports. The runtime is
Ubuntu 22.04.5 LTS, Node 24.21.0, npm/npx 11.19.0, and `gh` 2.102.0, with tools
under `~/.local/bin`. Remote Codex extension installation is present on disk;
live IDE activation and catalog composition are operator-confirmed. Exact portal
component versions and parameters are not exported or independently audited here.
No remote writes, infrastructure changes, installed-skill edits, staging, commits,
or pushes were performed during this documentation task.

## Remaining execution requirements

- `to-spec`: the readiness label is available; invoke the skill explicitly with
  an agreed plan and testing seams, rechecking the label before publication.
- `to-tickets`: recheck label availability; the human must review the spec before
  generation and approve the breakdown before publication, and tickets need
  acceptance criteria and correct blocking relationships.
- `implement`: start from one reviewed, unblocked issue with acceptance criteria,
  agreed testing seams, and feature-appropriate checks. Completion requires
  `code-review` and human acceptance before closure.
- `retro` is installed and available but remains untested. `implement-spec`
  remains installed and forbidden for execution pending successful single-ticket
  evaluation and explicit human enablement.

The earlier tracker activation updated only `AGENTS.md`, `docs/agents/issue-tracker.md`,
`docs/agents/workflow-experiment.md`, and the two existing experiment reports.
All pre-existing skill installation changes were preserved. `GLOSSARY.md` and
`surf/fair-hello-world.yml` remain byte-for-byte unchanged. No issues, labels,
commits, pushes, or F-AI-R implementation were produced during that activation.
