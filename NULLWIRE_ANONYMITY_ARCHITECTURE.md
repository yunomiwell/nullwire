# NullWire Phase 0 Architecture Notes

## What This Document Is

This is the architecture baseline for the prototype.

It is not a proof that NullWire defeats global traffic analysis.
It is not a production threat-model guarantee.
It is not a claim that E2E encryption is audited or production-safe.

## Core Architecture

NullWire Phase 0 combines:
- off-chain relay and gateway transport
- fixed-size packets (2048 bytes, Sphinx format)
- layered sealed hop directives with per-hop blinding
- configurable delay profiles (Poisson-distributed)
- continuous cover traffic
- Solana as decentralized control plane
- X3DH-style key bootstrap + Double Ratchet for message-layer E2E encryption (pre-alpha)

The hard boundary is simple:
- payload off-chain
- coordination on-chain

## Why Not On-Chain Payloads

Putting payloads in Solana accounts is the wrong move.

Problems:
- worse cost profile
- worse throughput profile
- more visible storage pattern
- unnecessary coupling between messaging and chain availability

GlassWorm was useful as a signal that blockchains can survive takedown pressure. It is not a reason to put messages on-chain.

## E2E Encryption Architecture

Message-layer end-to-end encryption is separate from per-hop relay encryption.

**Per-hop layer (Sphinx):** each relay hop uses ML-KEM-1024 + X25519 hybrid key agreement and XChaCha20-Poly1305 to encrypt routing information. Mix nodes cannot see the message payload.

**Message layer (E2E):** the payload itself is encrypted with a key derived from X3DH-style key agreement and evolved per-message via the Double Ratchet algorithm. Compromising a mix node's keys does not expose message content.

**Current status:** X3DH bootstrap and Double Ratchet are implemented in the pre-alpha prototype. This implementation has not been subjected to third-party cryptographic review and is not production-hardened.

## Control-Plane Integrity

The directory of active nodes is fetched from Solana RPC endpoints. A single compromised RPC can return a poisoned routing table, steering packets onto attacker-controlled nodes before any cryptography is exercised.

**Mitigation:** multi-RPC quorum validation. Clients fetch directory snapshots from multiple independent RPC endpoints and require k-of-n agreement before route construction. Freshness filtering excludes stale entries.

**Hardening roadmap:** cryptographic uptime attestations signed by validators, validator-backed node admission, auditable registry change logs.

## Prototype Threat Model

Phase 0 aims to test:
- whether 3-hop off-chain routing is operationally clean
- whether delay profiles are usable enough to continue
- whether gateway mailboxes can support offline recipients
- whether a Solana registry is enough to coordinate nodes without central infrastructure
- whether multi-RPC quorum validation is effective against RPC poisoning

Phase 0 does not prove:
- resistance to global passive adversaries
- meaningful anonymity under small network size
- censorship resistance against resourced state actors
- production-safe cryptographic composition
- E2E encryption security under adversarial conditions

## Delay Profiles

The prototype exposes three delay profiles for measurement only:

- `NoDelay`
- `ReducedPoisson`
- `LoopixLike`

These are test configurations.

They are not validated public anonymity modes, and they should not be marketed as such until measurements and review justify it.

## Solana Responsibilities

Solana handles:
- node registry
- stake state
- reward bookkeeping
- parameter placeholders for future protocol tuning

Solana does not handle:
- mailboxes
- packet forwarding
- message payload persistence
- user identity

## Deferred Work

The following are real ideas, but not Phase 0 work:

- Groth16 ZK admission and spam control
- Post-quantum key encapsulation (ML-KEM-1024 hybrid) — roadmap
- Third-party cryptographic review of E2E implementation
- Mobile and browser products
- Tokenomics
- Production governance
- Group messaging

## Honest Limitation

The biggest technical risk is still the same:

Mixnets are only worth anything if the measured latency, bandwidth overhead, and anonymity-set assumptions survive contact with a real network.

That is exactly what Phase 0 is for.
