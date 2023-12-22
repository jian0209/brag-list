# Authentication and Authorization in Applications

[Reference from daily.dev](https://www.permit.io/blog/authentication-vs-authorization?ref=dailydev)

- Authentication: AuthN
- Authorization: AuthZ
- AuthN is the process of who has access to a system.
- AuthZ is the process of what they can do within the system.
- The other words to say:
  - AuthN verifies who someone is.
  - AuthZ verifies what specific applications, files, and data the can access.
- ![auth image](https://media.graphassets.com/resize=width:2402,height:1431/Lsa2537QZ2N7RCgY1nZQ)
- What is Authentication
  - First step in the process of access control.
  - Common authentication methods:
    - Passwords
    - Biometrics
    - Multi-factor authentication
    - OTPs
  - Usually using token-based method for web applications.
- What is Authorization
  - The process of establishing permissions for a user determining the operations that they can perform.
  - Role-Based Access Control (RBAC) is a common model where access rights are grouped by roles, and users are assigned roles based on their responsibilities.