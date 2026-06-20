# BUG-002: Session Not Invalidated After Logout

| Field | Detail |
|---|---|
| **Bug ID** | BUG-002 |
| **Severity** | High |
| **Priority** | High |
| **Status** | Open |
| **Module** | Login / Security |
| **TC Reference** | TC_012 |
| **Found Date** | 14/06/2026 |
| **Environment** | Chrome 124 / Windows 11 |

## Steps to Reproduce

1. Navigate to `https://opensource-demo.orangehrmlive.com`
2. Login with `Admin / admin123`
3. Click username dropdown (top-right) → Logout
4. Confirm redirect to Login page
5. Press browser **Back** button

## Expected Result

Browser remains on Login page. Session is fully invalidated — Dashboard is NOT accessible without re-authentication.

## Actual Result

Dashboard loads successfully without re-authentication. Pressing the Back button after logout restores full Dashboard access. Session is not properly invalidated.

## Impact

Anyone with physical or remote access to the browser can access the system after the original user logs out. This is a critical security risk, especially in shared-device environments.

## Reference

NFR-S03 — Session Invalidation on Logout

## Screenshot

*[Đính ảnh chụp màn hình Dashboard hiện ra sau khi bấm Back vào đây]*
