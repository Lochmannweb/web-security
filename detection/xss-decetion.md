## XSS Detection

### What to look for
- HTML in input (like <img>, <script>, <svg>)
- JavaScript events (onerror, onload)
- Weird input in search or forms
- Strange encoded stuff in URLs

### Example
GET /#/search?q=<img src=x onerror=alert(1)>

### Detection ideas
- Look for HTML/JS in user input
- Watch for weird search queries
- Look for repeated attempts with different payloads

### Extra note
I was able to read some cookies:
- language
- welcomebanner_status
- continueCode

They are not sensitive, but still shows that not everything is protected.

### Why it matters
If this was real login/session cookies, it could be used to take over accounts.