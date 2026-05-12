# Repository standards

Every public repository under [github.com/humanbound](https://github.com/humanbound)
follows the conventions documented here. The standards are **descriptive** —
they record what our repos already look like so new ones can match, and so
contributors know what to expect when they land on any Humanbound project.

Per-repo `CONTRIBUTING.md` files should link here as the source of truth for
cross-cutting conventions. Repo-specific guidance (build steps, test
commands, package layout) lives in the repo's own files.

## How to read this document

Each rule has an **ID** (`A1`, `B2`, …), a **requirement**, and a
**verifiable artifact** — the concrete file, header, or pattern that satisfies
the rule. A simple compliance script can grep against the artifact column.

Changes to this standard are deliberate. Open a PR explaining the rationale;
landed changes generate work for every repo that needs to come into
compliance, so we batch them.

---

## A — First-touch experience

The first 100 lines of every `README.md` follow the same skeleton.
A reader landing on any Humanbound repo should recognise the layout instantly.

| ID | Requirement | Verifiable artifact |
|---|---|---|
| A1 | Centered logo + `<h3 align="center">` project name + two-line tagline | `<picture>` block referencing `assets/logo-{light,dark}.svg`; H3 immediately below |
| A2 | Pill nav after the tagline: 4–6 anchors separated by `&middot;`, ending with `Documentation` and `Contributing` | `<p align="center">` containing `&middot;`-separated `<a>` tags |
| A3 | Badge row: CI status, license, Discord, Documentation. Python packages add PyPI version, supported Python versions, and downloads | Shields.io badges with `style=flat-square&color=FD9506` |
| A4 | A `> 📖` markdown blockquote after the badges, pointing at the relevant area of `docs.humanbound.ai` | Single blockquote line |
| A5 | A copy-pastable Quick Start within the first 100 lines | Fenced shell block with the canonical install command |
| A6 | Contributing footer block with four bullets: 🐛 bug, 💡 feature, 🔒 security, 💬 Discord | Anchors to `issues/new/choose`, `SECURITY.md`, `discord.gg/gQyXjVBF` |
| A7 | License footer naming the licence AND linking the other public Humanbound repos by name | `[Apache-2.0](./LICENSE)` plus inline links to sibling repo URLs |

---

## B — Governance files

Every public repo carries the same set of root-level governance files.

| ID | Requirement | File |
|---|---|---|
| B1 | Apache-2.0 licence, full text | `LICENSE` |
| B2 | Private vulnerability disclosure with the 72h / 7d / 90d timeline | `SECURITY.md` |
| B3 | Contributor Covenant code of conduct, private reporting to `conduct@humanbound.ai` | `CODE_OF_CONDUCT.md` |
| B4 | Contributor Licence Agreement with a one-paragraph rationale | `CLA.md` |
| B5 | Trademark policy distinguishing "code is open" from "name is not" | `TRADEMARK.md` |
| B6 | SPDX header on every new source file: `# SPDX-License-Identifier: Apache-2.0` and `# Copyright (c) 2024-<year> Humanbound` | Source-file grep |

The fallback versions of `CONTRIBUTING.md`, `SECURITY.md`,
`CODE_OF_CONDUCT.md`, and the issue / PR templates live in this `.github`
repo. Repos that need to customise them ship their own; otherwise GitHub
serves the fallbacks automatically.

---

## C — Developer scaffolding

Each public repo ships the same developer-facing scaffolding.

| ID | Requirement | File |
|---|---|---|
| C1 | `.github/workflows/ci.yml` runs on `push` to `main` and every `pull_request`, with `concurrency.cancel-in-progress` enabled | CI workflow |
| C2 | `.github/workflows/release.yml` triggers on tag patterns (`v*` or `v-<pkg>-*`) and creates a GitHub Release from the matching CHANGELOG section | Release workflow |
| C3 | `.github/dependabot.yml` covers at least `github-actions` weekly; Python projects also cover `pip`. Grouped `minor-and-patch` updates | dependabot config |
| C4 | `.github/ISSUE_TEMPLATE/{bug_report,feature_request,config}.yml` — form-based, capture version + Python version + OS where relevant | Three issue templates |
| C5 | `.github/PULL_REQUEST_TEMPLATE.md` with Summary, Type-of-change, Tested-in, Checklist, Linked-issue sections | PR template |
| C6 | `.pre-commit-config.yaml` covering trailing whitespace, EOF newline, YAML/TOML/JSON validity, large-file guard, and the language-appropriate linter (`ruff` for Python, `shellcheck` for bash) | Pre-commit config |

Reusable workflow templates for `ci-python.yml`, `ci-shell.yml`, and
`release.yml` live in this repo's `workflow-templates/` directory and appear
under *Actions → New workflow → Templates from your organisation*.

---

## D — Release discipline

These rules govern how releases are cut, versioned, and documented.

| ID | Requirement | File |
|---|---|---|
| D1 | `CHANGELOG.md` follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). Always carries `## [Unreleased]` at the top. Sections: Added / Changed / Deprecated / Removed / Fixed / Security | `CHANGELOG.md` |
| D2 | Semantic Versioning per project. Multi-package repos version each project independently and prefix tags accordingly (`v-<pkg>-<version>`) | Tag pattern |
| D3 | `ROADMAP.md` with sections **Now / Next / Later / Not doing / Release cadence**. "Not doing" must be honest — it bounds expectations | `ROADMAP.md` |
| D4 | `CONTRIBUTING.md` with sections **Quick start / Filing issues / CLA / Change workflow / Code style / Tests / How changes ship / Community / Code of Conduct** | `CONTRIBUTING.md` |
| D5 | CHANGELOG link references at the bottom (`[Unreleased]: .../compare/...`) | `CHANGELOG.md` footer |

---

## E — Cross-linking

Repos cross-link so readers can find related projects.

| ID | Requirement | Where |
|---|---|---|
| E1 | The README's License section names the **other** public Humanbound repos by name and links them | README footer |
| E2 | The README points at `docs.humanbound.ai` in three places: the badge row, the docs callout, and the relevant sub-area path | README |
| E3 | Brand assets live at the same path in every repo: `assets/logo-light.svg` and `assets/logo-dark.svg` | Filesystem |
| E4 | Discord invite is `discord.gg/gQyXjVBF` everywhere. One source of truth | grep `discord.gg/` |
| E5 | When a package interoperates with a sibling (e.g. `pip install humanbound[firewall]`), the README has a "Using with X" section that names and links the sibling | README |

---

## F — Tone

Humanbound's open-source surface is technical. The rules below keep it
consistent across repos.

| ID | Requirement |
|---|---|
| F1 | No marketing verbs in OSS docs, code, comments, or CLI output: no "upsell", "convert", "upgrade to", "sign up", "free tier", "premium", "pricing" |
| F2 | The hosted Humanbound platform is mentioned **factually** as one execution target among others. When a local or air-gapped option exists, mention it first |
| F3 | Code comments and CLI output reference *capabilities*, not commercial tiers |
| F4 | If a package requires the hosted platform to function (e.g. an MCP client that dispatches to the backend), say so plainly in the README's Requirements section |
| F5 | Rationale for governance choices ("why a CLA", "why Apache-2.0", "why this trademark policy") stays matter-of-fact: operational flexibility, contributor's own use preserved, future commercial-channel options. No defensive language |

---

## G — Maturity signalling

Repos on `0.x` are in preview — their public surface (CLI flags, slash
commands, file layouts, import paths) may change before `1.0`. Readers
deserve to know that at a glance.

| ID | Requirement | Verifiable artifact |
|---|---|---|
| G1 | Pre-`1.0` repos carry a `status: preview` badge as the **first** entry in the README badge row | `<img src="https://img.shields.io/badge/status-preview-FD9506?style=flat-square" alt="Status: preview"/>` |
| G2 | Pre-`1.0` repos carry a `> ⚠ Preview` callout in the README immediately after the docs callout. The callout names the surfaces that may change before `1.0` and tells readers to pin to a specific tag if they depend on a particular shape | Markdown blockquote starting with `> ⚠ **Preview` |
| G3 | The release workflow marks GitHub Releases for `0.x` tags as pre-release. Tags at `1.0` or above flip to stable without manual intervention | `prerelease: ${{ startsWith(<version>, '0.') }}` (or equivalent) in `.github/workflows/release.yml` |
| G4 | The badge and callout are removed in the same PR that lands the first `1.0` release. No "preview" signal lingers after the public surface is committed-to | PR diff |

Repos at `1.0` or above do **not** carry the preview badge or callout. The
maturity signal is the version number itself.

---

## Adopting these standards

For a new repo, the easiest path is to copy the layout of an existing
compliant repo (currently
[`humanbound`](https://github.com/humanbound/humanbound) and
[`humanbound-firewall`](https://github.com/humanbound/humanbound-firewall))
and then walk this document section by section.

For an existing repo coming into compliance, the recommended sequencing is:

1. **D + B first** — rewrite `CHANGELOG.md`, `ROADMAP.md`, `CONTRIBUTING.md`
   to match the structure here. These are the artefacts a sceptical reader
   checks first.
2. **A second** — realign `README.md` to the skeleton (logo, badges, pill
   nav, quick start, footers).
3. **C third** — land the `.github/` scaffolding in one PR
   (`ISSUE_TEMPLATE/`, `dependabot.yml`, `PULL_REQUEST_TEMPLATE.md`,
   `release.yml`, `.pre-commit-config.yaml`).
4. **E + F as a sweep** — cross-link siblings, fix any tone drift, then tag
   the release.

## Compliance audits

A periodic audit can verify the rules above by grepping each repo for the
verifiable artifact in each row. The audit checklist is maintained by
Humanbound maintainers.
