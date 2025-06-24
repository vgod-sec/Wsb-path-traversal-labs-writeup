# 🔓 File Path Traversal – Absolute Path Bypass

**Goal:** Read `/etc/passwd`



##  Summary

The application blocks `../` traversal but does not block absolute paths. This allows us to directly access system files like `/etc/passwd`.


## 🛠️ Exploit Steps

1. Intercept the image request: GET/image?filename=example.png
2. modify the request parameter to : Get/image?filename=/etc/passwd
3.Forward the request and observe the response.

## Result

The contents of `/etc/passwd` were returned, confirming the vulnerability.

---

##  Fix

- Block absolute paths  
- Use filename whitelists  
- Restrict file access to safe directories
4. 
