# OrangeHRM — Test Scenario

> **Manual Testing Portfolio**

| | |
|---|---|
| **Document ID** | OHM-TS-2026 |
| **Version** | 1.0 |
| **Date** | June 2026 |
| **Reference** | OHM-RA-2026, OHM-TP-2026 |

---

## Overview

| Module | Total Scenarios |
|---|---|
| Login | 12 |
| PIM / My Info | 16 |
| Leave | 16 |
| Directory | 3 |
| **TOTAL** | **47** |

---

## 1. Login Module (TS-LGN-01 to TS-LGN-12)

| Scenario ID | Scenario Description | Type | Related FR |
|---|---|---|---|
| TS-LGN-01 | Verify login succeeds with valid Admin credentials | Positive | FR-LGN-001 |
| TS-LGN-02 | Verify login succeeds with valid ESS User credentials | Positive | FR-LGN-001 |
| TS-LGN-03 | Verify login fails with incorrect password | Negative | FR-LGN-002 |
| TS-LGN-04 | Verify login fails with incorrect username | Negative | FR-LGN-002 |
| TS-LGN-05 | Verify validation when both fields are left empty | Negative | FR-LGN-003 |
| TS-LGN-06 | Verify validation when username field is empty | Negative | FR-LGN-003 |
| TS-LGN-07 | Verify validation when password field is empty | Negative | FR-LGN-003 |
| TS-LGN-08 | Verify password field masks entered characters | Positive | FR-LGN-004 |
| TS-LGN-09 | Verify 'Forgot Password' link navigates correctly | Positive | FR-LGN-005 |
| TS-LGN-10 | Verify login behavior with username in ALL CAPS (case sensitivity) | Edge | FR-LGN-002 |
| TS-LGN-11 | Verify login behavior with leading/trailing spaces in username | Edge | FR-LGN-002 |
| TS-LGN-12 | Verify browser Back button cannot restore session after logout | Edge | FR-LGN-006 |

---

## 2. PIM / My Info Module (TS-PIM-01 to TS-PIM-16)

| Scenario ID | Scenario Description | Type | Related FR |
|---|---|---|---|
| TS-PIM-01 | Verify Admin can add a new employee with all required fields | Positive | FR-PIM-001 |
| TS-PIM-02 | Verify validation when First Name is missing | Negative | FR-PIM-006 |
| TS-PIM-03 | Verify validation when Last Name is missing | Negative | FR-PIM-006 |
| TS-PIM-04 | Verify Employee ID is auto-generated when adding a new employee | Positive | FR-PIM-007 |
| TS-PIM-05 | Verify Admin can edit an existing employee's personal details | Positive | FR-PIM-003 |
| TS-PIM-06 | Verify Admin can delete an employee from the system | Positive | FR-PIM-002 |
| TS-PIM-07 | Verify search by exact employee name returns correct result | Positive | FR-PIM-002 |
| TS-PIM-08 | Verify search by partial employee name returns matching results | Positive | FR-PIM-002 |
| TS-PIM-09 | Verify search with non-existent name returns empty result | Negative | FR-PIM-002 |
| TS-PIM-10 | Verify uploading a valid profile photo (JPG, under 1MB) | Positive | FR-PIM-004 |
| TS-PIM-11 | Verify uploading a profile photo over the size limit | Negative | FR-PIM-004 |
| TS-PIM-12 | Verify ESS User can view own Personal Details | Positive | FR-PIM-003 |
| TS-PIM-13 | Verify ESS User can edit own Contact Details | Positive | FR-PIM-003 |
| TS-PIM-14 | Verify ESS User cannot access another employee's profile | Permission | FR-PIM-003 |
| TS-PIM-15 | Verify ESS User cannot add a new employee | Permission | FR-PIM-001 |
| TS-PIM-16 | Verify Employee ID auto-generation does not produce duplicate IDs | Edge | FR-PIM-007 |


---

## 3. Leave Module (TS-LVE-01 to TS-LVE-16)

| Scenario ID | Scenario Description | Type | Related FR |
|---|---|---|---|
| TS-LVE-01 | Verify Admin can assign Leave Entitlement to an employee | Positive | FR-LVE-002 |
| TS-LVE-02 | Verify ESS User can view their leave balance | Positive | FR-LVE-002 |
| TS-LVE-03 | Verify ESS User can apply for Annual Leave with a valid date range | Positive | FR-LVE-001 |
| TS-LVE-04 | Verify applying leave with start date = today (boundary) | Edge | FR-LVE-001 |
| TS-LVE-05 | Verify validation when end date is before start date | Negative | FR-LVE-001 |
| TS-LVE-06 | Verify applying leave for a single day (start = end date) | Edge | FR-LVE-001 |
| TS-LVE-07 | Verify leave calculation for a date range spanning a weekend | Edge | FR-LVE-006 |
| TS-LVE-08 | Verify applying leave when balance is zero | Negative | FR-LVE-001 |
| TS-LVE-09 | Verify ESS User can cancel a Pending leave request | Positive | FR-LVE-005 |
| TS-LVE-10 | Verify behavior when attempting to cancel an Approved leave request | Edge | FR-LVE-005 |
| TS-LVE-11 | Verify Admin can approve a Pending leave request | Positive | FR-LVE-003 |
| TS-LVE-12 | Verify Admin can reject a Pending leave request with a reason | Positive | FR-LVE-004 |
| TS-LVE-13 | Verify ESS User can filter leave history by date range | Positive | FR-LVE-007 |
| TS-LVE-14 | Verify ESS User cannot approve another employee's leave | Permission | FR-LVE-003 |
| TS-LVE-15 | Verify applying leave with a Comment is saved correctly | Positive | FR-LVE-001 |
| TS-LVE-16 | Verify leave status notification behavior (if applicable in demo) | Low Priority | FR-LVE-008 |


---

## 4. Directory Module (TS-DIR-01 to TS-DIR-03)

| Scenario ID | Scenario Description | Type | Related FR |
|---|---|---|---|
| TS-DIR-01 | Verify employee search by name (exact and partial match) | Positive | FR-DIR-001, FR-DIR-005 |
| TS-DIR-02 | Verify filtering by Job Title and Location | Positive | FR-DIR-002, FR-DIR-003 |
| TS-DIR-03 | Verify Location filter returns consistent results across repeated attempts | Edge | FR-DIR-003 |


---

## 5. Scenario-to-Requirement Traceability Summary

| Module | FRs Covered | Scenarios Written | Coverage |
|---|---|---|---|
| Login | 7 (FR-LGN-001–007) | 12 | 100% — with extra edge cases |
| PIM / My Info | 8 (FR-PIM-001–008) | 16 | 100% — with extra edge cases |
| Leave | 8 (FR-LVE-001–008) | 16 | 100% — with extra edge cases |
| Directory | 5 (FR-DIR-001–005) | 3 | Partial — core flows only |

---

*Document ID: OHM-TS-2026 | Version 1.0 | June 2026*
*Reference: OHM-RA-2026, OHM-TP-2026*
*— End of OHM-TS-2026 —*
