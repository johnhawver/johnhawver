# John Hawver
**CS @ University of Michigan**
[LinkedIn](https://www.linkedin.com/in/john-hawver/) | [Email](mailto:jnhawver@umich.edu)

---

### Technical Profile

I am a Computer Science student at Michigan focused on systems programming and scalable backend architecture.

- **Current focus:** Kubernetes internals / distributed systems / real-time graph construction pipelines
- **Current project:** [GraphSched](https://github.com/johnhawver/graphsched) — a custom Kubernetes scheduler plugin that infers live pod communication topology from runtime cluster signals and uses it to co-locate dependent pods, with zero application-side changes required

---

### Technical Stack

- **Languages:** C++, Python, Java, TypeScript, SQL
- **Tools/Env:** Git, Linux (Ubuntu/Fedora), Docker, AWS, GDB/Valgrind
- **Frameworks:** Node.js, FastAPI, React

---

### Engineering Projects

#### GraphSched — Topology-Aware Kubernetes Scheduler *(In Development)*

**Technical Overview:** A custom Kubernetes scheduler plugin that constructs a live directed graph of pod dependencies from runtime cluster signals (Service selectors, PVC mounts, env var references) and uses topology-aware heuristic scoring to co-locate communicating pods — improving placement quality with no changes to existing workloads.

- **Deep technical work in:** Kubernetes scheduler internals (Filter / Score / Bind extension points), real-time concurrent watch stream pipelines, thread-safe graph maintenance with networkx, and gRPC service design.
- **Implementation:** Three concurrent K8s API watch streams (pods, services, PVCs) maintain a live `networkx.DiGraph`; a custom scorer computes `0.7 × co-location fraction + 0.3 × resource balance` per candidate node; Prometheus + Grafana expose scheduling latency and live co-location rate; full stack ships as a Helm chart with GitHub Actions CI.
- **Result:** In active development 
- [Source](https://github.com/johnhawver/graphsched)

---

### Contact

- **Email:** jnhawver@umich.edu
- **LinkedIn:** [linkedin.com/in/john-hawver](https://www.linkedin.com/in/john-hawver/)

[back to top](#)
