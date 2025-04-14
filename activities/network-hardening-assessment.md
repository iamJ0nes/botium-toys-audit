---
title: Network Hardening Assessment – Data Breach Response  
difficulty: Moderate  
estimated_time: 20 minutes  
---

### 🔐 Overview  
This case study focuses on a real-world data breach at a social media organization due to weak internal network security practices. As a security analyst, you’ll recommend hardening tools and methods to remediate identified vulnerabilities and reduce future risk.

# Security Risk Assessment Report  
## Network Hardening Response – Customer Data Breach

---

### Part 1: Select up to three hardening tools and methods to implement

**Tool/Method 1: Multifactor Authentication (MFA)**  
MFA provides an extra layer of identity verification, reducing the risk of unauthorized access from brute force or stolen credentials.

**Tool/Method 2: Firewall Maintenance and Rule Configuration**  
Implementing and regularly updating inbound and outbound firewall rules will control network traffic and help prevent unfiltered external access.

**Tool/Method 3: Password Policies and Privilege Controls**  
Establishing secure password policies aligned with NIST recommendations, and revoking shared credentials, will help protect sensitive systems. Applying the principle of least privilege further limits unnecessary access.

---

### Part 2: Explain your recommendations

The organization is vulnerable due to poor internal practices:

- **Password sharing** creates weak points in the authentication process. One compromised user means access for multiple roles.
- **Default admin passwords** are easily guessed by attackers and indicate poor security hygiene.
- **Lack of MFA** makes brute force attacks significantly more effective.
- **Firewall misconfigurations** leave the network exposed to unauthorized connections.

**How the selected methods address these issues:**

- **MFA** mitigates password sharing risks by requiring a second verification factor, such as a mobile OTP or fingerprint.
- **Firewall maintenance** allows the security team to define which types of traffic are allowed and actively block suspicious behavior or unusual IP ranges.
- **Password policies** ensure unique, strong credentials, and reducing privilege access limits the impact of any single compromised account.

**Outcome:**  
Together, these hardening practices reduce the attack surface and help establish a layered defense. They will prevent attackers from exploiting the same vulnerabilities that led to the original breach and align the organization’s network with industry security standards.

---
