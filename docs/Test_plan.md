# OrangeHRM — Test Plan

> **Manual Testing Portfolio | ISTQB-style approach**

| | |
|---|---|
| **Document ID** | OHM-TP-2026 |
| **Version** | 1.0 |
| **Date** | June 2026 |
| **Reference** | OHM-RA-2026 (Requirement Analysis Document) |

---

## 1. Project Overview

| Field | Detail |
|---|---|
| Project Name | OrangeHRM Manual Testing Portfolio |
| System Under Test | OrangeHRM Open Source Demo |
| URL | https://opensource-demo.orangehrmlive.com |
| Test Type | Manual Functional Testing |
| Modules in Scope | Login, PIM/My Info, Leave, Directory |
| Reference Document | OHM-RA-2026 |
| Document ID | OHM-TP-2026 |

---

## 2. Test Objectives

- Verify all 28 Functional Requirements (FR) identified in OHM-RA-2026 behave as documented.
- Identify defects across 4 core modules: Login, PIM, Leave, Directory.
- Validate both Admin and ESS User role permissions are correctly enforced.
- Confirm boundary and edge-case behaviors (date ranges, file size limits, weekend handling).
- Produce a structured, reviewable testing artifact suitable for a QA portfolio.

---

## 3. Scope

### 3.1 In Scope

| Module | Test Focus |
|---|---|
| Login | Valid/invalid login, validation messages, password masking, session behavior |
| PIM / My Info | Add/edit/delete employee, search, photo upload, role-based field visibility |
| Leave | Apply/approve/reject/cancel leave, balance calculation, date validation |
| Directory | Search, filter by Job Title/Location, employee card display |

### 3.2 Out of Scope

- Performance, Recruitment, Payroll modules
- Mobile / responsive testing
- Automated/API testing
- Load and performance testing
- Penetration/security testing (beyond basic session checks)

---

## 4. Test Strategy

| Test Level | Approach |
|---|---|
| Functional Testing | Manual execution against documented FRs and scenarios |
| Negative Testing | Invalid inputs, boundary values, empty required fields |
| Exploratory Testing | Free-form exploration to discover undocumented behavior |
| Regression (light) | Re-test affected areas after any environment reset |

**Test Design Techniques Used:**
- Equivalence Partitioning (e.g. valid/invalid date ranges)
- Boundary Value Analysis (e.g. file size limits, leave balance = 0)
- Error Guessing (based on prior testing experience from SauceDemo project)


---

## 5. Test Environment

| Item | Detail |
|---|---|
| Browser | Google Chrome 124 (primary) |
| OS | Windows 11 |
| Resolution | 1920×1080 |
| URL | https://opensource-demo.orangehrmlive.com |
| Admin Account | Admin / admin123 |
| ESS Account | Created manually via Admin → User Management (e.g. testess / Test@1234) |
| Bug Tracking | GitHub Issues |
| Test Case Management | Google Sheets |


## 6. Entry Criteria

- OHM-RA-2026 (Requirement Analysis Document) completed and reviewed.
- Test Scenarios (OHM-TS-2026) drafted and approved.
- Demo environment accessible and Admin credentials verified working.
- ESS test account created and confirmed functional.

## 7. Exit Criteria

- All planned Test Cases executed at least once.
- All Critical and High priority Functional Requirements verified.
- All discovered defects logged in GitHub Issues with severity assigned.
- Test Summary Report completed with Pass/Fail metrics.


---

## 8. Test Deliverables

| Deliverable | Status |
|---|---|
| Requirement Analysis Document (OHM-RA-2026) | Completed |
| Test Plan (this document, OHM-TP-2026) | Completed |
| Test Scenarios (OHM-TS-2026) | Completed |
| Test Cases (Google Sheets) | Completed — 50 TC |
| Bug Reports (GitHub Issues) | Completed — 3 confirmed bugs |
| Test Summary Report | Completed |

---

## 9. Roles & Responsibilities

| Role | Responsibility | Assigned to |
|---|---|---|
| Test Designer | Write RAD, Test Scenarios, Test Cases | QA Fresher (self) |
| Tester / Executor | Execute test cases, log results | QA Fresher (self) |
| Defect Reporter | Log and track bugs via GitHub Issues | QA Fresher (self) |


---

## 10. Risks & Mitigation

| Risk | Impact | Mitigation |
|---|---|---|
| Shared demo data reset/altered by other users | Medium | Re-verify test data before re-running affected test cases; document environment state |
| Undocumented business rules (file size limits, session timeout) | Medium | Mark as "to be confirmed" in Test Cases/RAD rather than guessing |
| No peer review of test design | Low-Medium | Self-review pass added before finalizing each document |
| Limited testing time (1-person, part-time effort) | Medium | Prioritized Critical/High FRs first; Low priority items tested last or partially |

---

## 11. Schedule (Approximate)

| Phase | Duration |
|---|---|
| Requirement Analysis (RAD) | 2-3 days |
| Test Plan | 1 day |
| Test Scenario Design | 1-2 days |
| Test Case Design | 2-3 days |
| Test Execution | 3-4 days |
| Bug Reporting & Summary | 1-2 days |

---

## 12. Lessons Learned (Test Planning Phase)

- Underestimated time needed for the Leave module — calendar/date logic had more edge cases than initially planned for.
- Should have created the ESS test account earlier — several Leave test cases were blocked until Leave Entitlement was assigned, which wasn't obvious from the UI alone.
- Writing "to be confirmed" notes during planning (rather than guessing) saved time later — it flagged exactly which Expected Results needed revision after real testing.

---

*Document ID: OHM-TP-2026 | Version 1.0 | June 2026*
*Reference: OHM-RA-2026*
*— End of OHM-TP-2026 —*
