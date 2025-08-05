

---

## 🕵️‍♂️ Vulnerability Overview

- 🐞 **Vulnerability Type:** Stored Cross-Site Scripting (XSS)  
- 🧩 **Affected Application:** SolidInvoice 2.4.0  
- 📍 **Vulnerability Location:** `/tax/rates`  
- 🧾 **Affected Parameter:** `name` (Tax Rate creation form)  
- 💥 **Impact:** Persistent JavaScript execution triggered when accessing the tax rate list, potentially impacting all authenticated users

---

## 🧪 Exploitation Steps

### 🐉 Step 1: Access the SolidInvoice project website and select the **Demo** environment

The vulnerability is demonstrated using the publicly available demo instance.

![Step 1 - Accessing the demo](stored%20xss%20client/imagens/1.png)

---

### 🧾 Step 2: Register a new user account on the demo platform

This provides access to all features, including client and tax rate management.

![Step 2 - Registering a user](stored%20xss%20client/imagens/2.png)

---

### 📊 Step 3: Navigate to the **Tax Rates** section via the sidebar

This section allows administrators to configure tax percentages applied to invoices.

![Step 3 - Navigating to Tax Rates](imagens/3.png)

---

### ➕ Step 4: Click on **Add Tax Rate** to access the creation form

The vulnerability lies in this input form.

![Step 4 - Opening Add Tax Rate form](imagens/4.png)

---

### 💉 Step 5: Inject a malicious JavaScript payload into the **Name** field and complete the other required fields

```html
<script>alert('VulDB')</script>
```

This input is not sanitized on submission and is stored in the database.

![Step 5 - Injecting XSS payload](imagens/5.png)

### 💥 Step 6: Upon saving, the payload is immediately executed when the `/tax/rates` page is reloaded

When the tax rates list is rendered, the `name` field content is inserted directly into the DOM without escaping, triggering the stored XSS.

![Step 6 - Execution of stored XSS on /tax/rates](imagens/6.png)