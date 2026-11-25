# TEEObserver prototype: implementation notes

The prototype source code cannot be released.
This document lists what the prototype changes in the Arm TC23.1 reference software stack.
The design and the evaluation are described in the paper and in [`hafnium-overview.pdf`](hafnium-overview.pdf).

## 1. Build

The stack is downloaded, built and run as described in the official [TC23.1 user guide for TC3](https://totalcompute.docs.arm.com/en/tc23.1/totalcompute/tc3/user-guide.html), with the Buildroot filesystem on the TC3 FVP 11.26.16.
The build system is not changed.

```sh
cd <TC_WORKSPACE>/build-scripts
export PLATFORM=tc3 FILESYSTEM=buildroot TC_TARGET_FLAVOR=fvp
./setup.sh
./run_docker.sh ./build-all.sh build
cd .. && ./run-scripts/tc3/run_model.sh -m <model binary path> -d buildroot
```

After a change, the affected component is rebuilt with its script from the table below, for example `./run_docker.sh ./build-hafnium.sh build deploy`.
Each signing configuration of Table 6 is a separate build, selected by `HASH_SHA_X` in Hafnium.
Figure 6(b) uses one build per partition set.

## 2. Changed components

| Component | Change | Files | Script |
|---|---|---|---|
| Hafnium v2.10 | Load-time and per-request measurement, write protection, FF-A extension | `src/measurement.c` (new), `src/hash.c` (new, MIRACL Core SHA-2), `src/api.c`, `src/manifest.c`, `src/init.c`, `src/arch/aarch64/hypervisor/handler.c` | `build-hafnium.sh` |
| Trusted Services 1.0.0 | New partition TOA (S-EL1) | `deployments/toa/`, `components/service/toa/` | `build-trusted-services.sh` |
| Trusted Services 1.0.0 | New Linux application TOP | `deployments/top/`, `components/app/top/` | `build-trusted-services.sh` |
| TF-A v2.11.0 | Device trees only: TOA is added like any other Secure Partition | In `plat/arm/board/tc/fdts/`: `tc_spmc_manifest.dtsi`, `tc_spmc_common_sp_manifest.dtsi`, `tc_spmc_optee_sp_manifest.dtsi`, `tc_tb_fw_config.dts` | `build-tfa.sh` |

TEEObserver requires no change to the code of OP-TEE, ITS, Crypto, FWU or Linux.

The measurement procedures of all experiments are described in Sections 6.2 and 6.4 of the paper.
[`data/README.md`](../data/README.md) describes the raw data.
