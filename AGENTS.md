# AGENTS.md

Ansible role that installs and configures Userli (email user self-management web app) on Debian (trixie).

## Layout

- `defaults/main.yml`: all role variables with defaults; `vars/` holds internal values
- `tasks/`: `main.yml`, `preflight.yml`, `primary.yml`, `deployment.yml` (install/update), `metrics.yml`
- `templates/`, `handlers/`, `meta/main.yml`: config templates, handlers and role metadata
- `molecule/default/`: integration test (Docker, Debian 13) with `prepare.yml` for the PHP/webserver/DB setup
- `requirements.yml`: collections the role needs (`community.general`, `ansible.mysql`)

## Checks

- `ansible-lint .` must pass (config in `.ansible-lint`, excludes `molecule/` and `.github/`)
- `yamllint .` uses `.yamllint`
- `molecule test` runs the role in a container; CI does this via the shared `systemli/github-ansible-workflow`
- `ansible-lint` creates `.ansible/`; it is git ignored, never commit it

## Conventions

- Use fully qualified module names, quoted octal `mode` values and `true`/`false` booleans
- Give every task a `name`
- New or changed role variables need an entry in `defaults/main.yml` and the README
- Pin GitHub Actions to commit SHAs with a trailing `# vX.Y.Z` comment; Dependabot updates them

## Commits and PRs

- Write in English, use conventional commit titles (`feat:`, `fix:`, `chore:`, `ci:`; `!` for breaking changes)
- The PR title sets the release-drafter label (`enhancement`, `bug`, `chore`, `breaking`); a breaking change bumps the major version
- Open PRs as draft and fill in `.github/pull_request_template.md`: what changed and why, plus a breaking changes section if needed
- Do not list changed files or claim test results in the description; CI covers that
