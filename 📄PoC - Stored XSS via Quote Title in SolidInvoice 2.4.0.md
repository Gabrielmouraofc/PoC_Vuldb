# 📄 PoC for Exploitation: Stored XSS in SolidInvoice 2.4.0


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

![Step 1 - Accessing the demo environment](stored%20xss%20client/imagens/1.png)

---

### 🧾 Step 2: Register a user account on the demo to unlock authenticated functionality

This allows full access to client, quote, and tax modules.

![Step 2 - User registration](stored%20xss%20client/imagens/2.png)

---

### 📑 Step 3: Open the **"Create Quote"** option from the main menu

This leads to the quote creation interface, where user input is later rendered in the quote list.

![Step 3 - Navigating to Create Quote](imagens/3.png)

---

### 💉 Step 4: Inject the payload into the **Quote Name** field, fill the required fields (e.g. client, product), and click **Save**

```html
<script>alert('Poc VulDB')</script>
```

No sanitization is applied to this field, which leads to the payload being stored as-is.

![Step 4 - Inserting the payload and submitting the form](imagens/4.png)

---

### 🧾 Step 5: After saving, navigate to **List Quotes** to verify if the payload was stored

The script is now stored in the system and will be executed upon rendering the quote list.

![Step 5 - Confirming the payload is stored](imagens/5.png)

---

### 💥 Step 6: When accessing the `/quotes` directory, the XSS payload executes immediately

The malicious script injected in the quote's `name` is rendered in the DOM without sanitization, causing client-side code execution for any user who views the list.

![Step 6 - Stored XSS triggers on /quotes](imagens/6.png)
