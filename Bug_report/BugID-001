# BUG-001: Username Login Is Case-Insensitive

| Field | Detail |
|---|---|
| **Bug ID** | BUG-001 |
| **Severity** | Medium |
| **Priority** | Medium |
| **Status** | Open |
| **Module** | Login / Security |
| **TC Reference** | TC_008 |
| **Found Date** | 14/06/2026 |
| **Environment** | Chrome 124 / Windows 11 |

## Steps to Reproduce

1. Navigate to `https://opensource-demo.orangehrmlive.com`
2. Enter Username: `ADMIN` (all caps)
3. Enter Password: `admin123`
4. Click Login

## Expected Result

Login fails with error: "Invalid credentials". Username field should be case-sensitive — `ADMIN` should not be treated the same as `Admin`.

## Actual Result

Login succeeds with username `ADMIN` (all caps). System is NOT case-sensitive for the username field. No error message displayed.

## Reference

NFR-S01 — Authentication Security

## Screenshot

*[Đính ảnh chụp màn hình login thành công với username ADMIN vào đây]*
