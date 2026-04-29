# Forensics & Incident Response — Complete Specification

## Overview

This document provides comprehensive coverage of digital forensics, network forensics, and incident response methodologies for the AEHM dataset.

**Target examples:** 3M
**Primary focus:** Digital forensics, network forensics, incident response playbooks

---

## Table of Contents

1. [Digital Forensics](#1-digital-forensics)
2. [Network Forensics](#2-network-forensics)
3. [Incident Response](#3-incident-response)
4. [Malware Forensics](#4-malware-forensics)
5. [Cloud Forensics](#5-cloud-forensics)

---

## 1. Digital Forensics

### 1.1 Memory Forensics
- Memory forensics — Volatility3 full command reference
- Memory acquisition techniques
- Memory analysis techniques
- Process analysis
- Thread analysis
- Handle analysis
- Network connection analysis
- Registry analysis
- Service analysis
- Driver analysis

### 1.2 Disk Forensics
- Disk forensics — Autopsy, Sleuthkit workflow
- Disk acquisition techniques
- Disk analysis techniques
- File system analysis
- Partition analysis
- Volume analysis
- MFT analysis
- Registry analysis
- Log analysis
- Artifact analysis

### 1.3 Windows Artifact Analysis

#### Registry Analysis
- Registry hives — SAM, SYSTEM, NTUSER.DAT
- Registry key analysis
- Registry value analysis
- Registry hive analysis
- Registry backup analysis
- Registry transaction analysis
- Registry forensics
- Registry recovery
- Registry parsing
- Registry extraction

#### Event Logs
- Event logs — Security, System, Application
- Security event analysis
- System event analysis
- Application event analysis
- Event log parsing
- Event log analysis
- Event log forensics
- Event log recovery
- Event log extraction
- Event log correlation

#### File System Artifacts
- Prefetch files
- LNK files
- Jump lists
- $MFT analysis
- $LogFile and $UsnJrnl
- NTFS analysis
- FAT analysis
- ExFAT analysis
- ReFS analysis
- File system forensics

#### Browser Artifacts
- Browser artifacts — Chrome, Firefox, Edge
- Chrome history analysis
- Firefox history analysis
- Edge history analysis
- Cookie analysis
- Cache analysis
- Download analysis
- Form data analysis
- Password analysis
- Bookmark analysis

#### Other Windows Artifacts
- Recycle bin analysis
- VSS (Volume Shadow Copies)
- Thumbnail cache
- Search history
- Run history
- Jump lists
- Recent files
- Shell bags
- Amcache

### 1.4 Linux Artifact Analysis
- `/var/log/` analysis
- bash_history, .zsh_history
- `/proc/` live analysis
- Systemd journal analysis
- Cron artifacts
- SSH known_hosts, authorized_keys
- `/etc/passwd`, `/etc/shadow` analysis
- Linux log analysis
- Linux process analysis
- Linux network analysis

### 1.5 macOS Artifact Analysis
- macOS log analysis
- macOS process analysis
- macOS network analysis
- macOS file system analysis
- macOS plist analysis
- macOS keychain analysis
- macOS spotlight analysis
- macOS time machine analysis
- macOS iCloud analysis
- macOS quarantine analysis

---

## 2. Network Forensics

### 2.1 PCAP Analysis
- PCAP analysis — Wireshark filters collection
- Packet capture analysis
- Protocol analysis
- Stream analysis
- Conversation analysis
- Endpoint analysis
- Statistics analysis
- Expert analysis
- I/O graph analysis
- TCP stream analysis

### 2.2 NetFlow Analysis
- NetFlow analysis
- NetFlow v5 analysis
- NetFlow v9 analysis
- IPFIX analysis
- sFlow analysis
- J-Flow analysis
- NetFlow collector
- NetFlow analyzer
- NetFlow visualizer
- NetFlow forensics

### 2.3 DNS Forensics
- DNS forensics — query logs
- DNS query analysis
- DNS response analysis
- DNS cache analysis
- DNS tunneling detection
- DNS exfiltration detection
- DNS rebinding detection
- DNS spoofing detection
- DNS poisoning detection
- DNS amplification detection

### 2.4 HTTP/HTTPS Traffic Analysis
- HTTP/HTTPS traffic analysis
- HTTP request analysis
- HTTP response analysis
- HTTP header analysis
- HTTP body analysis
- HTTP cookie analysis
- HTTP session analysis
- HTTP authentication analysis
- HTTP compression analysis
- HTTP encoding analysis

### 2.5 Email Forensics
- Email header forensics
- Email body analysis
- Email attachment analysis
- Email metadata analysis
- Email routing analysis
- Email authentication analysis
- Email encryption analysis
- Email signature analysis
- Email spoofing detection
- Email phishing detection

### 2.6 Malware C2 Traffic
- Malware C2 traffic identification
- C2 protocol analysis
- C2 beacon analysis
- C2 communication analysis
- C2 encryption analysis
- C2 encoding analysis
- C2 obfuscation analysis
- C2 evasion analysis
- C2 detection
- C2 blocking

### 2.7 Lateral Movement
- Lateral movement in network logs
- SMB lateral movement
- RDP lateral movement
- WinRM lateral movement
- WMI lateral movement
- SSH lateral movement
- PowerShell lateral movement
- PsExec lateral movement
- Custom lateral movement
- Lateral movement detection

### 2.8 Data Exfiltration
- Data exfiltration detection
- Exfiltration channel analysis
- Exfiltration protocol analysis
- Exfiltration timing analysis
- Exfiltration volume analysis
- Exfiltration pattern analysis
- Exfiltration destination analysis
- Exfiltration method analysis
- Exfiltration tool analysis
- Exfiltration prevention

---

## 3. Incident Response

### 3.1 IR Playbook Templates

#### Ransomware Incident
- Ransomware incident response
- Ransomware identification
- Ransomware containment
- Ransomware eradication
- Ransomware recovery
- Ransomware negotiation
- Ransomware payment
- Ransomware decryption
- Ransomware reporting
- Ransomware prevention

#### Data Breach
- Data breach response
- Data breach identification
- Data breach containment
- Data breach eradication
- Data breach recovery
- Data breach notification
- Data breach reporting
- Data breach communication
- Data breach prevention
- Data breach compliance

#### APT Detection
- APT detection response
- APT identification
- APT containment
- APT eradication
- APT recovery
- APT attribution
- APT reporting
- APT communication
- APT prevention
- APT hunting

#### Insider Threat
- Insider threat response
- Insider threat identification
- Insider threat containment
- Insider threat investigation
- Insider threat remediation
- Insider threat reporting
- Insider threat communication
- Insider threat prevention
- Insider threat monitoring
- Insider threat detection

#### Web Application Compromise
- Web application compromise response
- Web application identification
- Web application containment
- Web application eradication
- Web application recovery
- Web application reporting
- Web application communication
- Web application prevention
- Web application hardening
- Web application monitoring

#### Phishing Campaign
- Phishing campaign response
- Phishing identification
- Phishing containment
- Phishing eradication
- Phishing user education
- Phishing reporting
- Phishing communication
- Phishing prevention
- Phishing detection
- Phishing simulation

### 3.2 MITRE ATT&CK Mapping
- MITRE ATT&CK mapping for IR
- TTP identification
- TTP analysis
- TTP attribution
- TTP detection
- TTP prevention
- TTP response
- TTP reporting
- TTP communication
- TTP hunting

### 3.3 Containment Strategies
- Containment strategies by incident type
- Network containment
- System containment
- Account containment
- Data containment
- Service containment
- Application containment
- Device containment
- User containment
- Process containment

### 3.4 Evidence Collection
- Evidence collection and chain of custody
- Evidence acquisition
- Evidence preservation
- Evidence handling
- Evidence storage
- Evidence transport
- Evidence analysis
- Evidence reporting
- Evidence presentation
- Evidence disposal

### 3.5 Communication Templates
- Communication templates — stakeholders, legal, customers
- Stakeholder communication
- Legal communication
- Customer communication
- Employee communication
- Public communication
- Regulatory communication
- Media communication
- Partner communication
- Vendor communication

### 3.6 Post-Incident Analysis
- Post-incident analysis methodology
- Root cause analysis
- Impact assessment
- Lessons learned
- Improvement recommendations
- Process improvement
- Tool improvement
- Training improvement
- Documentation improvement
- Communication improvement

### 3.7 Threat Hunting
- Threat hunting procedures
- Hypothesis-based hunting
- Data-driven hunting
- Intelligence-driven hunting
- Behavioral hunting
- Anomaly hunting
- Signature hunting
- Pattern hunting
- Campaign hunting
- Actor hunting

---

## 4. Malware Forensics

### 4.1 Malware Analysis
- Static malware analysis
- Dynamic malware analysis
- Hybrid malware analysis
- Memory malware analysis
- Network malware analysis
- File malware analysis
- Registry malware analysis
- Process malware analysis
- Service malware analysis
- Driver malware analysis

### 4.2 Malware Identification
- Malware signature identification
- Malware heuristic identification
- Malware behavioral identification
- Malware network identification
- Malware file identification
- Malware registry identification
- Malware process identification
- Malware service identification
- Malware driver identification
- Malware memory identification

### 4.3 Malware Extraction
- Malware file extraction
- Malware memory extraction
- Malware registry extraction
- Malware process extraction
- Malware service extraction
- Malware driver extraction
- Malware network extraction
- Malware configuration extraction
- Malware data extraction
- Malware artifact extraction

### 4.4 Malware Reconstruction
- Malware code reconstruction
- Malware configuration reconstruction
- Malware data reconstruction
- Malware network reconstruction
- Malware timeline reconstruction
- Malware activity reconstruction
- Malware behavior reconstruction
- Malware capability reconstruction
- Malware intent reconstruction
- Malware attribution reconstruction

### 4.5 Malware Reporting
- Malware analysis report
- Malware technical report
- Malware executive report
- Malware legal report
- Malware regulatory report
- Malware stakeholder report
- Malware public report
- Malware peer report
- Malware threat intel report
- Malware attribution report

---

## 5. Cloud Forensics

### 5.1 AWS Forensics
- AWS CloudTrail analysis
- AWS VPC Flow Logs
- AWS S3 access logs
- AWS CloudFront logs
- AWS ELB logs
- AWS Lambda logs
- AWS RDS logs
- AWS CloudWatch logs
- AWS Config analysis
- AWS GuardDuty analysis

### 5.2 Azure Forensics
- Azure Activity Logs
- Azure Monitor logs
- Azure Network Security Group logs
- Azure Application Gateway logs
- Azure Load Balancer logs
- Azure SQL Database logs
- Azure Storage logs
- Azure Key Vault logs
- Azure Security Center logs
- Azure Sentinel analysis

### 5.3 GCP Forensics
- GCP Cloud Audit Logs
- GCP VPC Flow Logs
- GCP Cloud Storage logs
- GCP Cloud Load Balancing logs
- GCP Cloud Functions logs
- GCP Cloud SQL logs
- GCP Cloud Logging
- GCP Cloud Security Command Center
- GCP Chronicle analysis
- GCP Security Health Analytics

### 5.4 Container Forensics
- Docker container forensics
- Kubernetes pod forensics
- Container image forensics
- Container runtime forensics
- Container network forensics
- Container storage forensics
- Container process forensics
- Container system call forensics
- Container file system forensics
- Container registry forensics

### 5.5 SaaS Forensics
- Office 365 forensics
- Google Workspace forensics
- Salesforce forensics
- Slack forensics
- Zoom forensics
- Dropbox forensics
- Box forensics
- GitHub forensics
- GitLab forensics
- Jira forensics

---

*End of Forensics & Incident Response Specification*
