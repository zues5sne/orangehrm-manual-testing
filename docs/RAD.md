# OrangeHRM — Requirement Analysis Document

> **Manual Testing Portfolio**

| | |
|---|---|
| **Document ID** | OHM-RA-2026 |
| **Version** | 1.0 |
| **Date** | June 2026 |
| **Prepared by** | QA Fresher — Personal Portfolio Project |
| **System Under Test** | https://opensource-demo.orangehrmlive.com |

---

## 1. Document Overview

| Field | Detail |
|---|---|
| Document Name | OrangeHRM Requirement Analysis Document |
| Document ID | OHM-RA-2026 |
| System Under Test | OrangeHRM Open Source Demo |
| System URL | https://opensource-demo.orangehrmlive.com |
| Login Credentials | Admin / admin123 |
| Test Type | Manual Functional Testing |
| Modules Tested | Login, PIM/My Info, Leave, Directory |
| Total FRs Identified | 28 Functional Requirements |
| Total Test Scenarios | 47 scenarios |
| Prepared by | QA Fresher (Personal Portfolio Project) |
| Date Created | June 2026 |
| Status | Draft — Under Review |

> **Note:** This document was written after one week of self-exploring the OrangeHRM demo. Some behaviors are not 100% confirmed — clearly flagged in their respective sections. This is a personal portfolio project, not an official company document.

---

## 2. Scope & Test Objectives

### 2.1 In Scope

- Login / Authentication module
- PIM — Employee Records & Personal Information (My Info)
- Leave — Apply, Approve, and Cancel Leave
- Directory — Search & View Employee Information

### 2.2 Out of Scope

- Performance, Recruitment, Payroll modules
- Mobile / responsive testing
- Non-functional testing: performance, security

> **[?] To be confirmed:** 'Buzz' module (internal social feed) — unclear whether it's in scope; skipped for now.

---

## 3. Functional Requirements (28 FR)

> **Note:** The number 28 FR is the result of merging some duplicate sub-requirements. The initial list had 31 FR but 3 of them had very similar behavior so they were merged for clarity.

### 3.1 Login Module — FR-LGN-001 to FR-LGN-007

| FR ID | Requirement Description | Priority | Notes |
|---|---|---|---|
| FR-LGN-001 | System allows login with valid Admin credentials | Critical | |
| FR-LGN-002 | System rejects login with incorrect username/password | Critical | |
| FR-LGN-003 | System displays an error message on failed login | High | |
| FR-LGN-004 | Password field must mask input characters | High | |
| FR-LGN-005 | 'Forgot Password' link must be visible on login page | Medium | |
| FR-LGN-006 | Session must expire after a period of inactivity | Medium | Need to confirm exact timeout duration |
| FR-LGN-007 | System redirects to Dashboard after successful login | Critical | |

### 3.2 PIM / My Info Module — FR-PIM-001 to FR-PIM-008

| FR ID | Requirement Description | Priority | Notes |
|---|---|---|---|
| FR-PIM-001 | Admin can add a new employee to the system | Critical | |
| FR-PIM-002 | System displays employee list with search functionality | High | |
| FR-PIM-003 | User can update personal information | High | |
| FR-PIM-004 | Profile photo upload supports JPG/PNG formats | Medium | Size limit unclear — needs further testing |
| FR-PIM-005 | Emergency Contact section supports multiple entries | Medium | |
| FR-PIM-006 | System enforces required fields on save | High | |
| FR-PIM-007 | Employee ID is auto-generated when adding a new employee | High | |
| FR-PIM-008 | Documents can be attached to an employee profile | Low | Not thoroughly tested yet |

### 3.3 Leave Module — FR-LVE-001 to FR-LVE-008

| FR ID | Requirement Description | Priority | Notes |
|---|---|---|---|
| FR-LVE-001 | Employee can submit a leave application | Critical | |
| FR-LVE-002 | System displays remaining leave balance by type | High | |
| FR-LVE-003 | Admin/Manager can approve a leave request | Critical | |
| FR-LVE-004 | Admin/Manager can reject a leave request | Critical | |
| FR-LVE-005 | Employee can cancel a pending leave request | High | |
| FR-LVE-006 | System handles holidays/weekends in leave day calculation | Medium | Behavior unclear in demo env |
| FR-LVE-007 | Leave history can be filtered by date range | Medium | |
| FR-LVE-008 | System sends notification when leave status changes | Low | Demo env — email likely disabled |

### 3.4 Directory Module — FR-DIR-001 to FR-DIR-005

| FR ID | Requirement Description | Priority | Notes |
|---|---|---|---|
| FR-DIR-001 | User can search employees by name | High | |
| FR-DIR-002 | User can filter by Job Title | Medium | |
| FR-DIR-003 | User can filter by Location | Medium | |
| FR-DIR-004 | Directory displays employee card with photo and title | Medium | |
| FR-DIR-005 | Search returns partial match results | High | To be confirmed — partial match works but unclear if intentional |

---

## 4. Test Scenario Summary (47 Scenarios)

> **Note:** 47 scenarios are grouped by module. Some scenarios were added based on edge cases/negative cases discovered while using the real app — not entirely derived from requirements.

| Module | Positive | Negative | Edge Case | Total |
|---|---|---|---|---|
| Login | 4 | 6 | 2 | 12 |
| PIM / My Info | 8 | 5 | 3 | 16 |
| Leave | 7 | 6 | 3 | 16 |
| Directory | 2 | 1 | 0 | 3 |
| **TOTAL** | **21** | **18** | **8** | **47** |

### 4.1 Login Module — Scenario Details

| TC ID | Scenario Description | Type | Expected Result |
|---|---|---|---|
| TC-LGN-01 | Login with valid credentials (Admin/admin123) | Positive | Redirects to Dashboard; username shown in header |
| TC-LGN-02 | Login with incorrect password | Negative | Error shown: 'Invalid credentials' |
| TC-LGN-03 | Leave username field empty, click Login | Negative | Notification requiring username |
| TC-LGN-04 | Leave password field empty, click Login | Negative | Notification requiring password |
| TC-LGN-05 | Leave both fields empty, click Login | Negative | Both error messages displayed simultaneously |
| TC-LGN-06 | Enter SQL injection string in username field | Negative | Rejected; no system error info leaked |
| TC-LGN-07 | Click 'Forgot Password' link | Positive | Redirects to password reset page |
| TC-LGN-08 | Verify password field masking | Positive | Characters displayed as dots or asterisks |
| TC-LGN-09 | Login with username in ALL CAPS (ADMIN) | Edge | **REVISED:** Initially expected case-insensitive login — actual: ADMIN rejected. ER corrected after real testing. |
| TC-LGN-10 | Click browser Back after logout | Edge | Must not return to the ended session |
| TC-LGN-11 | Login with leading/trailing spaces in username | Edge | Needs confirmation — unclear if system trims whitespace |
| TC-LGN-12 | Multiple consecutive failed login attempts | Negative | Unclear — no account lockout observed in demo |

> **Note:** REVISED EXPECTED RESULT — TC-LGN-09: Initially wrote "case-insensitive (common for enterprise HRM systems)" but actual testing showed ADMIN/admin123 was rejected. Corrected. Documented here so reviewers know this was discovered through real testing.

### 4.2 PIM / My Info Module — Scenario Details

| TC ID | Scenario Description | Type | Expected Result |
|---|---|---|---|
| TC-PIM-01 | Add new employee with all required fields filled | Positive | Employee created; ID auto-generated; appears in list |
| TC-PIM-02 | Add new employee without First Name | Negative | Error message on First Name field |
| TC-PIM-03 | Edit employee personal details and save | Positive | Changes saved; success message shown |
| TC-PIM-04 | Upload valid JPG image (under 1MB) | Positive | Image displayed on employee profile |
| TC-PIM-05 | Upload image file over 2MB | Negative | **REVISED:** Initially assumed 5MB limit — actual: 2MB file rejected, 800KB OK. Exact limit not yet determined. |
| TC-PIM-06 | Search employee by partial name | Positive | Returns results matching the search keyword |
| TC-PIM-07 | Search for non-existent employee | Negative | Empty result displayed with appropriate message |
| TC-PIM-08 | Delete an employee from the system | Positive | Employee removed from list; search returns no results |

> **Note:** REVISED EXPECTED RESULT — TC-PIM-05: Assumed 5MB based on common default. After testing: 2MB upload failed, 800KB OK. Exact limit unknown — needs confirmation from developer or system config.

### 4.3 Leave Module — Scenario Details

| TC ID | Scenario Description | Type | Expected Result |
|---|---|---|---|
| TC-LVE-01 | Apply leave within a valid future date range | Positive | Leave request created with status 'Pending' |
| TC-LVE-02 | Apply leave with start date > end date | Negative | Error — invalid date range |
| TC-LVE-03 | Apply leave when leave balance = 0 | Negative | System warns or blocks — exact behavior not yet confirmed |
| TC-LVE-04 | Admin approves a pending leave request | Positive | Status changes to 'Approved'; leave days deducted |
| TC-LVE-05 | Admin rejects a leave request | Positive | Status changes to 'Rejected'; leave days restored |
| TC-LVE-06 | Employee cancels a pending leave request | Positive | Leave request deleted or marked 'Cancelled' |
| TC-LVE-07 | Apply leave spanning Saturday and Sunday | Edge | **REVISED:** Initially expected system to exclude weekends — actual: weekend days ARE counted in leave balance. May be a config setting. |
| TC-LVE-08 | Filter leave history by date range | Positive | Only leave requests within selected date range shown |

> **Note:** REVISED EXPECTED RESULT — TC-LVE-07: Real testing showed the system counts Sat/Sun in leave days. This could be a configurable feature (working days config), not a bug. Needs confirmation from stakeholder or system configuration review.

---

## 5. Tester's Notes — Real-World Observations

### 5.1 Findings From Exploratory Testing

- Demo environment resets periodically — data added during testing may disappear. Affects consistency when re-testing.
- Navigation menu behaves inconsistently when browser window is resized — hamburger icon doesn't appear at narrow widths.
- Leave module: page does NOT auto-refresh after approval — user must manually reload to see updated status.
- Directory: search uses 'contains' matching (partial match), not exact match. Tested with short strings — results returned correctly.
- Photo upload: UI appears to support drag-and-drop but it doesn't actually work. Must use the 'Browse' button.

> **Note:** Emergency Contact section in My Info — multi-entry edge cases not tested due to time constraints. Left for next round.

### 5.2 Potential Bugs Found (Not Yet Formally Reported)

| # | Observation Description | Severity | Status |
|---|---|---|---|
| OBS-01 | After logout, pressing browser Back does not return to the previous session (correct). But session cookie appears to persist longer than expected — needs investigation. | Low | To be confirmed |
| OBS-02 | In PIM: clicking Save twice in quick succession when adding a new employee creates a duplicate record. | Medium | Reproducible 2/3 times |
| OBS-03 | Leave application with start date = today: 'half day' option appears inconsistently. | Medium | Inconsistent — hard to reproduce |
| OBS-04 | Directory: filtering by Location — selecting a value doesn't consistently apply correctly. | Medium | Consistently reproducible |

---

## 6. Risks & Assumptions

### 6.1 Assumptions

- The demo environment accurately reflects real-world OrangeHRM behavior for testing purposes.
- The Admin account (Admin/admin123) has full access to all features under test.
- Email notifications are disabled in the demo environment — this feature is not tested.
- Personal portfolio project — no specific performance SLA requirements.

### 6.2 Risks

- **Data reset:** test data may be deleted by other users or auto-reset — affects consistency when re-testing.
- **Missing requirement documentation:** some behaviors (file size limits, session timeout duration) are undocumented — relying on assumptions.
- **Single tester:** no peer review of scenarios — possible blind spots.

---

## 7. Lessons Learned

> **Note:** This section is genuinely written, not generic filler. These are things I actually learned during one week of exploring OrangeHRM.

- Writing scenarios BEFORE testing helps reveal gaps in my own understanding — I had to rewrite 6 scenarios after using the real app.
- Expected Result is the hardest part to write. "System shows an error" is too vague — need to specify exact message and location.
- Exploratory first, scripted second — the first 2 hours of free exploration surfaced more issues than the entire scripted test pass.
- The habit of writing "to be confirmed" is genuinely useful — it reminds me that my assumptions are not requirements, helping avoid incorrect pass/fail verdicts.
- Shared demo environments are noisy. Other users adding/removing data wasted my time chasing "bugs" that turned out not to be real. Lesson: document environment state when reporting.
- I underestimated the complexity of the Leave module. Calendar logic (weekends, holidays, half-days) has far more edge cases than expected — needs more time allocated.

---

## 8. References

- OrangeHRM Demo: https://opensource-demo.orangehrmlive.com
- Official OrangeHRM Documentation: https://www.orangehrm.com/orangehrm-documentation
- ISTQB Foundation Level Syllabus (reference for test design techniques)

---

*Document ID: OHM-RA-2026 | Version 1.0 | June 2026*
*— End of OHM-RA-2026 —*
