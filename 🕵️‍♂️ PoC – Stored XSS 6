🕵️‍♂️ PoC – Stored XSS via Client Name Field in SolidInvoice 2.4.0
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

![image](https://github.com/user-attachments/assets/49f45210-606e-4130-835b-2c331b5ec431)

---

### 🧾 Step 2: Register a new user in the demo environment

![image](https://github.com/user-attachments/assets/6dd372e0-4e76-43cb-bc81-06ffe77492ce)

---

### 👤 Step 3: Navigate to the "Add New Client" section

![image](https://github.com/user-attachments/assets/c1f04fd9-b14f-4161-984d-e67034336888)

---

### 💉 Step 4: Inject a malicious payload in the "Name" field and fill required fields

```html
<script>alert('Poc VulDB')</script>
```
![image](https://github.com/user-attachments/assets/deffc120-bf90-4a92-97d6-81c9d20ebd3f)

---

### 💾 Step 5: Submit the form to store the client data

![image](https://github.com/user-attachments/assets/8f4a9f5c-635f-4088-a6d7-a0b6b381dbbc)

---

### 📦 Step 6: The payload is successfully stored

![image](https://github.com/user-attachments/assets/2c6eb32c-e9a9-45ef-848b-50adb3315647)

---

### 📋 Step 7: Open the "Clients List" page

![image](https://github.com/user-attachments/assets/56044ab3-3a0a-4ae2-9ffb-7e7e5f1fdccd)

---

### 💥 Step 8: When accessing the `/clients` page, the stored payload is rendered and executed in the browser

![image](https://github.com/user-attachments/assets/7acff6b1-d549-47e3-ab64-2588e970d33b)

---
