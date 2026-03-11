# Olympia Upgrade — Ethereum Classic Protocol Treasury

> Decentralized, permissionless, and sustainable funding for Ethereum Classic.

Olympia is the protocol upgrade that introduces a native treasury system to Ethereum Classic — enabling transparent, on-chain funding for public goods, infrastructure, and ecosystem growth, governed by code, not committees.

---

## Overview

Olympia is a multi-phase protocol upgrade for Ethereum Classic defined by 11 ECIPs across 5 stages:

**Stage 1 — Consensus (Implemented)**
- **ECIP-1111**: Activates EIP-1559 dynamic basefee pricing; redirects basefee to Treasury instead of burning
- **ECIP-1112**: Deploys the immutable Olympia Treasury contract with staged access control
- **ECIP-1121**: EVM compatibility sprint — 15 EIPs including MCOPY, transient storage, BLS12-381, and EOA delegation

**Stage 2 — Governance (In Progress)**
- **ECIP-1113**: CoreDAO governance framework — Governor, Timelock, Executor pipeline with NFT-based voting
- **ECIP-1114**: ECFP funding proposal process — permissionless, hash-bound proposal registry
- **ECIP-1119**: Sanctions constraint — three-layer defense at proposal, lifecycle, and execution layers

**Stage 3 — Experimental Governance (Planned)**
- **ECIP-1117**: Futarchy DAO — prediction market governance with conditional outcome markets
- **ECIP-1118**: Streaming disbursements — milestone-gated fund releases with governance-authorized clawback

**Stage 4 — Miner Distribution (Planned)**
- **ECIP-1115**: L-curve smoothing — governance-controlled miner incentive reshaping

**Stage 5 — Protocol Hardcode (Deferred)**
- **ECIP-1116**: Embed validated basefee split at consensus layer
- **ECIP-1122**: Protocol-native miner distribution curve

Together, these ECIPs provide a modular, non-inflationary, and permissionless system for sustainable protocol funding. Each stage builds on the operational reality of the previous one.

> **Mordor Testnet Activation**: Block 15,800,850 (~March 28, 2026)
> **ETC Mainnet Target**: ~Block 24,751,337 (~mid-June 2026)

---

## Why Olympia?

Ethereum Classic has operated for nearly a decade without a native development fund. This has led to:

- Team volatility and funding collapses
- Maintenance gaps in core client software
- Centralization risks from off-chain grant programs
- Critical security patches left unbackported

Olympia is a self-sustaining, credibly neutral, on-chain funding mechanism that aligns with ETC's founding values of immutability, decentralization, and code-is-law.

---

## Three Independent Clients

All consensus-critical changes are implemented and verified across three independent ETC clients:

| Client | Language | Status |
|--------|----------|--------|
| [core-geth](https://github.com/ethereumclassic/core-geth) | Go 1.24 | ALL PASS |
| [besu](https://github.com/ethereumclassic/besu) | Java 21 | ALL PASS |
| [fukuii](https://github.com/ethereumclassic/fukuii) | Scala 3.3 | ALL PASS |

Cross-client verification completed March 2026. All three clients produce identical Treasury balances and agree on all consensus-critical state transitions.

---

## Core Features

- **No new inflation** — uses existing basefee from EIP-1559, not block rewards
- **Immutable Treasury** — OpenZeppelin AccessControlDefaultAdminRules vault, no upgrade keys
- **Open Participation** — any NFT-holding member can submit and vote on proposals
- **Governance Isolated from Protocol** — funding logic is contract-layer, separate from consensus
- **Sanctions Compliance** — three-layer defense integrated at proposal, lifecycle, and execution stages
- **Modular and Extensible** — future governance experiments via additional ECIPs without hard forks

---

## Deployed Contracts (Mordor Testnet)

| Contract | Address |
|----------|---------|
| OlympiaGovernor | `0xEdbD61F1cE825CF939beBB422F8C914a69826dDA` |
| OlympiaExecutor | `0x94d4f74dDdE715Ed195B597A3434713690B14e97` |
| TimelockController | `0x1E0fADee5540a77012f1944fcce58677fC087f6e` |
| ECFPRegistry | `0xcB532fe70299D53Cc81B5F6365f56A108784d05d` |
| SanctionsOracle | `0xEeeb33c8b7C936bD8e72A859a3e1F9cc8A26f3B4` |
| OlympiaMemberNFT | `0x720676EBfe45DECfC43c8E9870C64413a2480EE0` |
| OlympiaTreasury | `0xd6165F3aF4281037bce810621F62B43077Fb0e37` |

---

## Philosophy

Olympia is grounded in Ethereum Classic's founding principles:

- **Code is Law** — governance rules are enforced by smart contracts, not committees
- **Immutability is Integrity** — the Treasury contract has no admin backdoors
- **Neutrality is Strength** — permissionless participation, no gatekeepers
- **Funding should be Permissionless** — anyone can propose, anyone can vote

---

## Repository Structure

| Repository | Description |
|------------|-------------|
| [olympia-framework](https://github.com/olympiadao/olympia-framework) | Specifications, technical documentation, and coordination |
| [olympia-governance-contracts](https://github.com/olympiadao/olympia-governance-contracts) | Solidity contracts (Governor, Executor, Registry, Oracle) |
| [olympia-treasury-contract](https://github.com/olympiadao/olympia-treasury-contract) | Treasury vault contract |
| [olympia-app](https://github.com/olympiadao/olympia-app) | Governance web application |
| [olympia-brand](https://github.com/olympiadao/olympia-brand) | Logo, design tokens, brand assets |

---

## Resources

- [OlympiaDAO.org](https://olympiadao.org) — Project overview and status
- [OlympiaTreasury.org](https://olympiatreasury.org) — Treasury monitoring
- [ECIPs 1111–1122](https://github.com/ethereumclassic/ECIPs) — Ethereum Classic Improvement Proposals
- [ETC Discord](https://discord.gg/ethereumclassic) — Community discussion

---

## License

Released under the [MIT License](./LICENSE).
