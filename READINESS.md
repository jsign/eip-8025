# Readiness


## zkevm-standards

Status tracks the standard itself; implementation is tracked in the guest program and zkVM tables below.

| Standard                                                                         | Status                                                                                                    |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [Host randomness](https://github.com/eth-act/zkevm-standards/pull/42)            | 🟡 Proposed                                                                                                |
| [Proving cost estimation](https://github.com/eth-act/zkevm-standards/pull/36)    | 🟡 Proposed                                                                                                |
| [Logging function](https://github.com/eth-act/zkevm-standards/pull/27)           | 🟡 Proposed                                                                                                |
| [Keccak-f[1600] permutation](https://github.com/eth-act/zkevm-standards/pull/26) | 🟡 Proposed                                                                                                |
| [U256 interface](https://github.com/eth-act/zkevm-standards/pull/22)             | 🟡 Proposed                                                                                                |
| [Minimum memory resources](https://github.com/eth-act/zkevm-standards/pull/20)   | 🟡 Proposed                                                                                                |
| Open issues (excluding PRs)                                                      | [12](https://github.com/eth-act/zkevm-standards/issues?q=is%3Aissue%20is%3Aopen) as of September 18, 2026 |

## Guest programs


🟢 Supported · 🟡 Partial · 🔴 Unsupported · ❓ Unknown · 🚧 TBD (assessment criteria not yet defined)

| Requirement                                                                                                                                                                                                                                                                                         | Ethrex                    | Reth                    | Zesu                    | Nethermind               | evm-asm               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- | ----------------------- | ----------------------- | ------------------------ | --------------------- |
| [MIT + Apache 2.0 dual licensing](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/guest-handbook.md#guest-program-rubric)                                                                                                                                                            | [🟢][guest-ethrex-license] | [🟢][guest-reth-license] | [🟢][guest-zesu-license] | 🔴                        | 🔴                     |
| [EEST specification compliance and passing all tests](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/guest-handbook.md#eest-specs-and-tests)                                                                                                                                        | ❓                         | ❓                       | ❓                       | ❓                        | ❓                     |
| [Signed ELF and verification-key release assets](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/guest-handbook.md#release-elfs-in-teams-gh-repo-via-ci)                                                                                                                             | [🟢][guest-ethrex-release] | [🟢][guest-reth-ci]      | 🟡                       | 🟡                        | ❓                     |
| [ELF builds via public, fully open-source CI](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/guest-handbook.md#release-elfs-in-teams-gh-repo-via-ci)                                                                                                                                | [🟢][guest-ethrex-ci]      | [🟢][guest-reth-ci]      | [🟢][guest-zesu-ci]      | [🟢][guest-nethermind-ci] | [🟢][guest-evm-asm-ci] |
| [ELF formal verification](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/guest-handbook.md#guest-program-rubric)                                                                                                                                                                    | 🚧                         | 🚧                       | 🚧                       | 🚧                        | 🚧                     |
| [RISC-V target](https://github.com/eth-act/zkevm-standards/blob/main/standards/riscv-target/target.md)                                                                                                                                                                                              | 🟢                         | 🟢                       | 🟢                       | 🟢                        | ❓                     |
| [I/O interface](https://github.com/eth-act/zkevm-standards/blob/main/standards/io-interface/README.md)                                                                                                                                                                                              | ❓                         | ❓                       | [🟢][guest-zesu-io]      | ❓                        | ❓                     |
| [Cryptographic accelerators C interface](https://github.com/eth-act/zkevm-standards/blob/main/standards/c-interface-accelerators/README.md)                                                                                                                                                         | ❓                         | ❓                       | ❓                       | ❓                        | ❓                     |
| [Accelerated memory operations](https://github.com/eth-act/zkevm-standards/blob/main/standards/accelerated-memory-operations/README.md)                                                                                                                                                             | ❓                         | ❓                       | ❓                       | ❓                        | ❓                     |
| [Standard entry point and vendor-library linking](https://github.com/eth-act/zkevm-standards/blob/main/standards/static-library-and-linker-script/README.md), including [vendor memory layout](https://github.com/eth-act/zkevm-standards/blob/main/standards/memory-layout-restrictions/README.md) | ❓                         | ❓                       | ❓                       | ❓                        | ❓                     |
| [ELF artifact compliance](https://github.com/eth-act/zkevm-standards/blob/main/standards/elf-loading-and-validation/README.md)                                                                                                                                                                      | ❓                         | ❓                       | ❓                       | ❓                        | ❓                     |
| [Exit codes and language-level failure mapping](https://github.com/eth-act/zkevm-standards/blob/main/standards/standard-termination-semantics/README.md)                                                                                                                                            | ❓                         | ❓                       | ❓                       | ❓                        | ❓                     |

Notes below apply only to non-green statuses.

### Zesu

- **Signed ELF and verification-key release assets — 🟡:** The [reviewed release](https://github.com/Consensys-Incorporated/zesu-zkvm/releases/tag/tests-glamsterdam-devnet%40v8.1.4) includes signed ELFs for ZisK, OpenVM, and Linea, but a signed verification key only for ZisK. The [release workflow][guest-zesu-ci] documents the missing keys for the other targets.

### Nethermind

- **MIT + Apache 2.0 dual licensing — 🔴:** The [guest source](https://github.com/NethermindEth/nethermind/blob/364eaaf/src/Nethermind/Nethermind.Stateless.ZiskGuest/Program.cs) is licensed LGPL-3.0-only.
- **Signed ELF and verification-key release assets — 🟡:** The [release workflow](https://github.com/NethermindEth/nethermind/blob/364eaaf/.github/workflows/release-zisk-guest.yml) signs an archive containing the guest ELF, but does not generate or publish a verification key.

### evm-asm

- **MIT + Apache 2.0 dual licensing — 🔴:** The [repository license](https://github.com/Verified-zkEVM/evm-asm/blob/7e65e4d/LICENSE) is MIT-only.
- **RISC-V target — ❓:** Support has not been established.

[guest-ethrex-license]: https://github.com/lambdaclass/ethrex/blob/5b611f1/Cargo.toml#L47
[guest-reth-license]: https://github.com/paradigmxyz/stateless/blob/881516c/Cargo.toml#L5
[guest-zesu-license]: https://github.com/Consensys-Incorporated/zesu/blob/1f5ef17/README.md#license
[guest-ethrex-release]: https://github.com/lambdaclass/ethrex/releases/tag/v27.0.0
[guest-ethrex-ci]: https://github.com/lambdaclass/ethrex/blob/5b611f1/.github/workflows/tag_release.yaml
[guest-reth-ci]: https://github.com/paradigmxyz/stateless/blob/881516c/.github/workflows/reth-guests.yml
[guest-zesu-ci]: https://github.com/Consensys-Incorporated/zesu-zkvm/blob/e9f6dd0/.github/workflows/release.yml
[guest-nethermind-ci]: https://github.com/NethermindEth/nethermind/blob/364eaaf/.github/workflows/stateless-tests.yml
[guest-evm-asm-ci]: https://github.com/Verified-zkEVM/evm-asm/blob/7e65e4d/.github/workflows/build.yml
[guest-zesu-io]: https://github.com/Consensys-Incorporated/zesu/blob/1f5ef17/src/zkvm/extern_io.zig

## zkVMs


🟢 Supported · 🟡 Partial · 🔴 Unsupported · 🚧 TBD (assessment criteria not yet defined) · ❓ Unknown · ⏸️ Delayed

| Requirement                                                                                                                                                                       | Zisk | OpenVM | SP1 | lambda-vm |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- | ------ | --- | --------- |
| [MIT + Apache 2.0 dual licensing](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/zkvm-handbook.md#zkvm-rubric)                                                    | 🟢    | 🟢      | 🟢   | 🟢         |
| [Circuit formal verification](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/zkvm-handbook.md#formal-verification-requirements)                                   | 🚧    | 🚧      | 🚧   | 🚧         |
| [RTP* on the EF reference cluster](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/zkvm-handbook.md#real-time-proving-rtp)                                         | 🚧    | 🚧      | 🚧   | 🚧         |
| [Final proof size ≤300 KiB](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/zkvm-handbook.md#zkvm-rubric)                                                          | ❓    | ❓      | ❓   | ❓         |
| [EF Cryptography review](https://github.com/eth-act/zkevm-standards/blob/main/handbooks/zkvm-handbook.md#cryptographic-security-proofs)                                           | ⏸️    | ⏸️      | ⏸️   | ⏸️         |
| [RISC-V target](https://github.com/eth-act/zkevm-standards/blob/main/standards/riscv-target/target.md) ([tracker](https://eth-act.github.io/zkevm-test-monitor/))                 | 🟡    | 🟢      | 🔴   | 🟢         |
| [I/O interface](https://github.com/eth-act/zkevm-standards/blob/main/standards/io-interface/README.md)                                                                            | 🟡    | ❓      | 🟡   | 🟡         |
| [Cryptographic accelerators C interface](https://github.com/eth-act/zkevm-standards/blob/main/standards/c-interface-accelerators/README.md)                                       | 🟢    | ❓      | ❓   | ❓         |
| [Accelerated memory operations](https://github.com/eth-act/zkevm-standards/blob/main/standards/accelerated-memory-operations/README.md)                                           | ❓    | ❓      | ❓   | ❓         |
| [Static library and linker script](https://github.com/eth-act/zkevm-standards/blob/main/standards/static-library-and-linker-script/README.md)                                     | 🟡    | ❓      | 🟡   | ❓         |
| [Memory layout restrictions](https://github.com/eth-act/zkevm-standards/blob/main/standards/memory-layout-restrictions/README.md)                                                 | 🟢    | ❓      | 🟢   | ❓         |
| [Memory safety guard regions](https://github.com/eth-act/zkevm-standards/blob/main/standards/memory-safety-guard-regions/README.md)                                               | ❓    | ❓      | ❓   | ❓         |
| [ELF loading and validation](https://github.com/eth-act/zkevm-standards/blob/main/standards/elf-loading-and-validation/README.md)                                                 | 🟡    | 🟡      | 🟡   | 🟡         |
| [Execution termination semantics](https://github.com/eth-act/zkevm-standards/blob/main/standards/standard-termination-semantics/README.md)                                        | 🟡    | 🟡      | 🟡   | 🟡         |
| [Instruction address misaligned exception semantics](https://github.com/eth-act/zkevm-standards/blob/main/standards/instruction-address-misaligned-exception-semantics/README.md) | ❓    | ❓      | ❓   | ❓         |

Notes below apply only to non-green statuses.

### ZisK

Reviewed September 18, 2026 at commit `b08d856c` (source review only; builds and conformance tests were not run). Unknown rows reassessed against [zkevm-standards at `d1191c57`](https://github.com/eth-act/zkevm-standards/tree/d1191c57b5c19c13e4ad3520adf08fa75bb8db4d).

- **RISC-V target — 🟡:** See the [standard ISA tracker](https://eth-act.github.io/zkevm-test-monitor/zkvm.html?name=zisk&suite=act4-standard&run=latest). A detailed explanation of the existing yellow status remains to be added.
- **I/O interface — 🟡:** The C library provides `read_input` and `write_output`, but the [output implementation](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/ziskos/entrypoint/src/lib.rs#L329-L349) limits public output to 256 bytes and asserts beyond that limit. The standard specifies concatenated output across calls without that cap and requires `write_output` not to fail.
- **Static library and linker script — 🟡:** Both are provided, but the [linker script](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/ziskbuild/zisk_linker_script.ld#L140-L142) defines `_heap_bottom` / `_heap_top` instead of the required `_heap_start` / `_heap_end` symbols. The I/O limitation above also remains.
- **ELF loading and validation — 🟡:** The [loader](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/transpilers/common/src/elf_extraction.rs) accepts both `PF_X` and `PF_X | PF_R` executable segments, whereas the standard requires a zkVM to accept exactly one combination.
- **Execution termination semantics — 🟡:** The [entrypoint](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/ziskos/entrypoint/src/lib.rs#L376-L401) forwards `main`'s return code in `a0`, but the [exit syscall handler](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/transpilers/riscv/src/riscv2zisk_context.rs#L3132-L3157) checks only `a7 == 93` and routes to the successful end path without checking `a0`. This is a source-level gap in the required zero/non-zero distinction; a compliance test should cover non-zero `main` returns through proof verification.

The other reassessed rows remain unknown:

- **Final proof size ≤300 KiB — ❓:** The [quickstart documents recursive proof compression](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/book/getting_started/quickstart.md#compressed-proof-optional), but does not establish the final serialized proof size for the L1 proving configuration. A measured artifact or configuration-specific size bound is needed.
- **Accelerated memory operations — ❓:** The [runtime includes all four standard memory functions](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/ziskos/entrypoint/src/lib.rs#L657-L661). Compliance still needs evidence for symbol resolution in the final guest link and C semantics across alignments, zero lengths, overlapping `memmove`, and `memcmp` result signs.
- **Memory safety guard regions — ❓:** The [linker places the stack at the start of RAM](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/ziskbuild/zisk_linker_script.ld#L97-L106). That layout alone does not establish the required fault behavior. Compliance tests should cover reads and writes throughout the null and stack guard regions, including proof-verification outcomes.
- **Instruction address misaligned exception semantics — ❓:** The [JALR implementation clears only bit 0 and supports compressed instructions](https://github.com/0xPolygonHermez/zisk/blob/b08d856c0f72b21d94fc49151deefaf8e7419b79/transpilers/riscv/src/riscv2zisk_context.rs#L1460-L1533). This alone establishes neither compliance nor a violation: tests must account for the supported ISA's alignment rules and check fault outcomes through proof verification.

### OpenVM

Reviewed September 18, 2026 at [`538c5488` (`v2.1.0-preview`)](https://github.com/openvm-org/openvm/tree/538c5488130da56c8442d33445efe3c1fe5ea8b8), the RV64 version pinned by the [ISA monitor](https://github.com/eth-act/zkevm-test-monitor/blob/9137dbb3eb7713238c053588b2f6a6007b652833/config.json#L21-L28). This and the SP1 and lambda-vm reviews below use zkevm-standards `d1191c57`; builds and conformance tests were not run.

- **ELF loading and validation — 🟡:** The [loader](https://github.com/openvm-org/openvm/blob/538c5488130da56c8442d33445efe3c1fe5ea8b8/crates/toolchain/transpiler/src/elf.rs) validates ELF64/RISC-V headers and loads `PT_LOAD` segments, but tests only the executable flag when classifying permissions. It does not reject writable executable segments or enforce exactly one of `PF_X` and `PF_X | PF_R`.
- **Execution termination semantics — 🟡:** The [runtime](https://github.com/openvm-org/openvm/blob/538c5488130da56c8442d33445efe3c1fe5ea8b8/crates/toolchain/openvm/src/lib.rs#L101-L115) calls `main` as a function returning no value, then [exits with code zero](https://github.com/openvm-org/openvm/blob/538c5488130da56c8442d33445efe3c1fe5ea8b8/crates/toolchain/openvm/src/process.rs). This does not preserve non-zero C `main` returns.

The other reviewed rows remain unknown:

- **Final proof size — ❓:** The [2.0 Beta benchmarks](https://blog.openvm.dev/2.0-beta) report Ethereum STARK proofs under 300 kB at 100 bits of provable security. They do not establish the bound for the reviewed RV64 version and the handbook's 128-bit configuration.
- **I/O, cryptographic C interface, static library/linker script, and memory layout — ❓:** The reviewed tree provides [Rust I/O](https://github.com/openvm-org/openvm/blob/538c5488130da56c8442d33445efe3c1fe5ea8b8/crates/toolchain/openvm/src/io/mod.rs) and [build-time linker flags](https://github.com/openvm-org/openvm/blob/538c5488130da56c8442d33445efe3c1fe5ea8b8/crates/toolchain/build/src/lib.rs#L320-L340). These do not establish delivery of the standard C interfaces and vendor library/linker-script package.
- **Accelerated memory operations, guard regions, and instruction-address faults — ❓:** Full linking/semantic compliance and the required fault behavior through proof verification have not been established.

### SP1

Reviewed September 18, 2026 at [`9ce13607`](https://github.com/succinctlabs/sp1/tree/9ce13607e9f464b9d5ccd8b4a6478de0e8f8bf1b).

- **RISC-V target — 🔴:** See the [standard ISA tracker](https://eth-act.github.io/zkevm-test-monitor/zkvm.html?name=sp1&suite=act4-standard&run=latest). A detailed explanation of the existing red status remains to be added.
- **I/O interface — 🟡:** The [C wrappers](https://github.com/succinctlabs/sp1/blob/9ce13607e9f464b9d5ccd8b4a6478de0e8f8bf1b/zkevm/libzkevm/src/io.rs) cache the first input chunk and concatenate output calls. However, input is consumed on the first `read_input` call, rather than during initialization before `main` as the standard requires. The documented host contract also requires all input in one chunk.
- **Static library and linker script — 🟡:** The [SDK supplies both](https://github.com/succinctlabs/sp1/blob/9ce13607e9f464b9d5ccd8b4a6478de0e8f8bf1b/zkevm/README.md), but the initialization and `main` return-value gaps described here prevent full compliance.
- **ELF loading and validation — 🟡:** The [loader explicitly accepts both ELF32 and ELF64](https://github.com/succinctlabs/sp1/blob/9ce13607e9f464b9d5ccd8b4a6478de0e8f8bf1b/crates/core/executor/src/disassembler/elf.rs#L104-L112); the standard requires rejecting a class other than ELF64.
- **Execution termination semantics — 🟡:** The [runtime forwards `(exit_code & 0xff) as u8`](https://github.com/succinctlabs/sp1/blob/9ce13607e9f464b9d5ccd8b4a6478de0e8f8bf1b/crates/zkvm/entrypoint/src/lib.rs#L237-L246). A non-zero C return such as `256` becomes zero, violating the required zero/non-zero distinction.

The other reviewed rows remain unknown:

- **Cryptographic accelerators C interface — ❓:** The [SDK implements all 19 functions](https://github.com/succinctlabs/sp1/blob/9ce13607e9f464b9d5ccd8b4a6478de0e8f8bf1b/zkevm/libzkevm/src/precompile/mod.rs), but its [encoding and validation notes](https://github.com/succinctlabs/sp1/blob/9ce13607e9f464b9d5ccd8b4a6478de0e8f8bf1b/zkevm/docs/upstream-issue-encoding-spec.md) identify unresolved interoperability questions. Matching symbols alone does not settle these.
- **Final proof size, accelerated memory operations, guard regions, and instruction-address faults — ❓:** No configuration-specific final L1 proof-size bound or complete evidence for the standard's linking, memory semantics, and proof-verification fault requirements was established.

### lambda-vm

Reviewed September 18, 2026 at [`c2ac5d54`](https://github.com/yetanotherco/lambda_vm/tree/c2ac5d546fba357564acdb222bd5d83f392d7fb1).

- **I/O interface — 🟡:** The [standard C functions](https://github.com/yetanotherco/lambda_vm/blob/c2ac5d546fba357564acdb222bd5d83f392d7fb1/syscalls/src/ef_io.rs) provide idempotent input and concatenated output, but the [executor caps total output at 1 MiB](https://github.com/yetanotherco/lambda_vm/blob/c2ac5d546fba357564acdb222bd5d83f392d7fb1/executor/src/vm/memory.rs#L199-L219) and errors beyond it. The standard requires `write_output` not to fail.
- **ELF loading and validation — 🟡:** The [loader](https://github.com/yetanotherco/lambda_vm/blob/c2ac5d546fba357564acdb222bd5d83f392d7fb1/executor/src/elf.rs#L271-L372) checks headers and loads segments, but classifies executable segments using only `PF_X`, without rejecting writable executable segments or enforcing one executable permission combination.
- **Execution termination semantics — 🟡:** The [entrypoint discards `main`'s return value](https://github.com/yetanotherco/lambda_vm/blob/c2ac5d546fba357564acdb222bd5d83f392d7fb1/syscalls/src/entrypoint.rs), then calls [`sys_halt`, which sets the exit code to zero](https://github.com/yetanotherco/lambda_vm/blob/c2ac5d546fba357564acdb222bd5d83f392d7fb1/syscalls/src/syscalls.rs#L139-L153).

The other reviewed rows remain unknown:

- **Final proof size — ❓:** The [continuation design](https://github.com/yetanotherco/lambda_vm/blob/c2ac5d546fba357564acdb222bd5d83f392d7fb1/docs/continuations_design.md#L599-L609) distinguishes continuation bundles from succinct compression; it does not establish a final L1 proof at or below 300 KiB.
- **Cryptographic C interface, static library/linker script, memory layout, and accelerated memory operations — ❓:** The [guest SDK](https://github.com/yetanotherco/lambda_vm/tree/c2ac5d546fba357564acdb222bd5d83f392d7fb1/syscalls) does not establish a complete standard C accelerator interface, vendor library/linker-script package, or memory-function linking and semantics contract.
- **Guard regions and instruction-address faults — ❓:** The [executor detects misaligned instruction addresses](https://github.com/yetanotherco/lambda_vm/blob/c2ac5d546fba357564acdb222bd5d83f392d7fb1/executor/src/vm/execution.rs#L107-L117), but this alone does not establish proof-verification behavior. Complete guard-region and fault conformance evidence remains missing.

## ELs

✅ Done · 🟡 Partial · ⏳ Pending · ❓ Unknown

| Requirement                                                                                                    | Ethrex                    | Reth | Besu | Nethermind                    | Nimbus                    | Geth                      | Erigon |
| -------------------------------------------------------------------------------------------------------------- | ------------------------- | ---- | ---- | ----------------------------- | ------------------------- | ------------------------- | ------ |
| Integrate into [EEST execution witness dashboard](https://github.com/eth-act/eest-execution-witness-dashboard) | [✅][el-dashboard-results] | ❓    | ❓    | [✅][el-dashboard-results]     | [✅][el-dashboard-results] | [✅][el-dashboard-results] | ❓      |
| Implement `engine_newPayloadWithWitness{V4, V5}`                                                               | 🟡                         | ❓    | ❓    | [✅][el-nethermind-payload-v4] | [✅][el-nimbus-payload]    | [✅][el-geth-payload]      | ❓      |
| Implement [`debug_executionWitness` RPC](https://github.com/ethereum/execution-apis/pull/847)                  | 🟡                         | 🟡    | ❓    | ❓                             | 🟡                         | 🟡                         | 🟡      |
| Implement [`POST /engine/v1/payloads/witness`](https://github.com/ethereum/execution-apis/pull/885))           | ⏳                         | ⏳    | ⏳    | ⏳                             | ⏳                         | ⏳                         | ⏳      |

Notes below apply only to non-green statuses.

### Ethrex

- **`engine_newPayloadWithWitness{V4, V5}` — 🟡:** Waiting for [PR #7286](https://github.com/lambdaclass/ethrex/pull/7286) to be merged.
- **`debug_executionWitness` RPC — 🟡:** The [method][el-ethrex-debug] accepts block numbers/tags, with block hashes handled by a separate method. The proposal requires accepting hashes through the same method.

### Reth

- **EEST execution witness dashboard integration — ❓:** Waiting for [PR #27083](https://github.com/paradigmxyz/reth/pull/27083) to be merged so Reth can be added to the EL dashboard.
- **`debug_executionWitness` RPC — 🟡:** The [witness format defaults to legacy][el-reth-witness-mode]; the proposal requires canonical output when no format parameter is supplied.

### Besu

- **`debug_executionWitness` RPC — ❓:** An [implementation exists][el-besu-debug], but full conformance with the proposed canonical witness requirements was not established.

### Nethermind

- **`debug_executionWitness` RPC — ❓:** An [implementation exists][el-nethermind-debug], but full conformance with the proposed canonical witness requirements was not established.

### Nimbus

- **`debug_executionWitness` RPC — 🟡:** The [method][el-nimbus-debug] accepts block numbers/tags, with block hashes handled by a separate method. The proposal requires accepting hashes through the same method.

### Geth

- **`debug_executionWitness` RPC — 🟡:** The [RPC returns `ExtWitness`][el-geth-debug], whose [`headers` field][el-geth-witness-encoding] contains JSON header objects rather than the required RLP bytes.

### Erigon

- **`debug_executionWitness` RPC — 🟡:** The [witness format defaults to legacy][el-erigon-debug]; the proposal requires canonical output when no format parameter is supplied.

[el-dashboard-results]: https://eth-act.github.io/eest-execution-witness-dashboard/listing.jsonl
[el-ethrex-payload]: https://github.com/lambdaclass/ethrex/blob/9ac97c8e89c4318813f40c828e7ad52d0322ff74/crates/networking/rpc/rpc.rs#L1481-L1493
[el-nethermind-payload-v4]: https://github.com/NethermindEth/nethermind/blob/93ca2644a45d1385d55e06d93a633408b4432c6f/src/Nethermind/Nethermind.Merge.Plugin/EngineRpcModule.Prague.cs#L25-L31
[el-nethermind-payload-v5]: https://github.com/NethermindEth/nethermind/blob/93ca2644a45d1385d55e06d93a633408b4432c6f/src/Nethermind/Nethermind.Merge.Plugin/EngineRpcModule.Amsterdam.cs#L32-L38
[el-nimbus-payload]: https://github.com/status-im/nimbus-eth1/blob/08aec3a4c9709e8402b5630cbf64e5ed09b5b56d/execution_chain/rpc/engine_api.nim#L110-L140
[el-geth-payload]: https://github.com/ethereum/go-ethereum/blob/aa1f2fcf512988eb8890d9352e601b898d6fdb2c/eth/catalyst/witness.go#L139-L187
[el-ethrex-debug]: https://github.com/lambdaclass/ethrex/blob/5b611f12483b31ef6bf39370d6c59a29e1e7f804/crates/networking/rpc/debug/execution_witness.rs#L7-L34
[el-reth-witness-mode]: https://github.com/paradigmxyz/reth/blob/0032bec310b1531dc24d6b5bfeffa690eb35531a/crates/trie/common/src/execution_witness.rs#L1-L27
[el-nimbus-debug]: https://github.com/status-im/nimbus-eth1/blob/5dfdf626b88baefd4754580ca5a5e058efa3172b/execution_chain/rpc/debug.nim#L263-L276
[el-geth-debug]: https://github.com/ethereum/go-ethereum/blob/a5b90d2a28e8b68c2d6c335e17af4c64e23f7323/eth/api_debug.go#L510-L532
[el-geth-witness-encoding]: https://github.com/ethereum/go-ethereum/blob/a5b90d2a28e8b68c2d6c335e17af4c64e23f7323/core/stateless/encoding.go#L97-L102
[el-erigon-debug]: https://github.com/erigontech/erigon/blob/ae4e8e4e12252a1da1e6e025fe172fc897dd0851/rpc/jsonrpc/debug_execution_witness.go#L551-L575
[el-besu-debug]: https://github.com/besu-eth/besu/blob/7e05c2342404d27bd06a992e336c5e0c86a5d8d1/ethereum/api/src/main/java/org/hyperledger/besu/ethereum/api/jsonrpc/internal/methods/DebugExecutionWitness.java
[el-nethermind-debug]: https://github.com/NethermindEth/nethermind/blob/364eaaf0315525b1217d062fdd7ef8d615ea3e5a/src/Nethermind/Nethermind.JsonRpc/Modules/DebugModule/DebugRpcModule.cs#L907-L927

## CLs

✅ Done · 🟡 Partial · ⏳ Pending · ❓ Unknown

| Requirement                                                                                 | Lighthouse                                           | Prysm                                           | Teku                                           | Nimbus                                           | Lodestar                                           | Grandine                                           |
| ------------------------------------------------------------------------------------------- | ---------------------------------------------------- | ----------------------------------------------- | ---------------------------------------------- | ------------------------------------------------ | -------------------------------------------------- | -------------------------------------------------- |
| EIP-8025 implementation on top of Glamsterdam                                                 | [✅][cl-lighthouse-gloas][^cl-lighthouse-gloas]         | [🟡][cl-prysm-gloas][^cl-prysm-gloas]             | [❓][cl-teku-proofs][^cl-teku-gloas]             | [❓][cl-nimbus-proofs][^cl-nimbus-gloas]           | [❓][cl-lodestar-proofs][^cl-lodestar-gloas]          | [🟡][cl-grandine-proofs][^cl-grandine-gloas]          |
| Integrated into `zkboost`                                                                    | 🟡                                                    | 🟡                                               | ❓                                              | ❓                                                | ❓                                                  | ❓                                                  |
| Integrated into [Kurtosis](https://github.com/ethpandaops/ethereum-package/tree/main/src/zkboost) | [✅][cl-lighthouse-kurtosis]                          | [✅][cl-prysm-kurtosis]                          | ❓                                              | ❓                                                | ❓                                                  | ❓                                                  |

Reviewed September 18, 2026. The Glamsterdam row assesses EIP-8025 support for Gloas payloads: ✅ means implemented in the linked branch, 🟡 means partially implemented, and ❓ means a Gloas implementation was not established. It does not require an upstream merge. Kurtosis ✅ means an EIP-8025 launch configuration connects the client to zkboost. This was a source review; builds, integration tests, and devnets were not run. The integration rows still refer to the older `optional-proofs` client images; they do not establish Glamsterdam interoperability. Implementation footnotes track relevant open PRs in the client repositories and the Lighthouse and Grandine forks.

Integration notes below apply only to non-green statuses.

### Lighthouse

- **Integrated into `zkboost` — 🟡:** The `optional-proofs` branch includes a proof-node client and [zkboost integration tests](https://github.com/eth-act/lighthouse/blob/e81a3165dedfee44b5275cd561cf03281ad1ab1d/testing/proof_engine_zkboost/src/lib.rs). However, the [reviewed client](https://github.com/eth-act/lighthouse/blob/e81a3165dedfee44b5275cd561cf03281ad1ab1d/beacon_node/execution_layer/src/eip8025/proof_node_client.rs#L181-L205) sends verification metadata in query parameters and raw proof bytes in the body. The [zkboost v0.9.0 handler][cl-zkboost-verification], used by the GPU examples, expects an SSZ `ProofVerificationBody` containing the metadata and proof. The request formats need to be aligned and interoperability retested.

### Prysm

- **Integrated into `zkboost` — 🟡:** The `optional-proofs` branch has a [zkboost verification client](https://github.com/OffchainLabs/prysm/blob/c4a6a9b76a08ccfcf77d73447d8150e25cc00114/beacon-chain/verification/verifier_client.go#L18-L41), and the [Kurtosis GPU example][cl-prysm-kurtosis] configures it as a verifier without an EL. It sends the same query-parameter metadata and raw proof body as Lighthouse, so it also needs to adopt the [zkboost v0.9.0 request format][cl-zkboost-verification] and be retested.

### Teku, Nimbus, Lodestar, and Grandine

- **Both integrations — ❓:** A connection to zkboost was not established in the reviewed sources. Lodestar has an [EIP-8025 Kurtosis setup with a dummy prover](https://github.com/ChainSafe/lodestar/blob/cd716e738484822b8735c828f4b43a1925705d52/scripts/eip8025-devnet/README.md), but this does not establish zkboost integration. General Kurtosis client support alone does not establish these integrations.

[cl-lighthouse-gloas]: https://github.com/eth-act/lighthouse/tree/optional-proofs-gloas
[cl-prysm-gloas]: https://github.com/OffchainLabs/prysm/tree/eip8025-optional-proofs
[cl-teku-proofs]: https://github.com/Consensys/teku/tree/optional-proofs
[cl-nimbus-proofs]: https://github.com/status-im/nimbus-eth2/tree/eip8025-initial
[cl-lodestar-proofs]: https://github.com/ChainSafe/lodestar/tree/optional-proofs
[cl-grandine-proofs]: https://github.com/eip8025-grandine/grandine/tree/feature/eip8025

[cl-lighthouse-kurtosis]: https://github.com/ethpandaops/ethereum-package/blob/c0db06b29b8266e65c9b80b64895e07058d28d0b/.github/tests/zkboost.yaml
[cl-prysm-kurtosis]: https://github.com/ethpandaops/ethereum-package/blob/c0db06b29b8266e65c9b80b64895e07058d28d0b/.github/tests/examples/8gpu_zkvm.yaml#L36-L43
[cl-zkboost-verification]: https://github.com/eth-act/zkboost/blob/v0.9.0/crates/server/src/http/v1/post_execution_proof_verifications.rs#L17-L27

[^cl-lighthouse-gloas]: **Lighthouse — ✅:** `optional-proofs-gloas` at `e676ea54` reconstructs proof inputs from Gloas bids and payload envelopes in its [gossip verification path](https://github.com/eth-act/lighthouse/blob/e676ea5459fc667d5fa4fec2ab4b96fdb79ff844/beacon_node/beacon_chain/src/execution_proof_verification/gossip_verified_execution_proof.rs), with an [in-process proof engine](https://github.com/eth-act/lighthouse/blob/e676ea5459fc667d5fa4fec2ab4b96fdb79ff844/beacon_node/proof_engine/src/lib.rs). Upstream progress: open [#10063](https://github.com/sigp/lighthouse/pull/10063) refactors proof envelopes and verification; draft [#10080](https://github.com/sigp/lighthouse/pull/10080) adds ERE verification and depends on #10063. The latter is also tracked in the fork as draft [eth-act/lighthouse#49](https://github.com/eth-act/lighthouse/pull/49).

[^cl-prysm-gloas]: **Prysm — 🟡:** Both [`optional-proofs-gloas`](https://github.com/OffchainLabs/prysm/tree/optional-proofs-gloas) and the newer `eip8025-optional-proofs` branch contain Gloas work. The latter, reviewed at `8d9d669e`, [derives proof inputs from revealed payloads](https://github.com/OffchainLabs/prysm/blob/8d9d669e711fce81fd7b9f9c9c79b27dc085b667/beacon-chain/blockchain/execution_proof.go). Open draft [#17490](https://github.com/OffchainLabs/prysm/pull/17490) explicitly remains WIP; its Gloas Kurtosis example uses mock proofs and requires the `nalepae/zkboost` fork.

[^cl-teku-gloas]: **Teku — ❓:** `optional-proofs` at `3828963a` contains a [prototype generator](https://github.com/Consensys/teku/blob/3828963a9a334a8960200700d5e9832c094f2592/ethereum/statetransition/src/main/java/tech/pegasys/teku/statetransition/executionproofs/ExecutionProofGeneratorImpl.java) that uses Electra schemas, reads the payload from the beacon block body, and generates dummy proofs. This does not establish support for Gloas payload envelopes. No relevant open EIP-8025 PR was found in `Consensys/teku`.

[^cl-nimbus-gloas]: **Nimbus — ❓:** Open draft [#8004](https://github.com/status-im/nimbus-eth2/pull/8004), from `eip8025-initial` into `optional-proofs`, tracks the initial implementation. At `9afbef91`, its [proof types](https://github.com/status-im/nimbus-eth2/blob/9afbef91191a42f4cf563d71bfa28c6acfb81924/beacon_chain/spec/datatypes/eip8025.nim) use Deneb payloads and Electra requests, and its [proof engine](https://github.com/status-im/nimbus-eth2/blob/9afbef91191a42f4cf563d71bfa28c6acfb81924/beacon_chain/spec/proof_engine.nim) has placeholder verification. Gloas support was not established; the PR still lists proof storage, validation, and prover plumbing as TODOs.

[^cl-lodestar-gloas]: **Lodestar — ❓:** `optional-proofs` at `cd716e73` contains an EIP-8025 prototype, but its [proof-input construction](https://github.com/ChainSafe/lodestar/blob/cd716e738484822b8735c828f4b43a1925705d52/packages/beacon-node/src/chain/eip8025/newPayloadRequestHeader.ts) still selects the Deneb payload schema for every fork from Deneb onward. Gloas proof support was not established. No relevant open EIP-8025 PR was found in `ChainSafe/lodestar`.

[^cl-grandine-gloas]: **Grandine — 🟡:** `feature/eip8025` at `2be90a1e` includes proof containers and [Gloas-specific payload binding](https://github.com/eip8025-grandine/grandine/blob/2be90a1e41dedf9afbeb8555886380bdde1332f1/types/src/eip8025/container_impls.rs). Open fork PRs track [BLS signing (#7)](https://github.com/eip8025-grandine/grandine/pull/7), the [proof-engine skeleton (#9)](https://github.com/eip8025-grandine/grandine/pull/9), [proof state (#10)](https://github.com/eip8025-grandine/grandine/pull/10), [task plumbing (#11)](https://github.com/eip8025-grandine/grandine/pull/11), and [verifier/prover separation (#15)](https://github.com/eip8025-grandine/grandine/pull/15); draft [#3](https://github.com/eip8025-grandine/grandine/pull/3) adds progressive-list Merkle tests. #15 supersedes the alternative designs in #13/#14. No relevant open EIP-8025 PR was found in upstream `grandinetech/grandine`.

## Specs

### Execution layer (EL)

| Item | Status | Next step / link |
| ---- | ------ | ---------------- |

| Fill benchmark test fixtures                      | ✅      | [Execution-specs releases](https://github.com/ethereum/execution-specs/releases) with `test-zkevm` in the name |
| Stateless EEST benchmark releases   | ✅      | [Execution-specs releases](https://github.com/ethereum/execution-specs/releases) with `tests-zkevm-benchmark` in the name                     |
| Stateful EEST beechmark releases   | 🔴      | Integrate into existing stateful filling infrastructure from STEEL                     |
| REST+SSZ execution API specs   | 🟡      | [execution-apis#885](https://github.com/ethereum/execution-apis/pull/885)                |
| `debug_executionWitness` spec  | 🟡      | Merge pending: [execution-apis#847](https://github.com/ethereum/execution-apis/pull/847) |
| Execution specs                | ✅      | [Implementation](https://github.com/ethereum/execution-specs/tree/projects/zkevm)        |
| High-coverage tests            | ✅      | [Test releases](https://github.com/ethereum/execution-specs/releases)                    |
| Merge execution specs upstream | 🟡      | Await acceptance                                                                         |

### Consensus layer (CL)

| Item                                      | Status     | Spec / pending PR                                                                                                                                                   |
| ----------------------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Main consensus specs                      | ✅ Merged   | [`consensus-specs/specs/_features/eip8025`](https://github.com/ethereum/consensus-specs/tree/master/specs/_features/eip8025)                                        |
| Refine `ProofData` and gossip validation  | 🟡 Proposed | [consensus-specs#5593](https://github.com/ethereum/consensus-specs/pull/5593)                                                                                       |
| Validation-only Proof Engine              | 🟡 Draft    | [consensus-specs#5639](https://github.com/ethereum/consensus-specs/pull/5639); depends on #5593; removes the prover guide and proof-generation/retrieval interfaces |
| Recursive execution proof guest           | 🟡 Draft    | [consensus-specs#5534](https://github.com/ethereum/consensus-specs/pull/5534)                                                                                       |
| Beacon API proof retrieval and submission | 🟡 Proposed | [beacon-APIs#569](https://github.com/ethereum/beacon-APIs/pull/569)                                                                                                 |

## Benchmarks & repricings

✅ Done · ⏳ Pending

| Item                                                 | Status | Next step / link                                                                                                                              |
| ---------------------------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Mainnet block benchmarks by zkVM and guest program   | ⏳      | Build a comparison table; assess [zkevm-prof](https://han0110.github.io/zkevm-prof/) as a data source                                         |
| EEST worst-case benchmarks by zkVM and guest program | ⏳      | Build a comparison table for the latest `test-zkevm` worst cases; assess [zkevm-prof](https://han0110.github.io/zkevm-prof/) as a data source |
| Gas repricing analysis for worst cases               | ⏳      | Link worst-case benchmark results to repricing analysis using `evm-gasfit`                                                                    |
