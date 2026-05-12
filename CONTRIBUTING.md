# Contributing to Humanbound projects

This document is the **org-wide fallback** — repositories that ship their own
`CONTRIBUTING.md` override it. If you're contributing to a specific repo,
check that repo's `CONTRIBUTING.md` first.

For the conventions that apply to **every** public Humanbound repo (README
skeleton, CHANGELOG format, governance files, CI scaffolding, tone), see
[`REPO_STANDARDS.md`](./REPO_STANDARDS.md).

## Quick start

1. Fork the repository and clone your fork
2. Create a branch off `main`
3. Make focused changes — one concern per PR
4. Add or update tests for your change
5. Run the repo's local quality checks (typically `pre-commit run --all-files`
   plus the project's test command)
6. Update the repo's `CHANGELOG.md` under `[Unreleased]`
7. Open a pull request using the template

## Filing issues

Bugs, feature requests, and questions all live in the repo's GitHub Issues.
Use the provided forms:

- **Bug report** — include the project version, your platform, and a minimal
  reproduction
- **Feature request** — describe the problem first, then the proposed
  solution

**Do not file security issues publicly.** See the repo's `SECURITY.md` (or
the [fallback](./SECURITY.md)) for the private disclosure channel.

## Contributor License Agreement

Every external contribution to a Humanbound project must be covered by the
[Humanbound Contributor License Agreement](https://github.com/humanbound/humanbound/blob/main/CLA.md).
The CLA gives Humanbound the operational flexibility to evolve a project
(including offering managed services on the Humanbound Platform) while
preserving Your right to use Your own contributions elsewhere and Your
authorship in the project's git history.

The first time you open a pull request, the CLAAssistant bot will comment
with a one-line instruction to sign. Sign once and all your future
contributions across Humanbound repositories are covered.

## Code style

- Every new source file gets the SPDX header:
  ```
  # SPDX-License-Identifier: Apache-2.0
  # Copyright (c) 2024-2026 Humanbound
  ```
- Python projects: `ruff` for lint + format, `mypy` for type checking (see
  the repo's `pyproject.toml` for exact configuration)
- Shell scripts: `bash` with `set -euo pipefail`, kept `shellcheck`-clean
  (document any deliberate exceptions inline with a `# shellcheck disable`
  comment and a one-line reason)
- JSON / YAML / TOML: 2-space indent, trailing newline
- `.pre-commit-config.yaml` enforces the above; run `pre-commit install`
  after cloning

## Tests

- Every new feature needs a test
- Every bug fix needs a regression test
- The repo's CI matrix is the contract — if CI passes on every supported
  platform, the change is mergeable

## How changes ship

Maintainers cut releases on a rolling basis, not on a fixed cadence.

| Step | Who | What |
|---|---|---|
| PR review | Maintainer | Reviews code, tests, CHANGELOG |
| Merge to `main` | Maintainer | Squash merge |
| Tag `vX.Y.Z` (or `v-<pkg>-<version>` for multi-package repos) | Maintainer | Triggers `release.yml` |
| Publish artifacts | CI | PyPI via Trusted Publishing for Python projects; GitHub Release for all repos |

Versioning follows [Semantic Versioning](https://semver.org).

## Community

- **Discord** — [discord.gg/gQyXjVBF](https://discord.gg/gQyXjVBF) for
  questions and discussion
- **GitHub Discussions** — on each repo, for longer-form topics
- **Documentation** — [docs.humanbound.ai](https://docs.humanbound.ai)

## Code of Conduct

Participation in any Humanbound project is governed by our
[Code of Conduct](./CODE_OF_CONDUCT.md). Violations can be reported
privately to [conduct@humanbound.ai](mailto:conduct@humanbound.ai).
