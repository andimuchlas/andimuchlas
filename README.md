# Andi Muchlas

Backend Engineer focused on **Spatial Systems**, **High-Throughput APIs**, and **Distributed Infrastructure**.
Specializing in building spatial computing services, designing routing engines, and optimizing databases for high performance.

---

## Tech Stack & Expertise

<p align="left">
  <img src="https://skillicons.dev/icons?i=go,ts,nodejs,py,postgres,redis,docker,kubernetes,aws,githubactions,linux,bash&theme=dark" alt="Tech Stack" />
</p>

- **Spatial & Specialized Systems:** PostGIS, OSRM (Open Source Routing Machine), Spatial Indexing (R-Tree / GiST), QGIS, NATS Messaging

---

## 📜 Certifications & Credentials

<p align="left">
  <a href="https://www.credly.com/badges/55f7f23f-acc6-40f1-a0cd-a3cb70e5db8e/public_url" target="_blank" title="AWS Certified Cloud Practitioner">
    <img src="https://images.credly.com/images/00634f82-b07f-4bbd-a6bb-53de397fc3a6/image.png" width="110" alt="AWS Certified Cloud Practitioner" />
  </a>
  &nbsp;&nbsp;
  <a href="https://www.credly.com/badges/210e19f0-0fb8-4055-b241-20978744c489/public_url" target="_blank" title="AWS re/Start Graduate">
    <img src="https://images.credly.com/images/44e2c252-5d19-4574-9646-005f7225bf53/image.png" width="110" alt="AWS re/Start Graduate" />
  </a>
  &nbsp;&nbsp;
  <a href="https://www.credly.com/badges/670ec7bf-3fdc-4e4c-bd24-0aa304ffadf2" target="_blank" title="Deploy Kubernetes Applications on Google Cloud">
    <img src="https://images.credly.com/images/f0388a0c-130f-47cd-8750-d6357e907e58/image.png" width="110" alt="Deploy Kubernetes Applications on Google Cloud" />
  </a>
  &nbsp;&nbsp;
  <a href="https://www.credly.com/badges/f94769f0-1891-429e-93e4-8d156ccca072" target="_blank" title="Unity Certified Associate: Game Developer">
    <img src="https://images.credly.com/images/99becefb-f627-413c-8ad3-b52534e50037/image.png" width="110" alt="Unity Certified Associate: Game Developer" />
  </a>
</p>

<details>
  <summary><b>View all Google Cloud Skills & Machine Learning Badges</b></summary>
  <br/>

- **Google Cloud Profile:** [skills.google/public_profiles/andimuchlas](https://www.skills.google/public_profiles/104038eb-cdaa-4a54-8bf4-4d575ae2c783)
- **Skill Badges:** Terraform Essentials, Core Infrastructure & Security, Modern App Deployment, Advanced App Ops
- **ML & AI:** [Fundamentals of Machine Learning &amp; AI](https://drive.google.com/file/d/1U2bKCxNZ11TE13CRJmRKNh6Ucdm7KFJE/preview), [Machine Learning Terminology and Process](https://drive.google.com/file/d/1u5fq3eVU0_nh5FONoHzm6Cr_Tw2IhzT6/preview), Sentiment & Cloud Vision APIs

</details>

---

## Key Projects & Engineering Work

### 1. Intelligent LLM Intent & Difficulty Router

An orchestrator layer that intercepts incoming user queries and routes them dynamically based on Intent (12 tasks, 32 sub-tasks) and Difficulty.

- **End-to-End ML Pipeline & Taxonomy Design:** Designed the entire custom multi-task classification taxonomy (5 orthogonal dimensions: Task, Sub-task, Tool, Difficulty, and Execution Mode) and fine-tuned the multilingual **DistilBERT** model from scratch on CPU/GPU.
- **Problem Solved:** High latency and API costs when sending all queries to frontier models, and boundary confusion on complex/ambiguous inputs.
- **Approach & Architecture:**
  - Implemented a **State Machine Routing Logic** with fallback rules (`MODEL_DIRECT`, `MULTI_INTENT`, `UNCERTAIN`).
  - **Soft Scoring Evaluation:** Dynamic model selection using weighted scores of Cost (35%), Task Affinity (30%), Difficulty Headroom (20%), and Execution Mode Fit (15%).
  - Built an **Interactive Interpretability Visualizer Suite** featuring token-level Saliency Maps and a 3D Vector Space PCA visualizer (`Plotly.js`) to debug `[CLS]` token clusters.

### 2. RAJADEREK — High-Performance Logistics & Spatial Routing Engine
Microservice & Gateway architecture designed for real-time vehicle towing dispatch and spatial routing handling millions of requests.
- **Routing Infrastructure & Dynamic Weights (OSRM):**
  - Configured and leveraged **Multi-Level Dijkstra (MLD)** instead of Contraction Hierarchies (CH) to support dynamic parameters (like toll road exclusion) without slow graph rebuilds.
  - Implemented client-side HTTP connection pooling and caching (Redis with spatial hashing) to minimize network handshake overhead.
- **Go Memory & GC Optimization:**
  - Optimized OSRM payload parsing in Go, replacing heap-allocated pointers with value-types and utilizing `sync.Pool` to reuse JSON decoders and coordinate slices, heavily reducing Garbage Collection (GC) latency.
- **Database & Query Performance (PostGIS):**
  - Tuned PostgreSQL runtime parameters (`work_mem = '8MB'`, `jit = off`) to speed up autocomplete search sorting operations and avoid disk spills.
  - Implemented a geographic partitioning query strategy using spatial bounding box constraints (`ST_Expand` bounding boxes via GIST index) to resolve search results within local clusters first before falling back to a global search.
- **Microservices & Real-time Messaging:** Built gRPC communication between the TypeScript Gateway and Go Core Engine, with NATS messaging for low-latency event distribution.
- **Tech Stack:** `Go`, `TypeScript`, `OSRM`, `PostgreSQL/PostGIS`, `gRPC`, `Redis`, `NATS`, `Docker`, `Kubernetes`.

### 3. ENTERPRISE GENSET MANAGEMENT — Clean Architecture & Distributed Pipeline
Enterprise equipment rental and field maintenance logistics platform built with Clean/Hexagonal Architecture in an NX Monorepo.
- Integrated BullMQ & Redis distributed job queues for async push alerts (FCM), digital BAST generation with e-signatures, and XLSX financial exports.
- Implemented Dependency Injection (`tsyringe`), end-to-end validation with shared Zod schemas, and Better-Auth RBAC.
- **Tech Stack:** `Node.js`, `TypeScript`, `Hono.js`, `Drizzle ORM`, `PostgreSQL`, `Redis`, `BullMQ`, `AWS S3`, `NX`.

### 4. CASANELA VILLA API — Reservation Engine & Real-time OTA Channel Sync
High-throughput backend service for villa reservations, dynamic pricing, and external OTA calendar synchronization.
- Decoupled background processing using BullMQ & Redis for automated OTA sync (HotelMu), reservation expiration timeouts, and email delivery.
- Built secure S3 Presigned URL media storage and automated PDF quotation/invoice generation (`jsPDF`).
- **Tech Stack:** `Bun`, `TypeScript`, `Hono.js`, `PostgreSQL`, `Drizzle ORM`, `Redis`, `BullMQ`, `AWS S3 / MinIO`, `Docker`.

---

## Connect with me

<p align="left">
  <a href="https://andi.is-a.dev"><img src="https://img.shields.io/badge/Website-andi.is--a.dev-111111?style=for-the-badge&logo=About.me&logoColor=white" alt="Website" /></a>
  <a href="https://www.linkedin.com/in/andimuchlas"><img src="https://img.shields.io/badge/LinkedIn-andimuchlas-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:andimuchlas156@gmail.com"><img src="https://img.shields.io/badge/Email-andimuchlas156%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>
