# 👥 Team 13 - Individual Contributions & GitHub Traceability

This document outlines the individual contributions, GitHub tracking history, Issue/PR traceability, and official **BM321 Software Engineering Rubric** responsibilities of each team member across **Sprint 1 (`v0.1.0-sprint1`)** and **Sprint 2 (`v0.2.0-sprint2`)**.

- **GitHub Repository:** `https://github.com/azra-428/rescuebite-surplus-food-market`
- **Release Tags:** `v0.1.0-sprint1` (Sprint 1) | `v0.2.0-sprint2` (Sprint 2)

----

### 1. Zeynep Bozdemir (230203005)
* **GitHub Username:** `zeynepbozdemirrr`
* **Project Role:** Product Owner and Requirements Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1`):**
  * Led requirements engineering and established the product vision for transparent surplus food listings.
  * Authored the Project Proposal, including problem evidence (UNEP and Turkey food waste statistics), stakeholder definitions, transparent listing solution, and risk mitigations.
  * Established the Epic > Feature > Story > Task hierarchy for the Product Backlog and defined backlog prioritization, Definition of Ready (DoR), and Definition of Done (DoD).
  * Owned requirements and scope definition for Food Waste Rescued Metrics (US-08).
* **Sprint 2 Contributions (`v0.2.0-sprint2`):**
  * Authored the **Detailed Software Requirements Specification (SRS)** in [`docs/sprint2/SPRINT2_REPORT.md`](docs/sprint2/SPRINT2_REPORT.md) (`FR-01` through `FR-16`) and formalized core domain business rules (`BR-01` through `BR-08`).
  * Led **Product Backlog Refinement** with Scrum Master Anıl Güngör, expanding the backlog to 12 stories (`US-01`–`US-12`) and validating stakeholder acceptance criteria against UI/UX flows.
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #4 - Project Proposal & Requirements Definition](https://github.com/azra-428/rescuebite-surplus-food-market/issues/4)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #10 - Detailed SRS & Refined Product Backlog` (`feature/10-srs-refined-backlog`)

---

### 2. Mehmet Kocagöz (220201035)
* **GitHub Username:** `mehmetkocagozz`
* **Project Role:** Lead Software Architect and Technical Lead
* **Sprint 1 Contributions (`v0.1.0-sprint1`):**
  * Designed the System Vision and Context Boundary diagram with external provider trust boundaries.
  * Authored the OpenAPI 3.1.0 Contract ([`api/openapi.yaml`](api/openapi.yaml)) following strict API-first design principles.
  * Engineered the HTTP 409 Conflict concurrency handling strategy for surplus food listing stock limits and courier assignment race conditions.
  * Architected backend schemas and endpoints for Store Approval (US-01), Surplus Food Listing Creation with transparent items (US-02), Order Reservation with concurrency lock (US-04), Store Order Preparation Status Transitions, and Courier Claim (US-06).
* **Sprint 2 Contributions (`v0.2.0-sprint2`):**
  * Authored the **Software Architecture Documentation** in [`docs/sprint2/SPRINT2_REPORT.md`](docs/sprint2/SPRINT2_REPORT.md), including Architecture Decision Records (`ADR-01`–`ADR-04`).
  * Designed the complete **C4 Model hierarchy** (Level 1 System Context, Level 2 Container, Level 3 Component, Level 4 Code Blueprint).
  * Modeled the **UML Diagrams Suite**: Use-Case Diagram, Domain/Class Diagram (with optimistic lock `version` attributes), Sequence Diagrams for HTTP 409 Checkout Race Resolution and Atomic Courier Claim/QR Verification, and State Machine Diagrams for Order and Listing lifecycles.
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #3 - OpenAPI 3.1.0 Contract & System Architecture](https://github.com/azra-428/rescuebite-surplus-food-market/issues/3)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #13 - Software Architecture, C4 Models & UML Diagrams` (`feature/13-c4-uml-architecture`)

---

### 3. Anıl Güngör (220205003)
* **GitHub Username:** `anlgr`
* **Project Role:** Scrum Master and Agile Process Coach
* **Sprint 1 Contributions (`v0.1.0-sprint1`):**
  * Managed the Agile sprint cadence, stand-up coordination, and team communication workflows.
  * Established and administered the team GitHub Projects Kanban board tracking Sprint 1 backlog items.
  * Authored the team Roles breakdown and RACI Responsibility Matrix aligned with the official BM321 rubric.
* **Sprint 2 Contributions (`v0.2.0-sprint2`):**
  * Authored the dedicated **Sprint 2 Agile Process Governance, RACI Matrix & Traceability Report** ([`docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md`](docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md)).
  * Updated the **Sprint 2 RACI Responsibility Matrix** mapping all 9 assessed Sprint 2 activities (SRS, Refined Backlog, NFRs, Figma/User-Flows, C4 Models, UML Diagrams, Agile Board, Release Tagging, Rubric Audit) to the 6 team members.
  * Facilitated and documented the **Sprint 1 Retrospective**, **Sprint 2 Stand-up Cadence Logs**, and **Impediment Tracking Log (`IMP-01`–`IMP-04`)**.
  * Co-led **Product Backlog Refinement** and compiled the **End-to-End Requirement-to-Artifact Traceability Matrix** (`FR` $\leftrightarrow$ `US` $\leftrightarrow$ `OpenAPI` $\leftrightarrow$ `Figma Screen` $\leftrightarrow$ `C4/UML` $\leftrightarrow$ `GitHub Issue/PR`).
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #9 - Agile Sprint Board & RACI Administration](https://github.com/azra-428/rescuebite-surplus-food-market/issues/9)
  * **Sprint 2 GitHub Issue & Branch:** `SCRUM-02 - Sprint 2 RACI Matrix, Agile Board & Refined Backlog` (`feature/SCRUM-02-sprint2-agile-backlog`)
  * **Pull Request & Commits:** Verified in repository history under `https://github.com/azra-428/rescuebite-surplus-food-market`.

---

### 4. Tuğçe Ertem (230201047)
* **GitHub Username:** `tugceertem`
* **Project Role:** Quality Assurance and Test Automation Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1`):**
  * Formulated rigorous, testable Acceptance Criteria using standard Gherkin Given-When-Then format across all user stories (US-01 through US-08).
  * Defined test scenarios covering boundary conditions, input validation failures (HTTP 400), unapproved merchant restrictions (HTTP 403), and concurrency conflicts (HTTP 409).
  * Formulated Doorstep Dynamic QR Verification (US-07) testing scenarios and failure conditions.
  * Executed the Sprint 1 Quality & Evidence Audit against the course submission checklist.
* **Sprint 2 Contributions (`v0.2.0-sprint2`):**
  * Authored the **Non-Functional Requirements (NFR) and Quality-Measure Specifications** in [`docs/sprint2/SPRINT2_REPORT.md`](docs/sprint2/SPRINT2_REPORT.md) aligned with **ISO/IEC 25010** (`NFR-PERF-01..03`, `NFR-CONC-01..02`, `NFR-SEC-01..02`, `NFR-REL-01..02`, `NFR-USA-01..02`, `NFR-MAINT-01`, `NFR-COMP-01`).
  * Formulated the 6 **SEI Quality Attribute Scenarios (`QAS-01`–`QAS-06`)** with stimulus, architectural response, and quantitative SLA response measures.
  * Co-verified the UML Sequence and State Machine diagrams for negative test coverage and executed the **Sprint 2 Rubric Quality Audit**.
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #6 - Acceptance Criteria & Quality Assurance Audit](https://github.com/azra-428/rescuebite-surplus-food-market/issues/6)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #11 - Non-Functional Requirements & Quality Measures` (`feature/11-nfr-quality-measures`) & `Issue #15 - Sprint 2 Quality Audit`

---

### 5. Azra Dostbil (230204031)
* **GitHub Username:** `azradostbil`
* **Project Role:** DevOps and CI/CD Infrastructure Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1`):**
  * Established Lightweight Git-Flow branching guidelines, branch protection rulesets, and GitHub Issue and Pull Request templates.
  * Configured GitHub repository governance rules prohibiting direct pushes to `main` and `develop`.
  * Managed Sprint 1 release packaging and version tagging workflow (`v0.1.0-sprint1`).
  * Prepared initial repository infrastructure for future CI/CD pipeline integration.
* **Sprint 2 Contributions (`v0.2.0-sprint2`):**
  * Specified container deployment boundaries in the **C4 Level 2 Container Diagram** (Docker Compose topology for Web PWA, REST API Server, PostgreSQL + PostGIS, and Redis).
  * Contributed infrastructure, availability, and CI test-coverage gate specifications (`NFR-REL-01`, `NFR-MAINT-01`, `NFR-COMP-01`).
  * Audited Git-Flow Pull Request merges into `develop` and executed the **`v0.2.0-sprint2`** release packaging workflow.
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #5 - Git-Flow Policy, Repository Governance & Templates](https://github.com/azra-428/rescuebite-surplus-food-market/issues/5)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #16 - Git-Flow Release Governance & v0.2.0-sprint2 Tag` (`release/v0.2.0-sprint2`)

---

### 6. Muhammed Fatih Ağaç (230201009)
* **GitHub Username:** `macig102`
* **Project Role:** Implementation and Integration Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1`):**
  * Executed feature implementations and cross-component integrations across frontend and backend modules.
  * Aligned API-UI contracts, ensuring seamless data flow between backend services and customer discovery/listing interfaces (US-03, US-05, US-06).
  * Supported system testing, debugging, and technical documentation consolidation for Sprint 1 deliverables.
* **Sprint 2 Contributions (`v0.2.0-sprint2`):**
  * Designed the **Figma UI/UX Prototypes** (`SCR-01` through `SCR-12`) covering the Customer Mobile App, Merchant 90-Second Listing Creator & Order Prep Board, Courier Dispatch & QR Scanner App, and Admin Hygiene Approval Console.
  * Authored the 4 **Actor User-Flow Diagrams** in [`docs/sprint2/SPRINT2_REPORT.md`](docs/sprint2/SPRINT2_REPORT.md) mapping every UI screen interaction to OpenAPI endpoints and `403`/`409` error recovery modals.
  * Assisted in mapping UI components to SRS requirements (`FR-01`–`FR-16`) and C4 Level 2/3 frontend-to-API interactions.
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** Linked feature development and integration tasks.
  * **Sprint 2 GitHub Issue & Branch:** `Issue #14 - Figma UI/UX Prototypes & Actor User-Flow Diagrams` (`feature/14-figma-ui-userflows`)
  * **Pull Request & Commits:** Verified in repository history under `https://github.com/azra-428/rescuebite-surplus-food-market`.
