
# BuildLedger Development Plan

> Version 1.0 (Hackathon MVP)

---

# Project Objective

Build a fully functional civic infrastructure platform connecting:

- Community Leaders
- Sponsors / Municipalities
- Contractors

using Data Engineering and Blockchain.

---

# Architecture

frontend/
backend/
data-engineering/
blockchain/

Each module is independent and communicates through REST APIs and Kafka.

---

# Folder Structure

buildledger/

├── frontend/
│   ├── app/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── services/
│   └── types/
│
├── backend/
│   ├── api/
│   ├── routes/
│   ├── models/
│   ├── schemas/
│   ├── services/
│   ├── auth/
│   └── database/
│
├── data-engineering/
│   ├── kafka/
│   │   ├── producer.py
│   │   └── consumer.py
│   │
│   ├── etl/
│   │   ├── extract.py
│   │   ├── transform.py
│   │   └── load.py
│   │
│   └── analytics/
│       ├── kpis.py
│       ├── heatmap.py
│       └── trends.py
│
├── blockchain/
│   ├── contracts/
│   ├── scripts/
│   ├── wallet/
│   └── ipfs/
│
├── docker-compose.yml
└── README.md

---

# Frontend Responsibilities

## Community

Pages:

- Home
- Report Issue
- Track Project
- Community Dashboard

Components:

- Camera Upload
- GPS Selector
- Status Timeline
- Heatmap

---

## Contractor

Pages:

- Tender Listings
- Tender Details
- Apply
- My Applications

Components:

- Document Upload
- Tender Card
- Requirement Viewer

---

## Sponsor

Pages:

- Review Claims
- Publish Tender
- Applications
- Milestone Verification

Components:

- Approval Table
- Project Creator
- KPI Dashboard

---

# Backend Responsibilities

FastAPI provides REST endpoints.

## Community APIs

POST /reports

GET /reports/{id}

GET /projects/status

---

## Sponsor APIs

GET /claims

PATCH /claims/{id}

POST /projects

GET /applications

PATCH /applications/{id}

---

## Contractor APIs

GET /tenders

GET /tenders/{id}

POST /applications

---

## Analytics APIs

GET /analytics/kpis

GET /analytics/heatmap

GET /analytics/trends

---

# Data Engineering

## Kafka Topics

community.reports

project.created

milestone.verified

payment.released

---

## ETL Pipeline

Extract

↓

Validate

↓

Clean

↓

Assign Ward

↓

Store PostgreSQL

↓

Generate KPIs

↓

Serve Analytics API

---

# Blockchain

## Smart Contract

Functions

registerProject()

fundProject()

verifyMilestone()

releasePayment()

closeProject()

---

# Role Permissions

Community Leader

✓ Submit reports

✓ Track progress

✗ View tenders

✗ View payments

Contractor

✓ View tenders

✓ Apply

✓ Upload milestones

✗ View competing bids

Sponsor

✓ Review claims

✓ Publish tenders

✓ Award contractor

✓ Release payments

---

# Database Flow

Community

↓

reports

↓

projects

↓

tenders

↓

applications

↓

milestones

↓

blockchain escrow

---

# Day 1 Deliverables

- Database
- FastAPI
- Kafka
- ETL
- Community Report UI

Goal:

A report reaches PostgreSQL automatically.

---

# Day 2 Deliverables

- Tender Portal
- Sponsor Dashboard
- Smart Contract
- Heatmap
- KPI Dashboard
- End-to-End Demo

Goal:

A community issue becomes a funded project with milestone tracking.

issue_link = https://chatgpt.com/share/6aac05cc-9840-83ea-a631-8122b65420a6
