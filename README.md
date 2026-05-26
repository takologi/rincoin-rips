# Rincoin Improvement Proposals (RIPs)

This repository contains the formal Rincoin Improvement Proposals (RIPs). RIPs describe consensus rules, processes, and best practices for the Rincoin protocol.

The RIP process itself is defined in [RIP-0001](rip-0001/rip-0001.md).

---

## Bootstrap status (read this first)

This repository is in a **bootstrap phase**. Specifically:

- The RIP process described in RIP-0001 was published without a prior public discussion period. RIP-0001 is itself in `Draft` and is subject to revision.
- No public discussion venue ("Discussion-To") is yet operational. Preambles list `TBD` accordingly.
- The set of editors is bootstrapped at two: the original author of these documents and one independent editor (see [`governance/editor-changes.md`](governance/editor-changes.md)). Further editors will be appointed per RIP-0001 §Editors.
- Almost every Standards Track RIP in this repository was authored unilaterally and has not yet undergone substantive editor or community review. Such RIPs are marked `Idea` (a pre-`Draft` state defined in RIP-0001 §RIP Status). Do not interpret their presence here as endorsement by Rincoin's user community.

Until that changes, RIPs in this repository should be read as **proposals from their respective authors**, not as ratified protocol policy.

---

## Index

| Number | Title | Layer | Type | Status |
|--------|-------|-------|------|--------|
| [0001](rip-0001/rip-0001.md) | RIP Process and Specifications | Process | Process | Draft |
| [0002](rip-0002/rip-0002.md) | Customized Halving Schedule | Consensus (HF) | Standards Track | Draft |
| [0003](rip-0003/rip-0003.md) | Conditional Stability Valve — Scenario III Activation Protocol | Consensus (HF, conditional) | Standards Track | Idea |
| [0004](rip-0004/rip-0004.md) | MWEB Integration with HogEx Consensus Fix | Consensus (SF) | Standards Track | Idea |
| [0005](rip-0005/rip-0005.md) | Proof of Rinne — Reincarnation Consensus Mechanism | Consensus (HF) | Standards Track | Idea |
| [0006](rip-0006/rip-0006.md) | Cryptographic Vault and ZKP Owner Recovery | Consensus (HF) | Standards Track | Idea |
| [0007](rip-0007/rip-0007.md) | Sweeper Bounty Mechanism for Forced Extraction | Consensus (HF) | Standards Track | Idea |
| [0008](rip-0008/rip-0008.md) | Phased Legacy Address Migration Protocol | Consensus (HF) | Standards Track | Idea |
| [0009](rip-0009/rip-0009.md) | RinHash Transaction Version Enforcement (RIN3) | Consensus (HF) | Standards Track | Idea |
| [0010](rip-0010/rip-0010.md) | Dynamic Subsidy Scaling | Consensus (HF) | Standards Track | Idea |
| [0011](rip-0011/rip-0011.md) | Rincoin Core Versioning Scheme | — | Informational | Draft |

Status meanings are defined in RIP-0001 §RIP Status.

---

## Whitepaper reference

Most Standards Track RIPs cite the Rincoin Whitepaper:

> Tokino, M. *On the Convergence of Regenerative Thermodynamic Security and Economic Incentives.* May 2026. DOI: [10.5281/zenodo.17141922](https://doi.org/10.5281/zenodo.17141922).

The whitepaper is a research document, not a normative protocol specification. Each RIP that depends on it cites the specific sections it uses.

---

## Repository Structure

```
rincoin-rips/
├── README.md
├── SECURITY.md
├── rip-NNNN/
│   └── rip-NNNN.md
├── doc/
│   └── assets/
├── governance/
│   ├── core-role.md          # Project-level role assignments (not part of the RIP process)
│   └── editor-changes.md     # Append-only log of RIP editor changes
└── security/
    └── *_public.asc          # Editor / author GPG keys
```

Reference implementations and simulation suites referenced by individual RIPs:

- [`rincoin-sim`](https://github.com/Aevust/rincoin-sim): regtest validation harness (1/1000 scale)
- [`rincoin-regenerative-simulations`](https://github.com/Aevust/rincoin-regenerative-simulations): Monte Carlo simulation suite

These are author-maintained and not part of this repository.

---

## Contributing

New RIPs and changes to existing RIPs SHOULD follow the procedure in RIP-0001 §RIP Workflow. While no public Discussion-To venue is operational, pre-RIP discussion can be opened as a GitHub issue against this repository.

---

## License

All RIPs in this repository are licensed under [CC0-1.0](https://creativecommons.org/publicdomain/zero/1.0/).
