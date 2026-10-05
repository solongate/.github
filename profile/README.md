<p align="center">
  <img src="https://avatars.githubusercontent.com/u/298001799?s=200&v=4" alt="SolonGate" width="160">
</p>

<h1 align="center">SolonGate</h1>

<p align="center">
  <strong>MAKE AI SECURE AGAIN</strong>
</p>

<p align="center">
  Security guardrails for AI agents — and for the software supply chain they run on.
</p>

<p align="center">
  <a href="https://solongate.com"><img src="https://img.shields.io/badge/website-solongate.com-2f81f7?style=flat-square" alt="Website"></a>
  <a href="https://github.com/orgs/solongate/repositories"><img src="https://img.shields.io/badge/repositories-2-2f81f7?style=flat-square" alt="Repositories"></a>
  <img src="https://img.shields.io/badge/built%20with-Go%20%7C%20TypeScript-2f81f7?style=flat-square" alt="Built with">
  <img src="https://img.shields.io/badge/local--first-no%20cloud%20required-2f81f7?style=flat-square" alt="Local-first">
</p>

---

## What we build

AI agents now read files, run commands, call tools and talk to other agents on
behalf of real users. That surface is wide, fast-moving and mostly unmonitored.
We build **open-source, local-first tooling** that makes it measurable:

- 🛡️ **Agent security posture** — audit what your agents actually did, scored against the OWASP Agentic Top 10.
- 📦 **Supply-chain impact analysis** — map newly disclosed CVEs to the product releases you already shipped.
- 🔒 **Your data stays yours** — no account, no telemetry, no cloud service. Everything runs on your machine, offline where it can.

## Projects

| Project | What it does | Stack |
| :--- | :--- | :--- |
| **[solongate-audit](https://github.com/solongate/solongate-audit)** <br> <img src="https://img.shields.io/github/stars/solongate/solongate-audit?style=flat-square&color=2f81f7&label=%E2%AD%90" alt="Stars"> <img src="https://img.shields.io/github/license/solongate/solongate-audit?style=flat-square&color=2f81f7" alt="License"> | AI agent security audit CLI. Reads local agent session logs (Claude Code, Gemini CLI, OpenClaw), parses every tool call, and scores all ten **OWASP Agentic Top 10 (2026)** categories as `PROTECTED` / `PARTIAL` / `NOT PROTECTED`. Live watch mode, JSON/CSV/HTML/PDF export, CI-friendly exit codes. | TypeScript · Node 18+ |
| **[psirtmap](https://github.com/solongate/psirtmap)** <br> <img src="https://img.shields.io/github/stars/solongate/psirtmap?style=flat-square&color=2f81f7&label=%E2%AD%90" alt="Stars"> <img src="https://img.shields.io/github/license/solongate/psirtmap?style=flat-square&color=2f81f7" alt="License"> | PSIRT-grade inventory and impact analysis for device, firmware and embedded software vendors. Ingests CycloneDX SBOMs into a local SQLite inventory, syncs OSV + CISA KEV snapshots, then scans your shipped releases **offline**. Durable findings, append-only assessments, air-gapped feed bundles. | Go · SQLite |

## Try it in 30 seconds

**Audit your AI agent's security posture**

```bash
npx solongate-audit --detailed
```

Returns a score out of 10 across ASI01–ASI10. In CI, it exits `0` at ≥ 7/10 and `1` below that:

```bash
npx solongate-audit   # add to your pipeline as a gate
```

**Map a new CVE to your shipped releases**

```bash
# install (macOS / Linux)
curl -fsSL https://raw.githubusercontent.com/solongate/psirtmap/main/scripts/install.sh | sh

psirtmap sync                                           # refresh OSV + KEV snapshots
psirtmap release import AG-200@2.2 ./firmware-2.2.cdx.json
psirtmap scan AG-200@2.2                                # offline, no account needed
```

> [!NOTE]
> PSIRTMap reports **potential impact**. A version match is evidence that needs
> human review — not proof of exploitability.

## Design principles

| | |
| :--- | :--- |
| **Local-first** | No account, no database server, no SolonGate cloud. Internet is optional and explicit. |
| **Honest findings** | We label uncertainty instead of hiding it — `PARTIAL`, `potential impact`, `requires review`. |
| **Standards-aligned** | OWASP Agentic Top 10, CycloneDX, OSV, CISA KEV. No proprietary formats. |
| **Automatable** | Every tool has `--json` and a meaningful exit code, so it drops into CI unchanged. |

## Contributing

Issues and pull requests are welcome on any repository. The quickest way to help:

- 🐛 **File an issue** — a false positive or a missed detection is the most valuable bug report we get.
- 🧩 **Add agent log support** — `solongate-audit` grows by learning new agent log formats.
- 📚 **Improve docs** — if a command confused you, it will confuse the next person too.

Start from the `CONTRIBUTING` notes in the relevant repository, and open an issue
before large changes so we can agree on the approach first.

## Security

Found a vulnerability in one of our tools? Please **do not** open a public issue.
Report it privately through the security advisory page of the affected
repository, and we will coordinate disclosure with you.

---

<p align="center">
  <a href="https://solongate.com">solongate.com</a>
  &nbsp;·&nbsp;
  <a href="https://github.com/orgs/solongate/repositories">Repositories</a>
  &nbsp;·&nbsp;
  <a href="https://github.com/solongate/solongate-audit/issues">Report an issue</a>
</p>

<p align="center">
  <sub>Built in the open. 🇺🇸 United States of America</sub>
</p>
