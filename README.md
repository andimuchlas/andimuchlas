# Andi Muchlas

Backend Engineer focused on **Spatial Systems**, **High-Throughput APIs**, and **Distributed Infrastructure**.

Specializing in building spatial computing services, designing routing engines, and optimizing databases for high performance.

---

## 🛠️ Tech Stack & Expertise

- **Languages:** Go, TypeScript/Node.js, Python, SQL
- **Spatial / Databases:** PostgreSQL (PostGIS), Redis, OSRM, Spatial Indexing (R-Tree/GiST), QGIS
- **Infrastructure:** Docker, Kubernetes, NATS, GitHub Actions, AWS

---

## 🚀 Key Projects & Engineering Work

### 1. Intelligent LLM Intent & Difficulty Router
An orchestrator layer that intercepts incoming user queries and routes them dynamically based on Intent (12 tasks, 32 sub-tasks) and Difficulty.
- **End-to-End ML Pipeline & Taxonomy Design:** Designed the entire custom multi-task classification taxonomy (5 orthogonal dimensions: Task, Sub-task, Tool, Difficulty, and Execution Mode) and fine-tuned the multilingual **DistilBERT** model from scratch on CPU/GPU.
- **Problem Solved:** High latency and API costs when sending all queries to frontier models, and boundary confusion on complex/ambiguous inputs.
- **Approach & Architecture:**
  - Implemented a **State Machine Routing Logic** with fallback rules (`MODEL_DIRECT`, `MULTI_INTENT`, `UNCERTAIN`).
  - **Soft Scoring Evaluation:** Dynamic model selection using weighted scores of Cost (35%), Task Affinity (30%), Difficulty Headroom (20%), and Execution Mode Fit (15%).
  - Built an **Interactive Interpretability Visualizer Suite** featuring token-level Saliency Maps and a 3D Vector Space PCA visualizer (`Plotly.js`) to debug `[CLS]` token clusters.

### 2. High-Performance Map Engine & Spatial Services
Designed and optimized a self-hosted routing engine and spatial queries handling millions of requests.
- **Routing Infrastructure (OSRM):**
  - Configured and leveraged **Multi-Level Dijkstra (MLD)** instead of Contraction Hierarchies (CH) to support dynamic parameters (like toll road exclusion) without slow graph rebuilds.
  - Implemented client-side HTTP connection pooling and caching (Redis with spatial hashing) to minimize network handshake overhead.
- **Go Memory & GC Optimization:**
  - Optimized OSRM payload parsing in Go, replacing heap-allocated pointers with value-types and utilizing `sync.Pool` to reuse JSON decoders and coordinate slices, heavily reducing Garbage Collection (GC) latency.
- **Database & Query Performance (PostGIS):**
  - Tuned PostgreSQL runtime parameters (`work_mem = '64MB'`, `jit = off`) to speed up autocomplete search sorting operations and avoid disk spills.
  - Implemented a geographic partitioning query strategy using spatial bounding box constraints (`ST_Expand` bounding boxes via GIST index) to resolve search results within local clusters first before falling back to a global search.

---

## 📫 Connect with me

- **Website/Blog:** [andi.is-a.dev](https://andi.is-a.dev)
- **LinkedIn:** [linkedin.com/in/andimuchlas](https://www.linkedin.com/in/andimuchlas)
- **Email:** [hello@andi.is-a.dev](mailto:hello@andi.is-a.dev)
