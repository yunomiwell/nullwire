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
- **X3DH + Double Ratchet E2E** — Forward-secret end-to-end encryption from the first message with ML-KEM-1024 hybrid key exchange (FIPS 203), HKDF-SHA3-256 (FIPS 202), key zeroization, session management. Pre-alpha with significant hardening, not yet externally audited.
- **Post-quantum encryption** — ML-KEM-1024 + X25519 hybrid key agreement (FIPS 203) + ChaCha20-Poly1305. Shipped and tested. Designed to resist harvest-now-decrypt-later attacks.
- **Tunable anonymity** — PRIVATE (nation-state resistant, requires sufficient network scale) / BALANCED (strong privacy) / FAST (everyday use).

---

## Documents

**[`NULLWIRE_WHITEPAPER_V3.pdf`](./NULLWIRE_WHITEPAPER_V3.pdf)** — v0.4, April 2026
24-page technical specification. Architecture, cryptographic stack, threat model, control-plane hardening, attack resistance, node economics.
IPFS: `bafkreiczb763vfas734ujr7wvyuqxtjrygxgvnkbvrhxcgpciu5iizpgpi`

**[`NULLWIRE_ARXIV_V3.pdf`](./NULLWIRE_ARXIV_V3.pdf)** — Academic paper, Revision 4, 32 pages
Submitted to arXiv cs.CR (pending endorsement). Formal anonymity guarantees, PQ security, E2E encryption analysis, control-plane integrity, multi-RPC quorum validation, limitations analysis.
IPFS: `bafybeids6l2dgx6xgqwvimh5cxsnqmaaofstdd7ux4v6zdgz6p5ur7buhu`

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

Whitepaper v0.4 and academic paper Revision 4 published. X3DH + Double Ratchet E2E encryption with ML-KEM-1024 hybrid (FIPS 203) and HKDF-SHA3-256 (FIPS 202) in pre-alpha with significant hardening. Protocol implementation in active development.

---

## License

MIT License — Copyright (c) 2026 yunomiwell

NullWire Protocol is a legitimate privacy tool. Building it is legal and protected as free speech ([Bernstein v. DOJ, 1999](https://en.wikipedia.org/wiki/Bernstein_v._United_States)).
