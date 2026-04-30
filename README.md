# Web Security

This repository contains hands-on web security testing exercises based on labs from platforms like: 
- TryHackMe 
- Hack The Box.


## Focus Areas
- OWASP Top 10
- Access Control (IDOR)
- Authentication & Session Management
- SQL Injection
- JWT Analysis


## Lab Writeups
### 1. IDOR Vulnerability
- Identified insecure direct object reference via parameter manipulation
- Exploited by modifying user ID in request
- Impact: Unauthorized data access
- Mitigation: Implement proper access control checks

### 2. Authentication Testing
- Tested login flow and session handling
- Observed lack of proper validation in edge cases
- Impact: Potential account compromise
- Mitigation: Strengthen validation and session controls
