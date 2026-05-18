# Security Policy

NullWire is **pre-alpha software** (current build `v0.1.3-rc48`) and has **not** undergone an external third-party security audit. Do not yet rely on it to protect you from a capable adversary. Treat it as a working prototype of the protocol.

## Reporting a vulnerability

Please report security issues **privately**. Do **not** open a public GitHub issue for a vulnerability.

- Email **relay@nullwire.xyz** with a subject line beginning `[SECURITY]`.
- Include a description, reproduction steps, the affected component and version, and the impact if you know it.

We aim to acknowledge a report within 5 business days. NullWire is maintained by a very small team — please allow reasonable time for a fix before any public disclosure. Coordinated disclosure is appreciated and credited.

## Scope

In scope:

- The cryptographic protocol and its implementation.
- The mixnet node software and the on-chain registry program.
- The installer and the release-signing pipeline.

Documented limitations — known, and not treated as new vulnerabilities:

- No external security audit has been performed yet.
- The live mesh is small and currently single-operator; it does not provide strong anonymity at scale today.
- The Solana node registry runs on devnet.
- Inter-relay transport hardening and metadata-correlation defenses are still in progress.

## Supported versions

During pre-alpha, only the most recent release receives security fixes. There is no long-term-support branch yet.
