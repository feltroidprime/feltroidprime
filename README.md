# feltroid prime

**Cryptographic libraries, proof verification, and open-source maintenance.**

I build cryptographic software in Rust, Cairo, Python, and TypeScript. I am the lead developer and maintainer of [Garaga](https://github.com/keep-starknet-strange/garaga).

My work spans arithmetic, witness generation, verifier integration, code review, CI, documentation, and releases. Much of this work lives in upstream repositories.

Garaga is referenced in public dependency manifests from [Blockstream Research](https://github.com/BlockstreamResearch/pq-p2pkh/blob/main/stwo-cairo/Scarb.toml), [Cartridge](https://github.com/cartridge-gg/controller-cairo/blob/main/Scarb.toml), [Ekubo](https://github.com/EkuboProtocol/privacy-pools/blob/main/Scarb.toml), and [Union](https://github.com/unionlabs/union/blob/main/Scarb.toml).

[Website](https://felt.md) · [X](https://x.com/feltroidPrime) · [Telegram](https://t.me/feltroidprime) · [Contribution catalog](https://github.com/feltroidprime/feltroidprime/blob/main/CONTRIBUTIONS.md)

## Work in upstream repositories

| Project | My work | Selected evidence |
| --- | --- | --- |
| **[Garaga](https://github.com/keep-starknet-strange/garaga)** | Lead development and maintenance across Cairo, Rust, Python, and TypeScript. Groth16, Noir/Honk, SP1 and RISC Zero integration, elliptic curves, signatures, SDKs, and releases. | [Rust calldata API](https://github.com/keep-starknet-strange/garaga/pull/229), [ECDSA and Schnorr](https://github.com/keep-starknet-strange/garaga/pull/300), [generated-artifact CI](https://github.com/keep-starknet-strange/garaga/pull/236), [maintainer review](https://github.com/keep-starknet-strange/garaga/pull/202#pullrequestreview-2339339144) |
| **[gnark](https://github.com/Consensys-Incorporated/gnark) / [gnark-crypto](https://github.com/Consensys-Incorporated/gnark-crypto)** | Independent cryptographic review, bug reports, optimization ideas, and a vulnerability fix. | [BN254 pairing soundness report](https://github.com/Consensys-Incorporated/gnark/issues/1213), [fake-GLV fix](https://github.com/Consensys-Incorporated/gnark-crypto/pull/680), [BLS12-381 optimization credit](https://github.com/Consensys-Incorporated/gnark/pull/1173) |
| **[Lambdaworks](https://github.com/lambdaclass/lambdaworks)** | Rust contributions to transcripts, Poseidon, Merkle backends, and polynomial arithmetic. | [Keccak transcript](https://github.com/lambdaclass/lambdaworks/pull/442), [Poseidon and Merkle backends](https://github.com/lambdaclass/lambdaworks/pull/641), [polynomial extended GCD](https://github.com/lambdaclass/lambdaworks/pull/885) |
| **[Kakarot / Keth](https://github.com/kkrt-labs/kakarot)** | BN254 curve arithmetic for cryptographic precompiles, EVM jump-destination scanning, faster u256 arithmetic, and constraint fixes. [Keth adopted Garaga for BN254 pairing.](https://github.com/kkrt-labs/keth/pull/1339) | [EC arithmetic](https://github.com/kkrt-labs/kakarot-ssj/pull/855), [jump destinations](https://github.com/kkrt-labs/kakarot/pull/1034), [u256 optimization](https://github.com/kkrt-labs/kakarot/pull/1070), [soundness fix](https://github.com/kkrt-labs/kakarot/pull/1199) |
| **[Herodotus](https://github.com/HerodotusDev/offchain-evm-headers-processor)** | Cairo programs that authenticate Ethereum header chains and maintain Keccak/Poseidon Merkle mountain range accumulators. | [Header processor](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/6), [differential tests](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/10), [audit fixes](https://github.com/HerodotusDev/offchain-evm-headers-processor/pull/11) |
| **[Katana TEE](https://github.com/cartridge-gg/katana-tee) (Cartridge)** | Rust proof clients, Garaga calldata, and TEE attestation checks in a standalone Katana testing project. | [Rust calldata integration](https://github.com/cartridge-gg/katana-tee/commit/c7ac2b99ea4177f842905301c2e123abf15da3fc), [TEE measurement checks](https://github.com/cartridge-gg/katana-tee/commit/1456cfa38bef286aec13ff8a244ae425aebe74f6) |
| **[Aztec / Noir](https://github.com/AztecProtocol/aztec-packages)** | Contributions to Honk verifier integration for Starknet. | [UltraStarknet Honk flavors](https://github.com/AztecProtocol/aztec-packages/pull/11489) |
| **[Raito](https://github.com/starkware-bitcoin/raito)** | Optimized digest conversions in the Cairo Bitcoin client. | [PR 157 and operation-specific gas measurements](https://github.com/starkware-bitcoin/raito/pull/157) |

## Security and correctness

- **gnark BN254 pairing:** I identified a missing constraint on a pairing hint. The maintainers credited my report and implemented the fix. [Report](https://github.com/Consensys-Incorporated/gnark/issues/1213)
- **CVE-2025-58157:** I reported a fake-GLV denial of service and co-authored the fix in gnark-crypto. [Official advisory](https://github.com/Consensys-Incorporated/gnark/security/advisories/GHSA-9fvj-xqr2-xwg8)
- **Privacy Pools Starknet:** I audited the Cairo contracts, Groth16 integration, and Merkle trees. The report contains 27 observations, including one High and three Medium. Circuit constraints were outside scope. [Public audit](https://github.com/fatlabsxyz/privacy-pools-starknet/blob/master/audits/audit_12_12_2025_feltroidprime/privacy_pools_starknet_feltroidprime_audit_v1.1.md)

In Garaga, I maintained Python/Rust calldata parity, generated-artifact consistency, and end-to-end verification on devnet. I also managed compatibility changes, deployed contracts, contributor reviews, and developer support.

## Post-quantum cryptography and developer tools

- **[S2morrow](https://github.com/feltroidprime/s2morrow):** I built a Falcon-based Starknet account and browser wallet, with Rust/WASM signer tooling, on the StarkWare project.
- **[falcon-rs](https://github.com/feltroidprime/falcon-rs):** Rust Falcon tooling with WASM bindings. The signer does not provide side-channel protection.
- **[SP1 Starknet template](https://github.com/feltroidprime/sp1-starknet-template):** An application template for proof verification through Garaga.
- **[Cairo profiling tools](https://github.com/feltroidprime/cairo-skills)** and **[performance snippets](https://github.com/feltroidprime/cairo-perfs-snippets):** Tools and examples for compiler output and execution costs.

My public Rust contributions date to June 2023, including a [transcript correction in the Lambdaworks STARK prover](https://github.com/lambdaclass/lambdaworks_stark_platinum/pull/87).

## Writing and research

- [Extension-field multiplication and pairing arithmetic](https://hackmd.io/@feltroidprime/B1eyHHXNT).
- [Starknet's credit for the Garaga SDK and Noir integration](https://www.starknet.io/blog/noir-on-starknet/).
- [BTQ's credit for Cairo Falcon development and consultation](https://www.btq.com/news/completing-the-first-falcon-signature-verification-in-starkware-initiating-the-transition-to-a-quantum-safe-ethereum).
- [StarkWare's discussion of S2morrow and quantum readiness](https://starkware.co/blog/the-architecture-advantage-starknets-quantum-readiness-roadmap/).

The [contribution catalog](https://github.com/feltroidprime/feltroidprime/blob/main/CONTRIBUTIONS.md) covers additional projects, reviews, diagnostics, and tools. The [public activity index](https://github.com/feltroidprime/feltroidprime/blob/main/ACTIVITY.md) lists the underlying GitHub records.

For engineering roles, audits, or research collaboration, contact me through [felt.md](https://felt.md) or [Telegram](https://t.me/feltroidprime).
