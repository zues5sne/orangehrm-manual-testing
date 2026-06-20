# 🧪 OrangeHRM Manual Testing Portfolio

> **Manual Functional Testing** project for [OrangeHRM](https://opensource-demo.orangehrmlive.com) — an open-source Human Resource Management System (HRMS).  
> This project demonstrates end-to-end QA skills including requirement analysis, test planning, test design, execution, and bug reporting on a real-world enterprise-style application.

---

## 📋 Project Overview

| Field | Detail |
|---|---|
| **Website Under Test** | https://opensource-demo.orangehrmlive.com |
| **Application Type** | HR Management System (Symfony backend, Vue.js frontend) |
| **Testing Type** | Manual Functional Testing |
| **Tester** | Nguyễn Long Vũ |
| **Test Period** | 10/06/2026 — 20/06/2026 |
| **Environment** | Chrome 124 / Windows 11 / 1920×1080 |

---

## 📊 Test Results Summary

| Metric | Result |
|---|---|
| **Total Test Cases** | 50 |
| **Passed** | 47 |
| **Failed** | 3 |
| **Pass Rate** | 94% |
| **Bugs Found** | 3 confirmed bugs |
| **Overall Status** | ✅ PASSED with 3 defects found |

### Results by Module

| Module | Total TC | Pass | Fail | Pass Rate |
|---|---|---|---|---|
| 🔐 Login | 12 | 10 | 2 | 83.3% |
| 📋 PIM / My Info | 15 | 14 | 1 | 93.3% |
| 🏖️ Leave | 15 | 15 | 0 | 100% |
| 📁 Directory | 8 | 8 | 0 | 100% |
| **TOTAL** | **50** | **47** | **3** | **94%** |

---

## 🐛 Bugs Found

| Bug ID | Title | Severity | Status | Report |
|---|---|---|---|---|
| BUG-001 | Username login is case-insensitive — "ADMIN" accepted same as "Admin" | Medium | Open | [BugID-001.md](./Bug_report/BugID-001.md) |
| BUG-002 | Session not invalidated after logout — Back button restores Dashboard access | High | Open | [BugID-002.md](./Bug_report/BugID-002.md) |
| BUG-003 | Auto-generated Employee ID may duplicate existing IDs | Medium | Open | [BugID-003.md](./Bug_report/BugID-003.md) |

Full tracking also available in [GitHub Issues](https://github.com/zues5sne/orangehrm-manual-testing/issues).

---

## 📁 Repository Structure

```
orangehrm-manual-testing/
│
├── README.md                       ← You are here
│
├── docs/
│   ├── RAD.md                      ← Requirement Analysis Document
│   ├── Test_plan.md                ← Test Plan (ISTQB-style approach)
│   └── Test_scenario.md            ← 47 Test Scenarios across 4 modules
│
├── Test-case/
│   └── OrangeHRM_test-case.xlsx    ← 50 Test Cases with execution results
│
├── Bug_report/
│   ├── BugID-001.md
│   ├── BugID-002.md
│   └── BugID-003.md
│
└── Test-summary/
    └── TEST_SUMMARY_REPORT.md      ← Final test summary and recommendations
```

---

## 📄 Documents

| Document | Description | Link |
|---|---|---|
| 📋 Requirement Analysis (RAD) | System analysis, 28 FR, 47 Test Scenarios, User Flow | [View](./docs/RAD.md) |
| 📝 Test Plan | Scope, Strategy, Entry/Exit Criteria, Risks | [View](./docs/Test_plan.md) |
| 🗂️ Test Scenario | 47 scenarios across 4 modules | [View](./docs/Test_scenario.md) |
| ✅ Test Cases | 50 TC with Steps, Expected & Actual Result, Status | [View](./Test-case/OrangeHRM_test-case.xlsx) |
| 🐛 Bug Reports | 3 confirmed bugs with steps and impact | [View folder](./Bug_report/) |
| 📊 Test Summary | Final results, metrics, recommendations | [View](./Test-summary/TEST_SUMMARY_REPORT.md) |

---

## 🔍 Modules Tested

### 1. 🔐 Login
- Valid login with both Admin and ESS User accounts
- Invalid credentials — error message validation
- Empty field validation
- Password masking
- Case sensitivity & whitespace handling
- Session behavior after logout (security check)

### 2. 📋 PIM / My Info
- Add / edit / delete employee records
- Auto-generated Employee ID
- Personal Details & Contact Details management
- Profile photo upload (format & size validation)
- Search employee by full / partial name
- Role-based access — ESS User restricted to own profile

### 3. 🏖️ Leave
- Leave Entitlement assignment (precondition)
- Apply Leave with valid / invalid date ranges
- Boundary cases: same-day leave, weekend handling
- Admin Approve / Reject leave requests
- Cancel Pending leave requests
- Leave history filtering by date range
- Role-based access — ESS User cannot approve own/others' leave

### 4. 📁 Directory
- Search employee by full / partial name
- Filter by Job Title and Location
- Employee card display (photo, name, job title)
- Filter consistency check across repeated attempts

---

## 🧪 Test Accounts Used

| Account | Type | Purpose |
|---|---|---|
| `Admin` / `admin123` | Admin | Full access — Happy path & administrative testing |
| `testess` / `Test@1234` | ESS User | Created manually — used to test role-based permission restrictions |

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Google Chrome 124 | Primary test browser |
| Google Sheets | Test Case management & execution tracking |
| GitHub Issues | Bug tracking |
| Snipping Tool | Screenshot evidence |

---

## 🔑 Key Findings

### ✅ What Works Well
- Full Leave workflow (Apply → Approve/Reject → Balance update) functions correctly end-to-end
- Leave day calculation correctly excludes weekends — Friday-to-Monday range correctly counted as 2 working days, not 4
- ESS User role permissions are properly enforced across PIM and Leave modules
- Directory search (exact and partial match) and filtering work as expected
- Form validations (required fields) work consistently across all tested modules

### ⚠️ Issues Found
- **Security (High):** Logout does not fully invalidate the session — Back button restores Dashboard access without re-authentication (BUG-002)
- **Security (Medium):** Username field is case-insensitive — "ADMIN" accepted the same as "Admin" (BUG-001)
- **Data Integrity (Medium):** Auto-generated Employee ID can suggest an ID that already belongs to another employee (BUG-003)

### 💡 Personal Notes
During testing, I discovered that:
- **TC_028** required assigning a Leave Entitlement before ESS User could apply for leave — this precondition wasn't obvious from the UI and cost ~30 minutes to figure out
- **TC_034** — initially assumed weekends would be included in leave duration (4 days for Fri–Mon); actual testing showed the system correctly excludes weekends (2 days). Expected Result was revised accordingly
- **TC_016** — found that auto-generated Employee IDs can duplicate existing ones; the system does catch it at save time but the UX around it is confusing
- **TC_008** — system accepts "ADMIN" the same as "Admin" (not case-sensitive), while **TC_009** correctly rejects extra whitespace in the username — an inconsistent validation approach worth noting

---

## 📈 Exit Criteria Status

| Criterion | Status |
|---|---|
| All planned Test Cases executed | ✅ 50/50 |
| All Critical/High FRs verified | ✅ Met |
| All discovered defects logged with severity | ✅ 3/3 on GitHub Issues |
| Test Summary Report completed | ✅ Done |

---

## 📌 How to Review This Portfolio

1. Start with **[RAD](./docs/RAD.md)** to understand the system and requirements
2. Review **[Test Plan](./docs/Test_plan.md)** for testing strategy and scope
3. Check **[Test Scenarios](./docs/Test_scenario.md)** for coverage overview
4. Open **[Test Cases (Excel)](./Test-case/OrangeHRM_test-case.xlsx)** to see detailed execution results
5. Review **[Bug Reports](./Bug_report/)** for the 3 confirmed defects
6. Read **[Test Summary Report](./Test-summary/TEST_SUMMARY_REPORT.md)** for final conclusions and recommendations

---

*Manual Testing Portfolio — Nguyễn Long Vũ — 2026*  
*OrangeHRM | opensource-demo.orangehrmlive.com*
