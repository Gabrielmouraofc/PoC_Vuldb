
# 🕵️‍♂️PoC -Stored XSS via Tax Rate Name Field in SolidInvoice 2.4.0
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

![image](https://github.com/user-attachments/assets/a1cd2028-d424-470c-9952-49d578c696d1)

---

### 🧾 Step 2: Register a new user account on the demo platform

This provides access to all features, including client and tax rate management.

![image](https://github.com/user-attachments/assets/5a50da08-3ce3-4724-861a-f5afafa0f03d)

---

### 📊 Step 3: Navigate to the **Tax Rates** section via the sidebar

This section allows administrators to configure tax percentages applied to invoices.

![image](https://github.com/user-attachments/assets/b9cd31ab-cf34-45c1-b34a-4368ce442017)

---


### ➕ Step 4: Click on **Add Tax Rate** to access the creation form

The vulnerability lies in this input form.

![image](https://github.com/user-attachments/assets/db0aa47c-b1a4-4158-84b6-db69d0fa00bf)

---


### 💉 Step 5: Inject a malicious JavaScript payload into the **Name** field and complete the other required fields

```html
<script>alert('VulDB')</script>
```

This input is not sanitized on submission and is stored in the database.

![image](https://github.com/user-attachments/assets/cf5d8192-c7e4-49fc-9087-25e9102aea14)

### 💥 Step 6: Upon saving, the payload is immediately executed when the `/tax/rates` page is reloaded

When the tax rates list is rendered, the `name` field content is inserted directly into the DOM without escaping, triggering the stored XSS.

![image](https://github.com/user-attachments/assets/6e288dfb-ca0b-4467-9180-a51a5afed6af)
