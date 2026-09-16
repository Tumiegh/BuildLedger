# KasiProof — MVP Blueprint

> **Tagline:** Civic transparency through Data Engineering + Blockchain

A hackathon-ready platform that empowers South African communities to report service delivery issues while creating a transparent, tamper-proof record of infrastructure projects and municipal spending.

---

# Vision

KasiProof is more than a reporting application.

It is a civic transparency platform that combines **Data Engineering** and **Blockchain** to help communities report infrastructure issues, enable municipalities to prioritise projects using real-time data, and ensure every project milestone is verifiable and accountable.

---

# The Problem

Across South Africa, communities experience daily service delivery challenges including:

- Potholes
- Water leaks
- Broken streetlights
- Illegal dumping
- Incomplete infrastructure projects

Although municipalities allocate significant budgets to infrastructure, residents and sponsors often have little visibility into where funds go or whether projects are progressing as promised.

### Core Problem

> Citizens know the problems, but they rarely know what happens after reporting them.

---

# Our Solution

KasiProof bridges the gap between **community reporting** and **transparent infrastructure delivery**.

The platform allows citizens to report issues using GPS and photos, processes those reports through a data engineering pipeline, identifies infrastructure hotspots, and records verified project milestones on the blockchain.

### Data Engineering

- Citizen report ingestion
- ETL pipeline
- PostgreSQL analytics database
- Heatmap generation
- Municipality KPI dashboard

### Blockchain

- Immutable report hashes
- Timestamp verification
- Smart contract milestone tracking
- Wallet authentication
- IPFS evidence storage

---

# Unique Value Proposition

**Transparent infrastructure funding from community report to verified project completion.**

Unlike traditional reporting apps, KasiProof provides both **real-time analytics** and **blockchain accountability** in one platform.

---

# System Architecture

```text
Citizen (Web/Mobile)
        │
        ▼
 GPS + Photo + Description
        │
        ▼
     FastAPI Backend
        │
        ▼
 Kafka Event Stream
        │
        ▼
 Python ETL Pipeline
        │
        ▼
 PostgreSQL Analytics
        │
 ┌──────┴────────┐
 ▼               ▼
Heatmaps     KPI Dashboard
        │
        ▼
 Smart Contract (Polygon)
        │
        ▼
 IPFS Evidence Storage
```

---

# User Journey

## Step 1
A citizen discovers a pothole and submits a report with a photo and GPS location.

## Step 2
The backend validates the report and publishes it to Kafka.

## Step 3
The ETL pipeline cleans and enriches the data before storing it in PostgreSQL.

## Step 4
The dashboard immediately updates the ward's infrastructure heatmap.

## Step 5
The municipality approves a repair project.

## Step 6
The contractor uploads milestone evidence to IPFS.

## Step 7
The smart contract verifies the milestone and records it permanently.

## Step 8
The community can track project progress and verify completion.

---

# MVP Features

## Citizen

- Report infrastructure issue
- Capture GPS location
- Upload photo
- Track report status
- View nearby issues

## Municipality

- View reports
- Prioritise hotspots
- Create projects
- Verify milestones
- Update project status

## Public Dashboard

- Live heatmap
- Project progress
- Budget transparency
- Response-time analytics

---

# Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React, Next.js, TypeScript |
| Backend | FastAPI |
| Data Engineering | Python, Kafka, PostgreSQL |
| Blockchain | Solidity, Polygon |
| Storage | IPFS |
| DevOps | Docker, GitHub |

---

# Database Design

## reports

| Field | Type |
|---|---|
| report_id | UUID |
| category | String |
| description | Text |
| latitude | Decimal |
| longitude | Decimal |
| image_url | String |
| ward | String |
| created_at | Timestamp |
| blockchain_hash | String |

## projects

| Field | Type |
|---|---|
| project_id | UUID |
| ward | String |
| budget | Decimal |
| contractor | String |
| status | String |

## milestones

| Field | Type |
|---|---|
| milestone_id | UUID |
| project_id | UUID |
| title | String |
| verified | Boolean |
| ipfs_hash | String |

---

# ETL Pipeline

## Extract

Receive reports through FastAPI and Kafka.

## Transform

- Validate coordinates
- Remove duplicate reports
- Categorise infrastructure issue
- Assign municipal ward
- Generate quality score

## Load

Store cleaned data inside PostgreSQL for analytics and dashboards.

---

# Analytics Dashboard

## KPI Cards

- Total reports
- Active issues
- Completed projects
- Average response time
- Service delivery score

## Heatmaps

- Pothole density
- Water leak hotspots
- Streetlight failures
- Illegal dumping clusters

## Predictive Insights

- Which ward has the highest recurring issues?
- Monthly infrastructure trend
- Municipality response performance
- Priority repair recommendations

---

# Blockchain Layer

## Smart Contract Responsibilities

- Register project
- Lock project budget
- Store milestone hashes
- Verify completion
- Release milestone payment

## Why Polygon?

- Low transaction fees
- Fast confirmations
- Ethereum compatibility
- Suitable for MVP deployment

---

# Folder Structure (TBD)

```text
kasiproof/

├── frontend/
│   ├── app/
│   ├── components/
│   └── pages/
│
├── backend/
│   ├── api/
│   ├── routes/
│   ├── models/
│   └── services/
│
├── data-engineering/
│   ├── kafka/
│   ├── etl/
│   ├── analytics/
│   └── dashboards/
│
├── blockchain/
│   ├── contracts/
│   ├── scripts/
│   └── ipfs/
│
├── docker-compose.yml
└── README.md
```

---

# Hackathon Development Roadmap (TBD)

## Before the Hackathon

### Planning

- [ ] Create GitHub repository
- [ ] Set up project structure
- [ ] Design database schema
- [ ] Create Figma wireframes
- [ ] Define REST API endpoints

### Environment

- [ ] Docker Compose
- [ ] PostgreSQL container
- [ ] Kafka container
- [ ] FastAPI starter
- [ ] Polygon test wallet

---

## Day 1 (Backend + Data)

### Data Engineering

- [ ] Report API
- [ ] Kafka producer
- [ ] ETL consumer
- [ ] PostgreSQL models
- [ ] Analytics endpoints

### Frontend

- [ ] Report form
- [ ] Map integration
- [ ] Dashboard layout

---

## Day 2 (Blockchain + Integration)

### Blockchain

- [ ] Smart contract
- [ ] WalletConnect
- [ ] Report hashing
- [ ] Milestone verification

### Final Integration

- [ ] Heatmap
- [ ] KPI dashboard
- [ ] QR verification
- [ ] Demo scenario

---

# Business Model

## Customer Segments

- Municipalities
- NGOs
- Infrastructure sponsors
- Community organisations

## Revenue Streams

- Municipal SaaS subscription
- Sponsor monitoring platform
- Infrastructure analytics reports
- Enterprise transparency dashboard

## Cost Structure

- Cloud hosting
- Polygon gas fees
- IPFS storage
- Database hosting
- Maintenance

---

# Technology Readiness Level

**TRL 3 — Experimental Proof of Concept**

- Problem validated
- Architecture designed
- Database model completed
- Smart contract workflow defined
- ETL pipeline specified
- Ready for MVP implementation during the hackathon

---

# Security Considerations

### Risk Assessment

- Prevent fraudulent reports
- Protect project funds
- Prevent data tampering
- Verify milestone authenticity

### Secure Development

- JWT authentication
- Role-based access control
- Parameterised SQL
- Environment variables
- Smart contract verification

---

# Winning Factors

KasiProof stands out because it combines:

- Community-generated infrastructure data
- Real-time ETL analytics
- Blockchain transparency
- Verifiable project milestones
- Evidence-based municipal decision making

This is not simply a reporting app—it is a **civic infrastructure intelligence platform** designed for South African communities.