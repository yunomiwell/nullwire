# NullWire Protocol

**A Solana-native anonymous communication protocol. Built for 2026.**

NullWire combines a Loopix-based mixnet, hybrid post-quantum encryption, and zero-knowledge identity into a single protocol — designed to make traffic analysis infeasible for the first time in a consumer product.

> *"Encrypting the content of a message is solved. Hiding the fact that you sent one is not. NullWire solves both."*

---

## Why NullWire Exists

Every existing privacy tool has a fatal flaw:

| Tool | The Problem |
|------|------------|
| **TOR** | Timing correlation attacks. Nation-states can deanonymize users in minutes. |
| **Signal** | Requires a phone number. Centralized servers. Metadata is visible. |
| **Session** | Onion routing — same fundamental weakness as TOR. |
| **Nym** | Sound mixnet architecture. NymVPN shipped 2025 — first real consumer mixnet. Token-dependent infrastructure, no PQ encryption, no formalized control-plane integrity. |

NullWire combines mixnet architecture with post-quantum encryption, multi-RPC quorum validation, and a consumer messaging strategy — properties currently split across different systems.

---

## How It Works

- **Mixnet routing** — Messages are batched, delayed, shuffled, and padded to identical size. Timing correlation becomes infeasible under the protocol's threat model.
- **Solana control plane** — Node registry, staking, and governance live on-chain. No central server. No single point of failure. Significantly higher censorship resistance than DNS-dependent infrastructure.
- **Zero-knowledge identity** — Stake SOL, generate a ZK proof of legitimacy, connect. The network never learns who you are.
- **X3DH + Double Ratchet E2E** — Forward-secret end-to-end encryption from the first message. Pre-alpha prototype implemented, not yet audited.
- **Post-quantum encryption** — ML-KEM-1024 + X25519 hybrid key agreement + XChaCha20-Poly1305. Designed to resist harvest-now-decrypt-later attacks.
- **Tunable anonymity** — GHOST (nation-state resistant, requires sufficient network scale) / SHADOW (balanced) / MIST (everyday use).

---

## Documents

**[`NULLWIRE_WHITEPAPER_V3.pdf`](./NULLWIRE_WHITEPAPER_V3.pdf)** — v0.3, April 2026
24-page technical specification. Architecture, cryptographic stack, threat model, control-plane hardening, attack resistance, node economics.
IPFS: `bafybeihtu45ifqzcq5equoeuqwgyzq2qp4dyud2trde5agdhjhohv2nwxu`

**[`NULLWIRE_ARXIV_V3.pdf`](./NULLWIRE_ARXIV_V3.pdf)** — Academic paper, Revision 3, 32 pages
Submitted to arXiv cs.CR (pending endorsement). Formal anonymity guarantees, PQ security, E2E encryption analysis, control-plane integrity, multi-RPC quorum validation, limitations analysis.
IPFS: `bafybeig4u7xldiacnxzn6c2ps5zelbkflovkjc5mb2s5adbvjofhi5mcui`

---

## Roadmap

| Phase | Timeline | Focus | Status |
|-------|----------|-------|--------|
| **Phase 0: Proof of Concept** | Q2–Q4 2026 | Rust prototype, Solana devnet, CLI client, X3DH + Double Ratchet E2E, mandatory security audit | In development |
| **Phase 1: Dark Alpha** | Q1–Q2 2027 | Desktop app, 3-hop mixnet, relay nodes, staking, waitlist launch | Planned |
| **Phase 2: Public Launch** | Q3–Q4 2027 | iOS/Android, web client, SDK, seed funding | Planned |
| **Phase 3: NullWire Mesh** | 2028 | Full traffic proxy, NullWire Browser, enterprise API | Planned |

Timelines are aspirational and subject to funding and Phase 0 validation results.

---

## Looking For

- **Solana / Rust engineers** interested in building privacy infrastructure
- **Cryptographers** familiar with Loopix / mixnet design
- Anyone who believes private communication is a right, not a privilege

**Contact:** Open an issue · X [@nllwrprtcl](https://x.com/nllwrprtcl) · relay@nullwire.xyz

---

## Status

Whitepaper v0.3 and academic paper Revision 3 published. X3DH + Double Ratchet E2E encryption in pre-alpha prototype. Protocol implementation in active development.

---

## License

MIT License — Copyright (c) 2026 yunomiwell

NullWire Protocol is a legitimate privacy tool. Building it is legal and protected as free speech ([Bernstein v. DOJ, 1999](https://en.wikipedia.org/wiki/Bernstein_v._United_States)).
