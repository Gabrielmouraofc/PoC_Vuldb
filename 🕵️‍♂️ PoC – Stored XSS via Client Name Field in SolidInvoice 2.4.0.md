
---

## 🕵️‍♂️ Vulnerability Overview

- 🐞 **Vulnerability Type:** Stored Cross-Site Scripting (XSS)  
- 🧩 **Affected Application:** SolidInvoice 2.4.0  
- 📍 **Vulnerability Location:** [`/clients` 
- 💥 **Impact:** Persistent execution of arbitrary JavaScript in users' browsers
- site do software :https://solidinvoice.co/ 
- link do demo: https://solidinvoice.app/

---

## 🧪 Exploitation Steps

### 🐉 Step 1: Access the SolidInvoice website and click the **Demo** option

![Accessing the official site and clicking demo](stored%20xss%20client/imagens/1.png)

---

### 🧾 Step 2: Register a new user in the demo environment

![Registering a new user](stored%20xss%20client/imagens/2.png)

---

### 👤 Step 3: Navigate to the "Add New Client" section

![Navigating to add client](stored%20xss%20client/imagens/3.png)

---

### 💉 Step 4: Inject a malicious payload in the "Name" field and fill required fields

```html
<script>alert('Poc VulDB')</script>
```

![Injecting payload](stored%20xss%20client/imagens/4.png)

---

### 💾 Step 5: Submit the form to store the client data

![Submitting the form](stored%20xss%20client/imagens/5.png)

---

### 📦 Step 6: The payload is successfully stored

![Payload stored successfully](stored%20xss%20client/imagens/6.png)

---

### 📋 Step 7: Open the "Clients List" page

![Navigating to clients list](imagens/7.png)

---

### 💥 Step 8: When accessing the `/clients` page, the stored payload is rendered and executed in the browser

![Payload execution](imagens/8.png)

---
