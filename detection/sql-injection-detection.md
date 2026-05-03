## SQL Injection Detection
### What happened
I identified a SQL injection vulnerability in the login endpoint by injecting:

' OR 1=1--

This resulted in a successful login without valid credentials and returned a valid authentication token.

This shows that user input was not properly sanitized and was directly used in a database query.

---

### Indicators
- SQL keywords in input (' OR 1=1--)
- Authentication success with clearly invalid input
- Unusual authentication patterns
- Sudden privilege change (user → admin)

---

### Example
POST /rest/user/login  

Payload:
email=' OR 1=1--  
password=anything  

Response:
- Login successful
- Authentication token returned

---

### Detection Ideas
- Alert on SQL keywords in input fields
- Monitor mismatch between input and login success
- Track abnormal login success rate
- Detect privilege escalation after login

---

### Detection Perspective (SOC thinking)
From a SOC perspective, this activity would look like:

- Login attempts containing SQL-like payloads
- Successful authentication with invalid credentials
- Immediate access to admin endpoints after login

This could indicate:
- SQL injection attack
- Authentication bypass
- Early-stage compromise

---

### Example Log Pattern (simplified)
POST /rest/user/login  
email=' OR 1=1--  

→ 200 OK (login success)

Followed by:

GET /rest/admin/application-configuration  

→ Indicates possible compromise

---

## Attack Chain Context
SQL Injection  
→ Authentication Bypass  
→ Token Access  
→ Admin Endpoint Access  
→ Potential Full System Compromise