<p align="center">
  <img src="https://raw.githubusercontent.com/solongate/.github/main/profile/assets/banner.png" alt="SolonGate" width="820">
</p>

## Who we are

SolonGate is named after Solon, the Athenian lawgiver who in 594 BC wrote the
laws down and read them out to the assembly. The point was never the rules
themselves. It was that they were written, public, and applied the same way to
everyone, so that power finally had something to answer to.

We are building that for AI that executes. Models no longer only answer
questions. They call tools, run commands, read files and hand work to other
agents, almost always carrying whatever authority the person who started them
happens to have. That authority is rarely written down anywhere, so nothing can
check it, and nobody can say afterwards what was actually allowed to happen.

## Why we build in the open

Security you cannot read is security you have to take on faith. We would rather
be audited than believed, so we publish the tools, we publish the method behind
them, and when we benchmark ourselves we publish what we missed as well.

We also think this work belongs on your machine instead of ours. Agent session
logs and SBOMs are some of the most revealing artifacts an engineering team
produces. The tools here read them locally, keep their state in a local file,
and reach the network only when you explicitly ask them to.

The gateway product lives at [solongate.com](https://solongate.com). What lives
in this organization is the open source side of that work: standalone tools you
can run today, with no account, no telemetry, and nothing of ours in the path.

## Projects

| Project | What it does |
|:---|:---|
| **[solongate-audit](https://github.com/solongate/solongate-audit)** | AI agent security audit CLI. Reads local agent session logs from Claude Code, Gemini CLI and OpenClaw, parses every tool call, then scores all ten **OWASP Agentic Top 10 (2026)** categories as `PROTECTED`, `PARTIAL` or `NOT PROTECTED`. |
| **[psirtmap](https://github.com/solongate/psirtmap)** | Inventory and impact analysis for teams shipping devices, firmware and embedded software. Ingests CycloneDX SBOMs into a local inventory, syncs OSV and CISA KEV snapshots, then scans your shipped releases offline. |

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
