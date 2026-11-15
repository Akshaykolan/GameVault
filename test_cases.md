# Question 2 — Login System Test Case Design

**Application:** Login System  
**Inputs:** Username, Password, and Login button.

## Test assumptions

- Sample valid account: username `user1`, password `pass123`.
- Password length is measured in characters; exactly 6 characters satisfies the minimum requirement.
- A failed authentication attempt is counted only when both fields pass input validation and the credentials are rejected.
- Lockout tests use a fresh account or reset test environment so the attempt counter starts at zero.
- No lockout duration is specified; the expected state is simply **locked**.

## Test case table

| Test Case ID | Test Scenario | Input Data | Expected Output |
|---|---|---|---|
| TC_01 | Submit with an empty username | Username: empty; Password: `pass123`; click Login | Login is not submitted. Display “Username is required.” No failed attempt is added. |
| TC_02 | Submit with an empty password | Username: `user1`; Password: empty; click Login | Login is not submitted. Display “Password is required.” No failed attempt is added. |
| TC_03 | Password shorter than 6 characters | Username: `user1`; Password: `abc12` (5 characters); click Login | Login is not submitted. Display “Password must be at least 6 characters.” |
| TC_04 | Password exactly 6 characters | Username: `user1`; Password: `abc123` (6 characters); click Login | Length validation passes. Credentials are invalid. Display “Invalid username or password.” Count one failed attempt. |
| TC_05 | Login with valid credentials | Username: `user1`; Password: `pass123`; click Login | Display “Login successful.” Allow access to the authenticated/home page. |
| TC_06 | Login with an incorrect password | Username: `user1`; Password: `wrong123`; click Login (attempt 1 of 3) | Display “Invalid username or password.” Account remains unlocked; failed-attempt count becomes 1. |
| TC_07 | Third consecutive failed login attempt | Username: `user1`; Password: `wrong123`; click Login after two previous failed attempts | Display “Account locked after 3 consecutive failed login attempts.” Deny login and mark the account locked. |
| TC_08 | Try logging in after account is locked | Username: `user1`; Password: `pass123`; click Login after TC_07 | Deny login even with correct credentials. Display “Account is locked. Login is not allowed.” |

## Coverage summary

- Username cannot be empty: TC_01.
- Password cannot be empty and must contain at least six characters: TC_02–TC_04.
- Valid credentials allow login: TC_05.
- Invalid credentials produce a clear error: TC_04 and TC_06.
- Three consecutive failed attempts lock the account: TC_07.
- Further login attempts are blocked after lockout: TC_08.
