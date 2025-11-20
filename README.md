# 🌐 **CloudJourney Web — Static Website Hosting on AWS (S3 + CloudFront + Route 53 + ACM + WAF)**

### **Live Website:**

👉 [https://cloudjourney.online](https://cloudjourney.online)

### **Tech Stack:**

**Frontend:** HTML, CSS
**Cloud Services:** Amazon S3, Amazon CloudFront, AWS Certificate Manager, Route 53, AWS WAF

---

## 📘 **Project Overview**

This project demonstrates how to host a **static website** on AWS using a fully secure, globally distributed, production-grade architecture.

The goal was to deploy a static front-end website and serve it using:

* **S3** as the origin (static hosting bucket)
* **CloudFront** as a global CDN
* **Route 53** for domain DNS
* **AWS Certificate Manager (ACM)** for HTTPS
* **AWS WAF** for security and request filtering

This project is perfect for showcasing real cloud engineering experience, including hands-on work with DNS, CDN, SSL, S3 origin access control, and web security.

---

## 🖼️ **Architecture Diagram**

<img width="940" height="215" alt="image" src="https://github.com/user-attachments/assets/5c7cb838-dcbf-4127-8887-a88503431ccb" />

---

## 🚀 **Architecture Summary**

### **1️⃣ Amazon S3 – Static Website Hosting**

* Stores HTML, CSS, JS, and image files
* Public access **blocked**
* CloudFront Origin Access Control (OAC) is used to securely read from S3
* Bucket configured with correct index document (`index.html`)

### **2️⃣ Amazon CloudFront – CDN Distribution**

* Delivers content with low latency
* Provides HTTPS via ACM
* Caches content globally
* Configured with OAC (Origin Access Control)
* Default root object points to `index.html`
* Custom domain: `cloudjourney.online`

### **3️⃣ AWS Certificate Manager – SSL/TLS Certificate**

* Created a public certificate for:

  * `cloudjourney.online`
  * `www.cloudjourney.online`
* Validated automatically via DNS in Route 53
* Attached to CloudFront

### **4️⃣ Amazon Route 53 – DNS Management**

* Hosted zone for `cloudjourney.online`
* Records created:

  * **A (Alias)** → CloudFront distribution
  * **CNAME (www)** → root domain
* Nameservers updated in GoDaddy domain dashboard

### **5️⃣ AWS WAF – Web Application Firewall**

* Attached to CloudFront
* Protects against:

  * SQL injection
  * XSS
  * Bad bots
  * Common OWASP Top 10 vulnerabilities

---

## 🧩 **Detailed Deployment Steps**

### **Step 1 — Create S3 Bucket**

* Bucket name: `cloudjourney.online`
* Disable public access
* Enable **Static Website Hosting**
* Upload the website files
* Create **Origin Access Control (OAC)** and apply to bucket policy

---

### **Step 2 — Create CloudFront Distribution**

* Origin: S3 bucket
* Assign OAC
* Set default root object: `index.html`
* Add alternate domain names:

  * `cloudjourney.online`
  * `www.cloudjourney.online`
* Attach the ACM certificate
* Deploy distribution

---

### **Step 3 — Request ACM Certificate**

Requested from N. Virginia (us-east-1)
Includes:

* `cloudjourney.online`
* `www.cloudjourney.online`

Validated via DNS entries in Route 53.

---

### **Step 4 — Configure Route 53**

Created Hosted Zone → Added records:

#### **A Record (Alias to CloudFront)**

```
Type: A
Value: dXXXXXX.cloudfront.net
Alias: Yes
```

#### **CNAME Record (www → root domain)**

```
Type: CNAME
www → cloudjourney.online
```

Updated GoDaddy nameservers to Route 53 nameservers.

---

### **Step 5 — Attach WAF to CloudFront**

* Created WAF Web ACL
* Enabled Managed Rule Groups:

  * AWS Core rule set
  * SQL injection rules
  * XSS rules
* Associated ACL with CloudFront

---

## 🌍 **Final Result**

* Website accessible globally
* HTTPS enabled
* Traffic secured using WAF
* Serverless, scalable, pay-as-you-go architecture
* Fully production-ready deployment

---

## 💡 **What I Learned**

* Hosting static websites on AWS
* Using CloudFront for CDN
* Setting up SSL using ACM
* Managing DNS via Route 53
* Understanding CDN caching and invalidations
* Implementing WAF security layers
* Working with custom domains from third-party registrars

---
