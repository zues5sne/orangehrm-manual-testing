# OrangeHRM — Test Summary Report

> **Manual Testing Portfolio**

| | |
|---|---|
| **Document ID** | OHM-SR-2026 |
| **Version** | 1.0 |
| **Reference** | OHM-RA-2026, OHM-TP-2026, OHM-TS-2026 |

---

## 1. Project Information

| Field | Detail |
|---|---|
| Project | OrangeHRM Manual Testing Portfolio |
| Website | https://opensource-demo.orangehrmlive.com |
| Tester | Nguyễn Long Vũ |
| Test Period | 10/06/2026 — 20/06/2026 |
| Environment | Chrome 124 / Windows 11 / 1920×1080 |
| Reference | OHM-RA-2026 \| OHM-TP-2026 \| OHM-TS-2026 |

---

## 2. Overall Results

| Total TC | Pass | Fail | Pass Rate | Status |
|---|---|---|---|---|
| 50 | 47 | 3 | 94% | ✅ PASSED with 3 defects found |

---

## 3. Results by Module

| Module | Total TC | Pass | Fail | Pass Rate | Notes |
|---|---|---|---|---|---|
| 🔐 Login | 12 | 10 | 2 | 83.3% | 2 security bugs: case-insensitive login, session not invalidated |
| 📋 PIM / My Info | 15 | 14 | 1 | 93.3% | 1 bug: auto-generated Employee ID duplicates existing IDs |
| 🏖️ Leave | 15 | 15 | 0 | 100% | All scenarios pass, including boundary cases (weekend = 2 days only) |
| 📁 Directory | 8 | 8 | 0 | 100% | All pass — OBS-04 (filter inconsistency) could not be reproduced consistently |
| **TOTAL** | **50** | **47** | **3** | **94%** | |

---

## 4. Confirmed Bugs

| Bug ID | Module | Severity | Status | TC Ref | Title |
|---|---|---|---|---|---|
| BUG-001 | Login | Medium | Open | TC_008 | Username login is case-insensitive — "ADMIN" accepted same as "Admin" |
| BUG-002 | Login | High | Open | TC_012 | Session not invalidated after logout — Back button restores Dashboard access |
| BUG-003 | PIM | Medium | Open | TC_016 | Auto-generated Employee ID may duplicate existing IDs — no uniqueness check on generation |

Full details available in [Bug Reports](../bug-reports/SUMMARY.md) and [GitHub Issues](https://github.com/zues5sne/orangehrm-manual-testing/issues).

---

## 5. Key Findings

### What Works Well ✅

- Full Leave workflow (Apply → Approve/Reject → Balance update) functions correctly end-to-end.
- Leave day calculation correctly excludes weekends — tested with a Friday-to-Monday range, resulting in 2 working days (not 4).
- ESS User role permissions are properly enforced across PIM and Leave modules — cannot view other employees' profiles or approve leave for others.
- Directory search (exact and partial match) and filtering work as expected.
- Form validations (required fields) work consistently across Login, PIM, and Leave.

### Issues Found ⚠️

- **Security (High):** Logout does not fully invalidate the session — browser Back button restores access to the Dashboard without re-authentication (BUG-002).
- **Security (Medium):** Username field is case-insensitive — "ADMIN" is accepted the same as "Admin", increasing exposure to credential guessing (BUG-001).
- **Data Integrity (Medium):** Auto-generated Employee ID can duplicate an existing ID. The system does catch this at save time with an error message, but the suggested ID itself is not validated before being shown to the user (BUG-003).

### Notable Test Findings (Not Logged as Bugs)

- TC_034 — Initial assumption was that weekend days would be included in leave duration (4 days for Fri–Mon). Actual testing showed the system correctly excludes weekends (2 days). Expected Result was revised accordingly — this was a testing assumption error, not a system defect.
- TC_009 — Username with leading/trailing spaces (`" admin "`) is correctly rejected, while TC_008 showed case is not enforced. The system is space-sensitive but not case-sensitive — an inconsistent validation approach worth flagging to the dev team even though it's not logged as a standalone bug.

---

## 6. Personal Notes — Tester's Own Observations

**Note 1 — TC_028 — Leave Entitlement setup**
Ban đầu không hiểu tại sao ESS User không apply leave được — cứ nghĩ là bug. Sau 30 phút mới phát hiện phải assign Entitlement trước (TC_028). Đây là precondition quan trọng phải làm trước khi test toàn bộ Leave module.

**Note 2 — TC_034 — Weekend calculation**
Assume lúc đầu: Thứ 6 → Thứ 2 = 4 ngày (tính cả Sat/Sun). Thực tế test ra = 2 ngày (chỉ working days). Phải sửa lại Expected Result. Bài học: không được assume behavior — phải test thật để biết.

**Note 3 — TC_016 — Auto-generated Employee ID**
Phát hiện bug thú vị: hệ thống tự tạo Employee ID nhưng ID đó đã thuộc về người khác. Hệ thống báo lỗi khi save — không mất data. Nhưng UX tệ vì người dùng phải tự tìm ID trống để điền.

**Note 4 — TC_008 — Case sensitivity**
ADMIN/admin123 đăng nhập được — hệ thống không phân biệt hoa/thường cho username. Đây là security weakness vì brute force dễ hơn. Log BUG-001. Ngược lại TC_009 " admin " với spaces bị reject — hệ thống nhạy cảm với spaces nhưng không nhạy cảm với case.

**Note 5 — TC_012 — Session bug**
Bug nghiêm trọng nhất: sau khi logout, bấm Back vẫn vào được Dashboard. Trong môi trường thật đây là lỗi bảo mật nguy hiểm — ai dùng máy chung có thể truy cập tài khoản người khác sau khi họ logout. Log BUG-002 với severity High.

---

## 7. Exit Criteria Status

| Criterion | Status |
|---|---|
| All planned Test Cases executed | ✅ 50/50 |
| All Critical/High FRs verified | ✅ Met |
| All discovered defects logged with severity | ✅ 3/3 logged on GitHub Issues |
| Test Summary Report completed | ✅ This document |

---

## 8. Conclusion & Recommendation

| Item | Detail |
|---|---|
| **Overall** | 94% pass rate (47/50 TC). Core HR workflows function correctly for both Admin and ESS User roles. |
| **Must Fix** | 🔴 BUG-002 (High): Session invalidation — logout must fully clear the session. Back-button access after logout is a real security risk. |
| **Should Fix** | 🟠 BUG-001 (Medium): Username should be case-sensitive. BUG-003 (Medium): Auto-generated Employee ID should be unique before being suggested to the user. |
| **Key Finding** | Leave module correctly calculates working days only — weekends are excluded. Leave approval workflow functions end-to-end without issues. |
| **Recommendation** | ✅ CONDITIONALLY APPROVED — fix BUG-002 before any production-like use. Core functionality meets requirements. |

---

*Document ID: OHM-SR-2026 | Version 1.0*
*Reference: OHM-RA-2026, OHM-TP-2026, OHM-TS-2026*
*— End of OHM-SR-2026 —*
