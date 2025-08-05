📄PoC - Stored XSS via Quote Title in SolidInvoice 2.4.0

---

## 🕵️‍♂️ Vulnerability Overview

- 🐞 **Vulnerability Type:** Stored Cross-Site Scripting (XSS)  
- 🧩 **Affected Application:** SolidInvoice 2.4.0  
- 📍 **Vulnerability Location:** `/quotes`  
- 🧾 **Affected Parameter:** `name` (Quote title field)  
- 💥 **Impact:** Malicious JavaScript is stored and executed when the quotes list is accessed by authenticated users

---

## 🧪 Exploitation Steps

### 🐉 Step 1: Access the SolidInvoice official site and enter the **Demo** environment

This instance replicates production features and allows authenticated testing.

![image](https://github.com/user-attachments/assets/2a58d016-6865-4c8c-8150-57b6e249e71a)

---

### 🧾 Step 2: Register a user account on the demo to unlock authenticated functionality

This allows full access to client, quote, and tax modules.

![image](https://github.com/user-attachments/assets/ce902677-61dd-434c-b2e3-46f92be6240b)

---

### 📑 Step 3: Open the **"Create Quote"** option from the main menu

This leads to the quote creation interface, where user input is later rendered in the quote list.

![image](https://github.com/user-attachments/assets/9ac796a5-9a7a-451b-bcdc-7724faafffec)

---

### 💉 Step 4: Inject the payload into the **Quote Name** field, fill the required fields (e.g. client, product), and click **Save**

```html
<script>alert('Poc VulDB')</script>
```

No sanitization is applied to this field, which leads to the payload being stored as-is.

![image](https://github.com/user-attachments/assets/61bb8d35-41a9-4180-801f-8306a88b58e0)

---

### 🧾 Step 5: After saving, navigate to **List Quotes** to verify if the payload was stored

The script is now stored in the system and will be executed upon rendering the quote list.

![image](https://github.com/user-attachments/assets/b2a920d0-cd06-46ce-ba8d-b4a4fb112ebb)

---

### 💥 Step 6: When accessing the `/quotes` directory, the XSS payload executes immediately

The malicious script injected in the quote's `name` is rendered in the DOM without sanitization, causing client-side code execution for any user who views the list.

![image](https://github.com/user-attachments/assets/79277b81-5560-4ca3-a052-31281a9d7e9f)
