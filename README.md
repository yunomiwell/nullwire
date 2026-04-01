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
| **Nym** | Correct mixnet architecture. No consumer product after 7 years. |

NullWire is the first protocol to combine the right architecture (mixnet) with economic incentives, post-quantum encryption, and a consumer product strategy.

---

## How It Works

- **Mixnet routing** — Messages are batched, delayed, shuffled, and padded to identical size. Timing correlation becomes infeasible under the protocol's threat model.
- **Solana control plane** — Node registry, staking, and governance live on-chain. No central server. No single point of failure. Significantly higher censorship resistance than DNS-dependent infrastructure.
- **Zero-knowledge identity** — Stake SOL, generate a ZK proof of legitimacy, connect. The network never learns who you are.
- **Post-quantum encryption** — ML-KEM-1024 + X25519 + XChaCha20-Poly1305 + Double Ratchet. Future-proof against quantum adversaries.
- **Tunable anonymity** — GHOST (nation-state resistant, requires sufficient network scale) / SHADOW (balanced) / MIST (everyday use).

---

## Documents

**[`NULLWIRE_WHITEPAPER_v2.pdf`](./NULLWIRE_WHITEPAPER_v2.pdf)** — v0.2, April 2026
26-page technical specification. Architecture, cryptographic stack, threat model, attack resistance, node economics.
IPFS: `bafkreibkk3653yifyy5gfuk33xiyysjm6ou2enzir5si4ogbcwydcyjoue`

**[`nullwire_arxiv.pdf`](./nullwire_arxiv.pdf)** — Academic paper, 21 pages
Submitted to arXiv cs.CR (pending endorsement). Formal treatment of anonymity guarantees, PQ security, and limitation analysis.
IPFS: `bafybeibir25fmtxqugeqthuhex57blkm5zgtpmfpk5kz36yha74vyr3uky`

---

## Roadmap

| Phase | Timeline | Focus | Status |
|-------|----------|-------|--------|
| **Phase 0: Proof of Concept** | Q3-Q4 2026 | Rust prototype, Solana devnet, CLI client, mandatory security audit | In development |
| **Phase 1: Dark Alpha** | Q1-Q2 2027 | Desktop app, 3-hop mixnet, relay nodes, staking | Planned |
| **Phase 2: Public Launch** | Q3-Q4 2027 | iOS/Android, web client, SDK, seed funding | Planned |
| **Phase 3: NullWire Mesh** | 2028 | Full traffic proxy, NullWire Browser, enterprise API | Planned |

Timelines are aspirational and subject to funding and Phase 0 validation results.

---

## Looking For

- **Solana / Rust engineers** interested in building privacy infrastructure
- **Cryptographers** familiar with Loopix / mixnet design
- Anyone who believes private communication is a right, not a privilege

**Contact:** Open an issue · X [@nllwrprtcl](https://x.com/nllwrprtcl) · nullwireprotocol@gmail.com

---

## Status

Whitepaper and architecture specification for NullWire Protocol v0.2. Protocol implementation in active development.

---

## License

MIT License — Copyright (c) 2026 yunomiwell

NullWire Protocol is a legitimate privacy tool. Building it is legal and protected as free speech ([Bernstein v. DOJ, 1999](https://en.wikipedia.org/wiki/Bernstein_v._United_States)).
