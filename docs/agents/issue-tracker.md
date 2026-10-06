# Issue tracker: GitHub Issues

The active tracker for specs and implementation issues is GitHub Issues in
`DataScienceINT/FAIR`: https://github.com/DataScienceINT/FAIR/issues.
Use the authenticated `gh` CLI and scope every issue command with
`--repo DataScienceINT/FAIR`; API endpoints below include the repository explicitly.

This supersedes the initial local-markdown tracker under `.scratch/<feature>/`.
Keep that experiment's history in `docs/experiments/matt-pocock-skills-setup.md`;
local files are not a fallback issue tracker. Domain documentation remains
configured separately in `docs/agents/domain.md`.

## Execution policy

Read `docs/agents/workflow-experiment.md` before using the workflow. This
configuration task authorizes local documentation changes only: no remote issue,
comment, dependency, or label writes. The commands below describe future workflow
operations, not actions to execute during setup.

After setup review, an explicitly requested workflow can publish a spec; ticket
generation requires human review of that spec, and publication requires approval
of the ticket breakdown. Implementation proceeds one issue per invocation.

## Read and publish work

- **Fetch an issue:** `gh issue view <number> --repo DataScienceINT/FAIR --comments`.
  Read the full body and conversation, then fetch structured fields when needed:
  `gh issue view <number> --repo DataScienceINT/FAIR --json number,title,body,state,labels,comments`.
- **List open issues:** `gh issue list --repo DataScienceINT/FAIR --state open --limit 100 --json number,title,body,labels`.
  Increase the limit or paginate with the API when more results are needed.
- **Publish a spec or ticket:** prepare the exact Markdown body in a temporary
  file outside the repository, then use
  `gh issue create --repo DataScienceINT/FAIR --title "<title>" --body-file <file> --label ready-for-agent`.
  One issue holds the spec; each approved implementation ticket gets its own
  issue with acceptance criteria, a parent-spec reference, and blockers.
  Publish blockers first so later tickets can reference their real issue numbers.
- **Update an issue body:** `gh issue edit <number> --repo DataScienceINT/FAIR --body-file <file>`.
  Read the current body first and preserve unrelated content and review history.
- **Add a comment:** `gh issue comment <number> --repo DataScienceINT/FAIR --body-file <file>`.
- **Update the current user's last comment:** use the comment command above plus
  `--edit-last`, after verifying it is the intended comment. Otherwise add a new
  comment rather than overwrite an unrelated human comment.

When a skill says "publish to the issue tracker", create a GitHub issue under
these conventions and the execution policy. When it says "fetch the relevant
ticket", read the referenced GitHub issue and its comments. Use issue numbers or
URLs as context pointers for fresh implementation sessions.

## Readiness and status vocabulary

The required planned-work vocabulary maps the canonical **`ready-for-agent`**
role to the GitHub label **`ready-for-agent`**. It means the spec or ticket is
sufficiently specified for its next agent step. The label does not replace human
review, acceptance criteria, or blocker checks.

- `to-spec` applies this label when publishing the spec.
- `to-tickets` applies it to approved tickets by default. Upstream permits an
  explicit alternative instruction, but this experiment retains the default.
- Use GitHub's existing **open/closed** issue lifecycle; no additional workflow
  states or labels are configured.

The label was created with explicit human authorization and verified on
2026-10-06. Its description is "Ready for the next agent step" and its color is
`0e8a16`. The earlier missing-label gate is resolved; history is retained in the
experiment reports.
Before publication, recheck it read-only with
`gh api --method GET repos/DataScienceINT/FAIR/labels/ready-for-agent`.
If it is unavailable, stop publication and obtain explicit authorization before
creating it remotely; do not silently publish without it or fall back to local files.

The `triage` skill is not needed for this human-reviewed planned-work flow. This
section provides the readiness vocabulary requested by `to-spec` and `to-tickets`;
there is no full triage state machine or separate triage-label configuration.

## Parent spec and blockers

Each implementation issue references its parent spec in a `## Parent` section.
Prefer GitHub native sub-issues when available; otherwise the child body's
`Part of #<spec>` reference preserves the relationship. During `to-tickets`, keep
the parent spec's body and lifecycle unchanged.

Prefer GitHub's native **blocked by** dependencies:

- Fetch the blocker's numeric database ID:
  `gh api --method GET repos/DataScienceINT/FAIR/issues/<blocker-number> --jq .id`.
- Add a blocking edge during authorized ticket publication:
  `gh api --method POST repos/DataScienceINT/FAIR/issues/<ticket-number>/dependencies/blocked_by -F issue_id=<blocker-database-id>`.
  Use the database ID, not the issue number or node ID.
- Read blockers:
  `gh api --method GET --paginate repos/DataScienceINT/FAIR/issues/<ticket-number>/dependencies/blocked_by --jq '.[] | {number, state, state_reason}'`.

If native dependencies are unavailable, write `Blocked by: #<number>, #<number>`
in the ticket's `## Blocked by` section and read each referenced issue's state.
Use "None (can start immediately)" for an issue without blockers.

An issue is ready to implement only when its blockers have been accepted as
completed and closed. A blocker closed as not planned does not satisfy the
dependency: refer the scope change to the human. Select one ready issue at a time;
the readiness label alone does not establish that dependencies are satisfied.

## Completion

An implementation issue is complete only when its acceptance criteria are met,
agreed verification passes, `code-review` has run and its findings are addressed,
and the human accepts the result. Record verification and review evidence in an
issue comment, then close it with
`gh issue close <number> --repo DataScienceINT/FAIR --reason completed`.
Keep the parent spec open until all its implementation issues have been accepted.

**PRs as a request surface: no.** This retains upstream's default; incoming PR
triage is outside the initial experiment.

Based on the installed upstream
[GitHub tracker template](../../.agents/skills/setup-matt-pocock-skills/issue-tracker-github.md)
and [GitHub's issue dependency API](https://docs.github.com/en/rest/issues/issue-dependencies).
