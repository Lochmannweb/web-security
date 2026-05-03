## IDOR (Broken Access Control)
### IDOR = changing a ID, getting access to something you shouldn't
Find a request like /rest/.../1234, without being logged in

#### Requests
- /rest/products/1/reviews

Since I get data back without being logged in, the system doesn't stop me,
which means that the endpoint is publicly available, but I do have to get data that I shouldn't have access to for it to be IDOR.

---

### Is the data I got meant to be published or not
- find endpoints like:
- /rest/user/whoami
- /rest/basket/{id}
- /rest/orders/{id}

---

### Exploitation Process
1. Identified endpoint:  
   /rest/basket/1  

2. Initial request returned:  
   - 401 Unauthorized (no token)

3. Added valid Authorization token obtained from previous SQL injection  

4. Successfully accessed:  
   /rest/basket/1  

5. Modified ID:  
   /rest/basket/5  

6. Received data belonging to another user:  
   - "UserId": 16  
   - Product data included  

---

### Result
Access to other user's basket data by simply modifying the ID.

---

### Why this is IDOR
- The system validates authentication (token required)  
- But does NOT validate ownership of the resource  

---

### Impact
- Unauthorized access to other user's data  
- Exposure of user-related information  
- Potential privacy violation  
- Can lead to further account-based attacks  

---

### Root Cause
Missing authorization checks on object ownership (Broken Access Control)

---

### Tools
- Burp Suite (Proxy + Repeater)

---

## Attack Chain Context
This demonstrates a vulnerability chain where SQL Injection leads to authentication bypass, which is then used to exploit Broken Access Control (IDOR).