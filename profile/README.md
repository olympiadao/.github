# Olympia — Protocol-Native Treasury for Ethereum Classic

> **Demo v0.2** — Olympia ECIP spec compliant. Deployed for live Mordor and ETC mainnet development testing. Pre-Olympia EVM (Shanghai), OpenZeppelin v5.1.0 (governance). Production deployment pending Olympia hard fork activation.

Olympia introduces a native treasury system to Ethereum Classic — transparent, on-chain funding for public goods, infrastructure, and ecosystem growth. No new inflation. No upgrade keys. Governed by soulbound NFT membership.

---

## How It Works

EIP-1559 basefee revenue flows to an immutable on-chain Treasury. Any ETC address can submit funding proposals through the [ECFPRegistry](https://ecips.ethereumclassic.org/ECIPs/ecip-1114). Soulbound NFT holders review, vote, and govern withdrawals through a timelock-protected pipeline with three layers of [sanctions compliance](https://ecips.ethereumclassic.org/ECIPs/ecip-1119).

**Miners are untouched.** Olympia uses basefee that would otherwise be burned — block rewards remain exactly as they are today.

**Governance pipeline:**

1. **Submit** — Any ETC address submits a funding proposal to the ECFPRegistry (permissionless)
2. **Review** — Draft enters a minimum review period before activation
3. **Vote** — Soulbound NFT holders vote via OlympiaGovernor (1 NFT = 1 vote)
4. **Queue** — Approved proposals enter a timelock delay
5. **Execute** — OlympiaExecutor withdraws from Treasury with a final sanctions check

---

## Five Stages

| Stage | Focus | Status |
|-------|-------|--------|
| **1 — Hard Fork** | [EIP-1559 activation](https://ecips.ethereumclassic.org/ECIPs/ecip-1111), [Treasury deployment](https://ecips.ethereumclassic.org/ECIPs/ecip-1112), [EVM compatibility](https://ecips.ethereumclassic.org/ECIPs/ecip-1121) (15 EIPs) | Implemented across 3 clients, activation block TBD |
| **2 — Governance** | [Governor](https://ecips.ethereumclassic.org/ECIPs/ecip-1113), [funding proposals](https://ecips.ethereumclassic.org/ECIPs/ecip-1114), [sanctions compliance](https://ecips.ethereumclassic.org/ECIPs/ecip-1119) | Demo v0.2 deployed to Mordor + ETC mainnet |
| **3 — Futarchy** | [Prediction market governance](https://ecips.ethereumclassic.org/ECIPs/ecip-1117), [streaming disbursements](https://ecips.ethereumclassic.org/ECIPs/ecip-1118) | Research complete |
| **4 — Miner Distribution** | [L-curve smoothing](https://ecips.ethereumclassic.org/ECIPs/ecip-1115) for miner incentives | Spec written |
| **5 — Protocol Hardcode** | [Basefee split](https://ecips.ethereumclassic.org/ECIPs/ecip-1116), [miner distribution curve](https://ecips.ethereumclassic.org/ECIPs/ecip-1122) at consensus layer | Deferred |

Each stage builds on the operational reality of the previous one. Defined by [11 ECIPs](https://github.com/olympiadao/olympia-framework) (ECIP-1111 through ECIP-1122).

> **Mordor Testnet Activation:** Block TBD
> **ETC Mainnet Target:** Block TBD

---

## Three Independent Clients

All consensus changes are implemented and verified across three ETC clients:

| Client | Language | Consensus Tests |
|--------|----------|----------------|
| [core-geth](https://github.com/ethereumclassic/core-geth) | Go | All passing |
| [besu](https://github.com/ethereumclassic/besu) | Java | All passing |
| [fukuii](https://github.com/ethereumclassic/fukuii) | Scala | All passing |

All three produce identical Treasury balances and agree on every consensus-critical state transition.

---

## Current Status

All repositories use a three-branch development model:

| Branch | Purpose | EVM | OpenZeppelin | Status |
|--------|---------|-----|-------------|--------|
| `demo_v0.1` | Early scaffolding, fast iteration | Shanghai | v5.1.0 (governance) | Archived snapshot |
| **`demo_v0.2`** | **ECIP spec-compliant testing** | **Shanghai** | **v5.1.0 (governance)** | **Active — deployed to Mordor + ETC mainnet** |
| `main` | Production target | Cancun (post-Olympia) | v5.6.0 (governance) | Drafted — deploys after Olympia hard fork activates |

**`demo_v0.2` is the active development branch across all repositories.** It runs on the current pre-Olympia EVM (Shanghai) and is deployed to both Mordor testnet and ETC mainnet for live governance testing. The Treasury contract is pure Solidity with no external dependencies — identical bytecode across all branches.

The `main` branch targets the post-Olympia EVM (Cancun with MCOPY, transient storage, etc.) and will be activated after the Olympia hard fork. It uses OpenZeppelin v5.6.0, which requires Cancun opcodes unavailable on the current EVM.

---

## Deployed Contracts (Demo v0.2)

Identical addresses on Mordor testnet and ETC mainnet (deterministic CREATE2 deployment).

| Contract | Address |
|----------|---------|
| OlympiaTreasury | [`0x035b…1bf`](https://etc.blockscout.com/address/0x035b2e3c189B772e52F4C3DA6c45c84A3bB871bf) |
| OlympiaGovernor | [`0xB85d…23D`](https://etc.blockscout.com/address/0xB85dbc899472756470EF4033b9637ff8fa2FD23D) |
| OlympiaExecutor | [`0x6462…9a`](https://etc.blockscout.com/address/0x64624f74F77639CbA268a6c8bEDC2778B707eF9a) |
| TimelockController | [`0xA583…C2`](https://etc.blockscout.com/address/0xA5839b3e9445f7eE7AffdBC796DC0601f9b976C2) |
| ECFPRegistry | [`0xFB4D…22`](https://etc.blockscout.com/address/0xFB4De5674a6b9a301d16876795a74f3bdacfa722) |
| SanctionsOracle | [`0xfF2B…09`](https://etc.blockscout.com/address/0xfF2B8D7937D908D81C72D20AC99302EE6ACc2709) |
| OlympiaMemberNFT | [`0x73e7…72`](https://etc.blockscout.com/address/0x73e78d3a3470396325b975FcAFA8105A89A9E672) |

---

## Repositories

| Repository | Purpose |
|------------|---------|
| [olympia-framework](https://github.com/olympiadao/olympia-framework) | 11 ECIP specifications and technical coordination |
| [olympia-governance-contracts](https://github.com/olympiadao/olympia-governance-contracts) | Governor, Executor, Registry, Oracle, NFT (Solidity) |
| [olympia-treasury-contract](https://github.com/olympiadao/olympia-treasury-contract) | Immutable Treasury vault (pure Solidity) |
| [olympia-app](https://github.com/olympiadao/olympia-app) | Governance web application |
| [olympia-brand](https://github.com/olympiadao/olympia-brand) | Logo, design tokens, brand assets |
| [olympiadao-org](https://github.com/olympiadao/olympiadao-org) | [olympiadao.org](https://olympiadao.org) |
| [olympiatreasury-org](https://github.com/olympiadao/olympiatreasury-org) | [olympiatreasury.org](https://olympiatreasury.org) |
| [ethereumclassicdao-org](https://github.com/EthereumClassicDAO/ethereumclassicdao-org) | [ethereumclassicdao.org](https://ethereumclassicdao.org) |

---

## Principles

- **Code is Law** — governance enforced by smart contracts
- **Immutability is Integrity** — no admin backdoors, no upgrade proxies
- **Neutrality is Strength** — permissionless participation
- **Funding is Permissionless** — anyone can submit proposals, soulbound NFT holders vote

---

## Learn More

- [OlympiaDAO.org](https://olympiadao.org) — Project overview
- [OlympiaTreasury.org](https://olympiatreasury.org) — Live treasury data
- [EthereumClassicDAO.org](https://ethereumclassicdao.org) — DAO LLC
- [Governance App](https://app.olympiadao.org) — Submit proposals, vote, execute
- [ECIPs 1111–1122](https://github.com/ethereumclassic/ECIPs) — Full specifications
- [ETC Discord](https://ethereumclassic.org/discord) — Community
