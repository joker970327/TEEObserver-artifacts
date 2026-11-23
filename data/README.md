# Raw measurement data

This folder contains the raw measurement records of the paper "TEEObserver: A Remote Attestation Scheme for ARM Secure World Based on Secure Virtualization".
There is one CSV file per data figure and one for Table 8.
Only per-request records are included. The aggregate values plotted or printed in the paper are not repeated.
The nine initialization values of Figure 6(b) and the TEEObserver row of Table 9 are aggregates, so they have no separate file.

| CSV | Figure / table | Contents | Rows |
|---|---|---|---|
| `fig06.csv` | Figure 6(a) | target hash time per request (4 targets × 3 configurations × 31 requests) | 372 |
| `fig07.csv` | Figure 7 | individual requests: latency, its three phases and the queueing time | 16,200 |
| `fig08.csv` | Figure 8 | Massif heap and stack snapshots, Raspberry Pi 3B | 187 |
| `table08.csv` | Table 8 | individual requests: measurement, AK certification, report signing | 558 |

Times are in ms, memory in KiB and sizes in bytes. The unit of each column is given in its name.
In `fig06.csv` and `table08.csv`, `run 1` is the discarded warm-up request (`warmup=1`), and the means use runs 2–31.

The measurement setup is described in Section 6 of the paper and in [`docs/`](../docs/).
