
---

## 🕵️‍♂️ Vulnerability Overview

- 🐞 **Vulnerability Type:** Stored Cross-Site Scripting (XSS)  
- 🧩 **Affected Application:** SolidInvoice 2.4.0  
- 📍 **Vulnerability Location:** `/invoice`  
- 🧾 **Affected Parameter:** `client name` (during invoice creation)  
- 💥 **Impact:** Arbitrary JavaScript is stored and later executed when listing invoices

---

## 🧪 Exploitation Steps

### 🐉 Step 1: Access the SolidInvoice official site and enter the **Demo** environment

Public demo access is used to simulate the vulnerability.

![Step 1 - Accessing the demo](stored%20xss%20client/imagens/1.png)

---

### 🧾 Step 2: Register a new user to unlock full access to the system

Account registration is required to access invoice-related features.

![Step 2 - Registering an account](stored%20xss%20client/imagens/2.png)

---

### 📥 Step 3: Click on **"Create Invoice"** from the main menu

This initiates the process of issuing a new invoice.

![Step 3 - Clicking on Create Invoice](imagens/3.png)

---

### ➕ Step 4: As no client exists yet, click on **“Please add one now”** to create a new client

Creating a client is mandatory for issuing invoices.

![Step 4 - Adding a new client](imagens/4.png)

---

### 👤 Step 5: Fill out the client form and click **Save** to create the new client

This client will be used for demonstration purposes in the payload.

![Step 5 - Saving the new client](imagens/5.png)

---

### 🔁 Step 6: After client creation, the form redirects. Now click again on **"Create Invoice"**

The invoice form should now be available.

![Step 6 - Returning to Create Invoice](imagens/6.png)  
![Step 6 continued - Clicking Create Invoice again](imagens/7.png)

---

### 💉 Step 7: Inject the payload into one of the invoice fields (e.g., description or client name), fill required fields, and click **Save**

```html
<script>alert('XSS')</script>
```

All mandatory fields must be filled for the payload to be accepted and stored.

![Step 7 - Creating an invoice with an XSS payload](imagens/8.png)

---

### 💾 Step 8: After successful creation, click on **"List Invoices"** to view saved entries

This is where the XSS will be triggered if the payload is rendered unsanitized.

![Step 8 - Navigating to List Invoices](imagens/9.png)

---

### 💥 Step 9: When accessing `/invoice`, the payload is rendered and executed

The script embedded in the invoice field executes automatically when the page loads, confirming stored XSS.

![Step 9 - XSS executed in /invoice](imagens/10.png)
