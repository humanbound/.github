<p align="center">
  <a href="https://whitebox-ai.github.io/whitebox">
<!--     <img src="https://raw.githubusercontent.com/whitebox-ai/.github/main/profile/whitebox.png" alt="Whitebox" width="50%"> -->
  </a>
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/humanbound/humanbound/main/assets/logo-dark.svg" alt="Humanbound" width="280"/>
</p>
 
<p align="center">
  Open-source adversarial testing engine, SDK, and CLI for AI agents.
  <br/>
  Runs locally or against the Humanbound Platform. No login required to start.
</p>
<p align="center">
  <a href="#quick-start">Quick Start</a> &middot;
  <a href="#usage">Usage</a> &middot;
  <a href="#repositories">Repositories</a> &middot;
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
 
- **Tests agents, not prompts.** Drives real multi-turn conversations against your live endpoint instead of scoring one-shot completions.
- **Probes tool use and scope.** Attempts the actions your agent shouldn't take — over-scoped tool calls, boundary violations — not just unsafe text generation.
- **Scores against your policy.** Findings are evaluated against a security policy you define, not a generic safety rubric.
- **Closes what it finds.** `hb guardrails` turns failing test cases directly into deployable guardrail rules, so a single run both surfaces and fixes the gap.
- **Local-first.** Runs entirely on your machine with no account required; connect to the Humanbound Platform only if you want managed runs, history, and team dashboards.
## Quick Start
 
### Install
 
```bash
pip install humanbound                       # CLI + SDK, core deps
pip install humanbound[engine]               # + OpenAI / Anthropic / Gemini / Ollama providers
pip install humanbound[firewall]             # + humanbound-firewall runtime
pip install humanbound[engine,firewall]      # everything
```
 
## Usage
 
> The commands below illustrate the shape of a typical run — check [docs.humanbound.ai](https://docs.humanbound.ai/) for the current, complete CLI reference before relying on exact flags.
 
Run an adversarial test suite against your endpoint:
 
```bash
hb run --endpoint https://api.yourapp.com/agent --policy policy.yaml
```
 
Convert failing tests into deployable guardrail rules:
 
```bash
hb guardrails --from-run last --out guardrails.yaml
```
 
Or drive it from the SDK:
 
```python
from humanbound import Engine
 
engine = Engine(endpoint="https://api.yourapp.com/agent", policy="policy.yaml")
results = engine.run()
 
if results.failures:
    engine.guardrails.generate(results, out="guardrails.yaml")
```
 
## Repositories
 
Humanbound is split across a few focused repos rather than one monolith:
 
| Repo | Description | Stars |
|---|---|---|
| [`humanbound`](https://github.com/humanbound/humanbound) | Open-source adversarial testing engine, SDK, and CLI for AI agents. Runs locally or against the Humanbound Platform. | ![GitHub Repo stars](https://img.shields.io/github/stars/humanbound/humanbound?style=flat-square&color=FD9506&label=) |
| [`humanbound-firewall`](https://github.com/humanbound/humanbound-firewall) | Multi-tier firewall for AI agents — blocks prompt injections, jailbreaks, and scope violations. Local tiers first; LLM judge only when uncertain. | ![GitHub Repo stars](https://img.shields.io/github/stars/humanbound/humanbound-firewall?style=flat-square&color=FD9506&label=) |
| [`plugins`](https://github.com/humanbound/plugins) | Humanbound plugin marketplace for Claude Code and Cursor — adversarial security testing for local AI agents. | ![GitHub Repo stars](https://img.shields.io/github/stars/humanbound/plugins?style=flat-square&color=FD9506&label=) |
| [`actions`](https://github.com/humanbound/actions) | Official GitHub Actions for Humanbound — adversarial security testing for AI agents in CI. | ![GitHub Repo stars](https://img.shields.io/github/stars/humanbound/actions?style=flat-square&color=FD9506&label=) |
 
See all repositories → [github.com/humanbound](https://github.com/humanbound)
 
## Contributing
 
Contributions welcome. See [CONTRIBUTING.md](https://github.com/humanbound/humanbound/blob/main/CONTRIBUTING.md) for the dev
loop, release process, and DCO sign-off requirement (see [DCO.md](https://github.com/humanbound/humanbound/blob/main/DCO.md)).
 
- 🐛 [Report a bug](https://github.com/humanbound/humanbound/issues/new/choose)
- 💡 [Request a feature](https://github.com/humanbound/humanbound/issues/new/choose)
- 🔒 [Report a security issue](https://github.com/humanbound/humanbound/blob/main/SECURITY.md) — **not via public Issues**
- 💬 [Join Discord](https://discord.gg/WgTMpmSFtN)
## License
 
Humanbound is licensed under the [Apache License 2.0](https://github.com/humanbound/humanbound/blob/main/LICENSE).
 
