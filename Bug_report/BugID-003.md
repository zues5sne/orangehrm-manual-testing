# BUG-003: Auto-Generated Employee ID Is Not Unique

| Field | Detail |
|---|---|
| **Bug ID** | BUG-003 |
| **Severity** | Medium |
| **Priority** | Medium |
| **Status** | Open |
| **Module** | PIM |
| **TC Reference** | TC_016 |
| **Found Date** | 16/06/2026 |
| **Environment** | Chrome 124 / Windows 11 |

## Steps to Reproduce

1. Login as Admin
2. Go to PIM > Employee List > Add
3. Observe the auto-generated Employee ID (e.g. `0395`)
4. Fill all required fields (First Name, Last Name)
5. Click Save without changing the ID

## Expected Result

Auto-generated Employee ID should be unique — the system should suggest an ID that is not yet assigned to any existing employee.

## Actual Result

Auto-generated ID (`0395`) already belonged to another employee. An error was shown on Save: "Employee Id already exists". The user is forced to manually find and enter a unique ID.

## Impact

Confusing UX — the user trusts the auto-generated value but must manually correct it before saving. Risk of data entry errors if the duplicate is not noticed in time.

## Reference

FR-PIM-007 — Employee ID auto-generated when adding a new employee

## Screenshot

<img width="1480" height="492" alt="image" src="https://github.com/user-attachments/assets/6dff1d95-5813-48e3-9c03-d86512075447" />

