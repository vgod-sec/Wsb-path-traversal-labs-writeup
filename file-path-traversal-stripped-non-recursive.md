# 🔒 Lab: File Path Traversal, Traversal Sequences Stripped Non-Recursively

**Platform:** PortSwigger Web Security Academy  
**Category:** File Path Traversal  
**Difficulty:** Practitioner  

---

##  Description

This lab contains a path traversal vulnerability in the display of product images.  
The application strips path traversal sequences (`../`) from the user-supplied filename **non-recursively**, meaning that encoded or obfuscated payloads can still be used to bypass the filter.


## Objective

> Retrieve the contents of the `/etc/passwd` file.
> 

##  Exploitation Steps

1. Intercept a product image request using **Burp Suite**.
2. Look for a request like:
3. GET /image?filename=example.jpg
4.Modify the `filename` parameter to a payload that bypasses non-recursive filters:
5. ....//....//....//etc/passwd
6.  Forward the request.
7. You will see the contents of the `/etc/passwd` file in the HTTP response.

---

## ✅l Result

Successfully retrieved the contents of `/etc/passwd`, completing the lab.


## 📚 Key Takeaways

- Applications that strip traversal sequences in a non-recursive manner are still vulnerable.
- Bypass filters with double dot and slash obfuscation, e.g., `....//`.
- Always test for multiple traversal payloads to identify weak input validation.  
