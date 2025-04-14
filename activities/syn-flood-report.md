---
title: SYN Flood Attack Analysis
difficulty: Moderate
estimated_time: 20 minutes
---

### 🛡️ Overview  
This case study investigates a SYN flood denial-of-service (DoS) attack using color-coded TCP packet data. The exercise highlights the telltale signature of a flooding attack and walks through how it affects server availability and performance.


# Cybersecurity Incident Report  
## SYN Flood Attack – Web Server Interruption

---

### Section 1: Identify the type of attack that may have caused this network interruption

**One potential explanation for the website's connection timeout error message is:**  
A **TCP SYN flood** attack — a form of **Denial of Service (DoS)** attack — is overwhelming the company’s web server by abusing the TCP handshake mechanism.

**The logs show that:**  
A large number of incoming **SYN packets** are being sent from the same IP address (`203.0.113.0`) to port 443 of the web server (`192.0.2.1`). These packets are not followed by completion of the handshake, leading to excessive consumption of server resources.

**This event could be:**  
A **direct SYN flood DoS attack**, where a single malicious source overwhelms the server with TCP SYN requests. This depletes the server's ability to maintain legitimate connections, leading to **504 Gateway Timeout** errors and **RST, ACK** (reset) responses for valid users.

---

### Section 2: Explain how the attack is causing the website to malfunction

**When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. Explain the three steps of the handshake:**

1. **SYN** – The client sends a SYN packet to the server to request a connection.  
2. **SYN-ACK** – The server responds with a SYN-ACK packet, acknowledging the request.  
3. **ACK** – The client replies with an ACK packet to finalize the connection.

---

**Explain what happens when a malicious actor sends a large number of SYN packets all at once:**  
The attacker sends a flood of SYN packets but never replies with the final ACK to complete the handshake. This leaves the server with many half-open connections, consuming memory and CPU cycles. Eventually, the server runs out of resources to handle legitimate connections.

---

**Explain what the logs indicate and how that affects the server:**  
- The logs show repeated SYN requests from `203.0.113.0` to port `443`.  
- The web server initially attempts to respond with SYN-ACK packets, but no ACK is received, leaving connections incomplete.  
- Over time, the server slows down and eventually stops responding to legitimate users (log entries after 125 show only SYN packets from the attacker).  
- Legitimate users receive either:  
  - **504 Gateway Timeout** responses (indicating delay in server replies), or  
  - **RST, ACK** packets (resetting the connection due to overload).

This confirms the web server was **overloaded by a SYN flood**, resulting in **denial of access** for both internal employees and external visitors.

---

**Next Steps:**
- Configure firewall or intrusion prevention systems to detect and mitigate SYN floods.
- Consider rate limiting, SYN cookies, or DDoS protection services for long-term resilience.
