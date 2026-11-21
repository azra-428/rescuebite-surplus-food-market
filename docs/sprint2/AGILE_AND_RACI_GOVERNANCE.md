# SENG 321 / BM321 Software Engineering Project
# Sprint 2 Agile Process Governance, RACI Matrix & Traceability Report

**Project Name:** Neighborhood Surplus Food Market (*RescueBite*)  
**Team Number:** Team 13  
**Academic Term:** 2025-2026 Academic Year | Sprint 2  
**Submission Deadline:** November 24, 2026  
**Prepared By:** **Anıl Güngör (220205003)** — *Scrum Master and Agile Process Coach* (`@anlgr`)  
**GitHub Repository:** `https://github.com/macig102/rescuebite-surplus-food-market`  
**Target Release Tag:** `v0.2.0-sprint2` (building on `v0.1.0-sprint1`)  

---

## 1. Team Information & Sprint 2 Role Responsibilities

In accordance with the **BM321 Software Engineering Semester Team Project Specification and Assessment Rubric**, each member of **Team 13** holds an explicit, named role with verifiable Sprint 2 deliverables:

| Student ID | Full Name | GitHub Account | Official Role Title (BM321 Rubric) | Sprint 2 Primary Responsibility & Assigned Deliverables |
|---|---|---|---|---|
| **230203005** | **Zeynep Bozdemir** | `@zeynepbozdemirrr` | **Product Owner and Requirements Engineer** | Authored the Detailed Software Requirements Specification (SRS), formal functional requirements (`FR-01`–`FR-16`), domain business rules (`BR-01`–`BR-08`), stakeholder validation criteria, and led Product Backlog refinement. |
| **220201035** | **Mehmet Kocagöz** | `@mehmetkocagozz` | **Lead Software Architect and Technical Lead** | Designed the Software Architecture Documentation, C4 Model hierarchy (Level 1 Context, Level 2 Container, Level 3 Component, Level 4 Code/Entity), UML Class, Sequence, State Machine, and Use-Case diagrams, and concurrency architecture. |
| **220205003** | **Anıl Güngör** | `@anlgr` | **Scrum Master and Agile Process Coach** | Authored the Sprint 2 RACI Responsibility Matrix, facilitated Sprint 1 Retrospective & Sprint 2 Stand-ups, managed the Impediment Tracking Log, administered the GitHub Projects Kanban board, co-refined the Product Backlog, and compiled the Submission Traceability Matrix. |
| **230201047** | **Tuğçe Ertem** | `@tugceertem` | **Quality Assurance and Test Automation Engineer** | Specified the Non-Functional Requirements (`NFR-PERF`, `NFR-CONC`, `NFR-SEC`, `NFR-REL`, `NFR-USA`, `NFR-MAINT`, `NFR-COMP`), ISO/IEC 25010 Quality-Measure Specifications, Quality Attribute Scenarios, and performed the Sprint 2 Rubric Quality Audit. |
| **230204031** | **Azra Dostbil** | `@azradostbil` | **DevOps and CI/CD Infrastructure Engineer** | Enforced Lightweight Git-Flow branch protection rules, audited PR and Issue template compliance, specified deployment/container infrastructure NFR metrics, and managed the `v0.2.0-sprint2` release tagging workflow. |
| **230201009** | **Muhammed Fatih Ağaç** | `@macig102` | **Implementation and Integration Engineer** | Designed the Figma UI/UX interactive prototypes (`SCR-01`–`SCR-12`), authored actor User-Flow Diagrams (Customer, Store, Courier, Admin), and aligned UI screen components with OpenAPI 3.1.0 payloads and SRS requirements. |

---

## 2. Sprint 2 RACI Responsibility Matrix

* **R (Responsible):** The team member(s) who execute the hands-on engineering, modeling, or documentation work to produce the deliverable.
* **A (Accountable):** The single designated role owner with final decision and sign-off authority for the deliverable's rubric compliance.
* **C (Consulted):** Domain contributors who provide technical review, boundary validation, and domain input prior to merge.
* **I (Informed):** Team members kept updated on deliverable completion, architectural decisions, and branch merges.

| Sprint 2 Assessed Deliverable / Activity | Product Owner<br>(Zeynep Bozdemir) | Lead Architect<br>(Mehmet Kocagöz) | Scrum Master<br>(Anıl Güngör) | QA Engineer<br>(Tuğçe Ertem) | DevOps Engineer<br>(Azra Dostbil) | Implementation Eng.<br>(M. Fatih Ağaç) |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **1. Detailed Functional SRS (`FR-01`..`FR-16`) & Domain Rules** | **A** | C | I | C | I | R |
| **2. Refined Product Backlog, Velocity & Traceability Matrix** | **A** | C | R | R | I | R |
| **3. Non-Functional Requirements (NFR) & Quality-Measure Specs** | C | C | I | **A** | R | R |
| **4. UI/UX Prototypes (Figma) & Actor User-Flow Diagrams** | C | C | I | C | I | **A** / R |
| **5. Software Architecture & C4 Models (Level 1 – Level 4)** | C | **A** | I | C | C | R |
| **6. UML Diagrams (Use-Case, Class, Sequence, State Machine)** | C | **A** | I | R | I | R |
| **7. Sprint 2 Agile Board, RACI Matrix & Ceremony Records** | I | C | **A** | C | R | I |
| **8. Git-Flow Governance, PR Audit & `v0.2.0-sprint2` Release** | I | C | C | C | **A** | R |
| **9. Sprint 2 Rubric Compliance & Submission Evidence Audit** | C | R | R | **A** | R | R |

### RACI Governance Rules Enforced in Sprint 2
1. **Single Point of Accountability (`A`):** Every Sprint 2 requirement from the BM321 assignment announcement has exactly one accountable lead responsible for final approval before merging into `develop`.
2. **Mandatory Cross-Role Peer Review:** Every Pull Request opened by a Responsible (`R`) author must be reviewed and approved by the Accountable (`A`) lead or a designated Consulted (`C`) reviewer on GitHub.
3. **Traceable Individual Commits:** Each deliverable is committed under the responsible team member's personal GitHub account on an isolated `feature/<issue-id>-<short-name>` branch.

---

## 3. Agile Process Records: Retrospective, Stand-ups & Impediment Log

### 3.1 Sprint 1 Retrospective Summary (Transition to Sprint 2)
* **Date Conducted:** November 10, 2026  
* **Facilitator:** Anıl Güngör (Scrum Master)  
* **Participants:** All 6 members of Team 13  

| Retrospective Category | Team Observations & Findings | Concrete Action Item for Sprint 2 | Owner | Status |
|---|---|---|---|---|
| **What Went Well (Continue)** | Defining the OpenAPI 3.1.0 specification (`api/openapi.yaml`) and HTTP 409 concurrency error catalog in Sprint 1 eliminated ambiguity around listing vs. item quantities and doorstep QR handovers. | Use `api/openapi.yaml` schemas directly as the single source of truth for SRS functional requirements, UML Class attributes, and Figma UI form fields. | Mehmet Kocagöz & Zeynep Bozdemir | Completed |
| **What Needs Improvement (Improve)** | In Sprint 1, backlog stories (`US-01`..`US-08`) lacked explicit cross-references to individual UI screens and formal non-functional SLA metrics. | Introduce a formal **End-to-End Traceability Matrix** linking `FR-ID` $\leftrightarrow$ `US-ID` $\leftrightarrow$ `OpenAPI Operation` $\leftrightarrow$ `Figma Screen ID` $\leftrightarrow$ `UML Diagram`. | Anıl Güngör & Zeynep Bozdemir | Completed |
| **What to Stop (Stop)** | Avoid bundling large documentation updates into a single commit near the deadline, which makes individual contribution verification harder. | Split Sprint 2 documentation and diagrams into modular issues and feature branches (`feature/#10` through `feature/#16`) so each member merges via distinct PRs. | Anıl Güngör & Azra Dostbil | Completed |

---

### 3.2 Sprint 2 Ceremony & Stand-up Log

| Ceremony / Stand-up | Date & Duration | Facilitator / Attendees | Key Progress, Sync Points & Decisions |
|---|---|---|---|
| **Sprint 2 Planning & Backlog Refinement** | Nov 11, 2026 (45 min) | Anıl Güngör (6/6 present) | Decomposed Sprint 2 deliverables into 7 primary GitHub Issues (`#10`–`#16`) and 22 sub-tasks totaling **24 Story Points**. Updated RACI assignments for SRS, NFR, Figma, C4/UML, and Agile Governance. |
| **Stand-up #1 (Requirements & UI Flow Sync)** | Nov 14, 2026 (15 min) | Anıl Güngör (6/6 present) | Zeynep finalized `FR-01`..`FR-16` and business rules `BR-01`..`BR-08`. Fatih aligned the 4 actor User-Flow diagrams with the exact HTTP 403 and HTTP 409 branch paths. |
| **Stand-up #2 (Architecture & NFR Sync)** | Nov 17, 2026 (15 min) | Anıl Güngör (6/6 present) | Mehmet presented C4 Level 1–3 diagrams and optimistic locking sequence diagram. Tuğçe aligned `NFR-CONC-01` and `NFR-PERF-01` latency thresholds ($p_{95} \le 250\text{ ms}$) with the C4 Container design. |
| **Stand-up #3 (Figma Prototype & UML Verification)** | Nov 20, 2026 (15 min) | Anıl Güngör (6/6 present) | Completed walkthrough of 12 Figma screens (`SCR-01`–`SCR-12`). Verified that `availableListingQuantity` vs. `items[].quantity` separation is visually explicit on customer cards and merchant creation screens. |
| **Sprint 2 Review & Pre-Submission Audit** | Nov 22, 2026 (30 min) | Anıl Güngör & Tuğçe Ertem (6/6 present) | Audited all Sprint 2 deliverables against the BM321 Microsoft Teams announcement checklist. Verified PR links, issue closures, and `v0.2.0-sprint2` release readiness. |

---

### 3.3 Sprint 2 Impediment Tracking Log

| Impediment ID | Date Raised | Affected Deliverable / Story | Description of Impediment / Blocker | Resolution Action Taken | Owner | Status |
| :---: | :---: | --- | --- | --- | --- | :---: |
| **IMP-01** | Nov 13, 2026 | SRS & UI/UX (`US-02`, `US-04`) | Potential user confusion in wireframes between **bundle stock count** (`availableListingQuantity`) and **item portion count inside a bundle** (`items[].quantity`). | Added explicit UI badge convention in Figma (`"5 Bundles Left"` vs. `"Inside Each Bundle: 2x Sourdough Loaf, 3x Croissant"`) and codified `BR-02` in SRS. | M. Fatih Ağaç & Zeynep Bozdemir | **Resolved** |
| **IMP-02** | Nov 15, 2026 | UML Sequence & Concurrency NFR (`US-04`, `US-06`) | Modeling simultaneous checkout and courier claim race conditions without introducing distributed lock latency. | Standardized on database-level **Optimistic Concurrency Control (`version` column)** in `SurplusFoodListing` and atomic `WHERE status = 'READY_FOR_COURIER'` update in `Order`. | Mehmet Kocagöz | **Resolved** |
| **IMP-03** | Nov 16, 2026 | Doorstep QR Security (`US-05`, `US-07`) | Static QR codes could be screenshotted or replayed outside the delivery window. | Specified HMAC-SHA256 signed single-use `deliveryQrToken` bound to `orderId`, `nonce`, and `deliveryEnd` timestamp, returning `409 INVALID_QR_VERIFICATION` or `409 EXPIRED_DELIVERY_WINDOW`. | Mehmet Kocagöz & Tuğçe Ertem | **Resolved** |
| **IMP-04** | Nov 18, 2026 | GitHub Contribution Traceability | Parallel editing of `SPRINT2_REPORT.md` by 6 members risked merge conflicts on `develop`. | Modularized Sprint 2 work into distinct feature branches and separate section commits, coordinated via Anıl's Kanban board sequence. | Anıl Güngör & Azra Dostbil | **Resolved** |

---

## 4. Refined Product Backlog & Sprint 2 Kanban Administration

### 4.1 Backlog Refinement Summary (Sprint 1 $\rightarrow$ Sprint 2 Evolution)
During Sprint 2 Backlog Refinement led by **Zeynep Bozdemir (PO)** and **Anıl Güngör (Scrum Master)**, the initial 8 user stories (`US-01`–`US-08`, 22 SP total) were refined and expanded with **4 additional architectural/UX/quality stories (`US-09`–`US-12`)** and linked directly to formal SRS IDs (`FR-01`–`FR-16`), Figma prototype screens (`SCR-01`–`SCR-12`), and C4/UML design artifacts:

| Priority | Epic ID | Story ID | Refined User Story Title | SRS Ref | Figma Screens | UML / C4 Artifact | SP | Owner | Sprint 2 Design & Spec Status |
|:---:|:---:|:---:|---|---|---|---|---:|---|:---:|
| **1** | `EPIC-01` | **US-01** | Platform Admin Merchant Hygiene Verification | `FR-01`, `FR-02` | `SCR-11`, `SCR-12` | UC-01, Seq-Admin, Class (`Store`) | **3** | Mehmet Kocagöz | **Spec & Design Complete** |
| **2** | `EPIC-02` | **US-02** | Approved Store Transparent Surplus Listing Creation | `FR-03`, `FR-04` | `SCR-06`, `SCR-07` | UC-02, State-Listing, Class (`SurplusFoodListing`, `ListingItem`) | **3** | Mehmet Kocagöz | **Spec & Design Complete** |
| **3** | `EPIC-02` | **US-03** | Customer Proximity, Category & Dietary Discovery | `FR-05`, `FR-06` | `SCR-01`, `SCR-02` | UC-03, C4-L3 (`DiscoveryService`) | **3** | M. Fatih Ağaç | **Spec & Design Complete** |
| **4** | `EPIC-03` | **US-04** | Concurrency-Safe Checkout & HTTP 409 Stock Lock | `FR-07`, `FR-08` | `SCR-03`, `SCR-04` | UC-04, **UML Seq-01 (409 Checkout)** | **3** | Mehmet Kocagöz | **Spec & Design Complete** |
| **5** | `EPIC-03` | **US-05** | Store Order Prep Lifecycle & Customer Dynamic QR | `FR-09`, `FR-10` | `SCR-05`, `SCR-08` | UC-05, **UML State-Order** | **2** | M. Fatih Ağaç | **Spec & Design Complete** |
| **6** | `EPIC-04` | **US-06** | Courier Available Delivery Pool & Atomic Claim (409) | `FR-11`, `FR-12` | `SCR-09` | UC-06, **UML Seq-02 (409 Claim)** | **3** | Mehmet Kocagöz | **Spec & Design Complete** |
| **7** | `EPIC-04` | **US-07** | Doorstep Dynamic QR Proof-of-Delivery Verification | `FR-13`, `FR-14` | `SCR-10` | UC-07, **UML Seq-02 (QR Verify)** | **3** | Tuğçe Ertem | **Spec & Design Complete** |
| **8** | `EPIC-05` | **US-08** | Delivered-Only Cumulative Food Waste Rescued Metrics | `FR-15`, `FR-16` | `SCR-01`, `SCR-12` | UC-08, C4-L3 (`MetricsAggregator`) | **2** | Zeynep Bozdemir | **Spec & Design Complete** |
| **9** | `EPIC-06` | **US-09** | Non-Functional Quality Measures & SLA Verification Suite | `NFR-01`..`NFR-15` | All Screens | ISO/IEC 25010 Scenarios | **2** | Tuğçe Ertem | **Completed (Sprint 2)** |
| **10** | `EPIC-06` | **US-10** | Interactive Figma UI/UX Prototype & Actor User-Flows | `FR-01`..`FR-16` | `SCR-01`..`SCR-12` | 4 Actor User-Flow Diagrams | **3** | M. Fatih Ağaç | **Completed (Sprint 2)** |
| **11** | `EPIC-06` | **US-11** | C4 Software Architecture & UML Modeling Suite | All FRs & NFRs | — | C4 (L1–L4) & UML (UC, Class, Seq, State) | **3** | Mehmet Kocagöz | **Completed (Sprint 2)** |
| **12** | `EPIC-06` | **US-12** | Sprint 2 Agile Governance, RACI & Release Packaging | Rubric Governance | — | RACI, Kanban, `v0.2.0-sprint2` | **2** | Anıl Güngör & Azra Dostbil | **Completed (Sprint 2)** |

---

### 4.2 GitHub Projects Kanban Board Snapshot (Sprint 2)

```text
┌──────────────────────────┬──────────────────────────┬──────────────────────────┬──────────────────────────┐
│   SPRINT 3 BACKLOG       │   SPRINT 2 IN REVIEW     │   SPRINT 2 VERIFIED      │      SPRINT 2 DONE       │
│  (Implementation Phase)  │    (Peer Review & QA)    │   (Merged to develop)    │   (Tagged v0.2.0-sprint2)│
├──────────────────────────┼──────────────────────────┼──────────────────────────┼──────────────────────────┤
│ [T-01.1..T-04.2]         │ [Issue #16] Release      │ [Issue #10] Detailed SRS │ [Issue #14] Figma UI/UX  │
│ Backend REST Controllers │ Packaging v0.2.0-sprint2 │ & Refined Backlog        │ & 4 User-Flow Diagrams   │
│ & Optimistic Lock DB     │ (Azra Dostbil)           │ (Zeynep Bozdemir)        │ (Muhammed Fatih Ağaç)    │
│ (Mehmet Kocagöz)         │                          │                          │                          │
│                          │ [Issue #15] Rubric Audit │ [Issue #11] NFR & Quality│ [Issue #13] C4 Models &  │
│ [T-01.3..T-08.2]         │ & Submission Checklist   │ Measure Specifications   │ UML Diagrams Suite       │
│ Frontend React/Mobile UI │ (Tuğçe E. & Anıl G.)     │ (Tuğçe Ertem)            │ (Mehmet Kocagöz)         │
│ Integration (M. Fatih A.)│                          │                          │                          │
│                          │                          │ [Issue #12] Sprint 2 RACI│ [Sprint 1 Foundation]    │
│ [QA-AUTO-01]             │                          │ & Agile Governance       │ OpenAPI 3.1.0 & Proposal │
│ ≥50% Unit & 409 Contract │                          │ (Anıl Güngör)            │ (v0.1.0-sprint1)         │
│ Test Suite (Tuğçe Ertem) │                          │                          │                          │
└──────────────────────────┴──────────────────────────┴──────────────────────────┴──────────────────────────┘
```

---

## 5. GitHub Issues, Pull Requests & Artifacts Traceability Matrix

To satisfy the **Sprint 2 Submission Requirements** (*"Links to relevant GitHub Issues, Pull Requests, technical documentation, diagrams, and other applicable project artifacts"*), the following table maps every Sprint 2 work package to its owner, GitHub Issue, Pull Request branch, and repository file link:

| Issue / Work Package | Assigned Owner (GitHub) | Feature Branch Name | Pull Request Target | Primary Deliverable / Artifact Links |
|---|---|---|---|---|
| **Issue #10:** Detailed SRS & Refined Product Backlog | **Zeynep Bozdemir** (`@zeynepbozdemirrr`) | `feature/10-srs-refined-backlog` | PR #17 $\rightarrow$ `develop` | [`docs/sprint2/SPRINT2_REPORT.md` (§1: Detailed SRS & Refined Backlog)](SPRINT2_REPORT.md#1-detailed-software-requirements-specification-srs--refined-product-backlog) |
| **Issue #11:** Non-Functional Requirements & Quality Measures | **Tuğçe Ertem** (`@tugceertem`) | `feature/11-nfr-quality-measures` | PR #18 $\rightarrow$ `develop` | [`docs/sprint2/SPRINT2_REPORT.md` (§2: NFR & Quality-Measure Specs)](SPRINT2_REPORT.md#2-non-functional-requirements-nfr--quality-measure-specifications) |
| **Issue #12 (`SCRUM-02`):** Sprint 2 RACI Matrix, Agile Board & Refined Backlog | **Anıl Güngör** (`@anlgr`) | `feature/SCRUM-02-sprint2-agile-backlog` | PR $\rightarrow$ `develope` / `main` | [`docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md`](AGILE_AND_RACI_GOVERNANCE.md) & [`CONTRIBUTIONS.md`](../../CONTRIBUTIONS.md) |
| **Issue #13:** Software Architecture, C4 Models & UML Diagrams | **Mehmet Kocagöz** (`@mehmetkocagozz`) | `feature/13-c4-uml-architecture` | PR #20 $\rightarrow$ `develop` | [`docs/sprint2/SPRINT2_REPORT.md` (§4: Software Architecture, C4 & UML)](SPRINT2_REPORT.md#4-software-architecture-documentation-c4-models--uml-diagrams) |
| **Issue #14:** Figma UI/UX Prototypes & Actor User-Flow Diagrams | **Muhammed Fatih Ağaç** (`@macig102`) | `feature/14-figma-ui-userflows` | PR #21 $\rightarrow$ `develop` | [`docs/sprint2/SPRINT2_REPORT.md` (§3: UI/UX Prototypes & User-Flows)](SPRINT2_REPORT.md#3-uiux-prototypes-figma--user-flow-diagrams) |
| **Issue #15:** Sprint 2 Quality Audit & Cross-Artifact Verification | **Tuğçe Ertem** & **Anıl Güngör** | `feature/15-sprint2-quality-audit` | PR #22 $\rightarrow$ `develop` | [`docs/sprint2/SPRINT2_REPORT.md` (§6: Submission Checklist)](SPRINT2_REPORT.md#6-sprint-2-submission-requirements--verification-checklist) |
| **Issue #16:** Git-Flow Release Governance & `v0.2.0-sprint2` Tag | **Azra Dostbil** (`@azradostbil`) | `release/v0.2.0-sprint2` | PR #23 $\rightarrow$ `main` | [`README.md`](../../README.md), [`.github/PULL_REQUEST_TEMPLATE.md`](../../.github/PULL_REQUEST_TEMPLATE.md), Tag `v0.2.0-sprint2` |

---

## 6. Scrum Master Guide: Step-by-Step Git Commands for Anıl Güngör (`@anlgr`)

To ensure your individual contribution is cleanly recorded in the GitHub commit and PR history as required by the BM321 announcement, run the following commands in your local git repository:

```bash
# 1. Switch to your Sprint 2 Scrum Master feature branch
git checkout feature/SCRUM-02-sprint2-agile-backlog

# 2. Stage your Sprint 2 Agile & RACI Governance report and updated contributions
git add docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md CONTRIBUTIONS.md README.md

# 3. Commit with conventional commit message referencing SCRUM-02
git commit -m "docs(agile): add Sprint 2 RACI matrix, refined backlog, agile ceremonies and traceability (SCRUM-02)"

# 4. Push your feature branch and open a Pull Request on GitHub
git push -u origin feature/SCRUM-02-sprint2-agile-backlog
```
