# Andi Muchlas

Full-Stack Software Engineer (Backend-Heavy) specializing in **High-Throughput APIs**, **Spatial Computing**, and **Modern Distributed Web Architectures**.  
Designing low-latency microservices, routing engines, geospatial ETL pipelines, and high-performance web applications.

---

## Tech Stack & Expertise

<p align="left">
  <img src="https://skillicons.dev/icons?i=go,ts,react,nextjs,tailwind,nodejs,bun,py,postgres,redis,docker,kubernetes,aws,unity,cs,githubactions,linux,bash&theme=dark" alt="Tech Stack" />
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white" height="22" alt="Next.js" />
  &nbsp;
  <img src="https://img.shields.io/badge/React_18-61DAFB?style=flat-square&logo=react&logoColor=black" height="22" alt="React" />
  &nbsp;
  <img src="https://img.shields.io/badge/Hono.js-E36002?style=flat-square&logo=hono&logoColor=white" height="22" alt="Hono" />
  &nbsp;
  <img src="https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat-square&logo=drizzle&logoColor=black" height="22" alt="Drizzle ORM" />
  &nbsp;
  <img src="https://img.shields.io/badge/Scrapy_ETL-60A839?style=flat-square&logo=scrapy&logoColor=white" height="22" alt="Scrapy" />
  &nbsp;
  <img src="https://img.shields.io/badge/Uber_H3-000000?style=flat-square&logo=uber&logoColor=white" height="22" alt="Uber H3" />
  &nbsp;
  <img src="https://img.shields.io/badge/PostGIS-336791?style=flat-square&logo=postgis&logoColor=white" height="22" alt="PostGIS" />
  &nbsp;
  <img src="https://img.shields.io/badge/NATS-27AAE1?style=flat-square&logo=natsdotio&logoColor=white" height="22" alt="NATS" />
  &nbsp;
  <img src="https://img.shields.io/badge/gRPC-244C5A?style=flat-square&logo=grpc&logoColor=white" height="22" alt="gRPC" />
</p>

---

## Featured Engineering Work

> *Featured production systems, open-source platforms, and architectural research. Summaries highlight system architecture, engineering decisions, and technical impact.*

### 1. RAJADEREK — Real-Time Spatial Routing & Logistics
**Role:** Backend & Spatial Engineer &nbsp;|&nbsp; `Private / Production System`  
Real-time dispatching and routing platform managing on-demand vehicle towing operations.

- **Service Decomposition:** Decoupled into a TypeScript Gateway (auth & aggregation) and a standalone Go Core Engine via **gRPC** to isolate heavy graph computations from business logic.
- **Data Ingestion (~2.8M Records):** Built automated **Scrapy ETL pipelines** scaling POI datasets from ~1.5M to ~2.8M records and ~70K administrative boundaries (Overture Maps, Overpass/OSM, BIG, Pertamina).
- **Low-Latency Search & Autocomplete (Typesense):** Migrated bottlenecked spatial SQL queries (which degraded from ~1s to 3–5s as data doubled) to **Typesense**, slashing latency to **<200ms** (p95) using tiered multi-search queries (45 km geofenced local priority, typo tolerance), protected by a Go-native circuit breaker with PostGIS GiST fallback.
- **Proximity Indexing (Uber H3):** Replaced slow polygon intersection queries with **Uber H3 hexagonal indexing** ($O(1)$ cell lookup) for instant driver-to-job proximity matching.
- **Dynamic Routing & GC Tuning:** Configured OSRM with **Multi-Level Dijkstra (MLD)** for dynamic toll-road weighting; reused memory buffers to minimize Go GC pressure under high dispatch throughput.
- **Stack:** `Go` · `TypeScript` · `Python (Scrapy)` · `Typesense` · `OSRM` · `Uber H3` · `PostgreSQL/PostGIS` · `gRPC` · `Redis` · `NATS` · `Kubernetes`

### 2. AI Avatar Unity — End-to-End AI & Real-Time Interactive System
**Role:** Unity & AI Systems Engineer &nbsp;|&nbsp; `Interactive System`  
Real-time AI avatar application combining a Unity client with a containerized voice-processing backend.

- **Voice Pipeline:** Implemented a voice pipeline connecting speech recognition, LLM inference, and speech synthesis for real-time conversational interaction.
- **Avatar & Lip-Sync Animation:** Integrated MetaPerson avatar and Oculus LipSync to translate generated audio into real-time facial and lip-sync animation.
- **Real-Time Communication:** Connected Unity to backend AI services through WebSocket-based real-time communication.
- **Stack:** `Unity` · `C#` · `WebSocket` · `Docker` · `STT` · `LLM` · `TTS` · `Oculus LipSync` · `MetaPerson`

### 3. Radar Harga (radarharga.shop) — Full-Stack Price Intelligence & Merchant Platform
**Role:** Full-Stack Software Engineer &nbsp;|&nbsp; [Live Website](https://www.radarharga.shop) &nbsp;|&nbsp; [GitHub](https://github.com/andimuchlas/marketplace-intelegence)  
Independent e-commerce price intelligence and merchant utility platform for Shopee, Tokopedia, TikTok Shop, and Lazada. Adopts a Dual-Portal architecture serving bargain-seeking consumers (B2C Price Radar) and MSME merchants requiring precision net margin simulations (B2B Merchant Hub).

- **Client-Side Zero-Latency Math Engine (< 5ms):** Engineered in-browser marketplace fee computation using Whole-IDR integer arithmetic with stepped rounding, eliminating native JavaScript IEEE 754 floating-point inaccuracies on merchant payout balances.
- **Dual-Portal & Persona Decoupling:** Decoupled application navigation into two independent domains—a consumer bargain radar and a seller profit calculator—powered by adaptive navigation components (compact mobile dropdown and active-line desktop tabs).
- **Resilient Click Attribution Pipeline:** Built an analytics redirect tracking route (`/api/radar/click`) equipped with bot/scraper detection regex and `X-Robots-Tag: noindex` headers, protecting the Neon Serverless PostgreSQL database from millions of crawler requests.
- **SEO-First Engineering & Google Indexing:** Implemented 15 structured search routes with injected JSON-LD schemas (`Product`, `FAQPage`, `BreadcrumbList`), multi-resolution favicons, and crawler fallbacks, achieving a **94%+** SEO audit score on Seobility and rapid Google Search Console indexation.
- **Automated Testing & Code Reliability:** Maintained strict reliability with automated testing via **Vitest** (28/28 unit tests passing), isolating financial math engines, IDR formatting, and sliding-window rate limiters with zero React DOM dependency.

<details>
  <summary><b>View System Architecture Diagram</b></summary>
  <br/>

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                           CLIENT TIER (Browser)                             │
│  ┌────────────────────────────────┐    ┌─────────────────────────────────┐  │
│  │ Consumer Price Radar (Route: /)│    │ Merchant Portal (Route: /seller)│  │
│  │ • Live Multi-Marketplace Grid  │    │ • Zero-Latency In-Browser Calc  │  │
│  │ • Deal & Discount Highlighter  │    │ • Whole IDR Margin Engine (<5ms)│  │
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

### 4. Casanela Villa — High-Throughput Reservation Engine
**Role:** Backend Engineer &nbsp;|&nbsp; `Private / Production System`  
Fast booking engine with dynamic pricing calculations and real-time OTA calendar synchronization.

- **Lightweight Runtime:** Built on **Bun + Hono.js** for sub-millisecond route handling and high concurrent request capacity.
- **OTA Channel Sync:** Automated two-way channel synchronization (HotelMu) and booking timeout management via BullMQ queues.
- **Direct S3 Uploads:** Integrated S3 Presigned URL workflows for direct media storage, bypassing backend proxy bottlenecks.
- **Stack:** `Bun` · `TypeScript` · `Hono.js` · `PostgreSQL` · `Drizzle ORM` · `Redis` · `BullMQ` · `AWS S3`

### 5. Intelligent LLM Intent & Difficulty Router
**Role:** ML Systems & Backend Architecture &nbsp;|&nbsp; `Private Research`  
Orchestration layer intercepting user queries and dynamically routing them across model tiers.

- **Taxonomy & Optimization:** Fine-tuned a multilingual DistilBERT model across 5 orthogonal dimensions (Task, Sub-task, Tool, Difficulty, Execution Mode).
- **Cost vs. Latency Balancing:** Implemented state-machine fallbacks and weighted soft-scoring to route routine tasks to cheap models and complex tasks to frontier LLMs.
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
  <a href="https://www.linkedin.com/in/andimuchlas"><img src="https://img.shields.io/badge/LinkedIn-andimuchlas-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:andimuchlas156@gmail.com"><img src="https://img.shields.io/badge/Email-andimuchlas156%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>
