# Neighborhood Surplus Food Market (RescueBite)
> **SENG 321 - Software Engineering Project | Sprint 1 Deliverables**

## 👥 Team Information
- **Project Name:** Neighborhood Surplus Food Market (*RescueBite*)
- **Core Business Model:** Local bakeries, grocery stores, and cafes list their unsold, fresh end-of-day surplus food items with completely transparent, itemized contents, declared quantities, allergen information, and discounted prices. Customers know exactly what items and amounts they are buying before placing an order (strictly **no surprise packages**, mystery boxes, or random selections). Orders are delivered directly to the customer's doorstep by local couriers, and handover is cryptographically verified via a dynamic single-use QR code.
- **Team Number:** Team 13
- **Academic Term:** 2025-2026 Academic Year
- **Course:** SENG 321 - Software Engineering Project
- **GitHub Repository:** `https://github.com/macig102/rescuebite-surplus-food-market`
- **Sprint 1 Release Tag:** `v0.1.0-sprint1`

| Student ID | Full Name | Official Role Title (BM321 Rubric) | Primary Responsibility | Required Outputs & Tasks |
|---|---|---|---|---|
| 230203005 | Zeynep Bozdemir | **Product Owner and Requirements Engineer** | Requirements engineering and product vision | User stories, acceptance criteria, product backlog, prioritization, and stakeholder validation. |
| 220201035 | Mehmet Kocagöz | **Lead Software Architect and Technical Lead** | System and software architecture | C4 model, UML diagrams, architecture strategy, API-first or microservices decisions, and code review leadership. |
| 220205003 | Anıl Güngör | **Scrum Master and Agile Process Coach** | Agile process management and communication | Stand-up and retrospective records, RACI matrix, impediment tracking, and GitHub Projects or Jira board administration. |
| 230201047 | Tuğçe Ertem | **Quality Assurance and Test Automation Engineer** | Quality assurance and test automation | Unit, integration, and end-to-end tests, test plans, defect tracking, and at least 50 percent unit-test coverage monitoring. |
| 230204031 | Azra Dostbil | **DevOps and CI CD Infrastructure Engineer** | Infrastructure, configuration, and deployment | GitHub Actions continuous integration and continuous delivery pipeline, Docker configuration, and docker-compose deployment. |
| 230201009 | Muhammed Fatih Ağaç | **Implementation and Integration Engineer** | Feature implementation, cross-component integration | Feature implementation, cross-component integration, API and UI coordination, integration defect resolution, and technical documentation support. |

---

## 📌 Sprint 1 Deliverables & Document Index
- 📄 **Comprehensive Sprint 1 Report:** [`docs/sprint1/SPRINT1_REPORT.md`](docs/sprint1/SPRINT1_REPORT.md)
  - 1. Project Proposal (Problem evidence, stakeholders, transparent listing solution, feasibility, risks, Apache 2.0 license)
  - 2. System Vision & System Boundary (Mermaid context diagram & external dependencies)
  - 3. OpenAPI 3.1.0 Contract Summary, Store Order Preparation & Concurrency Handling (HTTP 409 Conflict)
  - 4. Team Roles & RACI Matrix
  - 5. Git-Flow Workflow, Branch Protection Rules & Repository Operating Model
  - 6. Prioritized Initial Product Backlog (Epic > Feature > Story > Task, DoR, DoD, Acceptance Criteria)
  - 7. Sprint 1 Submission Checklist
- 📜 **OpenAPI 3.1.0 Specification (YAML):** [`api/openapi.yaml`](api/openapi.yaml)
- 📋 **GitHub Pull Request Template:** [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md)
- 🎫 **GitHub User Story Issue Template:** [`.github/ISSUE_TEMPLATE/user-story.md`](.github/ISSUE_TEMPLATE/user-story.md)
- ⚖️ **Open-Source License:** [`LICENSE`](LICENSE) (Apache License 2.0)
- 🧑‍💻 **Individual Contributions & GitHub Tracking:** [`CONTRIBUTIONS.md`](CONTRIBUTIONS.md)

---

## 🎨 Sprint 2 UI/UX Design & User-Flow Deliverables (Task B-4)
- **Assignee:** Muhammed Fatih Ağaç (*Implementation and Integration Engineer*)
- **Figma Project:** [RescueBite UI on Figma](https://www.figma.com/design/YqnIJn9K1PqsI2ZgTn2QHu/RescueBite-UI?node-id=0-1&t=RQDhqyHRI2qhTiVm-1) *(View-Only Link)*
- **Design Specification & Documentation:** [`docs/sprint2/design/README.md`](docs/sprint2/design/README.md)
- **High-Resolution Prototype Exports:**
  - 🏠 **Home / Dashboard:** [`docs/sprint2/design/Home.png`](docs/sprint2/design/Home.png)
  - 📋 **Offer List (Catalog & Proximity Map):** [`docs/sprint2/design/OfferList.png`](docs/sprint2/design/OfferList.png)
  - 📝 **Create Offer Form (Itemized Surplus Breakdown):** [`docs/sprint2/design/CreateOffer.png`](docs/sprint2/design/CreateOffer.png)
  - 🤝 **Claim Offer Workflow (Dynamic QR Handover):** [`docs/sprint2/design/ClaimOffer.png`](docs/sprint2/design/ClaimOffer.png)
  - 🛡️ **Admin Governance & Compliance Panel:** [`docs/sprint2/design/AdminPanel.png`](docs/sprint2/design/AdminPanel.png)
  - 🔄 **End-to-End User Flow Diagram:** [`docs/sprint2/design/Flow.png`](docs/sprint2/design/Flow.png)

---

## 🚀 Sprint 1 Project Scope & Setup Instructions

### Sprint 1 Scope Notice
Sprint 1 focuses strictly on **project foundation, system vision, boundary context modeling, API-first OpenAPI contract design, team operating rules (RACI), Git-Flow policies, and initial product backlog engineering**. Application source code (backend services, frontend client apps, and database migrations) is scheduled for implementation in Sprint 2 and Sprint 3 in accordance with the course roadmap.

### Validating the OpenAPI Contract
You can inspect and validate the OpenAPI 3.1.0 specification locally:
```bash
# View the raw specification file
cat api/openapi.yaml

# Open in Swagger Editor or use Redocly / Spectral CLI if installed:
# npx @stoplight/spectral-cli lint api/openapi.yaml
# npx @redocly/cli lint api/openapi.yaml
```
The contract validates against OpenAPI 3.1.0 standards and includes complete request/response schemas, RFC 7807/9457 Problem Details, and HTTP 409 Conflict error scenarios.

---

## 🏗️ Sprint 2 Architecture Documentation (C4 & UML)
All architecture diagrams are stored in `docs/sprint2/architecture/` and aligned with `api/openapi.yaml`:

- **C4 Context Diagram (`c4-context.png`):** Shows interactions between RescueBite, primary actors (Customer, Approved Store, Courier, Admin), and external services (Identity Provider, Payment Gateway, Notification Service).
- **C4 Container Diagram (`c4-container.png`):** Details the high-level technical building blocks (Web/Mobile UI, REST API Service, Auth Service, Primary Database).
- **C4 Component Diagram (`c4-component.png`):** Breaks down internal API Service components (Listing, Order, Delivery & QR, Store Approval, Food Waste Metrics, and Notification Handler).
- **UML Class Diagram (`uml-class.png`):** Models the core domain entities (`StoreSummary`, `SurplusFoodListing`, `ListingItem`, `Order`, `FoodWasteMetrics`), their attributes, and relationships.
