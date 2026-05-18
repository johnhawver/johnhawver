# John Hawver
**CS @ University of Michigan**
[LinkedIn](https://www.linkedin.com/in/john-hawver/) | [Email](mailto:jnhawver@umich.edu)

---

### Technical Profile

I am a Computer Engineering student at Michigan focused on systems programming and scalable backend architecture.

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
- **Result:** In active development — targeting ~60–80% dependent-pod co-location rate vs ~25–40% with the default kube-scheduler on 3-tier benchmark workloads.
- [Source](https://github.com/johnhawver/graphsched)

---

#### Current.ai — Weather-Driven Ecommerce Marketing Platform

**Technical Overview:** A Shopify-integrated SaaS platform that ingests live weather data and autonomously generates targeted SMS/email promotions using Claude AI — e.g. a detected cold front triggers a hoodie campaign at 15% off, pushed directly to a store's customer segments.

- **Deep technical work in:** Real-time environmental signal processing pipeline (OpenWeather API → campaign trigger engine) and autonomous AI-driven copy generation via the Anthropic SDK with structured product catalog context.
- **Implementation:** Built on Next.js App Router + TypeScript with Supabase as the backend (auth via Clerk, real-time DB for campaign state) and Tailwind CSS for the dashboard UI — designed around a webhook-driven architecture where weather threshold events fire Claude prompts pre-loaded with live catalog data to produce and schedule campaigns without manual input.
- **Result:** Currently in active development — core pipeline (weather ingestion → Claude prompt generation → campaign dispatch) functional end-to-end; preparing for pilot merchant onboarding.
- [Source](https://github.com/johnhawver/current.ai)

---

### Contact

- **Email:** jnhawver@umich.edu
- **LinkedIn:** [linkedin.com/in/john-hawver](https://www.linkedin.com/in/john-hawver/)

[back to top](#)
