# Hi, I'm Saipranav M

Welcome to my GitHub.

I'm an undergraduate Computer Science and Engineering student passionate about building secure, scalable systems and exploring machine learning, system design, and backend development.

I enjoy solving real-world problems with thoughtful engineering and clean, efficient code.

---
---

## GitHub Stats

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=AvGeeky&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
</p>
<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=AvGeeky&theme=react-dark&hide_border=true&area=true" alt="Activity Graph" />
</p>

---

## Areas of Focus

- Backend Development & System Design  
- Applied Machine Learning & Natural Language Processing  
- Cryptography & Blockchain Concepts  
- Distributed Systems & Cloud Infrastructure (Learning)
- DevOps (Docker, Kubernetes, Jenkins, NGINX etc) (Learning)
- Competitive Programming & Algorithms  

---

## Connect with me

<a href="https://www.linkedin.com/in/saipranav-m/"><img src="https://img.shields.io/badge/LinkedIn-blue?logo=linkedin&logoColor=white" /></a>
<a href="mailto:sai.saip2005@gmail.com"><img src="https://img.shields.io/badge/Gmail-red?logo=gmail&logoColor=white" /></a>

---
# 🚀 Projects

A collection of production-grade systems, and large-scale backend applications focused on **distributed systems, real-time data processing, security, and infrastructure engineering**.

Most of these systems are **deployed in real environments**, built with an emphasis on correctness, scalability, observability, and clean system design.

I have heavily been involved with the entire system design along with participating heavuly in backend developemt :)

---

## 🚌 Real-Time Bus Tracking Platform
**Official deployment for SSN College of Engineering & Shiv Nadar University Chennai**  
*Production system serving students and faculty | 2025*

🔗 **Live System:** http://bustracker.snuchennai.edu.in/

A high-performance real-time mobility tracking backend designed to support thousands of concurrent users during peak campus commute hours.

---

# 🚀 Key Highlights

- **3,000+ concurrent users** supported during peak traffic hours
- **Sub-50ms live location propagation** from ingestion → map render
- **Redis-backed in-memory state engine** for millisecond reads
- **Hot-path isolation** removing databases from live request paths
- **Concurrent GPS ingestion** from multiple heterogeneous vendor APIs
- **Adaptive polling system** based on data freshness and load
- **Full on-premise deployment** with production observability stack

---

# 🏗 System Architecture

```text
                 +----------------------+
                 |   GPS Hardware       |
                 | (Multiple Vendors)   |
                 +----------+-----------+
                            |
                            |
                     GPS API Polling
                            |
                            v
                +-----------------------+
                |   Spring Boot Backend |
                |  (Location Processor) |
                +-----------+-----------+
                            |
                Normalize / Clean GPS Data
                            |
                            v
                 +----------------------+
                 |        Redis         |
                 | In-Memory Live State |
                 | busId → GPS location |
                 | Caches student bus   |
                 | allocation and exam/ |
                 |  breakdown overrides |
                 +----------+-----------+
                            |
             +--------------+--------------+
             |                             |
             v                             v
     +---------------+            +---------------+
     |  Mobile App   |            |  Web Client   |
     | (Students)    |            | (Tracking UI) |
     +---------------+            +---------------+

         Monitoring & Observability Layer
      Prometheus → Metrics → Grafana Dashboards
```
## Performance at Scale

The system is engineered to support **thousands of simultaneous users** during campus rush hours.

### Key Optimizations

- **Redis Sets** acting as a high-speed in-memory state engine
- **No database access in the live request path**
- **Read-heavy endpoints optimized for in-memory access**

### Performance Characteristics

- **<50ms location propagation latency**
- Smooth UI updates during **morning and evening traffic spikes**
- Stable performance during **high concurrency bursts**

---

## Smart Location Processing

Campus buses use **different GPS hardware vendors**, producing inconsistent and noisy data streams.

The **Spring Boot backend acts as a normalization layer**, responsible for:

- Aggregating GPS signals from heterogeneous vendor APIs
- Cleaning noisy or inconsistent location updates
- Smoothing position data before publishing to clients
- Converting all GPS inputs into a **single unified location format**

The backend currently exposes **~60 API endpoints** used by mobile and web applications.

---

## Designed for Rush Hour

Campus transport usage spikes dramatically during commute windows.

To handle this load, the platform uses:

- **Containerized services** for predictable deployments
- **Load-balanced API servers**
- **Hot-path optimization** eliminating database reads
- **Adaptive GPS polling intervals** to reduce unnecessary upstream requests

These techniques ensure the system remains stable even when **thousands of users open the app simultaneously**.

---

## 📊 Observability & Reliability

The system runs **entirely on university infrastructure** with full operational visibility.

### Monitoring Stack

- **Prometheus** → system and application metrics
- **Grafana** → real-time operational dashboards
- **Custom alert pipelines**

Operational alerts allow issues to be **detected and resolved within minutes**, often before users notice service disruption.

---

## System Design Decisions

### Why Redis as the Live State Store?

The application is **read-heavy**, with thousands of clients requesting the same bus locations.

Redis enables:

- **In-memory reads (microsecond latency)**
- Efficient keyed access (`busId → location`)
- High throughput during traffic spikes

Using Redis prevents the primary database from becoming a bottleneck.

---

### Why Hot-Path Isolation?

Real-time location endpoints **never touch the SQL database**.

Instead:

1. GPS updates are processed by the backend
2. Cleaned data is written to Redis
3. Client requests read directly from Redis

#### Benefits

- Eliminates disk I/O during peak load
- Ensures predictable low latency
- Prevents cascading database failures

---

### Stateless Backend Design

Backend services are designed to be **stateless**, enabling:

- Horizontal scaling via containers
- Easy rolling deployments
- Simplified fault recovery

All shared state is **externalized into Redis**.

---

## Tech Stack
## 🧰 Tech Stack

- **Java**
- **Spring Boot**
- **Redis**
- **PostgreSQL**
- **Docker**
- **NGINX**
- **Prometheus**
- **Grafana**

---

## 📌 Deployment

The platform is deployed **on-premise within university infrastructure**, providing:

- **Low-latency internal network access**
- **Full operational control over infrastructure**
- **Secure integration with campus systems**

---

## 📈 Impact

- Serves **thousands of students and faculty daily**
- Provides **real-time visibility into campus transport routes**
- Handles **large traffic spikes reliably during peak commute hours**



## 💳 kPaymentPipeline — Payment Management & Reconciliation System  
**Deployed for SSN Invente Technical Fest | 2025**

A Kafka-based real-time payment reconciliation platform built to process thousands of digital transactions with strong correctness guarantees.

### Highlights
- Event-driven reconciliation pipeline using Kafka
- Stateful stream processing with joins, aggregations, and windowing
- Redis-backed email ingestion system for payment receipt detection
- Idempotent processing to prevent duplicate reconciliation
- Load-tested at **50,000+ records per minute** using K6
- Fully containerized production deployment

### Architecture Concepts
- Kafka producers and consumers
- Kafka Streams with time-windowed joins
- Redis-backed deduplication
- Transaction reconciliation pipelines
- Observability and throughput benchmarking

**Tech Stack**  
`Java • Spring Boot • Apache Kafka • Kafka Streams • Redis • PostgreSQL • Docker • K6`

🔗 https://github.com/AvGeeky/kpaymentpipeline

---

## 🧾 AttendEz — Secure Multi-Mode Attendance Platform  
**Deployed for SSN College | 2025**

A production-grade attendance system designed to eliminate proxy marking and manual verification overhead.

### Features
- Dynamic time-rotating QR codes
- One-time attendance codes for quick sessions
- Manual mode with teacher overrides
- Cryptographic device-bound verification
- Live attendance dashboards
- On-prem deployment

### Security Model
- HMAC-based authentication using device-bound secrets
- Time-limited code expiry
- Replay attack prevention
- Redis-managed verification windows

### Architecture Concepts
- Redis for real-time verification state
- MongoDB for persistent academic records
- Time-based validation engine
- SSE-driven live updates

**Tech Stack**  
`Java • Spring Boot • Redis • MongoDB • Docker • NGINX • JUnit • Jenkins`

🔗 https://github.com/AvGeeky/AttendanceSystemBE
🔗 Demo: https://www.youtube.com/watch?v=YFHxfV337GY

---

## 🔐 SecUrVote — Cryptographically Verifiable Voting Platform

A secure digital voting system focused on voter authenticity, privacy, and transparent verification.

### Features
- RSA-based vote encryption
- HMAC-secured Magic IDs for vote uniqueness
- PBKDF2-based authentication
- OTP login flow
- Immutable blockchain-style vote ledger
- Public vote verification interface

### Architecture Concepts
- Two-phase cryptographic voting
- Anonymous ballot storage
- Tamper-evident ledger design
- Modular backend services

**Tech Stack**  
`Java • Spring Boot • MongoDB • Cryptography • Docker`

🏆 **1st Prize — Encender Project Expo (CSE Department)**

🔗  
- Website: https://securvote.vercel.app  
- Demo Video: https://youtu.be/4nAzh8N8cbA  
- About: https://securvote.vercel.app/about  

## 🎤 InterVueX — AI-Powered Smart Hiring Platform

An intelligent interview platform combining technical assessment with behavioral analysis.

### Features
- Resume- and rubric-driven question generation
- Live coding interviews via Judge0
- Face detection and audio processing
- Sentiment analysis and automated summaries

🏆 **1st Place — InnovateX National Hackathon (100+ teams)**

**Tech Stack**  
`Python • AI/ML • Judge0 • Audio Processing`

---

## 🎓 PeerLearn — Peer-to-Peer Learning Platform

A collaborative learning ecosystem focused on incentivized education.

### Features
- Gamified in-app currency system (*Stars*)
- Community-generated learning roadmaps
- Dynamic teacher–learner role switching

Built within **24 hours** during Envision SSN.

**Tech Stack**  
`Spring Boot • Web • Gamification Systems`

---

## 🧩 Other Notable Projects

- 🚆 **Railway Reservation System (C)** — Seat allocation, scheduling, and ticket workflows  
- 🧍 **Missing Persons Identification System** — Facial recognition–based detection platform (high school project)

---

---
## Programming Languages

| C | Java | Python | SQL |
|:--:|:----:|:-----:|:----:|
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" alt="C" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" alt="Java" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" alt="MySQL" height="40"/> |

## Frameworks & Libraries

| Spring | Flask | Scikit-learn |
|:------:|:-----:|:------------:|
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/spring/spring-original.svg" alt="Spring" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flask/flask-original.svg" alt="Flask" height="40"/> | <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="Scikit-learn" height="40"/> |

## Databases & Cloud

| MongoDB | PostgreSQL | Redis | Docker | AWS |
|:-------:|:----------:|:-----:|:------:|:---:|
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg" alt="MongoDB" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" alt="PostgreSQL" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/redis/redis-original.svg" alt="Redis" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" alt="Docker" height="40"/> | <img src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" alt="AWS" height="40"/> |

## Tools & Platforms

| Git | GitHub | Linux | JetBrains | MongoDB Compass | Postman | Figma | Canva |
|:---:|:------:|:-----:|:---------:|:----------------:|:-------:|:-----:|:-----:|
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git" height="40"/> | <img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" alt="GitHub" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" alt="Linux" height="40"/> | <img src="https://upload.wikimedia.org/wikipedia/commons/2/2d/JetBrains_company_logo.svg" alt="JetBrains" height="40"/> | <img src="https://upload.wikimedia.org/wikipedia/commons/9/93/MongoDB_Logo.svg" alt="MongoDB Compass" height="40"/> | <img src="https://cdn.worldvectorlogo.com/logos/postman.svg" alt="Postman" height="40"/> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt="Figma" height="40"/> | <img src="https://upload.wikimedia.org/wikipedia/en/b/bb/Canva_Logo.svg" alt="Canva" height="40"/> |


---
## Research & Publications

- **CLEF 2024 (JOKER Lab)** – Genre classification of humorous text using transformer-based and traditional ML models.  
- **ILSUM 2024** – Multilingual text summarization using advanced NLG models like T5 and Gemini 1.0 Pro.

---
<p align="center">
  <img src="https://profile-counter.glitch.me/AvGeeky/count.svg" alt="Visitor Count" />
</p>
