# FAIR

F-AI-R framework development and SURF deployment

## Development environment

The current development workspace runs **Ubuntu 22.04.5 LTS (x86_64)** on
SURF Research Cloud. Development uses SSH, VS Code Remote-SSH, and Codex enabled
in the Remote Extension Host, with the repository cloned on the workspace.
Project-local Codex skills live in `.agents/skills/`.

### SURF Research Cloud catalog

The operator-confirmed catalog composition is:

- SRC-OS
- SRC-CO
- SRC-Nginx
- SRC-External plugin
- FAIR-Hello-World

`FAIR-Hello-World` is the project-specific component for the initial authenticated
web proof-of-life. Its playbook is [surf/fair-hello-world.yml](surf/fair-hello-world.yml).
The catalog item uses **web-interface** access through the Research Cloud reverse
proxy and SRAM authentication. This hello-world deployment does not define the
eventual F-AI-R scientific architecture.

Create/configure the component and catalog item in Research Cloud, using that
composition and the project playbook, before creating a workspace. Exact catalog
versions, parameters, and component wiring live in the portal and are not exported
here; check them there when recreating the workspace.

### SSH and VS Code

Add your **public** SSH key to your SRAM profile and log in to the Research Cloud
portal at least once so the key can be provisioned. Keep the private key on your
local computer. Use your Research Cloud username and the new workspace's address
in a local SSH configuration such as:

```sshconfig
Host fair-surf
    HostName <workspace-ip-or-hostname>
    User <research-cloud-username>
    IdentityFile ~/.ssh/<private-key>
```

In VS Code, install Remote-SSH and run **Remote-SSH: Connect to Host** →
`fair-surf`. In a remote terminal, clone the repository if it is not already there:

```bash
cd ~
git clone https://github.com/DataScienceINT/FAIR.git FAIR
```

Open `/home/<user>/FAIR` in the connected window. Install/enable the Codex extension
under **SSH: fair-surf** so it runs in the Remote Extension Host. In that window's
terminal, verify `hostname`, `whoami`, and `pwd` identify the intended workspace,
Research Cloud user, and remote repository.

See [SURF SSH access](https://servicedesk.surf.nl/wiki/spaces/WIKI/pages/195854434/Workspace%2Baccess%2Bwith%2BSSH),
[VS Code Remote-SSH](https://code.visualstudio.com/docs/remote/ssh), and the
[Codex extension guide](https://learn.chatgpt.com/docs/codex/ide).

### User-local tooling

This experiment's development tools are installed without depending on sudo:

| Tool | Verified version | Executable location |
| --- | --- | --- |
| Node.js | 24.21.0 | `~/.local/bin/node` |
| npm / npx | 11.19.0 | `~/.local/bin/npm`, `~/.local/bin/npx` |
| GitHub CLI | 2.102.0 | `~/.local/bin/gh` |

For the same Linux x86_64 setup, download `node-v24.21.0-linux-x64.tar.xz` and
`SHASUMS256.txt` from the [official Node release](https://nodejs.org/dist/v24.21.0/).
Verify the archive against its SHA-256 entry, extract it under `~/.local/share/`,
and link its `bin/node`, `bin/npm`, and `bin/npx` into `~/.local/bin/`.
For `gh`, download `gh_2.102.0_linux_amd64.tar.gz` and `gh_2.102.0_checksums.txt`
from the [official GitHub CLI release](https://github.com/cli/cli/releases/tag/v2.102.0),
verify the archive's SHA-256 entry, and install its `bin/gh` as `~/.local/bin/gh`.
Create the destination directories as needed. Use matching archives for other
architectures; these versions describe the verified environment, not an upgrade policy.

Ensure `~/.local/bin` is on PATH, including in remote terminals. If needed, add
`export PATH="$HOME/.local/bin:$PATH"` to your own shell startup configuration.
Check `node --version`, `npm --version`, `npx --version`, `gh --version`, and
`command -v gh`.

Authenticate interactively with `gh auth login` (GitHub.com, HTTPS, browser/device
login). Complete authentication yourself in the browser, then run:

```bash
gh auth status
gh repo view DataScienceINT/FAIR
```

Keep authentication output and credentials out of repository documentation.
**Security note:** credential-storage hardening remains a future task.

## Engineering workflow experiment

The Matt Pocock workflow is an **engineering workflow experiment**, separate from
F-AI-R scientific architecture and validation:

`grill-with-docs → optional prototype → to-spec → to-tickets → GitHub Issues → implement one issue at a time → code-review → retro`

GitHub Issues in `DataScienceINT/FAIR` is the active tracker, superseding the
initial local-markdown experiment. The verified `ready-for-agent` label means
“Ready for the next agent step”. It does not replace human approval or blocker
checks. Human review is required before ticket generation, ticket publication,
and implementation. Each issue needs acceptance criteria; completion requires
code review and human acceptance. `implement-spec` is installed but intentionally
not enabled for autonomous execution by repository policy.

The authoritative details and retained history are:

- [Execution policy](docs/agents/workflow-experiment.md)
- [GitHub tracker operations and readiness](docs/agents/issue-tracker.md)
- [Initial skills experiment](docs/experiments/matt-pocock-skills-setup.md)
- [Full workflow setup and verification](docs/experiments/matt-pocock-full-workflow.md)

## Recommended setup order

1. Configure the SURF component and catalog item described above.
2. Create an Ubuntu 22.04.5 LTS workspace from it.
3. Add your SSH public key through SRAM.
4. Connect using VS Code Remote-SSH.
5. Clone `DataScienceINT/FAIR` on the workspace and open `/home/<user>/FAIR`.
6. Enable Codex in the Remote Extension Host.
7. Install user-local Node/npm/npx, then use the project-local skills already in
   `.agents/skills/`. If bootstrapping them, use the upstream installer below.
8. Install user-local `gh` and complete interactive `gh auth login`.
9. Check the Codex skill selector (all 14 skills), `gh auth status`, and
   `gh repo view DataScienceINT/FAIR`. Restart Codex if discovery has not refreshed.
10. Test each workflow stage with human review before scientific use. Discovery
    and GitHub access are verified; the downstream workflow is not yet tested end to end.

To bootstrap the audited set, run from the remote repository root:

```bash
npx --yes skills@latest add mattpocock/skills --agent codex \
  --skill setup-matt-pocock-skills grill-with-docs grilling domain-modeling \
  prototype handoff to-spec to-tickets implement implement-spec code-review \
  retro tdd writing-for-agents --yes
```

This installs for Codex in the project, not globally. The audited installer was
`skills@1.7.0`; the installed upstream revision is recorded in the experiment
reports, and `skills-lock.json` records the skills. Recheck upstream changes when
bootstrapping with `latest`. See [Codex skill discovery](https://learn.chatgpt.com/docs/build-skills).
