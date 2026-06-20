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

1.Click logout buuton on header

<img width="581" height="440" alt="image" src="https://github.com/user-attachments/assets/792b4ccf-df7d-4051-92fd-c7089d334001" />


2.Click back button
<img width="1272" height="965" alt="image" src="https://github.com/user-attachments/assets/3ced06af-4963-4440-b901-ff95b1f4389c" />


3.Observe result -> session not invalidated after logout
<img width="1918" height="975" alt="image" src="https://github.com/user-attachments/assets/c37d2981-dd61-4047-aef7-4ecc4fc3f7d8" />


