#  Lab: File Path Traversal - Validation of Start of Path

> Category: Web Security Academy – File Path Traversal  
> Difficulty: Practitioner  

##  Lab Description

This lab contains a **path traversal vulnerability** in the display of product images.

The application **transmits the full file path** via a request parameter and **validates** that the supplied path starts with a specific directory (e.g., `/var/www/images/`). Your goal is to **bypass the prefix validation** and access sensitive system files.

> **Objective**: Retrieve the contents of the `/etc/passwd` file.


## 🛠️ Exploitation Steps

### 1.  Intercept Image Request Using Burp Suite

- Open Burp Suite and ensure the **intercept is on**.
- Navigate to a product page that loads an image.
- Capture the request to fetch an image file.

### 2.  Locate and Modify the `filename` Parameter

Example captured request:

GET /image?filename=/var/www/images/image.jpg HTTP/1.1

Now modify the filename to:

/var/www/images/../../../etc/passwd

This bypasses the **prefix validation** using traversal sequences (`../`), while still starting with the required folder path.

### 3. 🧾 Observe the Response

- Forward the modified request.
- The server should respond with the contents of the `/etc/passwd` file.

✅ **Lab Solved!**

---

##  Key Takeaways

- Applications that only **check if the path starts** with a prefix are vulnerable if they don’t **normalize** the path.
- `../` (dot-dot-slash) can move up directories and **bypass path-based access control**.
- This is a **classic example** of insufficient validation and a useful trick in CTFs and real-world bug bounty scenarios.


