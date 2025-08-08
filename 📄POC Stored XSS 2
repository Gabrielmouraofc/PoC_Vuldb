📄POC Stored XSS via Client Name during Invoice Creation in SolidInvoice 2.4.0
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

![image](https://github.com/user-attachments/assets/f95142b1-0b9e-401f-9b35-06d77d0bea68)

---

### 🧾 Step 2: Register a new user to unlock full access to the system

Account registration is required to access invoice-related features.

![image]("https://github.com/user-attachments/assets/f3f01cb0-58c8-45bd-99c8-8b2f7446495a)

---

### 📥 Step 3: Click on **"Create Invoice"** from the main menu

This initiates the process of issuing a new invoice.

![image](https://github.com/user-attachments/assets/f991be9b-ae74-4092-afee-3434e23f01d4)

---

### ➕ Step 4: As no client exists yet, click on **“Please add one now”** to create a new client

Creating a client is mandatory for issuing invoices.

![Step 4 - Adding a new client](https://github.com/user-attachments/assets/e61e329a-f415-48e1-82ea-4ab5f199937f)

---

### 👤 Step 5: Fill out the client form and click **Save** to create the new client

This client will be used for demonstration purposes in the payload.

![Step 5 - Saving the new client](https://github.com/user-attachments/assets/954b390b-1ba2-4444-8b09-83fd9437f253)

---

### 🔁 Step 6: After client creation, the form redirects. Now click again on **"Create Invoice"**

The invoice form should now be available.


![image](https://github.com/user-attachments/assets/4bad03d3-d388-45cd-8fb9-d481e8fa6021)  
![image]([imagens/7.png](https://github.com/user-attachments/assets/cb85e01c-1174-4687-88db-12bde7634a39))


---

### 💉 Step 7: Inject the payload into one of the invoice fields (e.g., description or client name), fill required fields, and click **Save**

```html
<script>alert('XSS')</script>
```

All mandatory fields must be filled for the payload to be accepted and stored.

![image](https://github.com/user-attachments/assets/445f65a6-92d7-4212-b64e-96bce96006fa)

---

### 💾 Step 8: After successful creation, click on **"List Invoices"** to view saved entries

This is where the XSS will be triggered if the payload is rendered unsanitized.

![image](https://github.com/user-attachments/assets/bd4192a7-c321-4a92-b3d5-9088cc04c7e1)

---

### 💥 Step 9: When accessing `/invoice`, the payload is rendered and executed

The script embedded in the invoice field executes automatically when the page loads, confirming stored XSS.

![image](https://github.com/user-attachments/assets/fc80ba75-af18-45c0-8910-8f9c047c9ef6)
