# Normal Network Traffic Analysis

## DNS Analysis
During packet capture, DNS traffic was observed prior to any application
communication. DNS queries such as `windows.msn.com` were visible, indicating
normal system and browser activity.

DNS traffic remains visible even when application-layer traffic is encrypted,
making it an important source of information for security monitoring.

## HTTP Traffic
When accessing websites over HTTP, request and response details such as URLs,
headers, and parameters were visible in Wireshark. This demonstrates that HTTP
traffic is transmitted in clear text and is susceptible to interception.

## HTTPS / TLS Traffic
For HTTPS traffic, the payload content is encrypted and not readable in
Wireshark. Only metadata such as source and destination IP addresses, ports,
and TLS handshake information is visible.

The TLS handshake occurs only after a successful TCP three-way handshake.


## Observation
Normal network communication follows this sequence:
1. DNS resolution
2. TCP three-way handshake
3. TLS handshake (for HTTPS traffic)
4. Encrypted application data transfer
