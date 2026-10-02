# Contributions and technical work

I build and maintain cryptographic software, with a focus on proof verification, arithmetic, and developer tooling.

This catalog connects my work to public code, reviews, reports, and project credits. Most major projects belong to external organizations.

[Profile](https://github.com/feltroidprime) · [Website](https://felt.md) · [Full public activity index](ACTIVITY.md)

## Garaga: library development and maintenance

I started Garaga in late 2022 and became its lead open-source developer and maintainer. The project began with practical pairing verification in Cairo.

My responsibilities covered the library, SDKs, contract integration, releases, contributor reviews, documentation, CI, and community support. Garaga is a collaborative project.

| Area | Work and evidence |
| --- | --- |
| Cryptographic arithmetic | Elliptic curves, pairings, emulated arithmetic, polynomial identities, multi-scalar multiplication, and witness generation. [Library](https://github.com/keep-starknet-strange/garaga) |
| Rust and bindings | Rust witness and calldata generation, Python bindings, and integration with WASM/TypeScript tooling. [Rust calldata API #229](https://github.com/keep-starknet-strange/garaga/pull/229) |
| Proof verification | Groth16, Noir/Honk, and verification paths for SP1 and RISC Zero proofs. [SP1 integration #398](https://github.com/keep-starknet-strange/garaga/pull/398), [version updates #438](https://github.com/keep-starknet-strange/garaga/pull/438) |
| Signatures | Witness generation and Cairo verification for ECDSA and Schnorr. [PR #300](https://github.com/keep-starknet-strange/garaga/pull/300) |
| CI and releases | Generated-artifact consistency, cross-language calldata parity, end-to-end contract verification, and compatibility changes. [CI #236](https://github.com/keep-starknet-strange/garaga/pull/236) |
| Review and API design | Review of Rust/WASM error handling and compatibility. [Review on #202](https://github.com/keep-starknet-strange/garaga/pull/202#pullrequestreview-2339339144) |
| Performance | Profiling and arithmetic optimization with correctness checks. [Profiling #417](https://github.com/keep-starknet-strange/garaga/pull/417), [addition chains #483](https://github.com/keep-starknet-strange/garaga/pull/483) |

The architecture combines Python circuit generation, Cairo verification, Rust witness computation, and SDK bindings. Cairo constraints must validate untrusted hints.

My maintenance work also included deployed verifier contracts, integration support, and the Garaga Telegram community.

[Starknet's Noir announcement](https://www.starknet.io/blog/noir-on-starknet/) credits the Garaga SDK and my integration work.

## Garaga use in other projects

These public manifests reference Garaga or a Garaga fork. They provide evidence of integration across different projects.

| Project | Dependency evidence |
| --- | --- |
| [EkuboProtocol/privacy-pools](https://github.com/EkuboProtocol/privacy-pools) | [Manifest snapshot](https://github.com/EkuboProtocol/privacy-pools/blob/fdaadcf673dfde5e22b173f4ab0a0bd071407682/Scarb.toml) |
| [cartridge-gg/controller-cairo](https://github.com/cartridge-gg/controller-cairo) | [Manifest snapshot](https://github.com/cartridge-gg/controller-cairo/blob/e3cb4d0e47ce686f9e8576916af6e00bfd89d8dc/Scarb.toml) |
| [argentlabs/exploration-private-token](https://github.com/argentlabs/exploration-private-token) | [Manifest snapshot](https://github.com/argentlabs/exploration-private-token/blob/f63dc1e09482f295cfd9c366e17d254f865b1711/contracts/Scarb.toml) |
| [NethermindEth/starknet-worldcoin-bridge](https://github.com/NethermindEth/starknet-worldcoin-bridge) | [Manifest snapshot](https://github.com/NethermindEth/starknet-worldcoin-bridge/blob/6e80cbf44c20801d45975b8e121a79de9b78e585/state_bridge_l2/world_id_state_bridge/Scarb.toml) |
| [HerodotusDev/hdp-cairo](https://github.com/HerodotusDev/hdp-cairo) | [Manifest snapshot](https://github.com/HerodotusDev/hdp-cairo/blob/5a64e65b0aee7dd8fadd708d73f4aa436c70f009/Scarb.toml) |
| [unionlabs/union](https://github.com/unionlabs/union) | [Manifest snapshot](https://github.com/unionlabs/union/blob/031785bb6dc6b957c624e62bc64c184409c97d7b/Scarb.toml) |
| [informalsystems/ibc-starknet](https://github.com/informalsystems/ibc-starknet) | [Manifest snapshot](https://github.com/informalsystems/ibc-starknet/blob/c62de65042653232149a22c4dd54855175570da3/cairo-libs/Scarb.toml) |
| [BlockstreamResearch/pq-p2pkh](https://github.com/BlockstreamResearch/pq-p2pkh) | [Manifest snapshot](https://github.com/BlockstreamResearch/pq-p2pkh/blob/2081f8a7e72fb744bc8a2f534a074e2def71f4a2/stwo-cairo/Scarb.toml) |
| [starkware-bitcoin/starkstr](https://github.com/starkware-bitcoin/starkstr) | [Manifest snapshot](https://github.com/starkware-bitcoin/starkstr/blob/e259ad278ac57b0024ee51d03f69761da0d5ebb2/packages/aggsig_checker/Scarb.toml) (Garaga fork) |

These references describe library dependencies, rather than my personal authorship of those projects or a commercial partnership.

## Security review and audits

| Project | My contribution | Outcome and source |
| --- | --- | --- |
| gnark BN254 pairing | Identified a missing subfield constraint on a pairing hint during review. | Maintainers confirmed the soundness issue and implemented the fix. [Review](https://github.com/Consensys-Incorporated/gnark/pull/1143#discussion_r1660331215), [report #1213](https://github.com/Consensys-Incorporated/gnark/issues/1213), [maintainer fix #1214](https://github.com/Consensys-Incorporated/gnark/pull/1214) |
| gnark / gnark-crypto fake-GLV | Reported non-convergence in an Eisenstein Half-GCD hint and co-authored the fix with Ivo Kubjas. | Credited in **CVE-2025-58157**. This was a denial of service in the prover. [Report #1483](https://github.com/Consensys-Incorporated/gnark/issues/1483), [merged fix #680](https://github.com/Consensys-Incorporated/gnark-crypto/pull/680), [official advisory](https://github.com/Consensys-Incorporated/gnark/security/advisories/GHSA-9fvj-xqr2-xwg8) |
| Kakarot | Fixed an underconstrained hint in `get_felt_bitlength`. | Added bounds and constraints for the bit-length calculation. [Merged PR #1199](https://github.com/kkrt-labs/kakarot/pull/1199) |
| Privacy Pools Starknet | Conducted the public audit of Cairo contracts, Cairo-side Groth16 integration, Merkle trees, and input handling. | **27 observations: 1 High, 3 Medium, 6 Low, 16 Coding Practice, 1 Documentation.** [Signed report](https://github.com/fatlabsxyz/privacy-pools-starknet/blob/master/audits/audit_12_12_2025_feltroidprime/privacy_pools_starknet_feltroidprime_audit_v1.1.md) |

The Privacy Pools report records 23 resolved observations and four acknowledged observations. Circom constraints, frontend, SDK, relayer, and deployment infrastructure were outside scope.

In gnark, I also reported subgroup-precondition behavior and discussed arithmetic edge cases. [Report #1484](https://github.com/Consensys-Incorporated/gnark/issues/1484), [Karabina discussion #375](https://github.com/Consensys-Incorporated/gnark-crypto/pull/375).

## Rust contributions: Lambdaworks and STARK Platinum

Public Rust contributions date to **June 2023**. These were open-source contributions during my work on Garaga.

| Contribution | Status and evidence |
| --- | --- |
| Proof serialization and Montgomery representation work | Submitted June 2023, closed without merge. [STARK Platinum #50](https://github.com/lambdaclass/lambdaworks_stark_platinum/pull/50) |
| Transcript field conversion, masking, and byte order | Merged June 2023, with tests and contributor collaboration. [STARK Platinum #87](https://github.com/lambdaclass/lambdaworks_stark_platinum/pull/87) |
| Keccak transcript integration | Merged June 2023. [Lambdaworks #442](https://github.com/lambdaclass/lambdaworks/pull/442) |
| Starknet Poseidon and Merkle backends | Merged August 2023, then restored in October after intervening changes. [#524](https://github.com/lambdaclass/lambdaworks/pull/524), [#641](https://github.com/lambdaclass/lambdaworks/pull/641) |
| Polynomial extended GCD | Merged September 2024, including Bézout-identity tests. [#885](https://github.com/lambdaclass/lambdaworks/pull/885) |
| Polynomial differentiation and display | Merged October 2024, for use in Garaga. [#929](https://github.com/lambdaclass/lambdaworks/pull/929) |

## Herodotus: Ethereum history and storage proofs

I developed Cairo programs that authenticate Ethereum block-header chains and build Keccak/Poseidon Merkle mountain range accumulators.

| Work | Merged contributions |
| --- | --- |
| Header processing, Poseidon, and Shanghai support | [Processor #4](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/4), [#5](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/5), [#6](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/6) |
| Differential/random tests, audit fixes, and execution scripts | [#10](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/10), [#11](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/11), [#16](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/16) |
| RLP and Merkle Patricia trie handling | [cairo-lib #19](https://github.com/HerodotusDev/cairo-lib/pull/19) |
| HDP arithmetic and byte handling | [hdp-cairo #14](https://github.com/HerodotusDev/hdp-cairo/pull/14), [#15](https://github.com/HerodotusDev/hdp-cairo/pull/15) |
| Ethereum serialization | [eth_essentials #4](https://github.com/HerodotusDev/eth_essentials/pull/4) |

These public contributions span 2023–2024. Header authentication proves chain history, not execution of every Ethereum transaction.

## Cartridge: Rust proof clients and TEE attestations

My public commits in Cartridge repositories cover Rust clients, Cairo contracts, and AMD SEV-SNP attestation verification through SP1 and Garaga.

| Work | Code evidence |
| --- | --- |
| SP1 proof conversion and Starknet calldata | [Rust calldata module](https://github.com/cartridge-gg/katana-tee/commit/c7ac2b99ea4177f842905301c2e123abf15da3fc) |
| Proof pipeline, CLI, and Starknet invocation | [Client integration](https://github.com/cartridge-gg/katana-tee/commit/dc4de15349401cbddca33d45cce807e17fa3f707) |
| Testable proving and certificate interfaces | [Backend traits](https://github.com/cartridge-gg/katana-tee/commit/f34b81a303cd1a5437abfcdb4cf16ccc9786dd28) |
| Attestation measurement validation | [Contract checks](https://github.com/cartridge-gg/katana-tee/commit/1456cfa38bef286aec13ff8a244ae425aebe74f6) |
| Certificate trust defaults | [AMD SDK change](https://github.com/cartridge-gg/amd-sev-snp-attestation-sdk-base/commit/1efd35844723a2e14557428803df5d44d3f54e5e) |

The KatanaTee contract is documented as a standalone testing integration. The project distinguishes it from production appchain settlement through Piltover.

## Pairing research and gnark optimization ideas

I published [Faster Extension Field Multiplications for Emulated Pairing Circuits](https://hackmd.io/@feltroidprime/B1eyHHXNT), with companion code and measurements.

The article credits Shahar Papini for the initial idea. My work develops its application to emulated extension-field arithmetic and pairing verification.

Two upstream gnark changes credit my optimization ideas. Youssef El Housni implemented them:

- [Miller-loop line precomputation #816](https://github.com/Consensys-Incorporated/gnark/pull/816).
- [BLS12-381 final-exponentiation check #1173](https://github.com/Consensys-Incorporated/gnark/pull/1173).

PR #1173 reports savings of 681,769 SCS constraints or 199,105 R1CS constraints per pairing. These are constraint counts, not runtime measurements.

## Noir/Honk, Kakarot, Keth, and Bitcoin tooling

| Project | Contribution and status |
| --- | --- |
| Aztec / Barretenberg | Merged UltraStarknet and UltraStarknetZK Honk flavors for Garaga integration. [#11489](https://github.com/AztecProtocol/aztec-packages/pull/11489). Later merged a Stark252 field-definition fix. [#17338](https://github.com/AztecProtocol/aztec-packages/pull/17338). These are C++ contributions. |
| Kakarot | Merged jump-destination optimization. [#1034](https://github.com/kkrt-labs/kakarot/pull/1034). My uint-add work was incorporated by Clément Walter. [#1070](https://github.com/kkrt-labs/kakarot/pull/1070). |
| Kakarot-SSJ | Merged elliptic-curve add and multiply. [#855](https://github.com/kkrt-labs/kakarot-ssj/pull/855). |
| Keth | Merged secp256k1 verification/recovery with ECIP and Garaga, plus MSM calldata handling. [#291](https://github.com/kkrt-labs/keth/pull/291), [#690](https://github.com/kkrt-labs/keth/pull/690). |
| Raito | Merged digest-conversion and Poseidon/Merkle optimizations in the Cairo Bitcoin client. [#157](https://github.com/starkware-bitcoin/raito/pull/157), [#312](https://github.com/starkware-bitcoin/raito/pull/312). |
| starknet-rust | Suggested a rejection-sampling approach for private keys. The PR author adopted the method. [Discussion on #98](https://github.com/software-mansion/starknet-rust/pull/98#issuecomment-3898037898). |

Raito #157 reports test gas changing from 1,850,000 to 183,852 for digest-to-u256 conversion. That measurement applies to this operation.

## Post-quantum cryptography

[BTQ's September 2023 announcement](https://www.btq.com/news/completing-the-first-falcon-signature-verification-in-starkware-initiating-the-transition-to-a-quantum-safe-ethereum) credits my Cairo development and consultation for Falcon signature verification.

In 2026, I extended the StarkWare [S2morrow project](https://github.com/starkware-bitcoin/s2morrow) with account contracts, wallet integration, and Rust/WASM signer tooling.

- [My S2morrow fork](https://github.com/feltroidprime/s2morrow) and [Falcon account implementation](https://github.com/feltroidprime/s2morrow/commit/a89a06f60c9baa0afe94c2c896630a6320359167).
- [falcon-rs](https://github.com/feltroidprime/falcon-rs), a Rust port of reference tooling with WASM bindings and configurable hash-to-point.
- [StarkWare's quantum-readiness roadmap](https://starkware.co/blog/the-architecture-advantage-starknets-quantum-readiness-roadmap/) discusses S2morrow.

The Cairo integration uses a Poseidon hash-to-point variant. It does not imply standard SHAKE Falcon interoperability for that mode.

The falcon-rs signer does not provide side-channel protection. Its public README describes the implementation and test vectors.

## Cairo ecosystem maintenance and diagnostics

| Project | Selected work |
| --- | --- |
| Cairo corelib | Merged circuit utilities and tuple support. [#6482](https://github.com/starkware-libs/cairo/pull/6482), [#6500](https://github.com/starkware-libs/cairo/pull/6500) |
| Cairo VM | Merged Cairo modular-arithmetic code and tests in the Kakarot fork, and Linux compatibility upstream. [kkrt-labs #5](https://github.com/kkrt-labs/cairo-vm/pull/5), [upstream #1422](https://github.com/starkware-libs/cairo-vm/pull/1422) |
| Alexandria | Merged storage-proof serialization. [#294](https://github.com/keep-starknet-strange/alexandria/pull/294) |
| starknet.py | Merged bounded-integer ABI parsing. [#1463](https://github.com/software-mansion/starknet.py/pull/1463) |
| Starknet documentation | Merged trie-hash clarification and cryptography documentation. [#1214](https://github.com/starknet-io/starknet-docs/pull/1214), [#1625](https://github.com/starknet-io/starknet-docs/pull/1625) |
| starkup | Merged compatibility with asdf 0.17. [#60](https://github.com/software-mansion/starkup/pull/60) |
| Cairo compiler | Reported compilation regressions and Sierra growth, with reproducible cases. [#9711](https://github.com/starkware-libs/cairo/issues/9711), [#9681](https://github.com/starkware-libs/cairo/issues/9681) |
| Starknet Foundry | Reduced a gas-disabled test configuration problem to a minimal reproduction. [#4151](https://github.com/foundry-rs/starknet-foundry/issues/4151). Maintainers added a clearer unsupported-configuration error. |
| Cairo Profiler | Reported syscall-cost attribution problems. [#239](https://github.com/software-mansion/cairo-profiler/issues/239) |

The [activity index](ACTIVITY.md) also includes open proposals and public review submissions. A report or review is distinct from an implemented patch.

## Personal tools, experiments, and earlier work

| Repository or source | What it contains |
| --- | --- |
| [sp1-starknet-template](https://github.com/feltroidprime/sp1-starknet-template) | SP1 application template with Cairo verification through Garaga, Rust proof generation, documentation, and CI. Built from Succinct's template. |
| [garaga-zero](https://github.com/feltroidprime/garaga-zero) | Historical Cairo Zero variant of Garaga for local proving. |
| [zk-ecip-py](https://github.com/feltroidprime/zk-ecip-py) | Archived Python prototype implementing Liam Eagen's ECIP work, later integrated in Garaga. |
| [builtins-hints](https://github.com/feltroidprime/builtins-hints) | Rust modular-arithmetic hints and Python AIR experiments. The prototype omits range checks. |
| [cairo-perfs-snippets](https://github.com/feltroidprime/cairo-perfs-snippets) | Execution-cost experiments and comparisons of Cairo implementations. |
| [cairo-skills](https://github.com/feltroidprime/cairo-skills) | Cairo development and profiling guides with compiler and performance examples. |
| [cairo-compiler-bug-2-15](https://github.com/feltroidprime/cairo-compiler-bug-2-15) | Reproduction of a compiler performance regression. |
| [snforge-cycle-repro](https://github.com/feltroidprime/snforge-cycle-repro) | Minimal reproduction for the Foundry test-configuration report. |
| [encodePacked-cairo](https://github.com/feltroidprime/encodePacked-cairo) | Early input-packing prototype for Keccak. Big-endian mode was not implemented. |
| [empiric-twap](https://github.com/feltroidprime/empiric-twap) | On-chain rolling-window TWAP prototype from 2022. |
| [Open Oracle mirror](https://github.com/joshualyguessennd/StarkNet-Open-Oracle/commit/9c9206bd6ce55d36ed99da858dbe4f9449159a77) | Preserved 2022 Cairo work on Ethereum-message signatures, serialization, and Keccak, in a third-party public mirror. |
| [hello_hints](https://github.com/feltroidprime/hello_hints) | Experimental Python client/server and Cairo hints example. |
| [CTF-starknet-cc](https://github.com/feltroidprime/CTF-starknet-cc) | Collaborative Cairo CTF challenges and scripts. |
| [python-design-guardrails-pack](https://github.com/feltroidprime/python-design-guardrails-pack) | Python engineering guidance and tools. The public activity index includes its development history. |
| [article2md](https://github.com/feltroidprime/article2md) | Next.js/TypeScript application that converts X articles to Markdown, with copy and download. |
| [telegram-clipboard](https://github.com/feltroidprime/telegram-clipboard) | Python bot that copies Telegram messages to a Linux clipboard, with systemd user-service installation. |
| [fedora-screenshot-tools](https://github.com/feltroidprime/fedora-screenshot-tools) | GNOME/Wayland screenshot workflows for Claude Code and file transfers to Tailscale peers. |
| [world-id-v4-starknet-brief](https://github.com/feltroidprime/world-id-v4-starknet-brief) | An integration brief, rather than a delivered verifier implementation. |

The [repository index](ACTIVITY.md#public-repositories) covers all public repositories, including forks and smaller utilities.

## General developer tooling

I contributed upstream changes beyond cryptography:

- **sandboxed.sh:** UI fixes and ARM support for packaged tooling and Linux environment setup. [#161](https://github.com/Th0rgal/sandboxed.sh/pull/161), [#162](https://github.com/Th0rgal/sandboxed.sh/pull/162), [#163](https://github.com/Th0rgal/sandboxed.sh/pull/163), [#165](https://github.com/Th0rgal/sandboxed.sh/pull/165). All merged.
- **thunderbird-mcp:** proposed fixes for JSON control characters, reply metadata, and attachments. [#1](https://github.com/mareurs/thunderbird-mcp/pull/1), [#2](https://github.com/mareurs/thunderbird-mcp/pull/2), [#3](https://github.com/mareurs/thunderbird-mcp/pull/3). Open at the snapshot date.
- **Conductor, Orca, and Smithers:** public tooling reports and discussions, listed in the activity index.

## Reading this catalog

Public sources were checked on **2 October 2026**. Dates refer to public commits, PRs, reports, or announcements, rather than employment contracts.

Merged, open, and closed-without-merge work have distinct labels in the activity index. Credits identify work incorporated by other authors.

Forks and copied commits do not establish authorship of an entire project. Contributions can include collaboration and AI-assisted commits, as recorded upstream.

Historical benchmark numbers remain tied to their source, input, and operation. This catalog does not re-run those benchmarks or audit current implementations.

The index covers public activity returned by GitHub search for this account. Private, deleted, unindexed, and other-account work falls outside that search.
