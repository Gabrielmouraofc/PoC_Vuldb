# 📄 PoC - Stored XSS via Client Name in Recurring Invoice Module – SolidInvoice 2.4.0

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

![image](https://github.com/user-attachments/assets/ae4d5c6c-9c39-4c4f-8e2e-c8c51eb98496)

---

### 🧾 Step 2: Register a new user account to access application features

The vulnerability requires authentication.

![image](https://github.com/user-attachments/assets/0aef3fb8-790c-46d9-8478-5ecf22616a2d)

---

### 👥 Step 3: Navigate to **Add Client** in the main menu

We need to create a client that will hold the malicious payload.

![image](https://github.com/user-attachments/assets/a6f71960-9fb5-42fb-9ea3-11ca479b828f)

---

### 💉 Step 4: Inject the XSS payload into the **Name** field and fill all required fields

```html
<script>alert('XSS')</script>
```

Then, click **Save** to store the client.

![image](https://github.com/user-attachments/assets/af20424a-9ff5-4e8d-92b4-0eca4f5baefe)

---

### 🔁 Step 5: Click on **Create Recurring Invoice** from the invoices menu

This action allows the creation of invoices that repeat periodically.

![Step 5 - Opening Recurring Invoice creation](https://github.com/user-attachments/assets/6c91077e-ce5a-410f-885a-5d8449f97d52)

---

### 📥 Step 6: In the creation form, select the previously created client (with payload)

The client field will now include the malicious `name`.

![image](https://github.com/user-attachments/assets/48fd75d6-0805-4488-ac5b-f0f58a2ae36e)

---

### 🧾 Step 7: Complete the remaining required fields and save the recurring invoice

All form fields must be filled to persist the entry.

![image](https://github.com/user-attachments/assets/9ed35846-662e-41b6-b759-99adce9b1bfe)

---

### 📋 Step 8: Open the **Recurring Invoices List** from the sidebar

This list will load the stored client data and render it in the table.

![image](https://github.com/user-attachments/assets/8ce20461-c258-4f3e-8f8e-ade916735e04)

---

### 💥 Step 9: The XSS payload is executed immediately upon accessing `/invoice/recurring`

As expected, the injected JavaScript is rendered unsanitized and executes on page load.

![image](https://github.com/user-attachments/assets/250105e5-6f33-4912-9922-8e049c6f949a)

---

### 🧪 Optional: The XSS also persists across refresh and navigation

Any authenticated user accessing the list will trigger the payload.

![image](https://github.com/user-attachments/assets/15baca69-a1cb-4869-a623-b62a9a3caaed)

---
