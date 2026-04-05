# NullWire Phase 0 Protocol Plan

## Executive Summary

NullWire Phase 0 is not a Tor replacement. It is a prototype of a blockchain-coordinated mixnet messaging system.

The prototype proves four things:
- off-chain encrypted payload routing through a 3-hop relay path works
- Solana can coordinate nodes and rewards as a control plane
- latency and bandwidth overhead can be measured instead of guessed
- the public docs can be made technically consistent

## Architecture Decision

One decision is now fixed:

- Solana is control plane only
- message payloads stay off-chain
- gateways and relays handle routing, buffering, and delivery

Solana stores:
- node registry
- stake state
- reward bookkeeping
- protocol parameter placeholders

Solana does not store:
- messages
- inbox contents
- sender or receiver identity
- communication metadata

If payloads go on-chain, the architecture gets worse on cost, throughput, and visibility. That path is dead.

## Phase 0 Scope

Build only:
- Solana devnet control-plane program for registry, staking state, and reward bookkeeping
- Rust relay service for 3-hop forwarding with layered sealed packets
- Rust gateway service for submission and mailbox polling
- Rust CLI for directory fetch, node registration, send, receive, and cover-traffic simulation
- measurement harness and operator docs

Do not build yet:
- on-chain payload routing
- token launch
- anonymous credentials or Groth16 (roadmap)
- mobile, web, or browser products
- group messaging
- file transfer
- voice or video
- "nation-state resistant" marketing

## E2E Encryption Status

X3DH-style key bootstrap and Double Ratchet end-to-end encryption are implemented in the pre-alpha prototype.

What this means:
- the sender performs an initial key agreement using the recipient's signed pre-key and one-time pre-key published to the recipient's gateway mailbox
- a shared secret is established from which session keys are derived via the Double Ratchet algorithm
- each message is encrypted with a unique per-message key, providing forward secrecy from the first exchange

What this does not mean:
- the implementation has been subjected to third-party cryptographic review
- it is production-safe
- it replaces the need for a formal audit before any public deployment

## Concrete Protocol Surface

### Node Registry

Each node publishes:
- `node_id`
- `role`
- `endpoint`
- `transport_pubkey_hex`
- `stake_state`
- `last_seen_unix`
- `reputation`

Roles:
- `RelayLayer1`
- `RelayLayer2`
- `RelayLayer3`
- `Gateway`

### Client to Gateway

Client actions:
- fetch directory snapshot (multi-RPC quorum validated)
- submit fixed-size packet
- poll recipient mailbox

Gateway actions:
- forward packet to first relay
- receive final delivery from last relay
- store mailbox entries for offline recipient retrieval
- publish recipient pre-keys for X3DH bootstrap

### Relay Packet

Phase 0 packet rules:
- fixed size only (2048 bytes)
- opaque encrypted payload body
- nested encrypted hop directives (Sphinx format)
- configurable delay profile
- optional cover-traffic flag

### Rewards

Phase 0 reward model:
- track forwarded packet counts
- record devnet-only lamport obligations per epoch
- no token
- no production governance

## Test Plan

### Functional

- Register 3 relays and 2 gateways.
- Fetch the directory snapshot.
- Send Alice -> Bob through 3 hops.
- Deliver to Bob's gateway mailbox.
- Poll and retrieve from Bob's mailbox.

### Failure

- Kill one relay and confirm forwarding failure is surfaced.
- Use stale registry data and confirm refresh is required.
- Simulate control-plane unavailability and confirm cached snapshot behavior is explicit.
- Submit a conflicting directory snapshot across RPCs and confirm quorum rejection.

### Measurement

- Measure median and p95 latency for:
  - no delay
  - reduced delay
  - Loopix-like delay
- Measure bandwidth overhead with and without cover traffic.
- Measure throughput ceiling per relay and per gateway on one host.

### Security Sanity

- Confirm payload never touches chain.
- Confirm logs do not contain plaintext.
- Confirm no stable user identity is required in the prototype.
- Confirm multi-RPC quorum rejects a single malicious directory snapshot.

## Success Criteria

Continue only if:
- 3-hop delivery works repeatedly
- measured latency is tolerable enough to justify a Shadow-like next phase
- docs and code describe the same system
- external review finds no fatal architectural flaw

Kill or pivot if:
- off-chain routing plus cover-traffic overhead looks non-viable
- relay coordination on Solana creates unacceptable operational friction
- the system only works by quietly dropping the anonymity goals

## Current Positioning

The right claim for Phase 0 is:

`NullWire is a pre-alpha prototype of a blockchain-coordinated mixnet messaging system with X3DH + Double Ratchet E2E encryption.`

The wrong claims are:
- Tor replacement
- nation-state resistant
- traffic analysis solved
- production ready privacy network
- E2E encryption is audited or production-safe
