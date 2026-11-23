# Refined Product Backlog (Sprint 2)
**Project:** Neighborhood Surplus Food Market (*RescueBite*)  
**Sprint:** Sprint 2 (Requirements, UI/UX, Architecture & Quality Planning)  
**Product Owner:** Zeynep Bozdemir  

---

## Sprint 1 Backlog Items (Status: Done)

| ID | Title | Description | Effort (SP) | Owner | Status |
|---|---|---|---|---|---|
| **US-01** | Project Proposal & System Vision | Define problem statement, transparent surplus food business model, and system boundary. | 3 | Zeynep Bozdemir | **Done** |
| **US-02** | OpenAPI 3.1.0 API-First Contract | Design full REST API specification (`api/openapi.yaml`) including schemas and HTTP 409 concurrency rules. | 5 | Mehmet Kocagöz | **Done** |
| **US-03** | Agile Process, RACI & Git-Flow | Establish RACI matrix, branch protection, PR/Issue templates, and GitHub board. | 3 | Anıl Güngör | **Done** |
| **US-04** | Initial Backlog & Quality Baseline | Create initial prioritized backlog, DoR/DoD, and license setup. | 3 | Zeynep & Tuğçe | **Done** |

---

## Sprint 2 Refined User Stories

### US-05: Detailed Software Requirements Specification (SRS)
* **Description:** As a Product Owner, I want a formal SRS document aligned with `api/openapi.yaml` so that all functional requirements and acceptance criteria are unambiguous before coding.
* **Definition of Ready (DoR):**
  * **Actor:** Product Owner / Development Team
  * **Value:** Establishes a verifiable baseline for implementation and testing.
  * **Acceptance:** `docs/sprint2/SRS.md` includes Introduction, MoSCoW FR table, NFR summary, External Interfaces, and Assumptions.
  * **Dependencies:** `api/openapi.yaml` (Done).
* **Effort:** 5 SP | **Owner:** Zeynep Bozdemir | **Status:** In Progress

### US-06: Non-Functional Requirements & Quality Measures
* **Description:** As a QA Engineer, I want measurable NFRs (performance, security, concurrency, usability) so that system quality can be objectively tested.
* **Definition of Ready (DoR):**
  * **Actor:** QA Engineer / Architect
  * **Value:** Prevents performance bottlenecks and security gaps.
  * **Acceptance:** `docs/sprint2/NFR.md` defines quantifiable metrics and verification methods for each quality attribute.
  * **Dependencies:** US-05 (SRS).
* **Effort:** 3 SP | **Owner:** Tuğçe Ertem | **Status:** In Progress

### US-07: Figma UI/UX Prototypes & User Flows
* **Description:** As a Customer/Merchant/Admin, I want interactive Figma prototypes covering Dashboard, Listing Browse, Create Listing, Checkout/QR, and Admin Approval so that usability is validated early.
* **Definition of Ready (DoR):**
  * **Actor:** Customer, Merchant, Courier, Admin
  * **Value:** Ensures transparent itemized food display and clear allergen visibility before development.
  * **Acceptance:** Shareable Figma link + PNG exports committed to `docs/sprint2/design/` and linked in `README.md`.
  * **Dependencies:** US-05 (SRS).
* **Effort:** 5 SP | **Owner:** Muhammed Fatih Ağaç | **Status:** In Progress

### US-08: System Architecture (C4 Models & UML Class Diagram)
* **Description:** As a Lead Architect, I want C4 (Context, Container, Component) and UML Class diagrams so that service boundaries and domain entities are clearly documented.
* **Definition of Ready (DoR):**
  * **Actor:** Software Architect / Developers
  * **Value:** Aligns backend services and database models with the OpenAPI contract.
  * **Acceptance:** 4 PNG diagrams committed to `docs/sprint2/architecture/` and documented in `README.md`.
  * **Dependencies:** `api/openapi.yaml` (Done).
* **Effort:** 5 SP | **Owner:** Mehmet Kocagöz | **Status:** In Progress

### US-09: Quality Audit, Test Plan & CI Pipeline Setup
* **Description:** As a QA & DevOps team, we want a Sprint 2 test plan (unit, integration, UI) and revised DoD checklist so that Sprint 3 implementation meets the ≥50% unit-test coverage requirement.
* **Definition of Ready (DoR):**
  * **Actor:** QA Engineer, Scrum Master, DevOps Engineer
  * **Value:** Automates quality gates and standardizes review criteria.
  * **Acceptance:** `docs/sprint2/quality.md` completed with test strategy, updated DoD, and CI pipeline plan.
  * **Dependencies:** US-06 (NFR), US-08 (Architecture).
* **Effort:** 5 SP | **Owner:** Anıl Güngör, Tuğçe Ertem, Azra Dostbil | **Status:** In Progress
