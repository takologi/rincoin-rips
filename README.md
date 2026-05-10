# Rincoin Improvement Proposals (RIPs)

This repository contains the formal Rincoin Improvement Proposals (RIPs). RIPs describe consensus rules, processes, and best practices for the Rincoin protocol.

The RIP process itself is defined in [RIP-0001](rip-0001.md).

## Index

| Number | Title | Layer | Type | Status | Requires |
|---|---|---|---|---|---|
| [0001](rip-0001.md) | RIP Process and Specifications | Process | Process | Active | — |
| [0002](rip-0002.md) | Customized Halving Schedule | Consensus (HF) | Standards Track | **Active** | RIP-0001 |
| [0003](rip-0003.md) | Conditional Stability Valve — Scenario III Activation Protocol | Consensus (HF, conditional) | Standards Track | Draft | RIP-0001, RIP-0002 |
| [0004](rip-0004.md) | MWEB Integration with HogEx Consensus Fix | Consensus (SF, mainnet `NEVER_ACTIVE`) | Standards Track | Draft | RIP-0001 |
| [0005](rip-0005.md) | Proof of Rinne — Reincarnation Consensus Mechanism | Consensus (HF) | Standards Track | Draft | RIP-0001, RIP-0002 |
| [0006](rip-0006.md) | Cryptographic Vault and ZKP Owner Recovery | Consensus (HF) | Standards Track | Draft | RIP-0001, RIP-0005 |
| [0007](rip-0007.md) | Sweeper Bounty Mechanism for Forced Extraction | Consensus (HF) | Standards Track | Draft | RIP-0001, RIP-0006 |
| [0008](rip-0008.md) | Phased Legacy Address Migration Protocol | Consensus (HF) | Standards Track | Draft | RIP-0001, RIP-0006, RIP-0007 |

## Activation Timeline

RIPs activate at the following block heights (mainnet, 60 s/block):

| Block Height | Approx. Year | RIP(s) Activating | Status | Mechanism |
|---|---|---|---|---|
| 0 (genesis) | 0 | RIP-0002 | ✅ Active | Embedded in chainparams from genesis (Core v1.0.6) |
| **— (mainnet `NEVER_ACTIVE`)** | — | RIP-0004 (MWEB) | **Suspended** | Sealed via BIP9 NEVER_ACTIVE; reactivation requires successor RIP |
| 840 (testnet/regtest) | — | RIP-0004 (MWEB) | Active on testnet/regtest | Soft-fork activation for validation purposes |
| 840,000 | ~1.60 | RIP-0002 CH activation boundary | ⏳ Pending | Hard-fork flag day |
| 5,250,000–6,260,000 | ~10–12 | RIP-0003 (CSV) — signaling window | ⏳ Pending | BIP9-style with objective gating, bit 1, threshold 90% |
| 6,300,000 | ~12 | RIP-0002 terminal phase entry / RIP-0003 (if activated) | ⏳ Pending | Automatic |
| 15,768,000 | ~30 | RIP-0007, RIP-0008 | ⏳ Pending | Time-deterministic hard fork |
| ~233,280,000 | ~444 | RIP-0005, RIP-0006 (full activation) | ⏳ Pending | Time-deterministic hard fork at PoR |

Current chain progress: see [Rincoin Core](https://github.com/Rin-coin/rincoin) repository.

RIP-0001 is `Active` as the governing process specification. RIP-0002 (Customized Halving) is `Active`: the schedule has been enforced from genesis on the Rincoin mainchain via Core v1.0.6, with Phase 0→1 and Phase 1→2 boundaries validated in production. RIP-0003 and RIP-0005 through RIP-0008 are `Draft`. Reference implementations exist in [`rincoin-sim`](https://github.com/Aevust/rincoin-sim) and [Rincoin Core](https://github.com/Rin-coin/rincoin) for RIP-0002 and RIP-0004; reference implementations for RIP-0003 and RIP-0005 through RIP-0008 are pending.

**Note on RIP-0004 (MWEB)**: While the specification is implemented in Core v1.0.6 and validated in `rincoin-sim`, the mainnet activation has been suspended via BIP9 `NEVER_ACTIVE` per a strategic decision of the Rincoin Core Authority. The suspension is documented in §2.1 of RIP-0004. Testnet and regtest activation at block 840 remains in effect for validation purposes. Any future reactivation requires a successor RIP per the conditions outlined in RIP-0004.

## Dependency Graph

```
RIP-0001 (Process, foundational)
    │
    ├──► RIP-0002 (Customized Halving)
    │       │
    │       ├──► RIP-0003 (Conditional Stability Valve)
    │       │
    │       └──► RIP-0005 (Proof of Rinne)
    │               │
    │               └──► RIP-0006 (Cryptographic Vault & ZKP)
    │                       │
    │                       ├──► RIP-0007 (Sweeper Bounty)
    │                       │
    │                       └──► RIP-0008 (Phased Migration) ──┐
    │                                ▲                          │
    │                                └──────────────────────────┘
    │                                      (also requires RIP-0007)
    │
    └──► RIP-0004 (MWEB Integration & HogEx Fix)
            (independent of regenerative stack)
```

## Status Definitions

- **Draft**: Initial state. Specification is open to revision.
- **Proposed**: Specification frozen, reference implementation available, ready for community review.
- **Active**: Process RIPs in effect; deployed Standards Track RIPs.
- **Final**: Standards Track RIPs whose activation has completed.
- **Replaced**, **Withdrawn**, **Deferred**, **Rejected**: see RIP-0001.

## Whitepaper Reference

All RIPs in this repository normatively cite the Rincoin Whitepaper v1.6.3:

> Tokino, M. *On the Convergence of Regenerative Thermodynamic Security and Economic Incentives.* May 2026. DOI: [10.5281/zenodo.17141922](https://doi.org/10.5281/zenodo.17141922).

The mapping between whitepaper sections and RIPs:

| Whitepaper Section | RIP |
|---|---|
| §1 Introduction (Tetra-Lemma) | Motivation contexts in RIP-0002, RIP-0005 |
| §2 Network Specifications | (informational; not RIP'd) |
| §3 Customized Halving Mechanism | RIP-0002 (baseline), RIP-0003 (Scenario III) |
| §4 Proof of Rinne | RIP-0005 |
| §5 Algorithmic Governance of τ | RIP-0005 §6 (Delay Parameter Governance) |
| §6 Adversarial Models & Asset Lifecycle | RIP-0006, RIP-0007, RIP-0008 |
| §6.1 Type A entropic loss | (mathematical foundation; not RIP'd directly) |
| §6.2 Type B adversarial extraction | RIP-0006 (Vault as defense), RIP-0007 (Sweeper as preemption) |
| §6.3 Sweeper Gold Rush | RIP-0007 |
| §6.4 Cryptographic Vault | RIP-0006 |
| §6.4.4 Phased Migration & Temporal Smoothing | RIP-0008 |
| §6.5 Macroeconomic equilibrium analysis | (referenced from RIP-0005, RIP-0006, RIP-0007) |
| §6.7 Sensitivity Boundaries | (referenced; future Informational RIP candidate) |

## Repository Structure

```
rincoin-rips/
├── README.md           # This file
├── SECURITY.md         # Editor contacts and signing key fingerprints
├── rip-0001.md         # RIP Process
├── rip-0002.md         # Customized Halving
├── rip-0003.md         # Conditional Stability Valve
├── rip-0004.md         # MWEB Integration & HogEx Fix
├── rip-0005.md         # Proof of Rinne
├── rip-0006.md         # Cryptographic Vault & ZKP
├── rip-0007.md         # Sweeper Bounty
├── rip-0008.md         # Phased Legacy Address Migration
└── security/
    └── *_public.asc    # PGP/GPG public keys referenced by SECURITY.md
```

Reference implementations and simulation suites:

- [`rincoin-sim`](https://github.com/Aevust/rincoin-sim): regtest validation harness (1/1000 scale)
- [`rincoin-regenerative-simulations`](https://github.com/Aevust/rincoin-regenerative-simulations): Monte Carlo simulation suite for whitepaper §4–§6

## Contributing

Pull requests for new RIPs MUST follow the procedure in RIP-0001 §RIP Workflow. Submit Pre-RIP discussion to the Rincoin development forum or `#rip-drafts` Discord channel before opening a PR.

## License

All RIPs in this repository are licensed under [CC0-1.0](https://creativecommons.org/publicdomain/zero/1.0/).
