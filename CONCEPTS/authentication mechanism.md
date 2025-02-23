### **Day 10: Authentication Mechanisms in System Design** 🚀  

Authentication is a **critical** component of system design, ensuring that only authorized users can access specific resources. Today, we will go deep into **OAuth**, **Token-Based Authentication**, **Access Control Lists (ACLs)**, and **Rule Engines** used in system design.  

---

## **🔹 OAuth (Open Authorization)**
OAuth is an open standard **authorization** framework that allows applications to securely access user data without exposing credentials.

### **🛠 How OAuth Works?**  
OAuth uses a **token-based** system, typically in a **three-party** model:
1. **Resource Owner** – The user who owns the data.
2. **Client** – The application requesting access.
3. **Authorization Server** – Issues the access tokens after authentication.
4. **Resource Server** – The API or service that stores the user's data.

### **🔄 OAuth Flow (Authorization Code Grant - Most Secure)**
1️⃣ **User Requests Access:**  
   - The user tries to log in to an application (client).  
2️⃣ **Redirect to Authorization Server:**  
   - The client redirects the user to the OAuth provider (e.g., Google, Facebook).  
3️⃣ **User Grants Permission:**  
   - The user consents to share access with the client application.  
4️⃣ **Authorization Code Issued:**  
   - The authorization server sends a temporary code to the client.  
5️⃣ **Client Requests Access Token:**  
   - The client exchanges the authorization code for an access token.  
6️⃣ **Access Token Used:**  
   - The client uses the token to access the resource server.  

### **✅ Advantages of OAuth**
- **No password sharing** – Applications don’t store user credentials.  
- **Third-party integration** – Users can log in with Google, Facebook, etc.  
- **Granular permissions** – Users can allow partial access (e.g., only read access).  

### **🚨 When to Use OAuth?**
- When you need **third-party authentication** (Google, Facebook Login).
- When **multiple services** need access control (e.g., APIs).  
- When **delegated access** is required (one app acting on behalf of another).  

---

## **🔹 Token-Based Authentication**
Token-based authentication is a **stateless** authentication mechanism that relies on **tokens** (usually JWTs - JSON Web Tokens) instead of session-based authentication.

### **🛠 How Token-Based Authentication Works?**  
1️⃣ **User logs in** → Provides username & password.  
2️⃣ **Server verifies credentials** → Generates a token (JWT).  
3️⃣ **Token sent to user** → User stores the token (browser storage, mobile app).  
4️⃣ **User makes API requests** → Sends token in the header (e.g., `Authorization: Bearer <token>`).  
5️⃣ **Server validates token** → Grants access to the resource.  

### **📌 JWT (JSON Web Token)**
A JWT consists of three parts:  
- **Header** → Contains metadata (e.g., token type, encryption method).  
- **Payload** → Contains user info (e.g., user ID, roles, expiry time).  
- **Signature** → Ensures token integrity.  

**Example JWT:**  
```json
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJ1c2VySWQiOiIxMjM0NTYiLCJyb2xlIjoiYWRtaW4iLCJleHAiOjE2ODg4ODg4MDB9.
hGKb_y6GxPfzD92Uj1_UfI1GzykmKXQJ2IY-QwXhRoU
```

### **✅ Advantages of Token-Based Authentication**
- **Stateless** → No need to store sessions in the database.  
- **Scalable** → Works well with microservices.  
- **Secure** → JWTs can be signed and encrypted.  

### **🚨 When to Use Token-Based Authentication?**
- In **REST APIs** to avoid session storage.  
- For **scalability in microservices**.  
- In **mobile applications** where sessions aren’t practical.  

---

## **🔹 Access Control Lists (ACLs)**
ACLs define **who** can access **what** resources by maintaining a list of permissions.

### **🛠 How ACLs Work?**
- Each resource has a **list of permissions** attached.
- Each user (or group) is assigned **specific permissions**.

### **📌 Example ACL Implementation**
| User | Resource | Permission |
|------|---------|-----------|
| Alice | File A | Read, Write |
| Bob | File A | Read |
| Charlie | File B | Execute |

- **Bob can read File A but not write.**  
- **Charlie can execute File B but not read/write.**  

### **✅ Advantages of ACLs**
- Fine-grained access control.  
- Easy to understand and implement.  

### **🚨 When to Use ACLs?**
- In **file systems** (Linux `chmod`, AWS S3 bucket permissions).  
- In **database role management**.  
- In **enterprise applications** with user roles.  

---

## **🔹 Rule Engines in System Design**
A **Rule Engine** allows dynamic decision-making based on rules defined at runtime.

### **🛠 How Rule Engines Work?**
1️⃣ **Input Data** → System receives input (e.g., user login, transaction request).  
2️⃣ **Rule Evaluation** → Engine checks input against predefined rules.  
3️⃣ **Decision Making** → If conditions match, a specific action is triggered.  
4️⃣ **Output Generation** → The system executes the decision.  

### **📌 Example: Fraud Detection Rule Engine**
A bank uses a rule engine to detect fraud:  
```json
IF transaction_amount > 10000 AND location != "home_country" THEN alert_fraud
```
- If a user makes a **$15,000 transaction from another country**, an **alert is triggered**.

### **✅ Advantages of Rule Engines**
- **Flexible & Configurable** → Rules can be updated without changing code.  
- **Automates Decision Making** → Reduces manual interventions.  
- **Scalable** → Used in fraud detection, access control, and recommendations.  

### **🚨 When to Use Rule Engines?**
- **Fraud detection** (banking, e-commerce).  
- **Access control** (if user is admin, grant full access).  
- **Dynamic pricing** (e.g., Uber surge pricing).  

---

## **🔹 Summary Table**
| Concept | Definition | Use Cases |
|---------|------------|------------|
| **OAuth** | Secure authorization framework using tokens | Third-party logins (Google, Facebook) |
| **Token-Based Auth** | Stateless authentication using JWT tokens | REST APIs, Microservices |
| **ACLs** | List of permissions attached to resources | File systems, databases, enterprise apps |
| **Rule Engine** | Dynamic decision-making based on predefined rules | Fraud detection, dynamic access control |

---

## **🚀 Final Thoughts**
- **Use OAuth** when integrating third-party logins or API authentication.  
- **Use Token-Based Authentication** when building stateless and scalable APIs.  
- **Use ACLs** when managing user-specific permissions in applications.  
- **Use Rule Engines** when decisions must be dynamic and configurable.  

Let me know if you need **code examples** or **real-world implementation details**! 🚀
