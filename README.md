# TEEObserver-artifacts

Implementation documentation and raw benchmark data for the paper:

> Minzhi Ji, Haiyuan Gao, Heng Cai, Yunyun Xie, Peiwen Chen, Juncheng Tong, Bo Zhao. "TEEObserver: A Remote Attestation Scheme for ARM Secure World Based on Secure Virtualization."

The source code of the TEEObserver prototype cannot be released due to project-related restrictions.
This repository documents what the prototype changes and how the reported results were measured.

## Contents

| Path | Contents |
|---|---|
| `docs/hafnium-overview.pdf` | One-page overview of the changes to Hafnium: modified files, measured and write-protected ranges, boot-time and per-request processing, and build configuration |
| `docs/implementation.md` | Build steps, and the components and files that the prototype changes |
| `data/` | Raw per-request measurement records behind Figures 6–8 and Table 8. See [`data/README.md`](data/README.md). |

## Platform

Arm FVP_TC3 11.26.16 with the TC23.1 software stack: TF-A 2.11.0, Hafnium 2.10, OP-TEE 4.2.0, Trusted Services 1.0.0 (mbedTLS 3.6.0) and Linux 6.1.75.
Latency results come from the FVP, which is not timing-accurate. Memory profiles come from a Raspberry Pi 3B.

## License

The documentation and data in this repository are licensed under [CC BY 4.0](LICENSE).

## Citation

If you use these materials, please cite the paper above.
