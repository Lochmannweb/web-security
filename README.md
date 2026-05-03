# Web Security & Threat Analysis Portfolio

This repository documents my hands-on work in web security, focusing on:

- Identifying vulnerabilities  
- Exploiting them in a controlled environment  
- Understanding how attacks work  
- Thinking from a SOC / detection perspective  

---

## Key Cases

### SQL Injection → Auth Bypass → Admin Access
- Bypassed login using SQL injection  
- Obtained a valid authentication token  
- Accessed admin-only functionality  
- Demonstrates full authentication bypass  

### IDOR (Broken Access Control)
- Accessed other users' data by modifying object IDs  
- Required valid authentication but no ownership validation  
- Demonstrates broken authorization logic  

---

## Detection Mindset

For each case, I include:

- Indicators of compromise  
- Suspicious behavior patterns  
- Detection ideas from a SOC perspective  

Focus:
- Detecting abnormal authentication behavior  
- Identifying privilege escalation  
- Recognizing ID enumeration patterns  

---

## Tools

- Burp Suite (Proxy, Repeater, Intruder)  
- Browser DevTools  

---

## Ongoing Learning

- OWASP Juice Shop  

---

## About Me

Professional Bachelor in Web Development (Web Security specialization)

Focused on:
- Cybersecurity  
- Threat detection  
- Understanding attacker behavior  
- Practical security testing  

---

## CV

Available in the `/CV` folder