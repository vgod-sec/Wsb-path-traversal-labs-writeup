#  Lab: File path traversal, validation of file extension with null byte bypass

> **Category:** Web Security Academy  
> **Level:** Practitioner 


##  Description

This lab contains a **path traversal vulnerability** in the display of product images.  
The application checks that the file name ends with a `.png` extension.  
However, this can be bypassed using a **null byte injection** (`%00`), allowing access to arbitrary files on the server.

##  Objective

> Retrieve and view the contents of the `/etc/passwd` file.


## 🗃️ Exploitation Steps

1. Intercept the request that fetches a product image using **Burp Suite**.
2. Modify the `filename` parameter to the following payload:
3. ../../../etc/passwd%00.png
4. Forward the request and observe the server's response.
5. You should see the contents of the `/etc/passwd` file.


##  Explanation

- The server validates that the file name ends in `.png`.
- `%00` (null byte) **terminates the string** at the filesystem level.
- The server processes only `/etc/passwd`, but thinks it’s `/etc/passwd.png`.


##  Mitigation

- Sanitize and canonicalize all user-supplied input paths.
- Reject null bytes and control characters.
- Use allow-lists for file access.
- Implement file access sandboxing or chroot jails.
