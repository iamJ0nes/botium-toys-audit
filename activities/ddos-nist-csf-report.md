---
title: DDoS Attack Response Using NIST CSF
difficulty: Moderate
estimated_time: 20 minutes
---

### 🧠 Overview  
This case study analyzes a Distributed Denial-of-Service (DDoS) attack using the National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF). The attack involved an ICMP packet flood that disrupted a multimedia company's internal network. The report outlines how the incident was identified, contained, and mitigated using best practices aligned with the NIST CSF.

# Incident Report: DDoS Attack on Internal Network  
## Based on the NIST Cybersecurity Framework (CSF)

---

### 🔍 Summary  
A DDoS attack flooded the company's internal network with ICMP packets, causing a total outage of network services for approximately two hours. The attack exploited an unconfigured firewall rule, allowing unrestricted ICMP traffic. The incident was resolved by blocking ICMP traffic and implementing new detection and mitigation controls.

---

## 🛡️ Identify  
- The vulnerability stemmed from an unconfigured firewall that allowed unrestricted ICMP traffic.  
- No IP filtering or packet inspection was enabled to detect or prevent abnormal traffic flows.  
- Internal assets, including communication systems and shared drives, were rendered unavailable.  
- No source IP verification was in place, allowing spoofed packets.

---

## 🔐 Protect  
- Firewall rules were updated to **limit incoming ICMP packet rate**.  
- **Source IP address verification** was added to prevent spoofing.  
- IDS/IPS systems were configured to detect DDoS indicators.  
- Internal documentation and procedures were updated to include best practices for protocol filtering.

---

## 📡 Detect  
- Network monitoring software was deployed to detect **abnormal ICMP traffic patterns**.  
- Alerts were configured to notify the security team when unusual packet volumes or ping floods occur.  
- Incident detection time was reduced through automated log inspection and anomaly detection.

---

## 🚨 Respond  
- Incoming ICMP packets were blocked during the incident.  
- Non-essential services were taken offline to preserve critical operations.  
- A temporary response team was assembled to assess impact and perform root cause analysis.  
- The team implemented real-time mitigations and updated firewall/IDS signatures.

---

## ♻️ Recover  
- Critical systems were restored within two hours using backup configurations.  
- A post-incident review was conducted to inform future improvements.  
- Lessons learned were documented and used to update disaster recovery procedures.

---

### 📝 Reflections / Notes:  
- This event highlights the importance of having proactive firewall configuration reviews.  
- Network behavior baselining and anomaly detection can greatly reduce incident duration.  
- The CSF model proved effective for structuring incident response.

