# certificates-all-types
Great — you're referring to **digital certificates** and **public key infrastructure (PKI)** concepts, particularly around **SSL/TLS certificates**. Here's a clear breakdown of all those terms:

---

## 🔐 **Types of SSL/TLS Certificates in the Certificate Chain**

### 1. **Root Certificate**

* **Issued by:** A trusted Certificate Authority (CA).
* **Stored in:** Your system/browser trust store.
* **Self-signed:** It signs itself.
* **Example:** `DigiCert Root CA`, `Let's Encrypt Authority X3`
* **Purpose:** Foundation of trust — the top of the certificate chain.

### 2. **Intermediate Certificate (a.k.a. Chain Certificate)**

* **Issued by:** Root CA or another intermediate CA.
* **Signs:** Leaf/server certificates.
* **Purpose:** Adds a layer between the root and leaf to improve security (so root CAs don't have to sign every cert).

### 3. **Leaf Certificate (a.k.a. End-Entity or Server Certificate)**

* **Issued by:** Intermediate CA.
* **Used for:** Actual server identity (e.g., `yourwebsite.com`).
* **Expires regularly** (e.g., every 90 days for Let's Encrypt).

---

## 🔑 **Key Concepts**

### **Private Key**

* **Used for:** Decrypting data encrypted with the public key; signing.
* **Stored on:** The server — **never shared**.
* **Format:** `.key` file (often PEM format).

### **Public Key**

* **Contained in:** The certificate.
* **Used for:** Encrypting data; verifying signatures.
* **Distributed freely.**

---

## 📄 **File Formats and Extensions**

| Format      | Extension                      | Description                                                            |
| ----------- | ------------------------------ | ---------------------------------------------------------------------- |
| **PEM**     | `.pem`, `.crt`, `.cer`, `.key` | Base64-encoded ASCII, contains certs or keys. Common in Linux/OpenSSL. |
| **DER**     | `.der`, `.cer`                 | Binary format. Used in Windows/Java.                                   |
| **PKCS#12** | `.pfx`, `.p12`                 | Binary. Includes cert + key + chain. Often password-protected.         |
| **CSR**     | `.csr`                         | Certificate Signing Request — used to request a cert from a CA.        |
| **KEY**     | `.key`                         | Private key (should be kept secure).                                   |

---

## 🔒 **TLS vs SSL**

| Feature            | SSL                       | TLS                                         |
| ------------------ | ------------------------- | ------------------------------------------- |
| **Full name**      | Secure Sockets Layer      | Transport Layer Security                    |
| **Current status** | Deprecated (SSL 2.0, 3.0) | Actively used (TLS 1.2, TLS 1.3)            |
| **Security**       | Vulnerable                | Stronger (TLS 1.3 is current best practice) |

**Use TLS 1.2 or 1.3 only**. SSL is outdated and insecure.

---

## 📚 **Summary of Certificate Chain (simplified)**

```text
[ Root CA ]
     ↓ signs
[ Intermediate CA ]
     ↓ signs
[ Leaf Certificate (your domain) ]
```

Your server uses:

* **Leaf certificate**
* **Private key**
* **Chain of trust (bundle of intermediate + root)** to send to clients.

---

Would you like help:

* Generating a certificate?
* Understanding how to install these on Apache/Nginx?
* Creating a local CA for development?

Let me know!
