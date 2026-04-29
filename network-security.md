# Network Security — Complete Specification

## Overview

This document provides comprehensive coverage of network security vulnerabilities, reconnaissance techniques, protocol exploits, and network-based attack methodologies for the AEHM dataset.

**Target examples:** 8M
**Primary focus:** Reconnaissance, protocol vulnerabilities, network attacks, Active Directory

---

## Table of Contents

1. [Reconnaissance](#1-reconnaissance)
2. [Protocol Vulnerabilities](#2-protocol-vulnerabilities)
3. [Active Directory Security](#3-active-directory-security)
4. [Network Attacks](#4-network-attacks)
5. [Wireless Security](#5-wireless-security)
6. [Network Forensics](#6-network-forensics)

---

## 1. Reconnaissance

### 1.1 Passive Reconnaissance
- WHOIS queries — domain ownership information
- DNS enumeration — subdomain discovery
- Shodan search — internet-connected devices
- Censys search — certificate and device enumeration
- FOFA search — Chinese internet device search
- ZoomEye search — Chinese cyber mapping
- BinaryEdge search — internet intelligence
- SecurityTrails — historical DNS data
- Wayback Machine — archived content
- Google Dorking — advanced search techniques
- Social media OSINT — employee, technology info
- Certificate transparency logs — subdomain discovery
- DNSSEC analysis — security configuration
- ASN lookup — network ownership
- BGP hijacking detection — route manipulation
- IP geolocation — physical location inference
- NetFlow analysis — traffic patterns
- Passive DNS replication — historical DNS records
- Threat intelligence feeds — known malicious IPs/domains

### 1.2 Active Reconnaissance

#### Port Scanning
- nmap scan types — full flag analysis
  - TCP SYN scan (-sS)
  - TCP connect scan (-sT)
  - UDP scan (-sU)
  - SCTP scan (-sY)
  - FIN scan (-sF)
  - NULL scan (-sN)
  - Xmas scan (-sX)
  - ACK scan (-sA)
  - Window scan (-sW)
  - Maimon scan (-sM)
- Service version detection (-sV)
- OS fingerprinting (-O)
- Aggressive scan (-A)
- Script scanning with NSE
- Timing templates (-T)
- Evasion techniques
- Fragmentation scans
- Decoy scans
- Source port manipulation
- MAC address spoofing

#### Service Enumeration
- Banner grabbing techniques
- Service fingerprinting
- Version detection
- Default credential testing
- Anonymous access testing
- Service misconfiguration detection
- Vulnerability scanning via nmap scripts
- Custom NSE script development

### 1.3 OS Fingerprinting
- TTL analysis — OS identification
- TCP stack behavior — window size, flags
- ICMP fingerprinting
- HTTP server header analysis
- SSH protocol version analysis
- FTP banner analysis
- SMB version detection
- SNMP system description
- NTP monlist detection
- Passive OS fingerprinting (p0f)

### 1.4 DNS Enumeration
- Zone transfer attempts (AXFR/IXFR)
- DNS brute force — subdomain discovery
- Reverse lookup — PTR records
- DNS record types — A, AAAA, MX, NS, TXT, SRV, CNAME
- DNSSEC validation
- Wildcard DNS detection
- DNS cache snooping
- DNSSEC NSEC/NSEC3 zone walking
- DNS rebinding detection
- DNS tunneling detection

### 1.5 Subdomain Enumeration
- Subfinder — passive subdomain discovery
- Amass — comprehensive subdomain enumeration
- dnsx — DNS resolution toolkit
- Assetfinder — subdomain discovery
- Sublist3r — fast subdomain enumeration
- DNSBrute — brute force subdomain discovery
- Aquatone — subdomain reconnaissance
- CTFR — certificate transparency subdomain enumeration
- Subscrapers — aggregated subdomain discovery
- Crt.sh — certificate transparency log mining

### 1.6 Network Topology Mapping
- Traceroute analysis — hop-by-hop path
- TTL-based hop detection
- ICMP-based traceroute
- TCP-based traceroute
- UDP-based traceroute
- AS path analysis
- BGP route visualization
- Network mapping tools
- Network diagram generation

### 1.7 Service-Specific Enumeration

#### SNMP Enumeration
- SNMP community strings — public, private
- SNMP MIB walking
- SNMPv3 authentication bypass
- SNMP trap monitoring
- SNMP set operations
- SNMP version detection

#### SMB Enumeration
- Null session authentication
- Share listing
- User enumeration
- Group enumeration
- Password policy enumeration
- SMB version detection
- SMB signing status
- SMB encryption status

#### LDAP Enumeration
- Anonymous bind
- Base DN discovery
- User enumeration
- Group enumeration
- Computer enumeration
- GPO enumeration
- ACL enumeration
- Schema enumeration

#### NFS Enumeration
- Showmount — exported shares
- NFS version detection
- NFS root squash testing
- NFS export testing
- NFS mount testing

#### RPC Enumeration
- rpcinfo — RPC service enumeration
- RPC program mapping
- RPC version detection
- Null RPC session
- RPC authentication bypass

---

## 2. Protocol Vulnerabilities

### 2.1 TCP/IP Vulnerabilities

#### TCP Attacks
- SYN flood — DoS methodology
- SYN cookie bypass
- TCP session hijacking
- TCP reset injection (RST)
- TCP sequence prediction
- TCP ACK storm
- TCP FIN scan evasion
- TCP window size manipulation
- TCP timestamp abuse
- TCP MD5 signature bypass

#### IP Attacks
- IP spoofing — when possible and limits
- IP fragmentation attacks
- Tiny fragment attack
- Overlapping fragment attack
- IP options abuse
- IP source routing
- IP record route abuse
- IP timestamp abuse

### 2.2 ARP Vulnerabilities
- ARP spoofing / ARP cache poisoning
- MITM via ARP — full attack chain
- Dynamic ARP Inspection bypass
- Gratuitous ARP abuse
- ARP flood DoS
- ARP cache timeout abuse
- ARP request spoofing
- ARP reply spoofing

### 2.3 DNS Vulnerabilities
- DNS spoofing / cache poisoning (Kaminsky attack)
- DNS amplification DDoS
- DNS tunneling — data exfiltration
- DNS rebinding — full attack chain
- NXDOMAIN hijacking
- DNS over HTTPS (DoH) — evasion technique
- DNS over TLS (DoT) — evasion technique
- DNSSEC bypass techniques
- DNS server exploitation
- DNS zone transfer abuse

### 2.4 SMB Vulnerabilities
- EternalBlue (MS17-010) — full exploitation
- SMB relay attack — NTLM relay to SMB
- PrintNightmare (CVE-2021-1675) — full chain
- PetitPotam — NTLM coercion
- SMBGhost (CVE-2020-0796)
- Pass-the-Hash via SMB
- Pass-the-Ticket via SMB
- SMB encryption bypass
- SMB signing bypass
- SMB1 exploitation

### 2.5 RDP Vulnerabilities
- BlueKeep (CVE-2019-0708) — analysis
- DejaBlue family (CVE-2019-1181, 1182)
- RDP credential brute force
- RDP session hijacking — tscon technique
- NLA bypass
- RDP man-in-the-middle
- RDP reverse connection
- RDP clipboard abuse
- RDP drive mapping abuse
- RDP printer abuse

### 2.6 LDAP/Kerberos Vulnerabilities
- Kerberoasting — full methodology
- AS-REP Roasting
- Pass-the-Ticket
- Golden Ticket attack
- Silver Ticket attack
- DCSync attack
- LDAP pass-back attack
- Kerberos delegation abuse
  - Unconstrained delegation
  - Constrained delegation
  - Resource-based constrained delegation
- Kerberoasting without SPN
- Shadow Credentials
- LDAP injection
- LDAP relay attack

---

## 3. Active Directory Security

### 3.1 AD Enumeration
- Domain enumeration
- Forest enumeration
- Trust relationship enumeration
- User enumeration
- Group enumeration
- Computer enumeration
- GPO enumeration
- OU enumeration
- ACL enumeration
- Schema enumeration

### 3.2 AD Authentication Attacks
- Password spraying
- Credential stuffing
- Brute force attacks
- Pass-the-Hash
- Pass-the-Ticket
- Golden Ticket
- Silver Ticket
- Diamond Ticket
- Forged SAML tokens
- LDAP bind redirect

### 3.3 AD Privilege Escalation
- Kerberoasting
- AS-REP Roasting
- Unconstrained delegation abuse
- Constrained delegation abuse
- Resource-based delegation abuse
- DCSync
- SID history injection
- AdminSDHolder abuse
- Shadow Credentials
- Group manipulation

### 3.4 AD Persistence
- Golden Ticket persistence
- Silver Ticket persistence
- Shadow Credentials persistence
- Custom SSP persistence
- SID history injection
- Forest trust abuse
- Backdoor accounts
- GPO abuse
- Scheduled task abuse
- Service abuse

### 3.5 AD Lateral Movement
- WMI lateral movement
- WinRM lateral movement
- PSExec lateral movement
- SMB lateral movement
- RDP lateral movement
- DCOM lateral movement
- Scheduled task lateral movement
- Service lateral movement
- PowerShell remoting
- Remote file copy

---

## 4. Network Attacks

### 4.1 Man-in-the-Middle Attacks
- ARP spoofing MITM
- DNS spoofing MITM
- ICMP redirect MITM
- BGP hijacking MITM
- SSL stripping
- HTTPS downgrade
- TLS interception
- Certificate spoofing
- HSTS bypass
- HPKP bypass

### 4.2 Denial of Service
- SYN flood DoS
- UDP flood DoS
- ICMP flood DoS
- HTTP flood DoS
- Slowloris attack
- Slow POST attack
- RUDY attack
- DNS amplification DoS
- NTP amplification DoS
- SSDP amplification DoS

### 4.3 Network Sniffing
- ARP poisoning for sniffing
- Hub sniffing
- Port mirroring abuse
- VLAN hopping
- MAC flooding
- DHCP spoofing
- STP manipulation
- CDP abuse
- LLDP abuse
- VTP abuse

### 4.4 Network Exploitation
- Router exploitation
- Switch exploitation
- Firewall exploitation
- IPS/IDS evasion
- VPN exploitation
- Load balancer exploitation
- Proxy exploitation
- NAT traversal
- Port forwarding abuse
- Tunneling techniques

---

## 5. Wireless Security

### 5.1 Wi-Fi Security
- WEP cracking
- WPA-PSK cracking
- WPA2-PSK cracking
- WPA3-SAE attacks
- WPA2 Enterprise attacks
- Evil Twin attack
- Karma attack
- Wi-Fi Pineapple attacks
- Deauthentication attack
- Beacon flooding

### 5.2 Bluetooth Security
- Bluejacking
- Bluesnarfing
- BlueBorne vulnerability
- Bluetooth PIN cracking
- Bluetooth MITM
- Bluetooth tracking
- Bluetooth DoS
- BLE exploitation
- Bluetooth pairing attacks
- Bluetooth relay attacks

### 5.3 NFC/RFID Security
- RFID cloning
- NFC relay attacks
- Contactless payment attacks
- Access card cloning
- RFID sniffing
- NFC MITM
- RFID jamming
- NFC DoS
- RFID replay attacks
- RFID encryption bypass

---

## 6. Network Forensics

### 6.1 Packet Analysis
- PCAP analysis methodology
- Wireshark advanced filtering
- Network traffic reconstruction
- Protocol analysis
- Stream reconstruction
- File extraction from PCAP
- Malware C2 detection
- Data exfiltration detection
- Lateral movement detection
- Anomaly detection

### 6.2 Log Analysis
- Firewall log analysis
- IDS/IPS log analysis
- Proxy log analysis
- DNS log analysis
- DHCP log analysis
- Authentication log analysis
- VPN log analysis
- NetFlow analysis
- sFlow analysis
- IPFIX analysis

### 6.3 Network Evidence Collection
- Memory acquisition for network evidence
- Network interface capture
- ARP table collection
- Routing table collection
- Network configuration collection
- Service collection
- Process network connection collection
- Open port collection
- Network statistics collection
- Network performance metrics

---

*End of Network Security Specification*
