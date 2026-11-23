# RescueBite — Non-Functional Requirements & Quality Measures

**Project:** Neighborhood Surplus Food Market (RescueBite)  
**Course:** SENG 321 / BM321 — Software Engineering Project  
**Team:** Team 13  
**Document version:** 1.0 — Sprint 2 requirements draft  
**Related specification:** [Sprint 2 SRS](SRS.md)  

## 1. Purpose and scope

This document defines measurable quality requirements and verification methods for RescueBite, following the quality-characteristic approach of **ISO/IEC 25010**. It supplements the functional requirements in the Sprint 2 SRS and the API contract defined in `api/openapi.yaml`.

RescueBite allows approved merchants to publish **transparent, itemized surplus-food listings** containing quantities and allergen information; customers place orders using a **sandbox payment token**; couriers claim deliveries and verify doorstep handover using a **single-use QR token**; administrators approve merchants. There are **no mystery/surprise packages** in the specified product.

The requirements below are **specifications and intended verification criteria**, not claims that the implemented application has passed tests. Where workload, test population, or tooling has not been defined, that detail is explicitly recorded in Section 4 rather than invented.

## 2. Non-functional requirements and quality measures

| ID | Quality characteristic | Requirement / measurable target | Measurement and verification method | Requirement basis |
|---|---|---|---|---|
| **NFR-01** | Performance efficiency | The `GET /listings` endpoint shall achieve a **95th-percentile response time of no more than 300 ms under normal load**. | Run an API performance test, calculate p95 latency, and record the number of requests, load, test data, and environment. **The normal-load profile must be defined before execution.** | Sprint 2 SRS §3; FR-03 |
| **NFR-02** | Interaction capability / usability | An eligible customer shall be able to inspect a listing's itemized contents and complete a valid order in **less than 120 seconds**. | Conduct a representative order-flow usability test and record task completion time and outcome for each participant. | Sprint 1 Report §1.3; SRS FR-03–FR-04 |
| **NFR-03** | Interaction capability / usability | An approved merchant shall be able to publish a valid itemized surplus-food listing in **less than 90 seconds**. | Use a predefined listing with quantities, prices, allergens, and delivery window; record task completion time and outcome. | Sprint 1 Report §1.3; SRS FR-02 |
| **NFR-04** | Interaction capability / user error protection | Before checkout, the customer interface shall display **all itemized contents and declared allergen warnings** for the selected listing. Target: **no required content or allergen field missing** in the defined review scenarios. | Inspect the listing and checkout flows against valid test listings; compare visible information with the listing data returned by the API. | Sprint 2 SRS §3; FR-02–FR-03 |
| **NFR-05** | Security / access control | **State-changing operations** shall require JWT Bearer authentication and enforce the documented **Customer, Merchant, Courier, and Admin** permissions. Unauthorized modifications must not succeed. | Execute positive and negative authorization tests for relevant endpoints; check response codes and verify that rejected requests do not modify persisted data. For example, an unapproved store creating a listing returns `403 STORE_NOT_APPROVED`. | Sprint 2 SRS §3; FR-01, FR-02, FR-05–FR-07; OpenAPI security schemes |
| **NFR-06** | Security / confidentiality | Customer delivery-address and contact data shall be disclosed only to authorized participants for an appropriate order or active delivery. Target: **zero unauthorized disclosures** in the agreed access-control test matrix. | Request order/delivery data as unrelated customers, merchants, couriers, and authorized participants; inspect returned fields and access decisions using synthetic data. | Sprint 1 Report §1.5 privacy mitigation; requires field-level access rules in architecture |
| **NFR-07** | Reliability / data integrity | **Stock must not be oversold.** With one listing unit remaining and two concurrent, otherwise-valid order requests, **at most one** shall create an order; the competing request shall return `409 LISTING_SOLD_OUT`, and stock shall never become negative. | Concurrency/integration test of `POST /orders`; verify HTTP responses, created orders, and persisted listing quantity. | Sprint 2 SRS §3; FR-04; OpenAPI `/orders` |
| **NFR-08** | Reliability / data integrity | A ready order shall not be assigned to more than one courier. When two eligible couriers claim the same order concurrently, **at most one** claim shall succeed; the conflicting claim shall return `409 DELIVERY_ALREADY_CLAIMED`. | Concurrency/integration test of `POST /deliveries/{orderId}/claim`; inspect assignment and status after both requests. | Sprint 2 SRS §3; FR-06; OpenAPI delivery claim |
| **NFR-09** | Security / delivery integrity | QR handover verification shall require the **assigned courier**, a **valid and unused QR token**, and an **active delivery window**. A token must never produce a second successful delivery confirmation. | Test valid, reused, invalid, expired, and unauthorized-courier scenarios for `POST /deliveries/{orderId}/verify-qr`; inspect final order state. Expected documented failures include `403 UNAUTHORIZED_COURIER`, `409 INVALID_QR_VERIFICATION`, and `409 EXPIRED_DELIVERY_WINDOW`. | Sprint 2 SRS FR-07; OpenAPI QR verification |
| **NFR-10** | Reliability / recoverability | A notification-provider outage shall **not prevent an authorized user from retrieving existing order status** via `GET /orders/{orderId}`. | Simulate notification-provider unavailability and verify the existing order-status endpoint still returns the expected order data without corrupting state. | Sprint 1 Report §1.2 (in-app status fallback); SRS FR-09 |
| **NFR-11** | Reliability / API error consistency | Documented API failures shall use the specified HTTP status and **`application/problem+json`** response format, with the agreed `Problem` fields (`title`, `status`, `code`, `detail`). | Validate the OpenAPI document; run contract checks covering representative `400`, `401`, `403`, `404`, and `409` responses, including conflict codes. Count contract mismatches (target: **zero** among executed defined checks). | Sprint 2 SRS §3–§4; OpenAPI 3.1.0 `Problem` schema |
| **NFR-12** | Functional correctness / data accuracy | Food-rescue metrics shall count **only orders in `DELIVERED` state**. Results shall match the expected totals for a known dataset containing delivered and non-delivered orders. | Use a fixture dataset with known food weights and order states; compare `GET /metrics/food-waste` results with manually calculated expected totals. | Sprint 2 SRS FR-08; OpenAPI metrics endpoint |
| **NFR-13** | Maintainability / testability | Automated unit-test coverage shall be **monitored against the team's documented 50% target** once executable application code exists. The coverage metric and included modules must be defined before reporting a percentage. | Run the selected unit-test framework with a coverage tool; save the report, metric definition, exclusions, and CI evidence when available. | Sprint 1 `README.md` (QA role expectations); measurement details not yet specified |

**Classification note:** Stock reservation, courier assignment, QR validation, and food-waste aggregation are defined primarily as **functional business rules** in the SRS. They appear here to specify **how their quality properties and correctness will be verified**; they do not introduce new product features.

## 3. Verification approach and evidence

1. **Requirement traceability:** Use the `FR-xx` identifiers from `docs/sprint2/SRS.md` and the corresponding OpenAPI operations. Confirm any changed user-story identifiers after the refined Product Backlog is available.
2. **Performance measurement:** Report p95 API latency, workload, duration, dataset, environment, and failure count. The **300 ms** threshold is taken from the SRS; no user count or duration has yet been agreed.
3. **Usability measurement:** Define the start/end of each task consistently. Record actual elapsed time, completion, and usability obstacles; do not invent a participant count or pass rate.
4. **Security and concurrency:** Test both successful and rejected requests, including saved database state. Use synthetic identities, QR tokens, addresses, and payment values.
5. **API contract validation:** Compare actual responses against the OpenAPI definitions; maintain error-body checks alongside expected HTTP statuses.
6. **Unit-test coverage:** Define whether 50% means line, statement, or branch coverage and which modules count. Do not claim achieved coverage until a report is generated.
7. **Evidence and status:** Save test case IDs, command outputs, CI links, screenshots, and defects when testing begins. **Current execution status: Not executed** (requirements-stage specification).

## 4. Details to finalize during specification alignment

These points **do not block preparation of this document**, but should be resolved before test execution and final project sign-off:

| Topic | Current specification | Still to define |
|---|---|---|
| API normal load | `GET /listings` p95 ≤ 300 ms | Concurrent-user/load profile, duration, seed dataset, test machine/environment |
| Customer and merchant task timing | Customer < 120 s; merchant < 90 s | Representative participants, exact start/end events, task datasets, pass-rate policy |
| Personal-data access | Role-based restriction and active-delivery privacy safeguard | Precise field-level access and masking policy |
| Test coverage | 50% monitoring target documented in project README | Tool, metric type, code scope and exclusions |
| Backlog references | Final functional requirements FR-01–FR-09 in Sprint 2 SRS | Reconcile User Story IDs with the refined Sprint 2 Backlog when it is available |
| Test execution | Specification stage; no results established by this document | Run tests after executable services and test environment exist |

## 5. Source references

- [Sprint 2 Software Requirements Specification](SRS.md) — scope, FR-01–FR-09, and the 300 ms p95 requirement.
- [Sprint 1 Project Report](../sprint1/SPRINT1_REPORT.md) — baseline success targets, risks, delivery and concurrency rules.
- [OpenAPI 3.1.0 contract](../../api/openapi.yaml) — operations, status codes, `Problem` responses, JWT security declarations.
- [Project README](../../README.md) — role-based quality and unit-test coverage expectations.
- [ISO/IEC 25010:2023 product quality model](https://www.iso.org/standard/78176.html) — reference vocabulary for software product quality characteristics; this document does **not** claim ISO certification.

---

**Document status:** Prepared as a Sprint 2 quality-requirements specification. Numerical criteria explicitly present in the SRS or Sprint 1 are retained; any unresolved measurement conditions are listed in Section 4. **No test result is represented as passed.**
