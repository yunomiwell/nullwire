# NullWire Protocol

**A post-quantum, mix-network messaging protocol with an on-chain node registry. Pre-alpha.**

NullWire pairs a Loopix-style mixnet with hybrid post-quantum end-to-end encryption. The aim is to protect both the *content* of a message and the *metadata* — the fact that you sent one, and to whom. The encryption is implemented and working today; the mixnet and its decentralization are early. See **Status** below for an honest picture.

> *"Encrypting the content of a message is well understood. Hiding the fact that you sent one is not. NullWire is an attempt at both."*

---

## Why NullWire exists

Every existing privacy tool makes a trade-off:

| Tool | The trade-off |
|------|---------------|
| **Tor** | Strong and widely used — but vulnerable to timing correlation by an adversary who can observe both ends. |
| **Signal** | Excellent content encryption — but requires a phone number and runs on centralized servers. |
| **Session** | Onion routing, so it shares Tor's end-to-end correlation weakness. |
| **Nym** | Strong mixnet design; NymVPN shipped in 2025. Infrastructure is token-gated. |

NullWire's bet is to combine a mixnet, post-quantum encryption, and an on-chain node registry in one consumer-focused protocol. That combination is the research goal — not a finished claim.

---

## How it works

- **Hybrid post-quantum E2E encryption** — ML-KEM-1024 + X25519 hybrid key agreement (FIPS 203), ChaCha20-Poly1305 AEAD, HKDF-SHA3-256, X3DH + Double Ratchet with header encryption. Forward-secret from the first message; designed to resist harvest-now-decrypt-later attacks. **Implemented, tested, working.**
- **Mixnet routing** — messages are padded to a fixed size, onion-wrapped, and routed through multiple hops so timing correlation is hard. **Implemented; today it runs on a small operator-run mesh — see Status.**
- **On-chain node registry** — the mesh directory lives on Solana (currently *devnet*) instead of DNS, for verifiable membership and censorship resistance.
- **Tunable routing** — trade latency against privacy depending on the threat you face.

---

## Status — the honest version

NullWire is **pre-alpha** (current build `v0.1.3-rc48`). Concretely:

- **The cryptography is real.** Hybrid post-quantum E2E encryption is implemented, carries a substantial test suite, and works end-to-end. It has **not** had an external third-party audit — that is the single biggest item before any production use.
- **The mixnet is small and single-operator.** The live mesh is a handful of nodes currently run by one operator. A mixnet's anonymity comes from many independent, non-colluding operators; recruiting them is a core roadmap item. For now, treat NullWire as a working prototype of the protocol — not as a network that delivers strong anonymity at scale.
- **The registry is on devnet.** The Solana node registry runs on devnet, a test network. Mainnet comes after the audit.

We would rather undersell this than oversell it. If a claim in this README isn't backed by the code, please open an issue.

---

## Documents

**`NULLWIRE_WHITEPAPER_V4.pdf`** — technical specification: architecture, the cryptographic stack, and the threat model.

---

## Roadmap

| Phase | Focus | Status |
|-------|-------|--------|
| **Phase 0 — Proof of Concept** | Rust implementation, Solana devnet, CLI + desktop client, hybrid PQ E2E, external security audit | In progress |
| **Phase 1 — Alpha** | Independent multi-operator mesh, hardened client, waitlist | Planned |
| **Phase 2 — Public** | Mobile clients, SDK, mainnet | Planned |

Timelines depend on funding, audit outcomes, and Phase 0 results. Anything beyond Phase 0 — staking, key recovery, broader identity options — is design work, not shipped code.

---

## Looking for

- **Rust / Solana engineers** interested in privacy infrastructure
- **Cryptographers** familiar with mixnet / Loopix design
- **Independent relay operators** — a mixnet needs operators who don't all answer to one party
- Anyone who believes private communication is a right, not a privilege

**Contact:** open an issue · X [@nllwrprtcl](https://x.com/nllwrprtcl) · relay@nullwire.xyz
**Security reports:** see [`SECURITY.md`](./SECURITY.md)

---

## License

MIT License — Copyright (c) 2026 yunomiwell

NullWire is a legitimate privacy tool. Writing and publishing cryptographic software is lawful and protected speech ([Bernstein v. United States](https://en.wikipedia.org/wiki/Bernstein_v._United_States)).
