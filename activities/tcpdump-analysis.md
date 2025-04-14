---
title: TCPDump Network Traffic Analysis
difficulty: Easy
estimated_time: 15 minutes
---

### 🛠️ Overview  
This case study analyzes a DNS-related service outage by inspecting packet captures with `tcpdump`. The investigation walks through identifying UDP and ICMP traffic and the resulting service disruption due to unreachable ports.


# Cybersecurity Incident Report:  
## Network Traffic Analysis

---

### Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log.

The **UDP protocol** reveals that:

> The user's browser attempted to resolve the domain name `www.yummyrecipesforme.com` by sending a DNS request to the DNS server at IP address `203.0.113.2` using UDP on port 53.

This is based on the results of the network analysis, which show that the **ICMP echo reply returned the error message**:

> `"udp port 53 unreachable"` — indicating that the DNS server did not respond to the request.

The port noted in the error message is used for:

> **Port 53**, which is used by **DNS (Domain Name System)** for resolving domain names to IP addresses using the UDP protocol.

The most likely issue is:

> The DNS service on `203.0.113.2` is **unavailable or blocked**, preventing resolution of the domain name. This caused users to receive a “destination port unreachable” error.

---

### Part 2: Explain your analysis of the data and provide at least one cause of the incident.

**Time incident occurred:**  
> `13:24:32.192571` (1:24 PM and 32 seconds)

**Explain how the IT team became aware of the incident:**  
> Multiple users reported that they were unable to access the website `www.yummyrecipesforme.com` and received a “destination port unreachable” error in their browser.

**Explain the actions taken by the IT department to investigate the incident:**  
> The IT team attempted to load the website and replicated the same error. They used the `tcpdump` network analyzer tool to capture live network traffic during the connection attempt. The packet capture logs were then reviewed to identify protocol behavior and error messages.

**Note key findings of the IT department's investigation (i.e., details related to the port affected, DNS server, etc.):**  
- DNS request was sent from the client at IP `192.51.100.15` to the DNS server at IP `203.0.113.2`.  
- The request used **UDP protocol on port 53**.  
- The DNS server responded with **ICMP messages** indicating that **UDP port 53 was unreachable**.  
- The browser was therefore unable to retrieve the IP address for the website, causing the website to be inaccessible.

**Note a likely cause of the incident:**  
> The DNS server may have been **offline**, misconfigured, or had **firewall settings blocking UDP port 53**, resulting in the failure to resolve the domain name.
