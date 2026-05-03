## IDOR Detection
### What happened
After gaining a valid authentication token through SQL injection, I tested access to object-based endpoints.

By modifying IDs in requests like:
- /rest/basket/1
- /rest/basket/5

I was able to access data belonging to different users.

The application required authentication, but did not validate ownership of the resource.

---

### Indicators
- Sequential ID access (/1 → /2 → /3)
- Access to resources with different user IDs
- Authenticated requests accessing unrelated user data
- Repeated requests to object-based endpoints

---

### Example
GET /rest/basket/1  
GET /rest/basket/5  

Response difference:
- "UserId": 1  
- "UserId": 16  

This indicates access to another user's data.

---

### Detection Ideas
- Alert on ID enumeration patterns
- Compare authenticated user vs resource owner
- Detect abnormal access patterns
- Monitor access to sensitive endpoints with changing IDs

---

### Detection Perspective (SOC thinking)
From a SOC perspective, this activity would look like:

- Same session / token making requests to multiple object IDs
- Rapid switching between IDs
- Access to resources not linked to the authenticated user

This could indicate:
- IDOR exploitation
- Data scraping attempts
- Privilege abuse

---

## Attack Chain Example
SQL Injection  
→ Authentication Bypass  
→ Token Access  
→ IDOR Exploitation  
→ Unauthorized Data Access