# John Hawver
**Computer Engineering @ University of Michigan**
[LinkedIn](https://www.linkedin.com/in/john-hawver/) | [Email](jnhawver@umich.edu) | [Portfolio](github.com/johnhawver)

---

### Technical Profile
I am a first-year Computer Engineering student at Michigan focused on systems programming and scalable backend architecture. I am currently seeking Software Engineering experience to contribute to high-growth technical teams.

- **Current focus:** Graph-structured neural networks in PyTorch / Distributed systems orchestration with Kubernetes
- **Current project:** [GraphSched](https://github.com/johnhawver/graphsched) — replacing Kubernetes' default scheduler with a GNN + multi-agent RL policy that uses live pod dependency topology to make smarter placement decisions

---

### Technical Stack
- **Languages:** C++, Python, Java, TypeScript, SQL
- **Tools/Env:** Git, Linux (Ubuntu/Fedora), Docker, AWS, GDB/Valgrind
- **Frameworks:** Node.js, FastAPI, React

---

### Engineering Projects

#### GraphSched — GNN + MARL Kubernetes Scheduler *(In Development)*
**Technical Overview:** A custom Kubernetes scheduler plugin that builds a live directed graph of pod dependencies and uses a Graph Attention Network + multi-agent PPO policy to co-optimize pod placement across all cluster nodes.

- **Deep technical work in:** Kubernetes internals (watch streams, scheduler extension points), graph neural network design (PyTorch Geometric), and multi-agent RL environment design (RLlib/PPO).
- **Implementation:** Building a real-time pod dependency graph watcher using K8s watch streams, a 3-layer GAT encoder trained with contrastive loss, and a gRPC service connecting the GNN to a custom scheduler plugin.
- **Result:** In active development — cluster setup and pod/node fundamentals complete; graph construction pipeline underway.
- [Source](https://github.com/johnhawver/graphsched)

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
