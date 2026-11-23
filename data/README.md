# Supplementary Material S2 — Raw measurement data

One CSV per data figure, plus Table 8. Only the per-request records are included;
the aggregate values plotted or printed are not repeated. `fig06.csv` holds the
per-request data of Figure 6(a); the nine initialization values of Figure 6(b)
and the TEEObserver row of Table 9 are aggregates and have no separate file.

| CSV | Figure / table | Contents | Rows |
|---|---|---|---|
| `fig06.csv` | Figure 6(a) | target hash time per request (4 targets × 3 configurations × 31 requests) | 372 |
| `fig07.csv` | Figure 7 | individual requests: latency, its three phases and the queueing time | 16,200 |
| `fig08.csv` | Figure 8 | Massif heap and stack snapshots, Raspberry Pi 3B | 187 |
| `table08.csv` | Table 8 | individual requests: measurement, AK certification, report signing | 558 |

Times are in ms, memory in KiB, sizes in bytes. `run 1` is the discarded
warm-up request (`warmup=1`); means use runs 2–31. Units are in the column
names; the measurement setup is described in Section 6 of the manuscript and
in S1.
