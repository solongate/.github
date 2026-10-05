<p align="center">
  <img src="https://raw.githubusercontent.com/solongate/.github/main/profile/assets/banner.png" alt="SolonGate" width="820">
</p>

## What we build

AI agents now read files, run commands, call tools and talk to other agents on
behalf of real users. That surface is wide, fast moving and mostly unmonitored.
We build open source security tooling that makes it measurable, and that runs
entirely on your own machine.

**Agent security posture.** Audit what your agents actually did, scored against
the OWASP Agentic Top 10.

**Supply chain impact analysis.** Map newly disclosed vulnerabilities to the
product releases you have already shipped.

**Your data stays yours.** No account, no telemetry, no cloud service. Internet
access is optional and always explicit.

## Projects

| Project | What it does | Stack |
|:---|:---|:---|
| **[solongate-audit](https://github.com/solongate/solongate-audit)** <br> <img src="https://img.shields.io/github/stars/solongate/solongate-audit?style=flat-square&color=2f81f7&label=stars" alt="Stars"> <img src="https://img.shields.io/github/license/solongate/solongate-audit?style=flat-square&color=2f81f7" alt="License"> | AI agent security audit CLI. Reads local agent session logs from Claude Code, Gemini CLI and OpenClaw, parses every tool call, then scores all ten **OWASP Agentic Top 10 (2026)** categories as `PROTECTED`, `PARTIAL` or `NOT PROTECTED`. Live watch mode, JSON, CSV, HTML and PDF export, plus exit codes you can gate a pipeline on. | TypeScript, Node 18+ |
| **[psirtmap](https://github.com/solongate/psirtmap)** <br> <img src="https://img.shields.io/github/stars/solongate/psirtmap?style=flat-square&color=2f81f7&label=stars" alt="Stars"> <img src="https://img.shields.io/github/license/solongate/psirtmap?style=flat-square&color=2f81f7" alt="License"> | Inventory and impact analysis for teams shipping devices, firmware and embedded software. Ingests CycloneDX SBOMs into a local SQLite inventory, syncs OSV and CISA KEV snapshots, then scans your shipped releases offline. Durable findings, append only assessments, and checksummed bundles for air gapped transfer. | Go, SQLite |

## Try it in 30 seconds

Audit your AI agent's security posture:

```bash
npx solongate-audit --detailed
```

It returns a score out of 10 across ASI01 through ASI10. In CI it exits `0` at
7/10 or above and `1` below that, so you can gate a pipeline on it directly:

```bash
npx solongate-audit
```

Map a newly disclosed vulnerability to the releases you shipped:

```bash
# install on macOS or Linux
curl -fsSL https://raw.githubusercontent.com/solongate/psirtmap/main/scripts/install.sh | sh

psirtmap sync                                              # refresh OSV and KEV snapshots
psirtmap release import AG-200@2.2 ./firmware-2.2.cdx.json # import a CycloneDX SBOM
psirtmap scan AG-200@2.2                                   # offline, no account needed
```

> [!NOTE]
> PSIRTMap reports **potential impact**. A version match is evidence that needs
> human review, not proof of exploitability.

## Design principles

| | |
|:---|:---|
| **Local first** | No account, no database server, no SolonGate cloud. Your SBOMs and agent logs never leave your machine. |
| **Honest findings** | We label uncertainty instead of hiding it: `PARTIAL`, `potential impact`, `requires review`. |
| **Standards aligned** | OWASP Agentic Top 10, CycloneDX, OSV, CISA KEV. No proprietary formats, no lock in. |
| **Automatable** | Every tool ships `--json` output and a meaningful exit code, so it drops into CI unchanged. |

## Contributing

Issues and pull requests are welcome on every repository. The quickest ways to
help:

**File an issue.** A false positive or a missed detection is the most valuable
bug report we get.

**Teach us a new log format.** `solongate-audit` grows by learning how more
agents write their session logs.

**Improve the docs.** If a command confused you, it will confuse the next person
too.

Please open an issue before large changes so we can agree on the approach first.

## Security

Found a vulnerability in one of our tools? Please do not open a public issue.
Report it privately through the security advisory page of the affected
repository and we will coordinate disclosure with you.

<p align="center">
  <a href="https://solongate.com">solongate.com</a>
  &nbsp;&middot;&nbsp;
  <a href="https://github.com/orgs/solongate/repositories">Repositories</a>
  &nbsp;&middot;&nbsp;
  <a href="https://github.com/solongate/solongate-audit/issues">Report an issue</a>
</p>
