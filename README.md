# Hi, I'm Andi Muchlas

Backend Engineer passionate about **Spatial Computing**, **High-Throughput APIs**, and **Distributed Systems**.
Designing routing engines, optimizing spatial queries over millions of records, and building resilient backend pipelines.

---

## Engineering Focus

- **Spatial Computing & Geospatial Data:** High-speed routing engines (OSRM), hexagonal hierarchical indexing (Uber H3), spatial indexing (PostGIS / GiST / R-Tree), boundary polygon lookups.
- **Data Ingestion & Spatial ETL:** Large-scale crawling pipelines (Scrapy), geo-coordinate normalization, and multi-source spatial aggregation (Overture Maps, Overpass/OSM, INA-Geoportal, BIG, Pertamina).
- **High-Throughput & Low-Latency APIs:** Distributed microservices in Go & TypeScript, gRPC service communication, memory reuse (`sync.Pool`), GC pause reduction.
- **Distributed & Event-Driven Architecture:** Asynchronous worker pipelines (BullMQ/Redis), event-driven messaging (NATS), background synchronization.

---

## Tech Stack & Expertise

<p align="left">
  <img src="https://skillicons.dev/icons?i=go,ts,nodejs,bun,py,unity,cs,postgres,redis,docker,kubernetes,aws,githubactions,linux,bash&theme=dark" alt="Tech Stack" />
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Hono.js-E36002?style=flat-square&logo=hono&logoColor=white" alt="Hono" height="24" />
  &nbsp;
  <img src="https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat-square&logo=drizzle&logoColor=black" alt="Drizzle ORM" height="24" />
  &nbsp;
  <img src="https://img.shields.io/badge/Scrapy_ETL-60A839?style=flat-square&logo=scrapy&logoColor=white" alt="Scrapy" height="24" />
  &nbsp;
  <img src="https://img.shields.io/badge/Uber_H3-000000?style=flat-square&logo=uber&logoColor=white" alt="Uber H3" height="24" />
  &nbsp;
  <img src="https://img.shields.io/badge/PostGIS-336791?style=flat-square&logo=postgis&logoColor=white" alt="PostGIS" height="24" />
  &nbsp;
  <img src="https://img.shields.io/badge/NATS-27AAE1?style=flat-square&logo=natsdotio&logoColor=white" alt="NATS" height="24" />
  &nbsp;
  <img src="https://img.shields.io/badge/gRPC-244C5A?style=flat-square&logo=grpc&logoColor=white" alt="gRPC" height="24" />
</p>

- **Core & Backend:** Go, TypeScript, Node.js, Bun, Python, C#, Hono.js, Drizzle ORM, gRPC, REST APIs
- **Spatial & Specialized Systems:** PostGIS, OSRM (Open Source Routing Machine), Uber H3 (Hexagonal Hierarchical Spatial Index), Spatial Indexing (R-Tree / GiST), QGIS, NATS Messaging, BullMQ
- **Data Engineering:** Scrapy (Distributed Web Crawling & Spatial Ingestion), Geo-Spatial Data Normalization & ETL
- **Interactive & Real-time:** Unity Engine (Game Programming & Spatial Installations), WebSockets

---

## Professional Engineering Work

> *Most core systems below are private production code. The summaries highlight my engineering responsibilities, system architecture, and technical problem-solving.*

### 1. RAJADEREK — High-Performance Logistics & Spatial Routing Engine

**Role:** Lead Backend & Spatial Engineer &nbsp;|&nbsp; `Private / Production System`  
A real-time logistics platform managing on-demand towing operations, automated driver dispatching, and large-scale spatial location processing.

- **Key Engineering Contributions & Problem Solved:**
  - **Service Boundary Decomposition:** Decoupled the architecture into a **TypeScript Gateway** (auth, validation, client aggregation) and a standalone **Go Core Engine** communicating via high-speed **gRPC**, eliminating resource contention between business logic and compute-heavy graph processing.
  - **Multi-Source Spatial Data Ingestion & Crawling (~1.5M Records):** Engineered an automated **Scrapy ETL pipeline** crawling and aggregating **~1.5M geospatial POIs** and **~70K administrative boundaries** across fragmented sources (*Overture Maps, Overpass API / OSM, Badan Informasi Geospasial / BIG, INA-Geoportal, and Pertamina*). Handled geo-coordinate normalization, deduplication, and schema homogenization.
  - **Spatial Search & Fuzzy Autocomplete Optimization:** Designed high-throughput spatial autocomplete search. Tuned PostgreSQL runtime (`work_mem = '8MB'`, `jit = off`) and applied bounded bounding-box query strategies (`ST_Expand` via GiST index) for local-first cluster resolution before fallback searches.
  - **Hierarchical Hexagonal Indexing (Uber H3):** Indexed driver zones and proximity radius lookups using **Uber H3** to achieve $O(1)$ hexagonal cell resolution and eliminate expensive spatial polygon intersection queries during dispatch matching.
  - **Dynamic Routing & Weight Calculations (OSRM):** Configured and deployed **Multi-Level Dijkstra (MLD)** instead of Contraction Hierarchies (CH) to support dynamic edge weight adjustments (e.g., real-time toll road exclusions) without expensive graph rebuilds. Added client-side HTTP connection pooling and Redis spatial hashing for hot-route caching.
  - **Go Memory & GC Optimization:** Optimized OSRM payload parsing in Go, replacing heap-allocated pointer structures with value types and utilizing `sync.Pool` to reuse JSON decoders and coordinate slice buffers, significantly reducing Garbage Collection (GC) latency spikes.
  - **Event-Driven Dispatching:** Integrated **NATS** messaging for sub-millisecond, asynchronous dispatch events between driver services.
- **Infrastructure & Stack:** `Go`, `TypeScript`, `Python (Scrapy)`, `OSRM`, `Uber H3`, `PostgreSQL/PostGIS`, `gRPC`, `Redis`, `NATS`, `Docker`, `Kubernetes`.

---

### 2. ENTERPRISE GENSET MANAGEMENT — Clean Architecture & Distributed Pipeline

**Role:** Backend Engineer &nbsp;|&nbsp; `Private / Production System`  
Enterprise equipment rental and field maintenance logistics platform built for end-to-end operational tracking across field crews and administration.

- **Key Engineering Contributions & Problem Solved:**
  - **Hexagonal Architecture (NX Monorepo):** Isolated core business domains from external frameworks using Dependency Injection (`tsyringe`) and enforced end-to-end type safety via shared Zod contracts across client and server.
  - **Decoupled Asynchronous Job Pipeline:** Integrated **BullMQ & Redis** to offload heavy background tasks (Firebase Cloud Messaging push alerts, automated PDF BAST generation with embedded digital e-signatures, and XLSX financial exports) away from the HTTP request-response lifecycle.
  - **Type-Safe Persistence & RBAC:** Designed transactional database workflows using **Drizzle ORM** with PostgreSQL and configured granular Role-Based Access Control via **Better-Auth**.
- **Infrastructure & Stack:** `Node.js`, `TypeScript`, `Hono.js`, `Drizzle ORM`, `PostgreSQL`, `Redis`, `BullMQ`, `AWS S3`, `NX`.

---

### 3. CASANELA VILLA API — Reservation Engine & Real-time OTA Channel Sync

**Role:** Backend Engineer &nbsp;|&nbsp; `Private / Production System`  
High-throughput reservation backend featuring dynamic pricing calculations, automated voucher validation, and real-time external OTA channel synchronization.

- **Key Engineering Contributions & Problem Solved:**
  - **High-Throughput Runtime:** Built on **Bun + Hono.js** to minimize execution overhead, eliminate cold-start latency, and maximize concurrent request handling.
  - **Distributed Queue for OTA Calendar Sync:** Deployed **BullMQ & Redis** background workers to manage two-way OTA availability synchronization (HotelMu), prevent double-booking race conditions, and handle booking expiration timeouts.
  - **Direct Cloud Storage & Document Pipelines:** Integrated AWS S3 / MinIO presigned URL flows for secure direct-to-storage media uploads, coupled with programmatic PDF invoice generation (`jsPDF`).
- **Infrastructure & Stack:** `Bun`, `TypeScript`, `Hono.js`, `PostgreSQL`, `Drizzle ORM`, `Redis`, `BullMQ`, `AWS S3 / MinIO`, `Docker`.

---

## Systems Research & Personal Engineering Projects

### 4. Intelligent LLM Intent & Difficulty Router

**Role:** ML Systems & Backend Architecture &nbsp;|&nbsp; `Private Research`  
A high-efficiency classification orchestrator layer designed to intercept user requests and dynamically route them to optimal models based on Intent (12 tasks, 32 sub-tasks) and Difficulty.

- **Key Engineering Focus & Decisions:**
  - **Inference Optimization & Benchmarking:** Designed a custom multi-task classification taxonomy (5 orthogonal dimensions) and fine-tuned a multilingual **DistilBERT** model. Evaluated runtime efficiency and transport overhead across model serving architectures.
  - **State Machine Routing Logic:** Implemented dynamic model fallback rules (`MODEL_DIRECT`, `MULTI_INTENT`, `UNCERTAIN`) paired with weighted soft-scoring (Cost 35%, Task Affinity 30%, Difficulty Headroom 20%, Execution Fit 15%) to cut expensive frontier LLM API costs.
  - **Interpretability Suite:** Built token-level Saliency Maps and a 3D Vector Space PCA visualizer (`Plotly.js`) to debug and inspect `[CLS]` token cluster boundaries.
- **Infrastructure & Stack:** `Python`, `PyTorch`, `DistilBERT`, `Transformers`, `FastAPI`, `Plotly.js`.

---

## Certifications & Credentials

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
- **ML & AI:** [Fundamentals of Machine Learning & AI](https://drive.google.com/file/d/1U2bKCxNZ11TE13CRJmRKNh6Ucdm7KFJE/preview), [Machine Learning Terminology and Process](https://drive.google.com/file/d/1u5fq3eVU0_nh5FONoHzm6Cr_Tw2IhzT6/preview), Sentiment & Cloud Vision APIs

</details>

---

## Connect with me

<p align="left">
  <a href="https://andi.is-a.dev"><img src="https://img.shields.io/badge/Website-andi.is--a.dev-111111?style=for-the-badge&logo=About.me&logoColor=white" alt="Website" /></a>
  <a href="https://www.linkedin.com/in/andimuchlas"><img src="https://img.shields.io/badge/LinkedIn-andimuchlas-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:andimuchlas156@gmail.com"><img src="https://img.shields.io/badge/Email-andimuchlas156%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>
