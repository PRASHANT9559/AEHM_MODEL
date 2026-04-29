# Red Team Operations — Complete Specification

## Overview

This document provides comprehensive coverage of red team operations, infrastructure setup, initial access techniques, post-exploitation methodologies, and operational security for the AEHM dataset.

**Target examples:** 3M
**Primary focus:** C2 infrastructure, initial access, post-exploitation, OPSEC

---

## Table of Contents

1. [Infrastructure](#1-infrastructure)
2. [Initial Access](#2-initial-access)
3. [Post-Exploitation](#3-post-exploitation)
4. [Operational Security](#4-operational-security)
5. [Reporting](#5-reporting)

---

## 1. Infrastructure

### 1.1 C2 Framework Comparison
- C2 framework comparison: Cobalt Strike, Sliver, Havoc, Brute Ratel
- Cobalt Strike setup and configuration
- Sliver setup and configuration
- Havoc setup and configuration
- Brute Ratel setup and configuration
- Empire setup and configuration
- Metasploit setup and configuration
- Covenant setup and configuration
- Koadic setup and configuration
- PoshC2 setup and configuration

### 1.2 Redirector Setup
- Redirector setup — Apache, nginx mod_rewrite
- Apache redirector configuration
- Nginx redirector configuration
- HAProxy redirector configuration
- Squid redirector configuration
- DNS redirector configuration
- CDN redirector configuration
- Cloud redirector configuration
- Load balancer redirector
- Proxy redirector

### 1.3 Domain Fronting
- Domain fronting technique
- Azure Front Door domain fronting
- CloudFront domain fronting
- Akamai domain fronting
- Fastly domain fronting
- Cloudflare domain fronting
- Imperva domain fronting
- F5 domain fronting
- NGINX domain fronting
- Apache domain fronting

### 1.4 CDN as C2 Cover
- CDN as C2 cover
- CloudFront C2
- Cloudflare C2
- Akamai C2
- Fastly C2
- Azure Front Door C2
- Google Cloud CDN C2
- Fastly C2
- Limelight C2
- Level3 C2

### 1.5 Malleable C2 Profiles
- Malleable C2 profiles
- HTTP profile configuration
- DNS profile configuration
- SMB profile configuration
- TCP profile configuration
- External C2 profile configuration
- Service profile configuration
- Process profile configuration
- User profile configuration
- Post-ex profile configuration

### 1.6 Payload Staging
- Payload staging infrastructure
- Staging server setup
- Staging server hardening
- Staging server OPSEC
- Staging server monitoring
- Staging server logging
- Staging server backup
- Staging server recovery
- Staging server rotation
- Staging server retirement

### 1.7 OPSEC Fundamentals
- OPSEC fundamentals — attribution avoidance
- Attribution avoidance techniques
- Identity protection
- Location protection
- Infrastructure protection
- Operational security
- Communication security
- Technical security
- Physical security

### 1.8 Operational Security Failures
- Operational security failures — real case studies
- Attribution case studies
- Detection case studies
- Compromise case studies
- Failure analysis
- Lessons learned
- Best practices
- Common mistakes
- Mitigation strategies
- Prevention techniques

---

## 2. Initial Access

### 2.1 Phishing with Payload Delivery
- Phishing with payload delivery
- Phishing email construction
- Phishing attachment preparation
- Phishing link preparation
- Phishing landing page
- Phishing infrastructure
- Phishing automation
- Phishing tracking
- Phishing analytics
- Phishing optimization

### 2.2 Malicious Macro Documents
- Malicious macro document construction
- VBA macro development
- Excel 4.0 macro development
- Word macro development
- PowerPoint macro development
- Macro obfuscation
- Macro evasion
- Macro persistence
- Macro C2
- Macro data theft

### 2.3 LNK File Payload
- LNK file payload delivery
- LNK file construction
- LNK file obfuscation
- LNK file evasion
- LNK file persistence
- LNK file C2
- LNK file data theft
- LNK file automation
- LNK file tracking
- LNK file analytics

### 2.4 ISO/IMG File Delivery
- ISO/IMG file delivery (UAC bypass)
- ISO file construction
- IMG file construction
- ISO file obfuscation
- IMG file evasion
- ISO file persistence
- IMG file C2
- ISO file data theft
- IMG file automation
- ISO file tracking

### 2.5 HTML Smuggling
- HTML smuggling technique
- HTML smuggling construction
- HTML smuggling obfuscation
- HTML smuggling evasion
- HTML smuggling persistence
- HTML smuggling C2
- HTML smuggling data theft
- HTML smuggling automation
- HTML smuggling tracking
- HTML smuggling analytics

### 2.6 Browser Exploit Delivery
- Browser exploit delivery
- Exploit kit setup
- Exploit kit configuration
- Exploit kit hardening
- Exploit kit OPSEC
- Exploit kit monitoring
- Exploit kit logging
- Exploit kit backup
- Exploit kit recovery
- Exploit kit rotation

### 2.7 External-Facing Service Exploitation
- External-facing service exploitation
- Service enumeration
- Service vulnerability assessment
- Service exploitation
- Service persistence
- Service C2
- Service data theft
- Service lateral movement
- Service privilege escalation
- Service detection evasion

### 2.8 Supply Chain Compromise
- Supply chain compromise (testing owned environments)
- Software supply chain
- Hardware supply chain
- Service supply chain
- Cloud supply chain
- Container supply chain
- Dependency supply chain
- Build supply chain
- Deployment supply chain
- Update supply chain

### 2.9 Physical Access Techniques
- Physical access techniques
- Physical intrusion
- Physical reconnaissance
- Physical attack
- Physical exploitation
- Physical persistence
- Physical C2
- Physical data theft
- Physical lateral movement
- Physical detection evasion

---

## 3. Post-Exploitation

### 3.1 Local Privilege Escalation
- Local privilege escalation — Windows (all techniques)
- Windows kernel exploits
- Windows service exploits
- Windows driver exploits
- Windows token manipulation
- Windows UAC bypass
- Windows registry abuse
- Windows scheduled task abuse
- Windows WMI abuse
- Windows COM abuse

### 3.2 Linux Privilege Escalation
- Local privilege escalation — Linux (all techniques)
- Linux kernel exploits
- Linux SUID exploits
- Linux sudo exploits
- Linux capability abuse
- Linux cron abuse
- Linux systemd abuse
- Linux PATH abuse
- Linux LD_PRELOAD abuse
- Linux library abuse

### 3.3 Credential Access
- Credential access — LSASS, credential manager, browser
- LSASS memory dumping
- Credential manager extraction
- Browser credential extraction
- Windows credential manager
- Linux keyring extraction
- macOS keychain extraction
- Password file extraction
- SSH key extraction
- Certificate extraction

### 3.4 Lateral Movement
- Lateral movement techniques
- Windows lateral movement
- Linux lateral movement
- Network lateral movement
- Application lateral movement
- Service lateral movement
- Protocol lateral movement
- Credential lateral movement
- Token lateral movement
- Certificate lateral movement

### 3.5 Persistence Mechanisms
- Persistence mechanisms — all OS types
- Windows persistence
- Linux persistence
- macOS persistence
- Registry persistence
- File system persistence
- Scheduled task persistence
- Service persistence
- WMI persistence
- Startup persistence

### 3.6 Defense Evasion
- Defense evasion — all techniques
- Process evasion
- File evasion
- Registry evasion
- Network evasion
- Memory evasion
- Logging evasion
- Monitoring evasion
- Detection evasion
- Analysis evasion

### 3.7 Exfiltration
- Exfiltration — all techniques and detection evasion
- Data exfiltration
- File exfiltration
- Database exfiltration
- Network exfiltration
- Cloud exfiltration
- Protocol exfiltration
- Channel exfiltration
- Method exfiltration
- Tool exfiltration

### 3.8 Impact
- Impact — ransomware simulation, data destruction
- Ransomware simulation
- Data destruction
- Service disruption
- Data corruption
- System corruption
- Network disruption
- Availability disruption
- Integrity disruption
- Confidentiality disruption

---

## 4. Operational Security

### 4.1 Attribution Avoidance
- Attribution avoidance techniques
- Identity protection
- Location protection
- Infrastructure protection
- Operational protection
- Technical protection
- Communication protection
- Physical protection
- Financial protection
- Legal protection

### 4.2 Infrastructure Protection
- Infrastructure protection techniques
- Domain protection
- IP protection
- Server protection
- Network protection
- Storage protection
- Application protection
- Service protection
- Account protection
- Credential protection

### 4.3 Communication Security
- Communication security techniques
- Encrypted communication
- Anonymous communication
- Secure communication
- Private communication
- Hidden communication
- Covert communication
- Ephemeral communication
- Disposable communication
- Temporary communication

### 4.4 Technical Security
- Technical security techniques
- Anti-forensics
- Anti-analysis
- Anti-detection
- Anti-monitoring
- Anti-logging
- Anti-tracing
- Anti-auditing
- Anti-investigation
- Anti-attribution

### 4.5 Physical Security
- Physical security techniques
- Location security
- Travel security
- Accommodation security
- Equipment security
- Communication security
- Financial security
- Identity security
- Document security
- Digital security

---

## 5. Reporting

### 5.1 Executive Summary
- Executive summary
- Executive overview
- Executive highlights
- executive findings
- Executive recommendations
- Executive timeline
- Executive budget
- Executive risks
- executive opportunities
- executive next steps

### 5.2 Technical Report
- Technical report
- Technical overview
- Technical findings
- Technical details
- Technical evidence
- Technical artifacts
- Technical timeline
- Technical recommendations
- Technical remediation
- technical validation

### 5.3 Findings Report
- Findings report
- Findings overview
- Findings details
- Findings evidence
- Findings artifacts
- Findings timeline
- Findings impact
- Findings severity
- Findings likelihood
- Findings confidence

### 5.4 Recommendations Report
- Recommendations report
- Recommendations overview
- Recommendations details
- Recommendations priority
- Recommendations timeline
- Recommendations budget
- Recommendations resources
- Recommendations validation
- Recommendations tracking
- Recommendations reporting

### 5.5 Appendix
- Appendix
- Technical details
- Evidence details
- Artifact details
- Timeline details
- Tool details
- Methodology details
- Scope details
- Limitations details
- Assumptions details
- Definitions details

---

*End of Red Team Operations Specification*
