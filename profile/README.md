<p align="center">
  <a href="https://whitebox-ai.github.io/whitebox">
<!--     <img src="https://raw.githubusercontent.com/whitebox-ai/.github/main/profile/whitebox.png" alt="Whitebox" width="50%"> -->
  </a>
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/humanbound/humanbound/main/assets/logo-dark.svg" alt="Humanbound" width="280"/>
</p>

<h3 align="center">humanbound</h3>

<p align="center">
  Open-source adversarial testing engine, SDK, and CLI for AI agents.
  <br/>
  Attack your agent the way real users and attackers will: live endpoints,
  multi-turn conversations, tool abuse. Then turn every failure into a firewall rule.
  <br/>
  Runs locally or against the Humanbound Platform. No login required to start.
</p>

<p align="center">
  <a href="#quick-start">Quick Start</a> &middot;
  <a href="https://docs.humanbound.ai/">Documentation</a> &middot;
  <a href="#contributing">Contributing</a>
</p>

<p align="center">
  <a href="https://pypi.org/project/humanbound/"><img src="https://img.shields.io/pypi/v/humanbound?style=flat-square&color=FD9506" alt="PyPI version"/></a>
  <a href="https://pypi.org/project/humanbound/"><img src="https://img.shields.io/pypi/pyversions/humanbound?style=flat-square&color=FD9506" alt="Python versions"/></a>
  <a href="https://pypi.org/project/humanbound/"><img src="https://img.shields.io/pypi/dm/humanbound?style=flat-square&color=FD9506" alt="Downloads"/></a>
  <a href="https://github.com/humanbound/humanbound/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/humanbound/humanbound/ci.yml?style=flat-square&color=FD9506" alt="CI"/></a>
  <a href="https://github.com/humanbound/humanbound/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-FD9506?style=flat-square" alt="License"/></a>
  <a href="https://discord.gg/WgTMpmSFtN"><img src="https://img.shields.io/badge/discord-community-FD9506?style=flat-square" alt="Discord"/></a>
  <a href="https://docs.humanbound.ai/"><img src="https://img.shields.io/badge/docs-humanbound.ai-FD9506?style=flat-square" alt="Docs"/></a>
</p>

---

> 📖 **Full documentation** lives at [**docs.humanbound.ai**](https://docs.humanbound.ai/) —
> this README covers the essentials; the docs have the depth.

## Why Humanbound

Most testing tools test prompts. Humanbound tests **agents**: it drives
multi-turn conversations against your real endpoint, probes tool use and scope
boundaries, and scores the results against your security policy. When tests
fail, `hb guardrails` converts the findings into deployable firewall rules —
so the same run that finds a hole also patches it.

## Quick Start

### Install

```bash
pip install humanbound                       # CLI + SDK, core deps
pip install humanbound[engine]               # + OpenAI / Anthropic / Gemini / Ollama providers
pip install humanbound[firewall]             # + humanbound-firewall runtime
pip install humanbound[engine,firewall]      # everything
```
## Contributing

Contributions welcome. See [CONTRIBUTING.md](https://github.com/humanbound/humanbound/blob/main/CONTRIBUTING.md) for the dev
loop, release process, and DCO sign-off requirement (see [DCO.md](https://github.com/humanbound/humanbound/blob/main/DCO.md)).

- 🐛 [Report a bug](https://github.com/humanbound/humanbound/issues/new/choose)
- 💡 [Request a feature](https://github.com/humanbound/humanbound/issues/new/choose)
- 🔒 [Report a security issue](https://github.com/humanbound/humanbound/blob/main/SECURITY.md) — **not via public Issues**
- 💬 [Join Discord](https://discord.gg/WgTMpmSFtN)

## Telemetry

The `hb` CLI sends anonymous usage data to help us improve it.
Disable with `hb telemetry disable`, `HB_TELEMETRY_DISABLED=1`, or
`DO_NOT_TRACK=1`. Turning telemetry off sends one final anonymous
`telemetry_disabled` event (once per machine, ever) so we can count
opt-outs. Full disclosure: [PRIVACY.md](https://github.com/humanbound/humanbound/blob/main/PRIVACY.md).

## License

[Apache-2.0](https://github.com/humanbound/humanbound/blob/main/LICENSE). Free to use in any context — commercial or
open-source — with attribution. See [TRADEMARK.md](https://github.com/humanbound/humanbound/blob/main/TRADEMARK.md) for the
trademark policy. The code is open; the name is not.

The sibling project [`humanbound-firewall`](https://github.com/humanbound/humanbound-firewall)
is also Apache-2.0 — same license, different product.
