# 📄 PoC for Exploitation: Stored XSS in SolidInvoice 2.4.0

---

## 🕵️‍♂️ Vulnerability Overview

- 🐞 **Vulnerability Type:** Stored Cross-Site Scripting (XSS)  
- 🧩 **Affected Application:** SolidInvoice 2.4.0  
- 📍 **Vulnerability Location:** `/invoice/recurring`  
- 🧾 **Affected Parameter:** `client name` (in Recurring Invoice creation)  
- 💥 **Impact:** JavaScript payload is persistently stored and triggered automatically when the recurring invoice list is accessed

---

## 🧪 Exploitation Steps

### 🐉 Step 1: Access the SolidInvoice official website and launch the **Demo** environment

The public demo simulates a real environment for testing purposes.

![Step 1 - Accessing the demo](stored%20xss%20client/imagens/1.png)

---

### 🧾 Step 2: Register a new user account to access application features

The vulnerability requires authentication.

![Step 2 - Registering a user](stored%20xss%20client/imagens/2.png)

---

### 👥 Step 3: Navigate to **Add Client** in the main menu

We need to create a client that will hold the malicious payload.

![Step 3 - Clicking Add Client](imagens/3.png)

---

### 💉 Step 4: Inject the XSS payload into the **Name** field and fill all required fields

```html
<script>alert('XSS')</script>
```

Then, click **Save** to store the client.

![Step 4 - Inserting the XSS payload into the client name](imagens/4.png)

---

### 🔁 Step 5: Click on **Create Recurring Invoice** from the invoices menu

This action allows the creation of invoices that repeat periodically.

![Step 5 - Opening Recurring Invoice creation](imagens/5.png)

---

### 📥 Step 6: In the creation form, select the previously created client (with payload)

The client field will now include the malicious `name`.

![Step 6 - Selecting the payload-bearing client](imagens/6.png)

---

### 🧾 Step 7: Complete the remaining required fields and save the recurring invoice

All form fields must be filled to persist the entry.

![Step 7 - Saving the Recurring Invoice](imagens/7.png)

---

### 📋 Step 8: Open the **Recurring Invoices List** from the sidebar

This list will load the stored client data and render it in the table.

![Step 8 - Navigating to Recurring Invoices List](imagens/8.png)

---

### 💥 Step 9: The XSS payload is executed immediately upon accessing `/invoice/recurring`

As expected, the injected JavaScript is rendered unsanitized and executes on page load.

![Step 9 - XSS Triggered on Recurring Invoices List](imagens/9.png)

---

### 🧪 Optional: The XSS also persists across refresh and navigation

Any authenticated user accessing the list will trigger the payload.

![Step 10 - Confirming persistent execution](imagens/10.png)

---
