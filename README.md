# Andi Muchlas Ramadani

**Full-Stack & Geospatial Software Engineer** specializing in **Interactive Web Applications**, **Spatial Systems**, and **High-Throughput Backends**.  
Experienced across modern frontend (TypeScript, React, Next.js, Three.js, Leaflet) and distributed backend architecture (Go, Node.js/Bun, PHP, PostgreSQL/PostGIS, Redis, Kubernetes). Comfortable owning features end-to-end across database schemas, routing engines, APIs, and responsive user-facing applications.

---

## Tech Stack & Expertise

<p align="left">
  <img src="https://skillicons.dev/icons?i=ts,react,nextjs,tailwind,threejs,go,postgres,redis,docker,kubernetes,aws,unity,cs,githubactions,linux,bash&theme=dark" alt="Tech Stack" />
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white" height="22" alt="Next.js" />
  &nbsp;
  <img src="https://img.shields.io/badge/React_18-61DAFB?style=flat-square&logo=react&logoColor=black" height="22" alt="React" />
  &nbsp;
  <img src="https://img.shields.io/badge/Three.js-000000?style=flat-square&logo=threedotjs&logoColor=white" height="22" alt="Three.js" />
  &nbsp;
  <img src="https://img.shields.io/badge/Leaflet-199900?style=flat-square&logo=leaflet&logoColor=white" height="22" alt="Leaflet" />
  &nbsp;
  <img src="https://img.shields.io/badge/PostGIS-336791?style=flat-square&logo=postgis&logoColor=white" height="22" alt="PostGIS" />
  &nbsp;
  <img src="https://img.shields.io/badge/Uber_H3-000000?style=flat-square&logo=uber&logoColor=white" height="22" alt="Uber H3" />
  &nbsp;
  <img src="https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white" height="22" alt="Go" />
  &nbsp;
  <img src="https://img.shields.io/badge/gRPC-244C5A?style=flat-square&logo=grpc&logoColor=white" height="22" alt="gRPC" />
  &nbsp;
  <img src="https://img.shields.io/badge/NATS-27AAE1?style=flat-square&logo=natsdotio&logoColor=white" height="22" alt="NATS" />
  &nbsp;
  <img src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" height="22" alt="Vitest" />
</p>

| Category | Skills & Technologies |
| :--- | :--- |
| **Languages** | TypeScript, JavaScript, Go, PHP, Python, SQL, C# |
| **Frontend & Web** | React, Next.js (App Router), Tailwind CSS, Three.js, Leaflet, D3.js, WebSockets |
| **Backend & APIs** | Go, Node.js (Bun, Hono.js), PHP, RESTful APIs, gRPC (Protobuf), NATS, BullMQ |
| **Databases & Spatial** | PostgreSQL, PostGIS, Spatial SQL, Uber H3 Grid, OSRM, Redis, Typesense, Drizzle ORM |
| **Real-Time & Interactive** | Unity (C#), LiDAR Sensor Telemetry, WebSocket Streaming, Oculus LipSync |
| **Cloud & DevOps** | Docker, Kubernetes, AWS (S3, IAM), Vercel, CI/CD, Linux |
| **Testing & Methods** | Vitest, Automated Unit Testing, TDD, SEO (JSON-LD), REST & gRPC API Design |
| **Spoken Languages** | Indonesian (Native), English (Professional Working Proficiency) |

---

## Professional Experience

- **PT Lintas Cakra Cipta** — `Software Engineer (Backend & Web Systems)` &nbsp;|&nbsp; *Sep 2025 – Present · Full-time (Bandung)*  
  Engineered high-performance backend services in Go/TypeScript, optimized PostGIS spatial queries sustaining sub-second SLAs, and integrated client-side interactive mapping web applications.
- **Molca Teknologi Nusantara** — `Interactive Software Engineer` &nbsp;|&nbsp; *Jun 2026 – Present · Remote Contract*  
  Developed interactive simulation systems and modular gameplay features in C# (Unity) with decoupled component architecture, optimizing runtime memory and frame rendering loops.
- **Automata Visual** — `Software Engineer (IoT & Interactive Systems)` &nbsp;|&nbsp; *Sep 2024 – Feb 2025 · Project Contract (Cimahi)*  
  Engineered an IoT interactive display at the Disaster Room of Geological Museum Bandung, transforming raw hardware LiDAR telemetry into real-time touch detection in C#.
- **UVISUAL Studio** — `Software Engineer (Web & Interactive Systems)` &nbsp;|&nbsp; *Aug 2023 – Sep 2024 · Freelance (Cimahi)*  
  Built Gephyrion, a full-stack real-time platform connecting a PHP/MySQL web application via WebSockets with Unity display runtimes for dynamic character projection.

---

## Featured Engineering Work

### 1. RAJADEREK — Real-Time Spatial Routing & Dispatch Logistics
**Role:** Backend & Spatial Systems Engineer &nbsp;|&nbsp; `Private / Production System`  
Real-time dispatching and routing platform managing on-demand vehicle towing and recovery operations.

- **Spatial Search & Leaflet Mapping:** Built interactive operator map interfaces using **Leaflet** for real-time dispatch and route inspection, supported by spatial search across ~2.8M POIs and ~70K boundaries via PostGIS, H3, and Typesense.
- **Automated Ingestion ETL (~2.8M Records):** Built automated **Scrapy ETL pipelines** scaling POI datasets from ~1.5M to ~2.8M records and ~70K administrative boundaries (Overture Maps, Overpass/OSM, BIG, Pertamina).
- **Decoupled Gateway & Routing Core:** Decoupled into a TypeScript Gateway (auth & aggregation) and a standalone Go Core Engine via **gRPC (Protobuf)** to isolate heavy graph computations from business logic.
- **Low-Latency Search & Autocomplete (Typesense):** Migrated bottlenecked spatial SQL queries to **Typesense**, slashing latency to **<200ms** (p95) using tiered multi-search queries (45 km geofenced local priority, typo tolerance), protected by a Go-native circuit breaker with PostGIS GiST fallback.
- **Proximity Indexing (Uber H3):** Replaced spatial table scans with **Uber H3 hexagonal indexing** for sub-second driver-to-job proximity lookups.
- **Dynamic Routing & Memory Pooling:** Configured OSRM with **Multi-Level Dijkstra (MLD)** for dynamic toll-road weighting; implemented buffer pooling (`sync.Pool`) to minimize heap allocations under high dispatch throughput.
- **Stack:** `Go` · `TypeScript` · `Leaflet` · `Python (Scrapy)` · `Typesense` · `OSRM` · `Uber H3` · `PostgreSQL/PostGIS` · `gRPC (Protobuf)` · `Redis` · `NATS` · `Kubernetes`

---

### 2. Radar Harga (radarharga.shop) — Full-Stack Price Intelligence & Merchant Platform
**Role:** Full-Stack Software Engineer &nbsp;|&nbsp; [Live Website](https://www.radarharga.shop) &nbsp;|&nbsp; [GitHub](https://github.com/andimuchlas/marketplace-intelegence)  
Independent e-commerce price intelligence and merchant utility platform for Shopee, Tokopedia, TikTok Shop, and Lazada. Adopts a Dual-Portal architecture serving bargain-seeking consumers (B2C Price Radar) and MSME merchants requiring precision net margin simulations (B2B Merchant Hub).

- **In-Browser Margin & Fee Calculator:** Engineered in-browser marketplace fee computation using integer arithmetic and stepwise rounding, preventing JavaScript floating-point rounding errors in seller disbursement calculations.
- **B2C & B2B Dual-Interface Design:** Designed responsive dual-interface navigation separating the B2C price-comparison radar from the B2B merchant margin calculator with adaptive layouts (mobile dropdown vs. desktop tabs).
- **Resilient Click Attribution Pipeline:** Built an analytics redirect tracking route (`/api/radar/click`) equipped with bot/scraper detection regex and `X-Robots-Tag: noindex` headers, protecting the Neon Serverless PostgreSQL database from crawler pollution.
- **SEO-First Engineering & Google Indexing:** Implemented 15 structured search routes with injected JSON-LD schemas (`Product`, `FAQPage`, `BreadcrumbList`), achieving a **94%+** SEO audit score on Seobility and rapid Google Search Console indexation.
- **Automated Testing & Code Reliability:** Maintained strict reliability with automated testing via **Vitest** (28/28 unit tests passing), isolating financial calculation logic, IDR formatting, and sliding-window rate limiters with zero React DOM dependency.

<details>
  <summary><b>View System Architecture Diagram</b></summary>
  <br/>

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                           CLIENT TIER (Browser)                             │
│  ┌────────────────────────────────┐    ┌─────────────────────────────────┐  │
│  │ Consumer Price Radar (Route: /)│    │ Merchant Portal (Route: /seller)│  │
│  │ • Live Multi-Marketplace Grid  │    │ • In-Browser Margin Calculator  │  │
│  │ • Deal & Discount Highlighter  │    │ • Stepwise Rounding & Fee Engine│  │
│  │ • Outbound Click Beacon        │    │ • Fee Anatomy & BEP Barometer   │  │
│  └────────────────┬───────────────┘    └────────────────┬────────────────┘  │
└───────────────────┼─────────────────────────────────────┼───────────────────┘
                    │ (Fetch Search / Beacon)             │ (Pre-rendered SSG)
                    ▼                                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                     EDGE & SERVERLESS TIER (Next.js 14)                     │
│  ┌───────────────────────────────┐     ┌─────────────────────────────────┐  │
│  │ App Router Server Components  │     │ Edge API Engine                 │  │
│  │ • Streaming SSR & Static Gen  │     │ • Sliding-Window Rate Limiter   │  │
│  │ • 15 Pre-rendered Intent URLs │     │ • Bot / Scraper Detection Filter│  │
│  │ • JSON-LD Rich Schemas Inject │     │ • Secure 302 Attribution Direct │  │
│  └───────────────┬───────────────┘     └────────────────┬────────────────┘  │
└──────────────────┼──────────────────────────────────────┼───────────────────┘
                   │                                      │
                   ▼                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                           DATA & PERSISTENCE TIER                           │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │ Drizzle ORM + PostgreSQL (Neon Serverless DB)                         │  │
│  │ • affiliate_clicks (Bot-filtered attribution log)                     │  │
│  │ • dynamic_promotions (Curated active campaign feeds)                  │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────┘
```

</details>

- **Stack:** `Next.js 14 (App Router)` · `React` · `TypeScript` · `Tailwind CSS` · `Framer Motion` · `Neon PostgreSQL` · `Drizzle ORM` · `Vitest` · `Vercel`

---

### 3. Creative 3D Interactive Portfolio — WebGL, Three.js, & GSAP Experience
**Role:** Full-Stack & Creative Frontend Engineer &nbsp;|&nbsp; [Live Website](https://landing-page-porfolio-one.vercel.app/)  
A cinematic, interactive 3D web experience showcasing creative web design, 3D spatial assembly, and smooth motion graphics.

- **Scroll-Choreographed 3D WebGL Viewport:** Implemented an interactive 3D scene using **Three.js** and **React Three Fiber (@react-three/fiber)**, rendering real-time mesh models, custom materials, dynamic lighting, and particle effects.
- **Cinematic Camera Traversal:** Integrated **Lenis smooth inertia scrolling** paired with **GSAP ScrollTrigger** timelines, seamlessly driving an animated 3D camera traversing scenes and pathways as the user navigates down the page.
- **Modern UI & Aesthetic Polish:** Built with Tailwind CSS v4, custom film grain shaders, dynamic scroll progress indicators, and responsive mobile-first layouts.
- **Stack:** `Next.js 16` · `React 19` · `Three.js` · `React Three Fiber` · `Drei` · `GSAP` · `Lenis` · `Tailwind CSS v4` · `Vercel`

---

### 4. AI Avatar Unity — End-to-End AI & Real-Time Interactive System
**Role:** Systems Architect & Full-Stack Engineer &nbsp;|&nbsp; `Open Source / GitHub` &nbsp;|&nbsp; [GitHub](https://github.com/andimuchlas/AI-Avatar-Unity)  
Real-time conversational AI avatar application combining a Unity client with a containerized voice-processing backend.

- **Full-Stack Streaming Architecture:** Connected a Unity (C#) client to containerized Docker backend services via bidirectional WebSockets for low-latency state and audio streaming.
- **Voice Pipeline:** Implemented an end-to-end voice pipeline connecting speech recognition (STT), LLM inference, and speech synthesis (TTS) for natural conversational interaction.
- **Avatar & Lip-Sync Animation:** Integrated MetaPerson 3D avatar meshes and Oculus LipSync to translate synthesized speech audio into real-time facial expressions and lip-sync animation.
- **Stack:** `Unity (C#)` · `Python` · `WebSocket` · `Docker` · `STT` · `LLM` · `TTS` · `Oculus LipSync` · `MetaPerson`

---

### 5. Gephyrion — Full-Stack Real-Time Interactive Platform
**Role:** Software Engineer (Web & Interactive Systems) &nbsp;|&nbsp; `Interactive Installation`  
Immersive room installation where a web-based interface connects with a Unity-powered projection system for real-time character visualization.

- **Dual-Tier System Architecture:** Engineered a responsive web portal in PHP/MySQL communicating with Unity projection runtimes via bidirectional WebSockets.
- **Event-Driven State Synchronization:** Built relational schemas and event endpoints to process visitor choices and project animated character outcomes into the physical space with sub-100ms latency.
- **Multi-Projector Calibration:** Deployed hardware multi-projector mapping pipelines ensuring stable 60 FPS performance during live exhibition operations.
- **Stack:** `PHP` · `MySQL` · `Unity` · `C#` · `WebSocket` · `Projection Mapping`

---

### 6. Casanela Villa — High-Concurrency Reservation Engine
**Role:** Full-Stack / Backend Engineer &nbsp;|&nbsp; `Private / Production System`  
Fast booking engine with dynamic pricing calculations and real-time OTA calendar synchronization.

- **Lightweight Runtime:** Built on **Bun + Hono.js** for sub-millisecond route handling and high concurrent request capacity.
- **OTA Channel Sync:** Automated two-way channel synchronization (HotelMu) and booking timeout management via BullMQ background queues.
- **Direct S3 Uploads:** Integrated AWS S3 Presigned URL workflows for direct media storage, bypassing backend proxy bottlenecks.
- **Stack:** `Bun` · `TypeScript` · `Hono.js` · `PostgreSQL` · `Drizzle ORM` · `Redis` · `BullMQ` · `AWS S3`

---

### 7. Intelligent LLM Intent & Difficulty Router
**Role:** ML Systems & Backend Engineer &nbsp;|&nbsp; `Private Research` &nbsp;|&nbsp; [GitHub](https://github.com/andimuchlas/LLM-Intent-Router)  
Orchestration layer intercepting user queries and dynamically routing them across model tiers based on semantic complexity.

- **Taxonomy & Intent Tuning:** Fine-tuned a multilingual DistilBERT model across 5 classification targets (Task, Sub-task, Tool, Difficulty, Execution Mode).
- **Cost vs. Latency Balancing:** Implemented dynamic fallback rules and confidence thresholds to route routine tasks to lightweight models, reserving frontier LLMs for complex queries.
- **Stack:** `Python` · `PyTorch` · `DistilBERT` · `Transformers` · `FastAPI` · `Plotly.js`

---

## Certifications & Credentials

<p align="left">
  <a href="https://www.credly.com/badges/55f7f23f-acc6-40f1-a0cd-a3cb70e5db8e/public_url" target="_blank" title="AWS Certified Cloud Practitioner">
    <img src="https://images.credly.com/images/00634f82-b07f-4bbd-a6bb-53de397fc3a6/image.png" width="100" alt="AWS Certified Cloud Practitioner" />
  </a>
  &nbsp;&nbsp;
  <a href="https://www.credly.com/badges/210e19f0-0fb8-4055-b241-20978744c489/public_url" target="_blank" title="AWS re/Start Graduate">
    <img src="https://images.credly.com/images/44e2c252-5d19-4574-9646-005f7225bf53/image.png" width="100" alt="AWS re/Start Graduate" />
  </a>
  &nbsp;&nbsp;
  <a href="https://www.credly.com/badges/670ec7bf-3fdc-4e4c-bd24-0aa304ffadf2" target="_blank" title="Deploy Kubernetes Applications on Google Cloud">
    <img src="https://images.credly.com/images/f0388a0c-130f-47cd-8750-d6357e907e58/image.png" width="100" alt="Deploy Kubernetes Applications on Google Cloud" />
  </a>
  &nbsp;&nbsp;
  <a href="https://www.credly.com/badges/f94769f0-1891-429e-93e4-8d156ccca072" target="_blank" title="Unity Certified Associate: Game Developer">
    <img src="https://images.credly.com/images/99becefb-f627-413c-8ad3-b52534e50037/image.png" width="100" alt="Unity Certified Associate: Game Developer" />
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
  <a href="https://landing-page-porfolio-one.vercel.app/"><img src="https://img.shields.io/badge/Creative_3D_Portfolio-landing--page-6851FF?style=for-the-badge&logo=vercel&logoColor=white" alt="Creative Portfolio" /></a>
  <a href="https://www.linkedin.com/in/andimuchlas"><img src="https://img.shields.io/badge/LinkedIn-andimuchlas-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:andimuchlas156@gmail.com"><img src="https://img.shields.io/badge/Email-andimuchlas156%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>
