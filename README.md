# John Hawver

**B.S.E. Computer Science, Mathematics minor — University of Michigan** · Class of 2029
[Email](mailto:jnhawver@umich.edu) · [LinkedIn](https://www.linkedin.com/in/john-hawver/)

I build low-latency systems and the tooling that proves they work. Most of my projects start
from a measurement problem: what is this system's actual p99, where does the time go, and how
do I keep a change from silently breaking correctness. I care about results that survive
scrutiny, so each project below documents its methodology and its caveats alongside its numbers.

Currently seeking **Summer 2027 software engineering internships** — systems, infrastructure,
and trading/fintech.

---

## Projects

### [C++ Limit Order Book & Matching Engine](https://github.com/johnhawver/lob-engine)

`C++17` · `CMake` · `Catch2` · `Google Benchmark` · `AddressSanitizer/UBSan`

A single-instrument, price–time priority matching engine with a single-threaded match path and
no order allocations in the hot loop.

- **O(1) cancel** from integer-tick prices, a fixed-capacity order pool with generation-tagged
  IDs that reject stale cancels, and intrusive per-price FIFO queues.
- **53–93 ns p50 / 83–579 ns p99** across add, cancel, match-heavy, and mixed workloads —
  from 100k per-op samples with 50k warm-up ops discarded, not aggregate averages. A pool
  counter asserts zero allocations outside the order pool on every measured window.
- Correctness locked by **400k differentially-fuzzed operations** against a slow reference book,
  structural invariants asserted after every operation, and a golden-tape regression test — all
  under sanitizers in CI.

### [GraphSched — Topology-Aware Kubernetes Scheduler](https://github.com/johnhawver/graphsched)

`Python` · `Kubernetes` · `NetworkX` · `Prometheus` · `Grafana` · `kind`

A custom Kubernetes scheduler that places pods by *who talks to whom*, not just by free CPU and
memory — with no affinity annotations added to the workloads.

- Reconstructs a live pod dependency graph from signals the cluster already has (Service
  selectors, environment-variable references) via concurrent Pod/Service/PVC watch streams, then
  scores nodes `0.7 × co-location + 0.3 × resource balance` and binds in dependency order.
- **Co-locates 100% of dependent pod pairs vs. 17–25% for the default scheduler** across a 3-run
  matrix of chain and hub workloads on a 4-worker kind cluster.
- Instrumented end to end: Prometheus metrics, a Grafana dashboard, a **36-test** pytest suite,
  and GitHub Actions CI. Per-pod scoring costs 50–100 ms — a trade-off the README measures and
  discusses rather than hides.

### [MNQ Intraday Microstructure Benchmark](https://github.com/johnhawver/microstructure-benchmark)

`Python` · `Polars` · `Numba` · `XGBoost` · `PyTorch` · `Databento`

A leakage-free benchmark for short-horizon prediction on MNQ futures, built to find out whether
the signal is real — and to report the answer either way.

- Transforms **187M MBP-1 market events** (17 sessions, 2.5 GB) into **5.96M feature rows** on
  100 ms bars: Cont–Kukanov–Stoikov OFI, Kyle's lambda, trade imbalance, microprice tilt, and
  Numba-compiled volatility and triple-barrier labels.
- Rules out look-ahead with a **22-test** suite that recomputes every feature on truncated history
  and asserts identical values, a hand-computed OFI fixture, a shuffled-label control that holds
  accuracy at chance, and walk-forward folds under a 10 s embargo.
- Profiles every pipeline stage **under 4 ms p99** against a 100 ms bar budget, and simulates
  execution with half-spread, commission, and delayed fills.
- **Reports an honest negative result:** AUC ≈ 0.51, unprofitable after costs. The value here is
  the validation harness that makes that conclusion trustworthy.

---

## Experience

### Software Engineering Intern — Mixel Studio · *May – Aug. 2026*
3D/XR publishing platform · Ann Arbor, MI

- Shipped publication analytics end to end across **7 instrumented event types**: a Next.js
  `sendBeacon` client that survives page unload, Java 17 / Spring Boot aggregation APIs, and
  Flyway-migrated Postgres tables.
- Eliminated a lost-update race on concurrent summary writes with row-level pessimistic locking
  under READ COMMITTED, backed by a JUnit suite exercising the parallel path — the bug was
  silently undercounting view metrics.
- Synced real-time scene and viewer state across **three clients in three languages** — a React
  Three Fiber editor, a Spring Boot server, and a Unity C# XR app whose STOMP WebSocket client
  and broadcast service I wrote from scratch.

### Planning & Engineering Services Intern — Charter Township of Canton · *May – Aug. 2026*
Canton, MI

- Replaced manual spreadsheet workflows across five planning functions with **5 internal Python
  tools**, encoding **76 species rules** and 27 conditional cases as pydantic-validated versioned
  YAML so staff could change policy without a code change.
- Reconciled a **48,529-record** parcel export against the municipal street registry into a
  **1,537-street** index in pandas, deriving quarter-section geography from parcel IDs and routing
  ambiguous rows to human review rather than guessing.

---

## Technical Skills

**Languages** — C++, Python, Java, TypeScript, C#, SQL

**Systems & Infra** — Linux, Kubernetes, Docker, PostgreSQL, Prometheus, Grafana, GitHub Actions

**Backend & Web** — Spring Boot (JPA, Flyway), Next.js/React, WebSockets/STOMP, REST APIs

**Data** — Polars, PyArrow, pandas, NumPy, Numba, XGBoost, PyTorch, NetworkX, Databento

**Testing & Tooling** — pytest, JUnit, Catch2, Google Benchmark, CMake, AddressSanitizer/UBSan, GDB/Valgrind, Git
