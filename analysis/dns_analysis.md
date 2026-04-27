# DNS Traffic Analysis – Wireshark

## Objective
Analyze DNS traffic generated using `nslookup` commands and observe DNS query/response behavior in Wireshark.

---

## Setup
- Tool: Wireshark
- Display Filter: `dns`
- DNS queries generated manually using PowerShell (`nslookup`)
- Capture interface: Wireless Adapter

---

## Observations

### 1. Standard DNS Queries
- Multiple DNS **A**, **AAAA**, and **PTR** queries were observed.
- Example domains:
  - `testdomain123.com`
  - `google.com`
- Queries were sent over **UDP port 53**.

---

### 2. NXDOMAIN / No Answer Responses
- Some DNS responses returned:
  - **No Answer Records**
  - Presence of **SOA records** in Authority Section
- This indicates:
  - Domain exists
  - But requested record type is unavailable
  - Common during reconnaissance or misconfigured queries

---

### 3. Reverse DNS (PTR) Queries
- Reverse lookups such as:
- Used to resolve IP addresses back to hostnames.
- Often seen in network discovery and logging activity.

---

## Packet-Level Details
- Transaction IDs matched correctly between query and response.
- Flags indicated:
- Standard query response
- No error
- DNS payload visible in plaintext (expected behavior).

---

## Security Relevance
- DNS traffic is **unencrypted**, making it valuable for:
- Detecting suspicious domains
- Identifying tunneling attempts
- Monitoring malware C2 communication
- Abnormal patterns would include:
- High-frequency queries
- Long/random subdomains
- Excessive NXDOMAIN responses

---

##wireshark Capture



## Conclusion
The observed DNS traffic represents **normal DNS behavior** generated through manual queries. This establishes a baseline for identifying abnormal or malicious DNS activity in later analysis.
