# Software Requirements Specification (SRS)
**Project:** Neighborhood Surplus Food Market (*RescueBite*)  
**Course:** BM321 / SENG 321 – Software Engineering Project  
**Version:** 2.0 (Sprint 2)  
**Team:** Team 13  

---

## 1. Introduction

### 1.1 Purpose
This Software Requirements Specification (SRS) defines the functional requirements, non-functional summary, external interfaces, and system assumptions for **RescueBite**, a neighborhood surplus food marketplace. It serves as the authoritative baseline for architecture, UI/UX design, implementation, and quality assurance.

### 1.2 Scope
RescueBite enables verified local bakeries, cafes, and grocery stores to list end-of-day surplus food items with **fully transparent, itemized contents, explicit quantities, allergen declarations, and discounted prices** (strictly avoiding surprise or mystery packages). Customers inspect exact contents before ordering, merchants manage order preparation, local couriers handle doorstep delivery, and handover is verified via a dynamic, single-use QR token. The platform also tracks cumulative food waste diversion and CO2 prevention metrics.

---

## 2. Functional Requirements

| ID | Description | MoSCoW | Acceptance Criteria |
|---|---|---|---|
| **FR-01** | **Store Registration Approval:** Platform Admin can approve or suspend merchant accounts after reviewing hygiene licenses (`PATCH /admin/stores/{storeId}/approve`). | Must | Unapproved stores receive `HTTP 403 STORE_NOT_APPROVED` when attempting to create listings; approved stores can publish listings immediately. |
| **FR-02** | **Transparent Listing Creation:** Approved merchants can create itemized surplus food listings with item names, quantities, units, allergens, prices, weight, and delivery windows (`POST /listings`). | Must | Listing is persisted with status `AVAILABLE` (`HTTP 201`); requests missing itemized `items` array or required fields return `HTTP 400`. |
| **FR-03** | **Geolocation & Dietary Listing Discovery:** Customers can browse and filter active listings by latitude, longitude, radius (km), category, and dietary preferences (`GET /listings`, `GET /listings/{listingId}`). | Must | Returns only active listings matching filters with complete itemized breakdown and allergen alerts (`HTTP 200`). |
| **FR-04** | **Atomic Order Placement:** Customers can reserve a listing with delivery address and sandbox payment token (`POST /orders`). | Must | Stock is decremented atomically, order starts as `PLACED`, and a unique `deliveryQrToken` is generated (`HTTP 201`). Concurrent depletion or payment failure returns `HTTP 409`. |
| **FR-05** | **Order Preparation Lifecycle:** Merchants can transition their own orders sequentially from `PLACED` → `PREPARING` → `READY_FOR_COURIER` (`PATCH /orders/{orderId}/status`). | Must | Invalid transitions return `HTTP 409 INVALID_STATUS_TRANSITION`; non-owner merchants receive `HTTP 403`. |
| **FR-06** | **Atomic Courier Delivery Claim:** Couriers can view `READY_FOR_COURIER` orders near their coordinates (`GET /deliveries/available`) and claim a delivery (`POST /deliveries/{orderId}/claim`). | Must | First courier transitions order to `IN_DELIVERY` (`HTTP 200`); concurrent claims by other couriers return `HTTP 409 DELIVERY_ALREADY_CLAIMED`. |
| **FR-07** | **Dynamic QR Handover Verification:** Assigned couriers scan and submit the customer's single-use QR token at doorstep delivery (`POST /deliveries/{orderId}/verify-qr`). | Must | Valid token within delivery window transitions order to `DELIVERED` and sets `deliveredAt`. Reused/invalid tokens or expired windows return `HTTP 409`. |
| **FR-08** | **Food Waste Rescue Metrics:** Users and stakeholders can query cumulative rescued food weight (kg), delivered orders, and prevented CO2 emissions (`GET /metrics/food-waste`). | Should | Metrics aggregate exclusively from `DELIVERED` orders; cancelled or unfulfilled orders are strictly excluded. |
| **FR-09** | **Order Tracking & Notifications:** Customers and merchants receive status updates throughout the order lifecycle (`GET /orders/{orderId}` + Notification Handler). | Should | Order detail endpoint returns current status, assigned courier, and QR token for authorized users (`HTTP 200`). |

---

## 3. Non-Functional Requirements (Summary)
*(Detailed quality measures and verification methods are specified in `docs/sprint2/NFR.md`.)*

* **Performance:** Standard read endpoints (`GET /listings`) shall respond within 300ms (p95) under normal load.
* **Concurrency & Data Integrity:** Stock reservation and courier claiming must enforce atomic transactions to prevent overselling or double-assignment (`HTTP 409 Conflict`).
* **Security:** All state-changing endpoints require JWT Bearer authentication (`BearerAuth`) with strict Role-Based Access Control (Customer, Merchant, Courier, Admin).
* **Reliability & Error Handling:** All API error responses must conform to RFC 7807 / RFC 9457 (`application/problem+json`).
* **Usability:** Every listing must visibly display itemized contents and allergen warnings prior to checkout.

---

## 4. External Interfaces
* **API Contract Reference:** All RESTful endpoints, request/response schemas, security schemes, and error models are formally defined in [`api/openapi.yaml`](../../api/openapi.yaml) (OpenAPI 3.1.0, base URL: `https://api.rescuebite.local/v1`).
* **Identity Provider:** External JWT Bearer token issuance and verification.
* **Sandbox Payment Gateway:** Simulates payment authorization via `paymentToken` during checkout.
* **Notification Service:** Delivers order preparation and doorstep delivery alerts to users.

---

## 5. Assumptions & Dependencies
* **Assumptions:** Merchants accurately declare food weights, quantities, and allergens; customers and couriers have internet-enabled devices capable of displaying/scanning QR codes.
* **Dependencies:** Availability of geolocation coordinates for radius filtering, sandbox payment gateway uptime for order creation, and adherence to the OpenAPI 3.1.0 specification across frontend and backend teams.
