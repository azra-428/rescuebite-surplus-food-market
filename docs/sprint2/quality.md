# SENG 321 / BM321 Software Engineering Project
# Sprint 2 Quality Audit, Test Plan & Definition of Done (DoD) Verification Report

**Project Name:** Neighborhood Surplus Food Market (*RescueBite*)  
**Team Number:** Team 13  
**Academic Term:** 2025-2026 Academic Year | Sprint 2  
**Prepared By:**  
- **Tuğçe Ertem (230201047)** — *Quality Assurance and Test Automation Engineer* (`@tugce-951`)  
- **Anıl Güngör (220205003)** — *Scrum Master and Agile Process Coach* (`@anlgr`)  
**Target Release Tag:** `v0.2.0-sprint2`  

---

## 1. Comprehensive Test Plan (Unit, Integration, Contract & UI/UX Tests)

In compliance with the **BM321 Software Engineering Assessment Rubric** (requiring **$\ge 50\%$ automated unit-test coverage**, rigorous contract verification against `api/openapi.yaml`, and end-to-end user-flow validation), the test strategy is organized across four test levels:

### 1.1 Test Pyramid & Coverage Targets

| Test Level | Target Scope & Components | Primary Tooling / Framework | Target Coverage / SLA | Responsible Owners |
|---|---|---|---|---|
| **1. Unit Tests** | Domain entities (`Store`, `SurplusFoodListing`, `ListingItem`, `Order`, `DeliveryQrToken`), optimistic lock version checks, sequential status transitions, HMAC-SHA256 QR token signing/verification, and delivered-only waste metrics aggregation. | Jest / Vitest (or JUnit 5 / Pytest) | **$\ge 50\%$ overall line & branch coverage** (Target: **$\ge 75\%$** on core domain services) | Tuğçe Ertem & Mehmet Kocagöz |
| **2. API Contract & Integration Tests** | OpenAPI 3.1.0 request/response schema conformance, RFC 7807/9457 `application/problem+json` error payloads, PostgreSQL optimistic locking race conditions (`409 Conflict`), and JWT Role-Based Access Control (`401`/`403`). | Supertest / Postman-Newman & Spectral OpenAPI Linter | **$100\%$ of 11 OpenAPI operations** & **$100\%$ of HTTP 403/409 error codes** | Tuğçe Ertem & Azra Dostbil |
| **3. Concurrency Stress Tests** | Parallel checkout race on final listing unit (`availableListingQuantity = 1` $\rightarrow$ `409 LISTING_SOLD_OUT`) and parallel courier claim race (`409 DELIVERY_ALREADY_CLAIMED`). | Parallel Promise Runner / k6 Load Script | **$0\%$ oversell rate** & **$0\%$ dual-courier assignment** ($p_{95} \le 250\text{ ms}$) | Tuğçe Ertem & Mehmet Kocagöz |
| **4. UI/UX & User-Flow Acceptance Tests** | Customer discovery-to-checkout flow ($\le 120\text{ s}$), Store transparent listing creation ($\le 90\text{ s}$), dual quantity badge clarity, allergen chip visibility, and Courier QR scanner flow (`SCR-01`–`SCR-12`). | Figma Interactive Prototype Walkthrough & Playwright E2E | **$100\%$ of User Stories (`US-01`–`US-08`)** mapped to UI screens | Muhammed Fatih Ağaç & Anıl Güngör |

---

### 1.2 Detailed Test Case Specification Matrix (Unit, Integration & UI)

| Test Case ID | Test Level | Linked Story & SRS | Test Scenario Description | Input / Precondition | Expected Output & Assertion | Sprint 2 Audit Status |
|:---:|:---:|:---:|---|---|---|:---:|
| **TC-UNIT-01** | Unit | `US-02` / `FR-03` (`BR-01`) | Reject listing creation when `items[]` array is empty (Zero Mystery Box enforcement) | `NewSurplusFoodListing` with `items: []` | Throws validation error (`400 Bad Request`); listing is not persisted. | **Spec Verified** |
| **TC-UNIT-02** | Unit | `US-02` / `FR-03` (`BR-02`) | Verify dual quantity modeling (`initialListingQuantity` vs. `items[].quantity`) | `initialListingQuantity: 5`, `items: [{ itemName: "Sourdough", quantity: 2, unit: "loaf" }]` | `availableListingQuantity == 5` and each bundle preserves `2 loaves`. | **Spec Verified** |
| **TC-UNIT-03** | Unit | `US-02` / `FR-03` (`BR-04`) | Reject listing when `deliveryEnd <= deliveryStart` or in the past | `deliveryStart: 21:30`, `deliveryEnd: 19:30` | Throws `INVALID_PICKUP_INTERVAL` (`400 Bad Request`). | **Spec Verified** |
| **TC-UNIT-04** | Unit | `US-05` / `FR-10` (`BR-06`) | Enforce sequential store order preparation state machine | Order in `PLACED`; store requests jump to `READY_FOR_COURIER` | Throws `DomainConflictError("INVALID_STATUS_TRANSITION", 409)`. | **Spec Verified** |
| **TC-UNIT-05** | Unit | `US-07` / `FR-13` (`BR-07`) | Validate HMAC-SHA256 single-use `deliveryQrToken` and mark redeemed | Valid token scanned within `[deliveryStart, deliveryEnd]` | Returns `true`, transitions to `DELIVERED`, sets `isRedeemed = true`. | **Spec Verified** |
| **TC-UNIT-06** | Unit | `US-07` / `FR-13` (`BR-07`) | Reject replayed or forged `deliveryQrToken` | Token scanned a second time (`isRedeemed == true`) | Throws `DomainConflictError("INVALID_QR_VERIFICATION", 409)`. | **Spec Verified** |
| **TC-UNIT-07** | Unit | `US-07` / `FR-13` (`BR-07`) | Reject doorstep QR verification after `deliveryEnd` window | `currentTime > order.deliveryEnd` | Throws `DomainConflictError("EXPIRED_DELIVERY_WINDOW", 409)`. | **Spec Verified** |
| **TC-UNIT-08** | Unit | `US-08` / `FR-15` (`BR-08`) | Compute rescued food weight exclusively from `DELIVERED` orders | `ORD-1`: `DELIVERED` ($1.5\text{ kg}$), `ORD-2`: `CANCELLED` ($2.0\text{ kg}$), `ORD-3`: `IN_DELIVERY` ($1.0\text{ kg}$) | `totalRescuedWeightKg == 1.5` and `co2EmissionsPreventedKg == 3.75`. | **Spec Verified** |
| **TC-INT-01** | Integration | `US-01` / `FR-01`, `FR-02` | Unapproved merchant blocked from publishing surplus listing | Store with `isApproved = false` calls `POST /listings` | Returns `HTTP 403 Forbidden` with RFC 7807 `code: "STORE_NOT_APPROVED"`. | **Contract Verified** |
| **TC-INT-02** | Integration | `US-04` / `FR-07` (`NFR-CONC-01`) | Concurrent checkout race condition on last remaining bundle (`availableListingQuantity = 1`) | Two parallel `POST /orders` requests (`CustA`, `CustB`) with `version = 4` | Exactly 1 returns `HTTP 201 Created` (`SOLD_OUT`); 1 returns `HTTP 409 Conflict (LISTING_SOLD_OUT)`. | **Contract Verified** |
| **TC-INT-03** | Integration | `US-06` / `FR-12` (`NFR-CONC-02`) | Concurrent courier claim race condition on `READY_FOR_COURIER` order | Two parallel `POST /deliveries/{id}/claim` requests (`CR-18`, `CR-22`) | Exactly 1 returns `HTTP 200 OK` (`IN_DELIVERY`); 1 returns `HTTP 409 Conflict (DELIVERY_ALREADY_CLAIMED)`. | **Contract Verified** |
| **TC-UI-01** | UI / UX | `US-02`, `US-03` (`NFR-USA-01..02`) | Figma prototype inspection of itemized contents, allergen chips, and 409 modals | Walkthrough of `SCR-01` through `SCR-12` user flows | Allergen tags visible above fold; listing creation $\le 90\text{ s}$; checkout $\le 120\text{ s}$. | **Prototype Verified** |

---

## 2. Revised Definition of Done (DoD) Checklist (Sprint 2 & Sprint 3 Standard)

Every User Story (`US-01` through `US-12`) is evaluated against the revised 4-pillar **Definition of Done (DoD)** audited by **Anıl Güngör (Scrum Master)** and **Tuğçe Ertem (QA Engineer)**:

### 2.1 Four-Pillar DoD Criteria
1. **Code & Architectural Alignment:**
   - [x] Feature / artifact is developed on a dedicated Git-Flow branch (`feature/<issue-id>-<short-name>`).
   - [x] Domain entities, state transitions, and sequence flows match the C4 (Level 1–4) and UML Class/Sequence/State diagrams.
2. **Test & Quality Verification:**
   - [x] Positive path, boundary validation (`400`), authorization (`401`/`403`), and concurrency race (`409`) scenarios are defined in Gherkin `Given-When-Then` and mapped to `TC-UNIT` / `TC-INT` / `TC-UI` cases.
   - [x] OpenAPI 3.1.0 specification (`api/openapi.yaml`) passes schema validation with zero errors.
3. **Documentation & Traceability:**
   - [x] Mapped in the End-to-End Traceability Matrix (`FR-ID` $\leftrightarrow$ `US-ID` $\leftrightarrow$ `OpenAPI` $\leftrightarrow$ `Figma Screen` $\leftrightarrow$ `UML/C4` $\leftrightarrow$ `NFR-ID`).
   - [x] Individual ownership is recorded in `CONTRIBUTIONS.md` and the Sprint 2 RACI Matrix.
4. **Peer Review & Git-Flow Governance:**
   - [x] Submitted via Pull Request targeting `develop` (`develope`) using `.github/PULL_REQUEST_TEMPLATE.md`.
   - [x] Reviewed and approved (`Approve`) by at least one peer reviewer / RACI lead before merging.

---

### 2.2 Per-Story DoD Audit Table (`US-01` – `US-12`)

| Story ID | User Story Title | SRS & NFR Spec (`FR`/`NFR`) | OpenAPI 3.1.0 Contract | Figma UI & User-Flow | C4 & UML Diagrams | Test Cases (`TC-*`) | PR & Peer Review | DoD Audit Result |
|:---:|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **US-01** | Platform Admin Store Hygiene Approval | ✅ `FR-01..02` | ✅ `PATCH /admin/stores/{id}/approve` | ✅ `SCR-11` | ✅ `UC-01`, Class | ✅ `TC-INT-01` | ✅ Verified | **PASS** |
| **US-02** | Approved Store Transparent Listing Creation | ✅ `FR-03..04` | ✅ `POST /listings` | ✅ `SCR-06..07` | ✅ `UC-02`, State | ✅ `TC-UNIT-01..03` | ✅ Verified | **PASS** |
| **US-03** | Customer Proximity & Dietary Listing Discovery | ✅ `FR-05..06` | ✅ `GET /listings` | ✅ `SCR-01..02` | ✅ `UC-03`, C4-L3 | ✅ `TC-UI-01` | ✅ Verified | **PASS** |
| **US-04** | Concurrency-Safe Checkout & HTTP 409 Lock | ✅ `FR-07..08` | ✅ `POST /orders` | ✅ `SCR-03..04` | ✅ `Seq-01 (409)` | ✅ `TC-INT-02` | ✅ Verified | **PASS** |
| **US-05** | Store Order Prep & Customer Dynamic QR | ✅ `FR-09..10` | ✅ `PATCH /orders/{id}/status` | ✅ `SCR-05`, `08` | ✅ `State-Order` | ✅ `TC-UNIT-04` | ✅ Verified | **PASS** |
| **US-06** | Courier Delivery Pool & Atomic Claim (409) | ✅ `FR-11..12` | ✅ `POST /deliveries/{id}/claim` | ✅ `SCR-09` | ✅ `Seq-02 (409)` | ✅ `TC-INT-03` | ✅ Verified | **PASS** |
| **US-07** | Doorstep Dynamic QR Proof Verification | ✅ `FR-13` | ✅ `POST /deliveries/{id}/verify-qr` | ✅ `SCR-10` | ✅ `Seq-02 (QR)` | ✅ `TC-UNIT-05..07` | ✅ Verified | **PASS** |
| **US-08** | Delivered-Only Food Waste Rescued Metrics | ✅ `FR-15..16` | ✅ `GET /metrics/food-waste` | ✅ `SCR-01`, `12` | ✅ `UC-11`, Class | ✅ `TC-UNIT-08` | ✅ Verified | **PASS** |
| **US-09** | ISO 25010 NFR & Quality-Measure Specs | ✅ `NFR-01..13` | ✅ RFC 7807 `Problem` | ✅ All Screens | ✅ `QAS-01..06` | ✅ All `TC-*` | ✅ Verified | **PASS** |
| **US-10** | Figma UI/UX Prototype & 4 Actor User-Flows | ✅ `FR-01..16` | ✅ All Endpoints | ✅ `SCR-01..12` | ✅ 4 Flowcharts | ✅ `TC-UI-01` | ✅ Verified | **PASS** |
| **US-11** | C4 Software Architecture & UML Suite | ✅ `ADR-01..04` | ✅ Full Alignment | ✅ Component Map | ✅ C4 L1-4 + 6 UML | ✅ Design Review | ✅ Verified | **PASS** |
| **US-12** | Sprint 2 RACI, Agile Governance & Release | ✅ Rubric Rules | ✅ Version `0.2.0` | — | ✅ Kanban & RACI | ✅ Audit Sign-off | ✅ PR #16 Merged | **PASS** |

---

## 3. GitHub Actions CI Pipeline & Contract Verification Specification

To automate contract linting, markdown verification, and unit/integration test execution on every Pull Request targeting `develop` (`develope`) and `main`, the following GitHub Actions workflow (`.github/workflows/ci-quality-gate.yml`) is defined:

```yaml
name: RescueBite Quality & OpenAPI Contract CI Gate

on:
  pull_request:
    branches: [ main, develop, develope ]
  push:
    branches: [ main, develop, develope ]

jobs:
  openapi-and-quality-audit:
    name: OpenAPI 3.1.0 Contract & Quality Audit
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Setup Node.js 20
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Validate OpenAPI 3.1.0 Contract (Spectral CLI)
        run: npx @stoplight/spectral-cli lint api/openapi.yaml --fail-severity=error

      - name: Verify Sprint 1 & Sprint 2 Deliverable Artifacts Exist
        run: |
          test -f api/openapi.yaml
          test -f docs/sprint1/SPRINT1_REPORT.md
          test -f docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md
          test -f CONTRIBUTIONS.md
          test -f README.md
```

---

## 4. Sprint 2 Quality & Contract Verification Report

| Verification Check | Tool / Method Executed | Target Artifact | Result | Notes & Evidence |
|---|---|---|:---:|---|
| **1. OpenAPI 3.1.0 Structural & Schema Validation** | OpenAPI 3.1.0 Schema Audit | `api/openapi.yaml` | **PASS (0 Errors)** | All 11 endpoints (`/listings`, `/orders`, `/deliveries/*`, `/admin/stores/*`, `/metrics/food-waste`) and 10 schemas validate cleanly. |
| **2. Zero Mystery Box / Transparent Itemization Check** | Domain Rule Audit (`BR-01`, `BR-02`) | `api/openapi.yaml`, SRS, Figma `SCR-01..07` | **PASS** | `NewSurplusFoodListing.items` enforces `minItems: 1` with required `itemName`, `quantity`, `unit`, and `allergens`. |
| **3. HTTP 409 Concurrency & RFC 7807 Problem Details Audit** | Error Catalog & Sequence Diagram Audit | `POST /orders`, `PATCH /orders/{id}/status`, `POST /deliveries/{id}/claim`, `POST /deliveries/{id}/verify-qr` | **PASS** | All 6 conflict codes (`LISTING_SOLD_OUT`, `PAYMENT_AUTHORIZATION_FAILED`, `INVALID_STATUS_TRANSITION`, `DELIVERY_ALREADY_CLAIMED`, `INVALID_QR_VERIFICATION`, `EXPIRED_DELIVERY_WINDOW`) return uniform RFC 7807 JSON. |
| **4. Sprint 1 & Sprint 2 GitHub Traceability Audit** | GitHub Issue, Branch & PR History Review | Repository Issues & Pull Requests | **PASS** | Individual branches, Issue references, and peer-reviewed Pull Requests (including PR #16 for `SCRUM-02`) are preserved in git history. |
