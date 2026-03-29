# NullWire Protocol

**The successor to TOR. Built for 2026.**

NullWire is a Solana-native anonymous communication protocol combining a Loopix-based mixnet, post-quantum encryption, and zero-knowledge identity — making traffic analysis mathematically impossible for the first time.

> *"Encrypting the content of a message is solved. Hiding the fact that you sent one is not. NullWire solves both."*

---

## Why NullWire Exists

Every existing privacy tool has a fatal flaw:

| Tool | The Problem |
|------|-------------|
| **TOR** | Timing correlation attacks. Nation-states can deanonymize users in minutes. |
| **Signal** | Requires a phone number. Centralized servers. Metadata is visible. |
| **Session** | Onion routing — same fundamental weakness as TOR. |
| **Nym** | Correct mixnet architecture. No consumer product after 7 years. |

NullWire is the first protocol to combine the right architecture (mixnet) with economic incentives, post-quantum encryption, and a consumer product.

---

## How It Works

- **Mixnet routing** — Messages are batched, delayed, shuffled, and padded to identical size. Timing analysis becomes mathematically infeasible.
- **Solana control plane** — Node registry, staking, and governance live on-chain. No central server. No kill switch. No court order works.
- **Zero-knowledge identity** — Stake SOL, generate a ZK proof of legitimacy, connect. The network never knows who you are.
- **Post-quantum encryption** — ML-KEM-1024 + X25519 + XChaCha20-Poly1305 + Double Ratchet. Future-proof against quantum adversaries.
- **Tunable anonymity** — GHOST (nation-state resistant) / SHADOW (balanced) / MIST (everyday use).

---

## Whitepaper

**[NULLWIRE_PROTOCOL_WHITEPAPER.pdf](./NULLWIRE_WHITEPAPER.pdf)** — v0.1, March 2026

20-page technical specification covering protocol architecture, cryptographic stack, Solana integration, competitor analysis, attack resistance, and tokenomics.

---

## Roadmap

| Stage | Focus | Status |
|-------|-------|--------|
| **Stage 1** | Secure anonymous messaging | 🔨 In development |
| **Stage 2** | Anonymous application layer (SDK) | Planned |
| **Stage 3** | Decentralized internet infrastructure — TOR replacement | Planned |

---

## Looking For

- Solana / Rust engineers interested in building privacy infrastructure
- Cryptographers familiar with Loopix / mixnet design
- Anyone who believes private communication is a right, not a privilege

**Contact:** Open an issue or reach out via X [@yunomiwell](https://x.com/yunomiwell)

---

## Status

This repository contains the whitepaper and architecture specification for NullWire Protocol v0.1.  
Protocol implementation is in active development.

---

## License

MIT License — Copyright © 2026 yunomiwell

*NullWire Protocol is a legitimate privacy tool. Building it is legal and protected as free speech (Bernstein v. DOJ, 1999).*
