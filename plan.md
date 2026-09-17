
# BuildLedger MVP Blueprint

> **Tagline:** Transparent Infrastructure. Verified Progress. Trusted Payments.

BuildLedger is a civic infrastructure platform that connects **Community Leaders**, **Municipal Sponsors**, and **Contractors** through Data Engineering and Blockchain. The platform separates public project transparency from financial contract management, ensuring every stakeholder only sees the information relevant to their role.

---

# Vision

BuildLedger enables communities to report infrastructure problems, municipalities to publish verified tenders, contractors to compete fairly for projects, and sponsors to release funding transparently through blockchain milestone payments.

Our goal is to make every infrastructure project **traceable from the first community report to the final completed milestone**.

---

# The Three Sectors

## 1. Street Committee / Community Leader

The community leader is responsible only for identifying infrastructure problems.

### Responsibilities

- Capture GPS location
- Upload photo evidence
- Describe the issue
- Track project progress
- View project stages

### Visible Project Stages

- Claim Submitted
- Under Review
- Accepted
- Project Started
- Milestone Progress
- Completed

> **Important:** Community leaders never see contractor negotiations, tender applications, budgets, or payment information.

---

## 2. Tenders / Contractors

Once an issue is approved, it becomes a public tender opportunity.

### Contractors can:

- Browse available projects
- View reference number
- Release & closing dates
- Project requirements
- Municipality contact details
- Download tender documents
- Upload completed application documents

After submission, the application is sent directly to the sponsor for review.

---

## 3. Sponsors / Municipality

Sponsors manage procurement and funding.

### Responsibilities

- Review community reports
- Approve issues as projects
- Publish tenders
- Review contractor applications
- Select successful contractor
- Approve milestone verification
- Release blockchain payments

Sponsors communicate privately with contractors after approval.

The community dashboard only reflects project progress—not financial decisions.

---

# Problem Statement

Communities report infrastructure failures, but they rarely know:

- whether the issue was accepted,
- who received the contract,
- whether work is progressing,
- or whether public funds produced real results.

BuildLedger separates **public transparency** from **financial governance** while keeping every milestone verifiable.

---

# Solution Architecture

```text
             COMMUNITY LEADER

   GPS + Photo + Description
               │
               ▼
        FastAPI Backend
               │
               ▼
      Kafka Event Streaming
               │
               ▼
      Python ETL Processing
               │
               ▼
 PostgreSQL Operational Database
               │
      Issue Approved
               │
               ▼
      Tender / Project Created
               │
        Contractors Apply
               │
               ▼
 Sponsor Reviews Applications
               │
      Contractor Approved
               │
               ▼
 Smart Contract Escrow Wallet
               │
     Milestone Verification
               │
               ▼
 Chunked Blockchain Payments
               │
               ▼
 Community Progress Dashboard
```

---

# User Journey

## Stage 1 — Report

A Street Committee leader photographs a pothole using GPS and submits a description.

Status:

- Claim Submitted

---

## Stage 2 — Review

Municipality reviews the evidence.

Possible outcomes:

- Rejected
- Accepted

If accepted, the issue becomes an official infrastructure project.

---

## Stage 3 — Tender Publication

A project listing is automatically created containing:

- Reference Number
- Category
- Ward
- Municipality
- Release Date
- Closing Date
- Required Documents
- Sponsor Contact Details

Contractors can now apply.

---

## Stage 4 — Contractor Application

The contractor uploads:

- Company registration
- Tax compliance
- CIDB documentation
- Quotation / Proposal
- Supporting documents

The complete application is sent directly to the Sponsor.

---

## Stage 5 — Award

The sponsor privately notifies the successful contractor.

This communication is **not visible** to the community.

---

## Stage 6 — Blockchain Funding

The sponsor releases project funds into the BuildLedger smart contract.

### Payment Rule

- 15% platform fee deducted once
- 85% placed into project escrow
- Remaining funds released by milestones

Example:

Project Value: R1,000,000

- BuildLedger: R150,000 (15%)
- Escrow: R850,000

Escrow releases only after verified milestones.

---

## Stage 7 — Milestone Tracking

Contractor uploads evidence:

- Images
- Documents
- GPS verification
- Completion notes

Evidence stored in IPFS.

The ETL pipeline updates project analytics while the smart contract records verification.

---

## Stage 8 — Community Transparency

Residents see:

- Current project stage
- Percentage completed
- Latest milestone
- Expected completion date
- Before & after evidence

Residents never see:

- Contractor payments
- Bid amounts
- Tender scoring
- Financial negotiations

---

# MVP Features

## Community Module

- Report issue
- GPS capture
- Photo upload
- Description
- Track project status
- View nearby projects

---

## Tender Module

- Browse available tenders
- Search by category
- View project details
- Download tender documents
- Upload application
- Submit proposal

---

## Sponsor Module

- Review claims
- Approve / reject issues
- Publish tenders
- Review contractor applications
- Award contracts
- Verify milestones
- Release payments

---

## Public Dashboard

- Live project map
- Heatmap of issues
- KPI analytics
- Progress timeline
- Response time statistics

---

# Technology Stack

| Layer | Technology |
|--------|------------|
| Frontend | Next.js + React |
| Backend | FastAPI |
| Streaming | Apache Kafka |
| ETL | Python |
| Database | PostgreSQL |
| Blockchain | Solidity + Polygon |
| Storage | IPFS |
| DevOps | Docker |

---

# Database Schema

## reports

| Field | Type |
|--------|------|
| report_id | UUID |
| category | TEXT |
| description | TEXT |
| latitude | DECIMAL |
| longitude | DECIMAL |
| ward | TEXT |
| image_url | TEXT |
| status | TEXT |
| created_at | TIMESTAMP |

---

## projects

| Field | Type |
|--------|------|
| project_id | UUID |
| report_id | UUID |
| reference_number | TEXT |
| municipality | TEXT |
| category | TEXT |
| release_date | DATE |
| closing_date | DATE |
| status | TEXT |

---

## tenders

| Field | Type |
|--------|------|
| tender_id | UUID |
| project_id | UUID |
| contractor | TEXT |
| proposal_url | TEXT |
| status | TEXT |

---

## milestones

| Field | Type |
|--------|------|
| milestone_id | UUID |
| project_id | UUID |
| percentage | INTEGER |
| ipfs_hash | TEXT |
| verified | BOOLEAN |

---

# Analytics KPIs

| KPI | Description |
|------|-------------|
| Total Reports | Community issues submitted |
| Accepted Claims | Approved infrastructure issues |
| Active Projects | Projects currently running |
| Completed Projects | Finished infrastructure projects |
| Avg Response Time | Days from report to review |
| Avg Completion Time | Days from start to completion |

---

# Heatmap Analytics

The ETL pipeline generates geospatial hotspots for:

- Potholes
- Water leaks
- Electricity faults
- Road damage
- Illegal dumping

The frontend consumes these coordinates to render a live heatmap.

---

# Blockchain Responsibilities

## Smart Contract

- Create project escrow
- Deduct 15% platform fee
- Lock remaining funds
- Verify milestone hash
- Release milestone payment
- Record immutable audit trail

---

# Security Model

## Community

Can only access:

- Reports
- Project stages
- Dashboard

## Contractors

Can access:

- Tenders
- Applications
- Own submissions

## Sponsors

Can access:

- Applications
- Contractor selection
- Budget management
- Payment approval

Role-based access control ensures complete separation of responsibilities.

---

# Hackathon MVP Roadmap

## Day 1

### Data Engineering

- Citizen Report API
- PostgreSQL schema
- Kafka Producer
- Kafka Consumer
- ETL Pipeline

### Frontend

- Report page
- Map
- Project tracker

---

## Day 2

### Blockchain

- Smart Contract
- Escrow payments
- IPFS upload
- Milestone verification

### Integration

- Heatmap
- KPI Dashboard
- End-to-end demo

---

# GitHub Issue Backlog

## EPIC 1 — Data Engineering

### Issue #1 — Create PostgreSQL Schema

**Label:** data

Create reports, projects, tenders and milestones tables.

---

### Issue #2 — Citizen Report API

**Label:** data

Build FastAPI endpoint for GPS/photo issue submission.

---

### Issue #3 — Kafka Producer

**Label:** data

Publish every new report to the `community.reports` topic.

---

### Issue #4 — ETL Consumer

**Label:** data

Consume Kafka events, validate coordinates, assign wards and store cleaned data.

---

### Issue #5 — Heatmap Analytics API

**Label:** data

Return clustered geolocation data for frontend visualization.

---

### Issue #6 — KPI Analytics API

**Label:** data

Generate Total Reports, Active Projects and Response Time metrics.

---

## EPIC 2 — Community

### Issue #7 — Community Reporting Page

**Label:** frontend

Build issue submission UI with GPS and photo upload.

---

### Issue #8 — Community Project Tracker

**Label:** frontend

Display only project stages from Claim to Completed.

---

## EPIC 3 — Tenders

### Issue #9 — Tender Listing Page

**Label:** frontend

Display all approved projects available for contractors.

---

### Issue #10 — Tender Details

**Label:** frontend

Show reference number, dates, requirements and downloadable documents.

---

### Issue #11 — Contractor Application Upload

**Label:** frontend

Allow document upload and tender submission.

---

## EPIC 4 — Sponsor Portal

### Issue #12 — Review Community Claims

**Label:** data

Approve or reject submitted infrastructure issues.

---

### Issue #13 — Publish Project Tender

**Label:** data

Convert accepted reports into public tender listings.

---

### Issue #14 — Review Contractor Applications

**Label:** data

Accept uploaded documents and manage application status.

---

## EPIC 5 — Blockchain

### Issue #15 — Escrow Smart Contract

**Label:** blockchain

Lock project funds and deduct 15% platform fee.

---

### Issue #16 — Milestone Verification

**Label:** blockchain

Store IPFS hashes and verify milestone completion.

---

### Issue #17 — Chunked Payment Release

**Label:** blockchain

Release escrow funds according to verified project milestones.

---

## EPIC 6 — Final Integration

### Issue #18 — Live Dashboard

**Labels:** data, frontend

Connect KPIs and Heatmap to the React dashboard.

---

### Issue #19 — End-to-End Demo

**Labels:** integration

Demonstrate the complete workflow from community report to blockchain milestone payment.

---

# Technology Readiness

**TRL 3 – Proof of Concept**

- Community reporting defined
- Tender workflow defined
- Data pipeline specified
- Blockchain escrow model specified
- Role-based architecture completed
- Ready for hackathon MVP implementation
