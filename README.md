

---

<div align="center">

<img src="assets/profile-card.svg" width="100%" alt="saipranav@github terminal card"/>

</div>
<div align="center">

<!-- <img src="assets/header.svg" alt="Saipranav M - Backend / Scalable / Real-World" width="100%"/> -->

<a href="https://github.com/AvGeeky">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=36BCF7&center=true&vCenter=true&width=700&lines=Building+systems+that+serve+3%2C000%2B+real+users;Kafka+%C2%B7+Redis+%C2%B7+Spring+Boot+%C2%B7+AWS+Glue;Low-latency+backends+%E2%80%A2+Event-driven+design;Ex-SDE+Intern+@+Barclays+%F0%9F%8F%A6" alt="Typing SVG" />
</a>

<br/>

<a href="https://www.linkedin.com/in/saipranav-m/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
<a href="mailto:sai.saip2005@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/></a>
<a href="https://drive.google.com/file/d/1ZIh0Wfvmlf-RY3_MEJmrkvA8kn-d52zm/view?usp=sharing"><img src="https://img.shields.io/badge/Resume-View_PDF-success?style=for-the-badge&logo=googledrive&logoColor=white"/></a>
<a href="http://bustracker.snuchennai.edu.in/"><img src="https://img.shields.io/badge/Live_Project-Bus_Tracker-orange?style=for-the-badge&logo=googlemaps&logoColor=white"/></a>

<br/><br/>

<img src="https://komarev.com/ghpvc/?username=AvGeeky&label=Profile%20views&color=0e75b6&style=flat" alt="views"/>
<img src="https://img.shields.io/github/followers/AvGeeky?style=flat&logo=github&label=Followers"/>
<img src="https://img.shields.io/github/stars/AvGeeky?style=flat&logo=github&label=Stars"/>

</div>

## 👋 About me

I'm a **B.E. Computer Science** student at **SSN College of Engineering, Chennai** (CGPA 8.47) who likes building backends that actually get used. Several of my systems run in production for thousands of students at **SSN** and **Shiv Nadar University Chennai**, and I'm usually involved in the whole thing, from system design through to deployment and monitoring.

```java
public class Saipranav {
    String role      = "Ex-SDE Intern @ Barclays (Jun-Jul 2026)";
    String studying  = "B.E. CSE, SSN College of Engineering (2023-2027)";
    String obsessed  = "latency, correctness, idempotency, observability";
    String[] learning = { "Kubernetes", "Distributed systems", "Cloud infra" };
    String funFact   = "Loves aviation!";
}
```

---

## 📊 GitHub at a glance

<div align="center">

<img src="assets/stats.svg" width="100%" alt="GitHub stats"/>

<br/>

<a href="https://github.com/AvGeeky?tab=repositories"><img src="https://img.shields.io/github/followers/AvGeeky?style=for-the-badge&logo=github&color=7c3aed&labelColor=0d1117"/></a>
<a href="https://github.com/AvGeeky?tab=repositories"><img src="https://img.shields.io/github/stars/AvGeeky?style=for-the-badge&logo=github&color=7c3aed&labelColor=0d1117"/></a>
<img src="https://img.shields.io/github/last-commit/AvGeeky/AttendanceSystemBE?style=for-the-badge&logo=git&color=7c3aed&labelColor=0d1117&label=last%20commit"/>

</div>

<img src="assets/divider.svg" width="100%" alt=""/>

## 🧭 Experience

| | Role | What I did |
|---|---|---|
| 🏦 | **Former SDE Intern, Barclays** <br/>*Pune · Jun-Jul 2026* | Rebuilt a legacy dataset-comparison tool as a **distributed AWS Glue / PySpark** framework: **92% faster** (1.5 hrs to 7 min on 10M+ rows × 700+ columns). Supports Iceberg and Hive, schema-drift detection, parallel chunked-column processing, and a synthetic data generator. |
| ⚙️ | **Full Stack Engineering Intern, Dexio LabX** <br/>*Chennai · Oct 2025-Feb 2026* | Built an **event-driven async job pipeline** (FastAPI, Redis lists, AsyncIO) with idempotent handling, exponential-backoff retries and **dead-letter-queue** routing for poison-pill tasks. Streamed ingestion for large LLM inputs. |

---

## 🚀 Featured projects

### 🚌 Real-Time Bus Tracking Platform
**Production system for SSN College & SNU Chennai** · [🔴 Live](http://bustracker.snuchennai.edu.in/) · [Code](https://github.com/AvGeeky/SSN_SNUC_Bus_Assignment_Tracking_BackEnd)

> Live transport tracking for **3,000+ users across 2 universities**, with **<500ms p90 API latency** under a 100-concurrent-user ramped load test.

- Concurrent GPS ingestion from **~20 heterogeneous vendor APIs**, one thread per vendor with time-of-day adaptive polling, so one slow vendor never cascades
- **Redis Hashes** state store with last-timestamp-wins semantics; **no database on the hot path**
- Redis transactions and pipelining for multi-key updates and batched reads
- Admin dashboard: fleet monitoring, breakdown handling, hot-swappable route allocation, broadcast/targeted notifications, RBAC
- Fully **on-prem**: NGINX, Docker Compose, Prometheus, Grafana and Loki with automated alerts

```mermaid
flowchart LR
    G[GPS vendors<br/>~20 APIs] -->|parallel polling| S[Spring Boot<br/>normalise and smooth]
    S --> R[(Redis<br/>live state)]
    R --> M[Mobile app]
    R --> W[Web client]
    S -.-> P[Prometheus]
    P -.-> GR[Grafana and Loki]
```

`Java` `Spring Boot` `Redis` `PostgreSQL` `Docker` `NGINX` `Prometheus` `Grafana`

---

### 💳 Payment Pipelines for Invente (SSN's tech fest)

| | **Kafka Payment Pipeline (2025)** | **Redis Payment Pipeline (2026)** |
|---|---|---|
| Scale | **3,000+ transactions** at the fest | k6 load test: **1,000 req/s at 517ms p95, 0% failures** over 100K+ requests |
| Core idea | Transactional Outbox producers + **Kafka Streams windowed joins** to reconcile payments with settlement receipts | Transactional Outbox on Postgres (`FOR UPDATE SKIP LOCKED`) feeding **Redis Streams** consumer groups |
| Reliability | Handles out-of-window events; ceiling validated at **50,000+ events/min** | XCLAIM sweeper threads, dead-letter queues, idempotent processing |
| Ops | Prometheus, Grafana, NGINX-fronted VPS | NGINX gateway, SSL, Prometheus/Grafana/Loki, Cloudflare |
| Code | [kpaymentpipeline](https://github.com/AvGeeky/kpaymentpipeline_invente2025PaymentSystem) | [SSNInventePaymentSystem_Backend2026](https://github.com/AvGeeky/SSNInventePaymentSystem_Backend2026) |

---

### 🧾 AttendEz: secure multi-mode attendance
**Deployed at SSN College** · 🥈 *2nd Place, Encender 3.0 Project Expo 2026* · [Code](https://github.com/AvGeeky/AttendanceSystemBE) · [Demo ▶](https://www.youtube.com/watch?v=YFHxfV337GY)

- Three modes: manual, one-time codes, **time-rotating QR**
- **HMAC-SHA256** verification with per-user, device-bound secrets, plus biometric-gated auth
- Redis-backed ephemeral QR state with **sub-millisecond** server-side verification
- Cut manual verification overhead by **95%**; **200+ concurrent submissions** in production

`Java` `Spring Boot` `Redis` `MongoDB` `Docker` `NGINX` `JUnit` `Jenkins`

---

### 🔐 SecUrVote: cryptographically verifiable voting
🥇 *1st Place, Encender 2.0 Project Expo 2025* · [Backend](https://github.com/AvGeeky/SecUrVote_BE) · [Frontend](https://github.com/AvGeeky/SecUrVote_Frontend) · [Site](https://securvote.vercel.app) · [Demo ▶](https://youtu.be/4nAzh8N8cbA)

RSA vote encryption, HMAC-secured Magic IDs for uniqueness, PBKDF2 auth with OTP login, and an immutable blockchain-style ledger with public verification.

### 🎤 InterVueX: AI-powered hiring
🥇 *1st Place, InnovateX National Hackathon (100+ teams)* · [Backend](https://github.com/AvGeeky/InterVueX-Backend)

Resume- and rubric-driven question generation, live coding via Judge0, face detection, audio processing and sentiment analysis.

### 🎓 PeerLearn: peer-to-peer learning
Built in **24 hours** at Envision SSN · [Backend](https://github.com/AvGeeky/PeerLearn_Backend)

Gamified "Stars" currency, community roadmaps, and dynamic teacher/learner roles.

<details>
<summary><b>🧩 More projects</b></summary>

<br/>

- 🔑 [Simple Password Manager](https://github.com/AvGeeky/simplePasswordManager_SoftwareSecurityAssignment): Java, software security coursework
- 🚆 [Railway Reservation System](https://github.com/AvGeeky/Railway_Reservation_CLangProject): C, booking, PNR status, cancellation
- 🧍 [P-DaISy](https://github.com/AvGeeky/csproject-P-DaISy): police database and facial-recognition identification (high school project)
- 🩺 [healthbusters](https://github.com/AvGeeky/healthbusters): Dart / Flutter
- 🎮 [QGameRepo](https://github.com/AvGeeky/QGameRepo): Godot game for the FAI lab
- 🧠 [ML Lab](https://github.com/AvGeeky/ML_Lab_Sai) · ⚙️ [Compiler Design Lab](https://github.com/AvGeeky/CompilerDesignLab)

</details>

---

## 🛠️ Tech stack

<div align="center">

**Languages**<br/>
<img src="https://skillicons.dev/icons?i=java,python,c,postgres,js,html,css" /><br/>
**Backend & data**<br/>
<img src="https://skillicons.dev/icons?i=spring,fastapi,flask,postgres,mongodb,redis,kafka" /><br/>
**Cloud & DevOps**<br/>
<img src="https://skillicons.dev/icons?i=aws,docker,nginx,linux,jenkins,prometheus,grafana,git" /><br/>
**Frontend & tools**<br/>
<img src="https://skillicons.dev/icons?i=react,postman,figma,idea,github" />

</div>

**Also:** PySpark · AWS Glue/Athena/Lake Formation · Kafka Streams · Redis Streams · k6 · JUnit

---

## 🏆 Achievements

- 🥇 **1st**, InnovateX National Hackathon, 100+ teams (InterVueX)
- 🥇 **1st**, Encender 2.0 Project Expo 2025 (SecUrVote)
- 🥈 **2nd**, Encender 3.0 Project Expo 2026 (AttendEz)

## 👥 Leadership

- **Vice Chairperson**, ACM Chapter SSN (Jul 2026-Present)
- **Lead, Full Stack Development**, SSN Coding Club (Sep 2026-Present)
- **Deputy Head (Technical)**, ACM Chapter SSN (2025-2026)
- **Placement Committee Member**, SSN College of Engineering

## 📚 Research

- **CLEF 2024 (JOKER Lab):** genre classification of humorous text with transformer and traditional ML models
- **ILSUM 2024:** multilingual text summarisation with T5 and Gemini 1.0 Pro

---

---

<div align="center">

**Open to SDE / backend opportunities, so feel free to reach out.**

<img src="assets/divider.svg" width="100%" alt=""/>

</div>
