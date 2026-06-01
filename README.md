# John Hawver
**CS @ University of Michigan**
[LinkedIn](https://www.linkedin.com/in/john-hawver/) | [Email](mailto:jnhawver@umich.edu)

---

### Technical Profile

Computer Science student at Michigan focused on systems programming and backend infrastructure.

- **Interests:** Kubernetes internals, distributed systems, real-time graph pipelines
- **Recent project:** [GraphSched](https://github.com/johnhawver/graphsched) — a custom Kubernetes scheduler that infers which pods communicate from runtime cluster signals and co-locates them, with no changes to the workloads themselves

---

### Technical Stack

- **Languages:** C++, Python, Java, TypeScript, SQL
- **Infra/Tools:** Kubernetes, Docker, Prometheus, Grafana, Git, Linux, AWS, GDB/Valgrind
- **Frameworks:** Node.js, FastAPI, React

---

### Engineering Projects

#### GraphSched — Topology-Aware Kubernetes Scheduler

A custom Kubernetes scheduler that builds a live dependency graph of pods from runtime signals (Service selectors and environment-variable references) and scores nodes to co-locate communicating pods. It needs no affinity annotations on existing workloads.

- **How it works:** Three concurrent Kubernetes watch streams (pods, Services, PVCs) maintain a thread-safe `networkx` dependency graph. For each pending pod, the scheduler scores every node as `0.7 × co-location fraction + 0.3 × resource balance` and binds pods in dependency order so a pod's dependencies are already placed when it's scored.
- **Engineering:** Concurrent watch-stream pipeline, batch scheduling with retries and stale-cache fallbacks, Prometheus metrics on a `/metrics` endpoint, a Grafana dashboard, a 36-test pytest suite, and GitHub Actions CI.
- **Result:** Co-locates 100% of dependent pod pairs on chain and hub workloads, versus ~17–25% for the default scheduler, benchmarked over a 3-run matrix on a 4-worker kind cluster. Scheduling latency is a measured trade-off; the scheduler's own decision time is ~50–100ms per pod. Tagged v0.1.0.
- [Source](https://github.com/johnhawver/graphsched)

---

### Contact

- **Email:** jnhawver@umich.edu
- **LinkedIn:** [linkedin.com/in/john-hawver](https://www.linkedin.com/in/john-hawver/)

[back to top](#)
