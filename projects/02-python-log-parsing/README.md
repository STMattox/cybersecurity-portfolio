# Project 02: Automated Security Scripting: Access Control

## Executive Summary
This project investigates a simulated internal security incident involving anomalous network activity detected on an internal enterprise subnet (`192.168.1.0/24`). Using command-line packet sniffing (`tcpdump`) and graphical protocol analysis (`Wireshark`), I inspected raw PCAP files to identify reconnaissance activity (SYN stealth scans), verify an unencrypted authentication breach, and isolate the originating malicious host.

---

## Environment & Tools
* **Analysis Tools:** Wireshark, `tcpdump`
* **Protocols Analyzed:** TCP, UDP, DNS, HTTP, ARP
* **Operating Environment:** Linux (Ubuntu 22.04 LTS)
* **Framework Alignment:** NIST SP 800-61 Rev. 2 (Computer Security Incident Handling Guide)

---

## Scenario Overview
A network monitoring alert flagged anomalous packet bursts originating from internal host `192.168.1.55`. Security operations requested a PCAP review to determine:
1. Did reconnaissance take place against internal assets?
2. Were unauthorized services accessed?
3. Were sensitive credentials transmitted in cleartext?

---

## Investigation Methodology & Step-by-Step Findings

### Phase 1: High-Level Inspection via `tcpdump`
To triage large packet volume efficiently without GUI overhead, I executed `tcpdump` to isolate connection attempts and inspect flagged flags:

```bash
# Filter for SYN packets with no ACK (indicative of port scans)
tcpdump -nn -r incident_capture.pcap 'tcp[tcpflags] & (tcp-syn) != 0 and tcp[tcpflags] & (tcp-ack) == 0'
