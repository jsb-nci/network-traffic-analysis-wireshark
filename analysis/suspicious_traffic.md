# Suspicious Traffic Analysis – Port Scanning

## Description
Port scanning activity was simulated using PowerShell to generate multiple TCP
connection attempts to sequential destination ports.
// 1..100 | ForEach-Object { Test-NetConnection localhost -Port $_ -InformationLevel Quiet } 

## Observed Pattern
- Repeated TCP SYN packets
- No completion of the TCP three-way handshake
- No TLS handshake initiation
- Multiple destination ports targeted

## Wireshark Display Filter Used
tcp.flags.syn == 1 && tcp.flags.ack == 0


## Analyst Interpretation
Repeated SYN packets without corresponding ACK responses indicate
reconnaissance behavior. This pattern is typical of port scanning, where an
attacker probes a system to identify open and listening services.

Because the TCP handshake does not complete, higher-layer protocols such as TLS
are never initiated.

## Conclusion
Port scanning generates identifiable network patterns that can be detected
through network traffic analysis, even when no application data is exchanged.
