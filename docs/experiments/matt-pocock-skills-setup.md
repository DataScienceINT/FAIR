# Matt Pocock Skills Setup Experiment

The sections through "Open questions" record the original local-tracker setup.
The follow-up sections below record later preparation and GitHub tracker activation.

## Purpose

Evaluate a lightweight engineering workflow for F-AI-R development.
This is tooling/setup only; the workflow is experimental and is not an adopted F-AI-R architecture.

## Environment

- SURF Research Cloud: `fairworkspace4.ombion.src.surf-hosted.nl`, user `mliem2`.
- Ubuntu 22.04.5 LTS, x86_64.
- Intended IDE: VS Code Remote-SSH; this setup was executed over authorized SSH from a local Codex session.
- Target coding agent: Codex.
- Repository: `DataScienceINT/FAIR` at `/home/mliem2/FAIR`.
- Starting branch: `main` at `88313a6`; initial working tree clean.
- Experiment branch: `experiment/matt-pocock-skills`.
- Git `2.34.1`; Node.js `v24.21.0`; npm/npx `11.19.0`.

Missing Node tooling was installed after explicit user authorization. Official Node LTS
binaries were downloaded from `https://nodejs.org/dist/v24.21.0/` and SHA-256 checked
against the published checksum. Installation is user-local at
`~/.local/share/node-v24.21.0-linux-x64/`, with `node`, `npm`, and `npx` symlinks
in `~/.local/bin/`. The existing `~/.profile` already adds that directory to PATH;
no shell configuration or system packages were changed.

## Upstream

- Repository: https://github.com/mattpocock/skills
- Inspected revision: `4588b32ecab9ecc9fc8cc6b6c5e7d675b6004b0d`.
- All 23 installed skill files match this revision byte for byte.
- Installation command: `npx skills@latest add mattpocock/skills`.
- Installer version resolved: `skills@1.7.0`.
- Interactive choices: exactly the seven skills below; Codex only; project scope.
- Declined the optional `find-skills` offer.

## Installed skills

- setup-matt-pocock-skills
- grill-with-docs
- grilling
- domain-modeling
- prototype
- handoff
- to-spec

Installer output: 23 files under `.agents/skills/<skill>/` plus `skills-lock.json`.
Installed skill contents were not edited. No global skills or Claude Code plugin were installed.

## Repository setup

Applied the installed prompt-driven `setup-matt-pocock-skills` once, using the user's
preselected local tracker and the recommended single-context domain layout:

- Created `AGENTS.md` with only the Agent skills tracker/domain pointers.
- Created `docs/agents/issue-tracker.md` from the local tracker template, omitting
  unused wayfinding operations and triage-label references.
- Created `docs/agents/domain.md` from the domain template, scoped to this single-context repository.
- Created this experiment report separately.

No pre-existing instructions or documentation were overwritten. No triage configuration
was created. `.scratch/`, `GLOSSARY.md`, and `docs/adr/` are configured destinations,
created lazily when there is actual content; this setup creates no tickets, domain terms, or ADRs.

## Experimental workflow

`grill-with-docs → optional prototype → to-spec`

Prototype is NOT a mandatory phase. Use it only when a design uncertainty requires
runnable/observable evidence that conversation alone cannot resolve.
None of these workflow skills was invoked during setup.

## Tracker choice

The initial experiment uses local markdown under `.scratch/<feature-slug>/`, with
`spec.md` for a spec and `issues/<NN>-<slug>.md` for individual tickets.
It does not write GitHub issues.

## Verification

Commands/checks used:

- `hostname`, `whoami`, `pwd`, `uname -a`, `cat /etc/os-release`.
- `git remote -v`, `git branch --show-current`, `git status --short --branch`,
  `git log -5 --oneline`, and initial `git status --short`.
- `git --version`, `node --version`, `npm --version`, `npx --version`;
  also checked Node tooling in a fresh login shell.
- `git ls-remote https://github.com/mattpocock/skills.git HEAD`; read README and all seven SKILL.md files.
- File inventory, front matter, supporting metadata, and SHA-256 comparison with upstream.
- `git status --short`, `git diff --stat`, `git diff`, and `git diff --check`.
- `git status --short --untracked-files=all` and per-file `git diff --no-index`
  for reviewing new, untracked files without staging.
- `test -f surf/fair-hello-world.yml`, SHA-256 comparison, and
  `git diff --exit-code HEAD -- surf/fair-hello-world.yml`.

PASS: all seven skills have readable manifests and Codex metadata under the documented
repository discovery path, `.agents/skills/`.
[Official Codex discovery documentation](https://learn.chatgpt.com/docs/build-skills).
PASS: installed files match inspected upstream and remain unmodified.
PASS: SURF proof-of-life playbook remains present and unchanged, SHA-256
`e1c3ee76b3b317ca31e36ab9b7905fa5dcecf7cc98e4d6c146e21fa6b8c9daf6`.

All additions are untracked and uncommitted. Normal `git diff` and `git diff --stat`
are empty because these commands omit untracked files. No existing tracked files changed.

## Open questions

- End-to-end Codex IDE discovery has not been exercised from the remote FAIR workspace.
  The remote `codex` CLI is not on PATH; no CLI or credentials were installed.
  Open FAIR in the remote IDE and check the skill selector; restart Codex if needed.
- Upstream `to-spec` asks for triage vocabulary and a `ready-for-agent` label even though
  setup explicitly omits triage configuration when `triage` is absent. Its behavior
  with this minimal setup remains untested; resolve before the first real spec session.
- Whether a future design question needs a prototype is undecided.
- No framework architecture, validation criteria, scientific evidence claims, or data
  processing was selected or implemented. Prototype capture/commit behavior is not tested;
  this setup task's no-commit/no-push rule remains in force.

## Follow-up: full workflow preparation (2026-10-06)

The intended tracker has changed to GitHub Issues. The dedicated
`experiment/matt-pocock-full-workflow` branch adds the downstream skills and an
initial execution policy. Tracker activation stopped because `gh` was missing;
local markdown is not a fallback. This section records the change of intent and
preserves the original setup history above. See
[the full workflow preparation report](matt-pocock-full-workflow.md) for current
readiness, proposed GitHub conventions, verification, and remaining blockers.

## Follow-up: GitHub tracker activation (2026-10-06)

After user-local installation and interactive authentication of `gh`, repository
access was verified as `michael-liem`. GitHub Issues in `DataScienceINT/FAIR` is
now the active tracker in `AGENTS.md` and `docs/agents/issue-tracker.md`, explicitly
superseding the initial local convention. The history above describes the earlier
experiment and remains preserved. At activation, the missing `ready-for-agent`
label was proposed but not created; spec/ticket publication was blocked until it
became available.
No issues, labels, implementation, commits, or pushes were created during activation.
The full workflow report records the current state and the retained execution policy.

## Follow-up: readiness label and development guide (2026-10-06)

After separate explicit human authorization, `ready-for-agent` was created and
verified in `DataScienceINT/FAIR`, with description "Ready for the next agent step"
and color `0e8a16`. No issues were created. The missing-label gate is resolved;
human review and the single-issue execution policy remain required.

The subsequent documentation-only task added the verified SURF runtime, generic
SSH/Remote-SSH setup, user-local tooling, catalog composition supplied by the
operator, and reproduction order to [README.md](../../README.md). It synchronized
the current label status while preserving the earlier experiment history. It
created no issues or labels and changed no infrastructure or installed skills.
