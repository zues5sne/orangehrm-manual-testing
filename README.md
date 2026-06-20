# OrangeHRM — Manual Testing Portfolio

Manual functional testing project on the [OrangeHRM](https://opensource-demo.orangehrmlive.com) open-source HRMS demo. Built as a hands-on QA portfolio — covering requirement analysis, test design, execution, and bug reporting across four core modules.

---

## 🎯 Project Overview

| | |
|---|---|
| **System Under Test** | [OrangeHRM Open Source Demo](https://opensource-demo.orangehrmlive.com) |
| **Test Type** | Manual Functional Testing |
| **Modules Covered** | Login, PIM / My Info, Leave, Directory |
| **User Roles** | Admin, ESS User (Employee Self Service) |
| **Functional Requirements** | 28 |
| **Test Cases** | 50 |
| **Pass Rate** | 94% (47/50) |
| **Bugs Found** | 3 |

This project simulates a real QA workflow on a live HR system — from reading the application's behavior, to writing structured test cases, to actually finding and documenting defects.

---

## 📂 Repository Structure

```
orangehrm-manual-testing/
├── docs/             → Requirements analysis & test planning documents
├── Test-case/        → Test cases by module (.md)
├── Bug_report/        → Defects found during execution (.md)
├── Test-summary/      → Test execution summary & results (.md)
└── README.md
```

| Folder | Contents |
|---|---|
| [`docs/`](./docs) | Requirements & Analysis Document, Test Plan |
| [`Test-case/`](./Test-case) | Manually written test cases — happy path, negative, boundary, and permission scenarios |
| [`Bug_report/`](./Bug_report) | Defect reports with repro steps, expected vs. actual result, and severity |
| [`Test-summary/`](./Test-summary) | Execution results and overall test summary |

---

## 📊 Results by Module

| Module | Test Cases | Pass | Fail | Pass Rate |
|---|---|---|---|---|
| 🔐 Login | 12 | 10 | 2 | 83.3% |
| 📋 PIM / My Info | 15 | 14 | 1 | 93.3% |
| 🏖️ Leave | 15 | 15 | 0 | 100% |
| 📁 Directory | 8 | 8 | 0 | 100% |
| **Total** | **50** | **47** | **3** | **94%** |

> Test Period: 10/06/2026 – 20/06/2026 · Environment: Chrome 124 / Windows 11 / 1920×1080

---

## 🧩 Scope

**In Scope**
- Login / Authentication
- PIM — Employee Profile & My Info
- Leave — Apply, Approve, Reject, Cancel
- Directory — Search & Filter

**Out of Scope**
- Performance, Recruitment, Payroll modules
- Automated testing
- Mobile / responsive testing

A key focus of this project is **role-based permission testing** — verifying that Admin-only actions (managing employees, approving leave) are correctly blocked for ESS Users, and that ESS Users can only access their own data.

| Feature | Admin | ESS User |
|---|---|---|
| Add / Delete Employee | ✅ Allowed | ⛔ Must be blocked |
| Approve / Reject Leave | ✅ Allowed | ⛔ Must be blocked |
| Apply Own Leave | ✅ Allowed | ✅ Allowed |
| View Directory | ✅ Allowed | ✅ Allowed |

---

## 🐞 Confirmed Bugs

3 defects found and logged during test execution (50 test cases, 94% pass rate):

| Bug ID | Module | Severity | Issue |
|---|---|---|---|
| BUG-002 | Login | 🔴 High | Session not invalidated after logout — browser Back button restores Dashboard access without re-authentication |
| BUG-001 | Login | 🟠 Medium | Username login is case-insensitive — `ADMIN` is accepted the same as `Admin` |
| BUG-003 | PIM | 🟠 Medium | Auto-generated Employee ID can suggest a value that already exists — caught at save time, but not validated before being shown |

**Must fix:** BUG-002 — a real security risk on shared machines, since a logged-out session can still be accessed via Back button.

Full details — steps to reproduce, expected vs. actual result — are in [`Bug_report/`](./Bug_report) and the [Test Summary Report](./Test-summary).

---

## 🛠️ How to Reproduce This Testing

1. Go to the demo site: `https://opensource-demo.orangehrmlive.com`
2. Log in as Admin: `Admin / admin123`
3. Create an ESS User account (**Admin → User Management → Add User**, role: ESS, linked to an employee)
4. Assign a Leave Entitlement to that employee (**Leave → Entitlements → Add Entitlements**) — required before the ESS User can apply for leave
5. Use the test cases in [`Test-case/`](./Test-case) to execute manually, recording actual results against expected results

---

## 📝 Notes

- Leave duration correctly excludes weekends — a Friday-to-Monday range resolves to 2 working days, not 4. This was an initial testing assumption error on my part, corrected after actually running the test (see TC_034 in the Test Summary Report).
- ESS User role permissions are properly enforced across PIM and Leave — cannot view other employees' profiles or approve leave for others.
- This is a public demo environment shared by many testers — data may be reset or modified by others, which can affect reproducibility.
- This project is part of an ongoing QA portfolio. Feedback and suggestions are welcome via [Issues](../../issues).

---

## 👤 Author

**Nguyễn Long Vũ** — Fresher QA Tester
📧 [your-email@gmail.com](mailto:0945862729vu@gmail.com) · 💻 [GitHub](https://github.com/zues5sne)
