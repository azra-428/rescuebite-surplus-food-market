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

In accordance with the **BM321 Software Engineering Semester Team Project Specification and Assessment Rubric**, each member of **Team 13** holds an explicit, named role with assigned Sprint 2 deliverables:

| Student ID | Full Name | GitHub Account | Official Role Title (BM321 Rubric) | Sprint 2 Assigned Deliverables & Target Repository Paths |
|---|---|---|---|---|
| **230203005** | **Zeynep Bozdemir** | `@zeynepbozdemirrr` | **Product Owner and Requirements Engineer** | **B1 & B2:** Detailed Software Requirements Specification (`docs/sprint2/SRS.md`), functional requirements (`FR-01`–`FR-16`), domain business rules, and Refined Product Backlog (`docs/sprint2/Backlog.md`). |
| **220201035** | **Mehmet Kocagöz** | `@mehmetkocagozz` | **Lead Software Architect and Technical Lead** | **B5:** Software Architecture Documentation, C4 Model hierarchy (Context, Container, Component), and UML Diagrams (Class, Sequence, State Machine, Use-Case) under `docs/sprint2/architecture/`. |
| **220205003** | **Anıl Güngör** | `@anlgr` | **Scrum Master and Agile Process Coach** | **A6, A7, SCRUM-02 & B6:** Sprint 1 Issue link audit (`#2`–`#9`), Sprint 2 RACI Responsibility Matrix, Retrospective & Stand-up logs, Impediment Log (`docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md`), and co-authoring Sprint 2 Quality Audit (`docs/sprint2/quality.md`). |
| **230201047** | **Tuğçe Ertem** | `@tugce-951` | **Quality Assurance and Test Automation Engineer** | **B3 & B6:** Non-Functional Requirements & Quality-Measure Specifications (`docs/sprint2/NFR.md`) and Sprint 2 Quality Audit, Test Plan & Revised DoD (`docs/sprint2/quality.md`). |
| **230204031** | **Azra Dostbil** | `@azra-428` | **DevOps and CI/CD Infrastructure Engineer** | **A4, A5 & B7:** Branch protection ruleset (`protect-main` targeting `main` and `develop`), Sprint 1 tag verification (`v0.1.0-sprint1`), CI pipeline setup, and `v0.2.0-sprint2` GitHub Release packaging. |
| **230201009** | **Muhammed Fatih Ağaç** | `@macig102` | **Implementation and Integration Engineer** | **A1, A3 & B4:** Repository collaborator administration, `develop` branch configuration, Figma UI/UX Interactive Prototypes and User-Flow Diagrams (`docs/sprint2/design/`). |

---

## 2. Sprint 2 RACI Responsibility Matrix

* **R (Responsible):** The team member(s) who execute the hands-on engineering, modeling, or documentation work to produce the deliverable.
* **A (Accountable):** The single designated role owner with final decision and sign-off authority for the deliverable's rubric compliance.
* **C (Consulted):** Domain contributors who provide technical review, boundary validation, and domain input prior to merge.
* **I (Informed):** Team members kept updated on deliverable completion, architectural decisions, and branch merges.

| Sprint 2 Assessed Deliverable / Activity | Product Owner<br>(Zeynep Bozdemir) | Lead Architect<br>(Mehmet Kocagöz) | Scrum Master<br>(Anıl Güngör) | QA Engineer<br>(Tuğçe Ertem) | DevOps Engineer<br>(Azra Dostbil) | Implementation Eng.<br>(M. Fatih Ağaç) |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **1. Detailed Functional SRS (`docs/sprint2/SRS.md`) — [B1]** | **A** / R | C | I | C | I | C |
| **2. Refined Product Backlog (`docs/sprint2/Backlog.md`) — [B2]** | **A** / R | C | R | C | I | C |
| **3. Non-Functional Requirements (`docs/sprint2/NFR.md`) — [B3]** | C | C | I | **A** / R | C | I |
| **4. UI/UX Prototypes (Figma) & User-Flows (`docs/sprint2/design/`) — [B4]** | C | C | I | C | I | **A** / R |
| **5. Software Architecture: C4 Models (`docs/sprint2/architecture/`) — [B5]** | C | **A** / R | I | C | C | C |
| **6. UML Diagrams (Class, Sequence, State, Use-Case) — [B5]** | C | **A** / R | I | C | I | C |
| **7. Sprint 2 Agile Board, RACI Matrix & Issue Audit — [A6, A7, SCRUM-02]** | C | C | **A** / R | C | I | I |
| **8. Sprint 2 Quality Audit, Test Plan & Revised DoD (`docs/sprint2/quality.md`) — [B6]** | C | C | R | **A** / R | C | I |
| **9. Branch Protection (`protect-main`) & Release `v0.2.0-sprint2` — [A4, B7]** | I | C | C | C | **A** / R | C |

---

## 3. Agile Process Records: Retrospective, Stand-ups & Impediment Log

### 3.1 Sprint 1 Retrospective Summary (Transition to Sprint 2)
* **Date Conducted:** November 10, 2026  
* **Facilitator:** Anıl Güngör (Scrum Master)  
* **Participants:** All 6 members of Team 13  

| Retrospective Category | Team Observations & Findings | Concrete Action Item for Sprint 2 | Assigned Owner |
|---|---|---|---|
| **What Went Well (Continue)** | Defining the OpenAPI 3.1.0 specification (`api/openapi.yaml`) and HTTP 409 concurrency error catalog in Sprint 1 eliminated ambiguity around listing vs. item quantities and doorstep QR handovers. | Use `api/openapi.yaml` schemas directly as the single source of truth for `SRS.md`, UML Class attributes, and Figma UI form fields. | Mehmet Kocagöz & Zeynep Bozdemir |
| **What Needs Improvement (Improve)** | In Sprint 1, `CONTRIBUTIONS.md` was missing the clickable Issue #7 link under Muhammed Fatih Ağaç, and the integration branch name had a typo (`develope`). | Audit all Sprint 1 Issue links (**A6**), fix `CONTRIBUTIONS.md` link traceability, and standardize the integration branch name to `develop` (**A3**). | Anıl Güngör & M. Fatih Ağaç |
| **What to Stop (Stop)** | Avoid editing a single monolithic markdown file across 6 members simultaneously, which causes merge conflicts. | Split Sprint 2 deliverables into modular files (`SRS.md`, `Backlog.md`, `NFR.md`, `quality.md`, `AGILE_AND_RACI_GOVERNANCE.md`, `design/`, `architecture/`) merged via separate PRs into `develop` (**B8**). | All Team Members |

---

### 3.2 Sprint 2 Ceremony & Stand-up Log

| Ceremony / Stand-up | Date & Duration | Facilitator / Attendees | Key Agenda & Decisions |
|---|---|---|---|
| **Sprint 2 Planning & Task Breakdown (A & B Phases)** | Nov 11, 2026 (45 min) | Anıl Güngör (6/6 present) | Established the 10-step **Phase A (Repo & Governance Setup: A1–A10)** and 9-step **Phase B (Sprint 2 Deliverables: B1–B9)** execution plan and updated the Sprint 2 RACI matrix. |
| **Stand-up #1 (Phase A Verification & Issue Audit)** | Nov 15, 2026 (15 min) | Anıl Güngör (6/6 present) | Verified collaborator invitations (**A1–A2**), audited Sprint 1 Issue links `#2, #3, #4, #5, #6, #7, #9` (**A6**), and identified the missing `#7` link in `CONTRIBUTIONS.md`. |
| **Stand-up #2 (Requirements, NFR & UI Flow Sync)** | Nov 19, 2026 (15 min) | Anıl Güngör (6/6 present) | Coordinated alignment between `SRS.md` (**B1**), `Backlog.md` (**B2**), `NFR.md` (**B3**), and Figma screen flows (**B4**) around transparent itemized food listings. |
| **Stand-up #3 (Architecture, Quality Audit & PR Merges)** | Nov 22–23, 2026 (20 min) | Anıl Güngör (6/6 present) | Merged `SCRUM-02` RACI & Agile Governance ([PR #16](https://github.com/macig102/rescuebite-surplus-food-market/pull/16)) into `develop`, finalized `docs/sprint2/quality.md` (**B6**), and tracked remaining Phase B PR merges (**B8**). |

---

### 3.3 Sprint 2 Impediment Tracking Log

| Impediment ID | Date Raised | Affected Task | Description of Impediment / Blocker | Resolution Action Taken | Owner | Status |
| :---: | :---: | :---: | --- | --- | --- | :---: |
| **IMP-01** | Nov 15, 2026 | **A3** (`develop` branch) | Integration branch was initially named `develope` instead of `develop`. | Renamed/standardized branch to `develop` on GitHub so all Sprint 2 PRs target `develop`. | M. Fatih Ağaç | **Resolved** |
| **IMP-02** | Nov 15, 2026 | **A6 & A8** (`CONTRIBUTIONS.md`) | `CONTRIBUTIONS.md` lacked the clickable link for Fatih's Sprint 1 issue (`Issue #7`). | Audited all Sprint 1 links (`#2, #3, #4, #5, #6, #7, #9`) and added `[Issue #7](.../issues/7)` and `[PR #2](.../pull/2)` to `CONTRIBUTIONS.md`. | Anıl Güngör | **Resolved** |
| **IMP-03** | Nov 18, 2026 | **B1–B6** (Parallel PRs) | Editing a single report file risked Git merge conflicts among 6 contributors. | Partitioned Sprint 2 outputs into independent modular files (`SRS.md`, `Backlog.md`, `NFR.md`, `quality.md`, `AGILE_AND_RACI_GOVERNANCE.md`, `design/`, `architecture/`). | Anıl Güngör & Azra Dostbil | **Resolved** |
| **IMP-04** | Nov 20, 2026 | **B4 & B5** (Domain Consistency) | Ensuring UI prototypes and C4/UML diagrams strictly reflect transparent itemized listings (no mystery boxes) and HTTP 409 concurrency locks. | Enforced `api/openapi.yaml` schema verification in `docs/sprint2/quality.md` (**B6**). | Tuğçe Ertem & Mehmet Kocagöz | **Resolved** |

---

## 4. Sprint 1 Issue Link Audit Report (Task A6 Verification Evidence)

As required by **Task A6 (`Sprint 1 Issue linklerini kontrol et`)**, all issue and PR references across `CONTRIBUTIONS.md` were audited against the live GitHub repository:

| Reference Number | Assigned Team Member | GitHub URL | Live Verification Result |
|:---:|---|---|---|
| **#2** | Mehmet Kocagöz | `https://github.com/macig102/rescuebite-surplus-food-market/pull/2` | ✅ **Valid Pull Request** (`docs: add CONTRIBUTIONS.md link to README` — Merged) |
| **#3** | Mehmet Kocagöz | `https://github.com/macig102/rescuebite-surplus-food-market/issues/3` | ✅ **Valid Issue** (`[US-01]: Platform Admin Store Approval` — Open) |
| **#4** | Zeynep Bozdemir | `https://github.com/macig102/rescuebite-surplus-food-market/issues/4` | ✅ **Valid Issue** (`[US-08]: Food Waste Rescued Metrics` — Open) |
| **#5** | Azra Dostbil | `https://github.com/macig102/rescuebite-surplus-food-market/issues/5` | ✅ **Valid Issue** (`[GIT-01]: Git-Flow Rules, Branch Protection & Templates` — Open) |
| **#6** | Tuğçe Ertem | `https://github.com/macig102/rescuebite-surplus-food-market/issues/6` | ✅ **Valid Issue** (`[US-07]: Sprint 1 End-to-End Quality Assurance (QA) Testing` — Open) |
| **#7** | Muhammed Fatih Ağaç | `https://github.com/macig102/rescuebite-surplus-food-market/issues/7` | ✅ **Valid Issue** (`[US-03]: Package Discovery & Filtering` — Added clickable link to `CONTRIBUTIONS.md`) |
| **#9** | Anıl Güngör | `https://github.com/macig102/rescuebite-surplus-food-market/issues/9` | ✅ **Valid Issue** (`[SCRUM-01]: Agile Sprint Board & Issue Tracking Setup` — Open) |

---

## 5. Sprint 2 Work Packages, Kanban Tracking & Deliverable Map (Phase A & Phase B)

The table below tracks the live repository status of each Sprint 2 work package in strict alignment with the team's **A1–A10** and **B1–B9** work breakdown:

| Task Code | GitHub Issue | Sprint 2 Deliverable / Work Package | Responsible Owner (GitHub) | Target File / Artifact in Repository | Current Repository Status |
|:---:|:---:|---|---|---|---|
| **A1–A3** | — | Collaborator Invitations & `develop` Branch Standardization | **Muhammed Fatih Ağaç** (`@macig102`) | GitHub Settings & `develop` branch | **Completed (`develop` active)** |
| **A4–A5** | — | Branch Protection (`protect-main`) & `v0.1.0-sprint1` Tag Verification | **Azra Dostbil** (`@azra-428`) | GitHub Rulesets & Releases (`v0.1.0-sprint1`) | **Completed (`v0.1.0-sprint1` verified)** |
| **A6 & A7** | [#18–#24](https://github.com/azra-428/rescuebite-surplus-food-market/issues) | Sprint 1 Issue Links Audit (`#2`–`#9`) & Sprint 2 Issues Creation (`#18`–`#24`) | **Anıl Güngör** (`@anlgr`) | [`CONTRIBUTIONS.md`](../../CONTRIBUTIONS.md) & [`issuesA.txt`](../../issuesA.txt) | **Completed (All 7 Issues Created & Assigned)** |
| **SCRUM-02** | [Issue #20](https://github.com/azra-428/rescuebite-surplus-food-market/issues/20) | Sprint 2 RACI Matrix, Agile Ceremonies & Impediment Governance | **Anıl Güngör** (`@anlgr`) | [`docs/sprint2/AGILE_AND_RACI_GOVERNANCE.md`](AGILE_AND_RACI_GOVERNANCE.md) | **Completed (Merged via [PR #16](https://github.com/azra-428/rescuebite-surplus-food-market/pull/16))** |
| **B1** | [Issue #18](https://github.com/azra-428/rescuebite-surplus-food-market/issues/18) | Detailed Software Requirements Specification (SRS) | **Zeynep Bozdemir** (`@zeynepbozdemirrr`) | `docs/sprint2/SRS.md` | **In Progress (Assigned to Zeynep)** |
| **B2** | [Issue #18](https://github.com/azra-428/rescuebite-surplus-food-market/issues/18) | Refined Product Backlog (Sprint 2) | **Zeynep Bozdemir** (`@zeynepbozdemirrr`) | `docs/sprint2/Backlog.md` | **In Progress (Assigned to Zeynep)** |
| **B3** | [Issue #19](https://github.com/azra-428/rescuebite-surplus-food-market/issues/19) | Non-Functional Requirements (NFR) & Quality Measures | **Tuğçe Ertem** (`@tugce-951`) | `docs/sprint2/NFR.md` | **In Progress (Assigned to Tuğçe)** |
| **B4** | [Issue #22](https://github.com/azra-428/rescuebite-surplus-food-market/issues/22) | Figma UI/UX Prototypes & User-Flow Diagrams | **Muhammed Fatih Ağaç** (`@macig102`) | `docs/sprint2/design/` & `README.md` | **In Progress (Assigned to Fatih)** |
| **B5** | [Issue #21](https://github.com/azra-428/rescuebite-surplus-food-market/issues/21) | Software Architecture: C4 Model & UML Diagrams | **Mehmet Kocagöz** (`@mehmetkocagozz`) | `docs/sprint2/architecture/` & `README.md` | **In Progress (Assigned to Mehmet)** |
| **B6** | [Issue #23](https://github.com/azra-428/rescuebite-surplus-food-market/issues/23) | Sprint 2 Quality Audit (Test Plan, Revised DoD & CI Verification) | **Anıl Güngör** (`@anlgr`) & **Tuğçe Ertem** (`@tugce-951`) | [`docs/sprint2/quality.md`](quality.md) & [`.github/workflows/ci-quality-gate.yml`](../../.github/workflows/ci-quality-gate.yml) | **Completed (Submitted for PR Merge)** |
| **B7** | [Issue #24](https://github.com/azra-428/rescuebite-surplus-food-market/issues/24) | Release `v0.2.0-sprint2` Tag & GitHub Release Packaging | **Azra Dostbil** (`@azra-428`) | GitHub Release `v0.2.0-sprint2` | **Scheduled after B1–B6 PR Merges** |
