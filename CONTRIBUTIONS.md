# 👥 Team 13 - Individual Contributions & GitHub Traceability

This document outlines the individual contributions, GitHub tracking history, Issue/PR traceability, and official **BM321 Software Engineering Rubric** responsibilities of each team member for **Sprint 1 (`v0.1.0-sprint1`)** and **Sprint 2 (`v0.2.0-sprint2`)**.

- **GitHub Repository:** `https://github.com/azra-428/rescuebite-surplus-food-market`
- **Release Tags:** `v0.1.0-sprint1` (Sprint 1) | `v0.2.0-sprint2` (Sprint 2)

----

### 1. Zeynep Bozdemir (230203005)
* **GitHub Username:** `zeynepbozdemirrr`
* **Project Role:** Product Owner and Requirements Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1` - Completed):**
  * Led requirements engineering and established the product vision for transparent surplus food listings.
  * Authored the Project Proposal, including problem evidence (UNEP and Turkey food waste statistics), stakeholder definitions, transparent listing solution, and risk mitigations.
  * Established the Epic > Feature > Story > Task hierarchy for the Product Backlog and defined backlog prioritization, Definition of Ready (DoR), and Definition of Done (DoD).
  * Owned requirements and scope definition for Food Waste Rescued Metrics (US-08).
* **Sprint 2 Assigned Responsibilities (`v0.2.0-sprint2` - B1 & B2):**
  * Detailed Software Requirements Specification (`docs/sprint2/SRS.md`) and Refined Product Backlog (`docs/sprint2/Backlog.md`).
  * Peer review and merge verification of Sprint 2 Agile & RACI governance ([PR #16](https://github.com/macig102/rescuebite-surplus-food-market/pull/16)).
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #4 - Project Proposal & Requirements Definition](https://github.com/azra-428/rescuebite-surplus-food-market/issues/4)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #10 - Detailed SRS & Refined Product Backlog` (`feature/10-srs-refined-backlog`)

---

### 2. Mehmet Kocagöz (220201035)
* **GitHub Username:** `mehmetkocagozz`
* **Project Role:** Lead Software Architect and Technical Lead
* **Sprint 1 Contributions (`v0.1.0-sprint1` - Completed):**
  * Designed the System Vision and Context Boundary diagram with external provider trust boundaries.
  * Authored the OpenAPI 3.1.0 Contract ([`api/openapi.yaml`](api/openapi.yaml)) following strict API-first design principles.
  * Engineered the HTTP 409 Conflict concurrency handling strategy for surplus food listing stock limits and courier assignment race conditions.
  * Architected backend schemas and endpoints for Store Approval (US-01), Surplus Food Listing Creation with transparent items (US-02), Order Reservation with concurrency lock (US-04), Store Order Preparation Status Transitions, and Courier Claim (US-06).
* **Sprint 2 Assigned Responsibilities (`v0.2.0-sprint2` - B5):**
  * Software Architecture Documentation, C4 Models (Context, Container, Component), and UML Diagrams (`docs/sprint2/architecture/`).
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #3 - OpenAPI 3.1.0 Contract & System Architecture](https://github.com/azra-428/rescuebite-surplus-food-market/issues/3)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #13 - Software Architecture, C4 Models & UML Diagrams` (`feature/13-c4-uml-architecture`)

---

### 3. Anıl Güngör (220205003)
* **GitHub Username:** `anlgr`
* **Project Role:** Scrum Master and Agile Process Coach
* **Sprint 1 Contributions (`v0.1.0-sprint1` - Completed):**
  * Managed the Agile sprint cadence, stand-up coordination, and team communication workflows.
  * Established and administered the team GitHub Projects Kanban board tracking Sprint 1 backlog items.
  * Authored the team Roles breakdown and RACI Responsibility Matrix aligned with the official BM321 rubric.
* **Sprint 2 Contributions (`v0.2.0-sprint2` - A6, A7, SCRUM-02, B6):**
  * Verified all Sprint 1 GitHub Issue and PR traceability links (`#2, #3, #4, #5, #6, #7, #9`) and fixed missing link references in `CONTRIBUTIONS.md` (**A6**).
  * Authored the **Sprint 2 Agile Process Governance, RACI Matrix & Traceability Report** ([`docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md`](docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md)), documenting the Sprint 2 RACI Responsibility Matrix, Sprint 1 Retrospective, Sprint 2 Stand-up Cadence Logs, and Impediment Log (`IMP-01`–`IMP-04`) (**SCRUM-02**).
  * Co-authored the **Sprint 2 Quality Audit, Test Plan & Revised Definition of Done (DoD) Report** ([`docs/sprint2/quality.md`](docs/sprint2/quality.md)) alongside QA Engineer Tuğçe Ertem (**B6**).
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #9 - Agile Sprint Board & RACI Administration](https://github.com/azra-428/rescuebite-surplus-food-market/issues/9)
  * **Sprint 2 GitHub Issue & Branch:** `SCRUM-02 - Sprint 2 RACI Matrix, Agile Board & Refined Backlog` (`feature/SCRUM-02-sprint2-agile-backlog`)
  * **Pull Request & Commits:** Verified in repository history under `https://github.com/azra-428/rescuebite-surplus-food-market`.

---

### 4. Tuğçe Ertem (230201047)
* **GitHub Username:** `tugce-951` (`tugceertem`)
* **Project Role:** Quality Assurance and Test Automation Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1` - Completed):**
  * Formulated rigorous, testable Acceptance Criteria using standard Gherkin Given-When-Then format across all user stories (US-01 through US-08).
  * Defined test scenarios covering boundary conditions, input validation failures (HTTP 400), unapproved merchant restrictions (HTTP 403), and concurrency conflicts (HTTP 409).
  * Formulated Doorstep Dynamic QR Verification (US-07) testing scenarios and failure conditions.
  * Executed the Sprint 1 Quality & Evidence Audit against the course submission checklist.
* **Sprint 2 Assigned Responsibilities (`v0.2.0-sprint2` - B3 & B6):**
  * Non-Functional Requirements (NFR) and Quality-Measure Specifications (`docs/sprint2/NFR.md`) and Sprint 2 Quality Audit & Test Plan (`docs/sprint2/quality.md`).
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #6 - Acceptance Criteria & Quality Assurance Audit](https://github.com/azra-428/rescuebite-surplus-food-market/issues/6)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #11 - Non-Functional Requirements & Quality Measures` (`feature/11-nfr-quality-measures`) & `Issue #15 - Sprint 2 Quality Audit`

---

### 5. Azra Dostbil (230204031)
* **GitHub Username:** `azra-428` (`azradostbil`)
* **Project Role:** DevOps and CI/CD Infrastructure Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1` - Completed):**
  * Established Lightweight Git-Flow branching guidelines, branch protection rulesets, and GitHub Issue and Pull Request templates.
  * Configured GitHub repository governance rules prohibiting direct pushes to `main` and `develop`.
  * Managed Sprint 1 release packaging and version tagging workflow (`v0.1.0-sprint1`).
  * Prepared initial repository infrastructure for future CI/CD pipeline integration.
* **Sprint 2 Assigned Responsibilities (`v0.2.0-sprint2` - A4, A5, B7):**
  * Branch protection ruleset verification (`protect-main`), CI pipeline configuration, and Sprint 2 release packaging (`v0.2.0-sprint2`).
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** [Issue #5 - Git-Flow Policy, Repository Governance & Templates](https://github.com/azra-428/rescuebite-surplus-food-market/issues/5)
  * **Sprint 2 GitHub Issue & Branch:** `Issue #16 - Git-Flow Release Governance & v0.2.0-sprint2 Tag` (`release/v0.2.0-sprint2`)

---

### 6. Muhammed Fatih Ağaç (230201009)
* **GitHub Username:** `macig102`
* **Project Role:** Implementation and Integration Engineer
* **Sprint 1 Contributions (`v0.1.0-sprint1` - Completed):**
  * Executed feature implementations and cross-component integrations across frontend and backend modules.
  * Aligned API-UI contracts, ensuring seamless data flow between backend services and customer discovery/listing interfaces (US-03, US-05, US-06).
  * Supported system testing, debugging, and technical documentation consolidation for Sprint 1 deliverables.
* **Sprint 2 Assigned Responsibilities (`v0.2.0-sprint2` - A1, A3, B4):**
  * Repository collaborator administration, `develop` branch configuration, and Figma UI/UX Prototypes & User-Flow Diagrams (`docs/sprint2/design/`).
* **Traceability Links:**
  * **Sprint 1 GitHub Issue:** Linked feature development and integration tasks.
  * **Sprint 2 GitHub Issue & Branch:** `Issue #14 - Figma UI/UX Prototypes & Actor User-Flow Diagrams` (`feature/14-figma-ui-userflows`)
  * **Pull Request & Commits:** Verified in repository history under `https://github.com/azra-428/rescuebite-surplus-food-market`.
