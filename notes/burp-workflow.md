## Burp Suite Workflow
### 1. Intercept traffic
- Turn on Proxy
- Capture login or API requests

---

### 2. Send to Repeater
- Right click → Send to Repeater
- Modify inputs manually

---

### 3. Test for vulnerabilities
I usually test:

- SQL Injection (' OR 1=1--)
- IDOR (changing IDs)
- Authentication issues
- Missing authorization

---

### 4. Analyze responses
- Status codes (200, 401, 403)
- Response size differences
- Returned data (UserId, tokens, etc.)

---

### 5. Confirm vulnerability
- Repeat request
- Modify parameters
- Verify access to unauthorized data

---

### Goal
Understanding:
- What the system allows
- What it should NOT allow