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

1.<img width="1918" height="870" alt="image" src="https://github.com/user-attachments/assets/843dd7c1-04c1-4e7e-acfc-85d595498670" />
2.<img width="1918" height="965" alt="image" src="https://github.com/user-attachments/assets/364ad51c-d993-4458-8ce8-df7d1e0343af" />


