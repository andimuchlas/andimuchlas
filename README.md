# Andi Muchlas

Backend Engineer focused on **Spatial Systems**, **High-Throughput APIs**, and **Distributed Infrastructure**.
Specializing in building spatial computing services, designing routing engines, and optimizing databases for high performance.

---

## Tech Stack & Expertise

<p align="left">
  <img src="https://skillicons.dev/icons?i=go,ts,nodejs,bun,py,unity,cs,postgres,redis,docker,kubernetes,aws,githubactions,linux,bash&theme=dark" alt="Tech Stack" />
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Hono.js-E36002?style=flat-square&logo=hono&logoColor=white" alt="Hono" height="24" />
   
  <img src="https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat-square&logo=drizzle&logoColor=black" alt="Drizzle ORM" height="24" />
   
  <img src="https://img.shields.io/badge/Uber_H3-000000?style=flat-square&logo=uber&logoColor=white" alt="Uber H3" height="24" />
   
  <img src="https://img.shields.io/badge/PostGIS-336791?style=flat-square&logo=postgis&logoColor=white" alt="PostGIS" height="24" />
   
  <img src="https://img.shields.io/badge/NATS-27AAE1?style=flat-square&logo=natsdotio&logoColor=white" alt="NATS" height="24" />
   
  <img src="https://img.shields.io/badge/gRPC-244C5A?style=flat-square&logo=grpc&logoColor=white" alt="gRPC" height="24" />
</p>

- **Core & Backend:** Go, TypeScript, Node.js, Bun, Python, C#, Hono.js, Drizzle ORM, gRPC, REST APIs
- **Spatial & Specialized Systems:** PostGIS, OSRM (Open Source Routing Machine), Uber H3 (Hexagonal Hierarchical Spatial Index), Spatial Indexing (R-Tree / GiST), QGIS, NATS Messaging, BullMQ
- **Interactive & Real-time:** Unity Engine (Game Programming & Spatial Installations), WebSockets

---

## Certifications & Credentials

<p align="left">
  <a href="https://www.credly.com/badges/55f7f23f-acc6-40f1-a0cd-a3cb70e5db8e/public_url" target="_blank" title="AWS Certified Cloud Practitioner">
    <img src="https://images.credly.com/images/00634f82-b07f-4bbd-a6bb-53de397fc3a6/image.png" width="110" alt="AWS Certified Cloud Practitioner" />
  </a>
    
  <a href="https://www.credly.com/badges/210e19f0-0fb8-4055-b241-20978744c489/public_url" target="_blank" title="AWS re/Start Graduate">
    <img src="https://images.credly.com/images/44e2c252-5d19-4574-9646-005f7225bf53/image.png" width="110" alt="AWS re/Start Graduate" />
  </a>
    
  <a href="https://www.credly.com/badges/670ec7bf-3fdc-4e4c-bd24-0aa304ffadf2" target="_blank" title="Deploy Kubernetes Applications on Google Cloud">
    <img src="https://images.credly.com/images/f0388a0c-130f-47cd-8750-d6357e907e58/image.png" width="110" alt="Deploy Kubernetes Applications on Google Cloud" />
  </a>
    
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

- **Problem Solved:** Resource contention in monolithic architectures where compute-heavy spatial graph computations degraded core business logic, high Garbage Collection (GC) latency during large spatial payload parsing, and disk spill bottlenecks on spatial searches.
- **Approach & Architecture:**
  - **Single Responsibility Service Decomposition:** Decoupled the architecture into a **TypeScript Gateway** (handling auth, request aggregation, and client contracts) and an isolated **Go Core Engine** via high-speed **gRPC**, ensuring each service handles a dedicated responsibility without cross-domain performance interference.
  - **Routing Infrastructure & Dynamic Weights (OSRM):** Configured and leveraged **Multi-Level Dijkstra (MLD)** instead of Contraction Hierarchies (CH) to support dynamic parameters (like toll road exclusion) without slow graph rebuilds. Implemented client-side HTTP connection pooling and caching (Redis with spatial hashing) to minimize network handshake overhead.
  - **Go Memory & GC Optimization:** Optimized OSRM payload parsing in Go, replacing heap-allocated pointers with value-types and utilizing `sync.Pool` to reuse JSON decoders and coordinate slices, heavily reducing Garbage Collection (GC) latency.
  - **Spatial Indexing & Query Tuning (H3, PostGIS, Redis):** Indexed discrete driver zones and proximity lookups using **Uber H3 (Hexagonal Hierarchical Spatial Index)** for O(1) hexagonal resolution and fast spatial aggregations. Tuned PostgreSQL runtime parameters (`work_mem = '8MB'`, `jit = off`) and applied bounded bounding-box query strategies (`ST_Expand` via GIST index) for local-first cluster searching.
  - **Real-Time Event Messaging:** Leveraged **NATS** for ultra-low latency, decoupled driver dispatch messaging.
- **Tech Stack:** `Go`, `TypeScript`, `OSRM`, `Uber H3`, `PostgreSQL/PostGIS`, `gRPC`, `Redis`, `NATS`, `Docker`, `Kubernetes`.

### 3. ENTERPRISE GENSET MANAGEMENT — Clean Architecture & Distributed Pipeline

Enterprise equipment rental and field maintenance logistics platform built for end-to-end operational tracking across field crews and administration.

- **Problem Solved:** Tight coupling between business domain rules and infrastructure/third-party services, synchronous bottlenecks during heavy document generation, and state inconsistency across mobile apps and web portals.
- **Approach & Architecture:**
  - **Hexagonal / Clean Architecture (NX Monorepo):** Strictly isolated business domains from external frameworks using Dependency Injection (`tsyringe`) and shared type-safe Zod contracts across client and server.
  - **Decoupled Asynchronous Job Pipeline:** Integrated **BullMQ & Redis** to offload heavy background tasks (Firebase Cloud Messaging push alerts, automated PDF BAST generation with embedded digital e-signatures, and XLSX financial exports) away from the HTTP lifecycle.
  - **Type-Safe Persistence & RBAC:** Utilized **Drizzle ORM** with PostgreSQL for type-safe transactional queries and enforced granular Role-Based Access Control via **Better-Auth**.
- **Tech Stack:** `Node.js`, `TypeScript`, `Hono.js`, `Drizzle ORM`, `PostgreSQL`, `Redis`, `BullMQ`, `AWS S3`, `NX`.

### 4. CASANELA VILLA API — Reservation Engine & Real-time OTA Channel Sync

High-throughput backend service for villa reservations, dynamic pricing calculations, and real-time external OTA channel synchronization.

- **Problem Solved:** Double-booking risks across third-party Online Travel Agencies (OTAs), race conditions during concurrent bookings, and latency overhead on static media delivery.
- **Approach & Architecture:**
  - **High-Throughput Runtime:** Built with **Bun + Hono.js** to minimize execution overhead and achieve sub-millisecond route handling.
  - **Distributed Queue for OTA Calendar Sync:** Deployed **BullMQ & Redis** background workers to manage real-time two-way OTA availability sync (HotelMu), reservation expiration timeouts, and transactional email triggers.
  - **Direct Cloud Storage & Document Pipelines:** Integrated AWS S3 / MinIO presigned URL flows for secure direct-to-storage media uploads, coupled with programmatic PDF invoice generation (`jsPDF`).
- **Tech Stack:** `Bun`, `TypeScript`, `Hono.js`, `PostgreSQL`, `Drizzle ORM`, `Redis`, `BullMQ`, `AWS S3 / MinIO`, `Docker`.

---

## Connect with me

<p align="left">
  <a href="https://andi.is-a.dev"><img src="https://img.shields.io/badge/Website-andi.is--a.dev-111111?style=for-the-badge&logo=About.me&logoColor=white" alt="Website" /></a>
  <a href="https://www.linkedin.com/in/andimuchlas"><img src="https://img.shields.io/badge/LinkedIn-andimuchlas-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:andimuchlas156@gmail.com"><img src="https://img.shields.io/badge/Email-andimuchlas156%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>
