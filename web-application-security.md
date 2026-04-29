# Web Application Security — Complete Specification

## Overview

This document provides comprehensive coverage of web application security vulnerabilities, testing methodologies, and mitigation strategies for the AEHM dataset.

**Target examples:** 10M
**Primary focus:** OWASP Top 10 (2021), advanced web techniques, API security

---

## Table of Contents

1. [OWASP Top 10 (2021)](#1-owasp-top-10-2021)
2. [Advanced Web Techniques](#2-advanced-web-techniques)
3. [API Security](#3-api-security)
4. [GraphQL Security](#4-graphql-security)
5. [WebSocket Security](#5-websocket-security)

---

## 1. OWASP Top 10 (2021)

### 1.1 Broken Access Control (A01)

#### IDOR (Insecure Direct Object Reference)
- IDOR — numeric ID enumeration: `/user/1234` → `/user/1235`
- IDOR — UUID prediction (UUIDv1 timestamp-based)
- IDOR — hashed ID bypass techniques
- Horizontal privilege escalation — same-role resource access
- Vertical privilege escalation — role bypass to admin
- Missing function-level access control — hidden admin endpoints
- Path traversal to access unauthorized files
- JWT claims manipulation — role elevation
- GraphQL — excessive data exposure via introspection
- GraphQL IDOR via object ID in queries
- API versioning bypass — `/v1/admin` accessible but `/v2/admin` not
- Mass assignment — `isAdmin: true` in request body
- Insecure direct object reference in file download
- Referrer-based access control bypass
- Regex-based path matching bypass — `/admin/../user`

#### Access Control Patterns
- Role-based access control (RBAC) bypass techniques
- Attribute-based access control (ABAC) misconfigurations
- Session-based access control flaws
- API key/Token based access control issues
- OAuth2 scope bypass
- SAML assertion manipulation
- JWT algorithm confusion attacks
- Cookie-based session hijacking
- Session fixation vulnerabilities

### 1.2 Cryptographic Failures (A02)

#### Data in Transit
- Cleartext transmission of sensitive data
- Weak cipher suites — TLS 1.0/1.1 still supported
- Mixed content — HTTP resources on HTTPS page
- Certificate validation failures
- Self-signed certificates in production
- Certificate pinning bypass
- TLS downgrade attacks (POODLE, BEAST, CRIME)
- Forward secrecy missing
- HSTS misconfiguration
- OCSP stapling issues

#### Data at Rest
- Weak password hashing — MD5, SHA1, unsalted
- Hardcoded credentials in source
- Insufficient entropy in session tokens
- Sensitive data in URL parameters
- Sensitive data in logs
- Insecure cookie flags — missing Secure/HttpOnly
- Local storage of sensitive data (browser)
- Database encryption missing
- Backup encryption missing
- Key management failures

#### Cryptographic Implementation
- ECB mode usage
- Static IV in CBC mode
- Reused nonces
- Weak key sizes
- Custom crypto implementations
- Timing attacks
- Side-channel vulnerabilities
- Random number generation failures
- Key derivation function misuse

### 1.3 Injection (A03)

#### SQL Injection
- Classic `' OR '1'='1` — detection
- UNION-based SQLi — column count enumeration
- Error-based SQLi — `extractvalue()`, `updatexml()`
- Blind boolean SQLi — `AND 1=1` vs `AND 1=2`
- Time-based blind SQLi — `SLEEP(5)`
- Out-of-band SQLi — DNS exfiltration
- Second-order SQLi — stored then executed
- Stored procedure injection
- NoSQL injection (MongoDB, Redis, etc.)
- ORM injection patterns

#### Cross-Site Scripting (XSS)
- Reflected XSS — URL parameter injection
- Stored XSS — database persistence
- DOM-based XSS — client-side manipulation
- Self-XSS
- XSS via SVG
- XSS via PDF
- XSS in JSON responses
- XSS in HTTP headers
- XSS in WebSockets
- XSS polyglots

#### Other Injection Types
- LDAP injection — `(&(uid=*)(password=*))`
- XPath injection — `/users/user[name/text()='' or ''='' and password/text()='' or ''='']`
- Command injection — all OS types
- SSTI — all templating engines (Jinja2, EJS, Pug, Handlebars, etc.)
- SSRF — cloud metadata, internal services
- XXE — all XML parsers
- HTTP header injection — CRLF
- Email header injection
- Template injection
- Expression language injection

### 1.4 Insecure Design (A04)

#### Authentication Design Flaws
- Missing rate limiting — brute force vectors
- Lack of CAPTCHA — automated form submission
- Insufficient account lockout
- Predictable password reset tokens
- Password reset link not expiring
- Security questions as sole recovery method
- Lack of MFA on privileged actions
- Weak password policies
- Password reuse detection missing
- Credential stuffing protection missing

#### Authorization Design Flaws
- Overly permissive default permissions
- Missing principle of least privilege
- Privilege escalation paths
- Missing separation of duties
- Insecure direct object references
- Missing input validation at design level
- Business logic flaws
- Race conditions in business logic
- Insecure state management
- Missing transaction integrity

### 1.5 Security Misconfiguration (A05)

#### Default Configurations
- Default credentials — list of 200+ default creds by software
- Directory listing enabled
- Debug mode in production
- Unnecessary features/services enabled
- Default accounts not removed
- Default passwords not changed
- Sample code left in production
- Default security headers missing
- Default error pages revealing info
- Default logging levels too verbose

#### Security Headers
- Content-Security-Policy missing or misconfigured
- X-Frame-Options missing
- X-Content-Type-Options missing
- Referrer-Policy missing
- Permissions-Policy missing
- HSTS missing or misconfigured
- Strict-Transport-Security preload issues
- Public-Key-Pins (deprecated but still seen)
- X-XSS-Protection (deprecated but still relevant)

#### CORS Misconfiguration
- CORS wildcard `*` with credentials
- CORS reflecting Origin header without validation
- CORS allowing all methods
- CORS allowing all headers
- CORS preflight cache poisoning
- CORS bypass via null origin
- CORS bypass via subdomain takeover
- CORS bypass via DNS rebinding

#### Cloud & Container Misconfigurations
- Cloud storage bucket public access
- Docker daemon exposed without auth
- Kubernetes dashboard without auth
- Kubernetes RBAC misconfiguration
- Cloud metadata endpoint exposure
- Unsecured cloud databases
- Container escape vulnerabilities
- Orphaned cloud resources
- Unrestricted security groups
- Public IP assignments for private resources

### 1.6 Vulnerable Components (A06)

#### Dependency Management
- Dependency scanning methodology
- CVE exploitation of common frameworks
- Transitive dependency risks
- Component version enumeration techniques
- License compliance as security signal
- Container image vulnerability scanning
- OS package vulnerability management
- Dependency confusion attacks
- Supply chain attacks
- Typosquatting attacks

#### Known Vulnerabilities
- Log4Shell (CVE-2021-44228) — complete analysis
- Spring4Shell (CVE-2022-22965)
- Struts2 vulnerabilities
- Apache Tomcat vulnerabilities
- OpenSSL vulnerabilities (Heartbleed, etc.)
- jQuery XSS vulnerabilities
- Prototype pollution in libraries
- Deserialization vulnerabilities in libraries
- XXE vulnerabilities in parsers
- SSRF in HTTP client libraries

### 1.7 Authentication Failures (A07)

#### Credential Attacks
- Credential stuffing attack methodology
- Password spraying — avoiding lockout
- Brute force with timing correlation
- Dictionary attacks
- Rainbow table attacks
- Pass-the-hash attacks
- Pass-the-ticket attacks
- Golden ticket attacks
- Silver ticket attacks
- Kerberoasting

#### Session Management
- Session fixation attack
- Session token in URL — referrer leakage
- Insufficient session expiration
- Concurrent session handling flaws
- "Remember me" token security
- Session hijacking via XSS
- Session hijacking via network sniffing
- Session prediction attacks
- Session replay attacks
- Session timeout issues

#### Multi-Factor Authentication
- OAuth2 flow vulnerabilities
- SAML authentication bypass
- OpenID Connect misconfigurations
- MFA bypass techniques
- SMS interception for 2FA
- TOTP time sync issues
- Push notification fatigue attacks
- Backup code vulnerabilities
- Device trust issues
- Biometric bypass techniques

### 1.8 Integrity Failures (A08)

#### CI/CD Pipeline Security
- CI/CD pipeline injection
- Supply chain attacks in build process
- Malicious dependency injection
- Build script injection
- Artifact tampering
- Signing key compromise
- Pipeline credential exposure
- Unauthorized code merging
- Environment variable injection
- Container image tampering

#### Software Integrity
- Insecure deserialization (see language-specific sections)
- NPM/pip package integrity
- Update mechanism without signature verification
- Auto-update with HTTP — MITM attack
- Code signing bypass
- Binary tampering
- Source code integrity
- Configuration file tampering
- Database integrity
- Log file tampering

### 1.9 Logging & Monitoring Failures (A09)

#### Logging Issues
- Insufficient logging — what MUST be logged
- Log injection — what to sanitize
- Log4Shell detection signatures
- Missing alerting on suspicious events
- SIEM rule construction for web attacks
- Honeypot field technique
- Log retention policies
- Log access control
- Log tampering detection
- Centralized logging issues

#### Monitoring Gaps
- Missing real-time monitoring
- No anomaly detection
- Missing performance monitoring
- No uptime monitoring
- Missing security event correlation
- No user behavior analytics
- Missing fraud detection
- No DDoS detection
- Missing bot detection
- No API abuse monitoring

### 1.10 SSRF (A10)

#### SSRF Attack Vectors
- Internal network scanning via SSRF
- Cloud metadata — AWS `169.254.169.254`
- Cloud metadata — GCP `metadata.google.internal`
- Cloud metadata — Azure `169.254.169.254/metadata`
- Redis via SSRF — Gopher protocol
- Elasticsearch via SSRF
- SSRF to RCE chain — full examples
- DNS rebinding attack
- File access via SSRF
- Port scanning via SSRF

#### SSRF Filter Bypass
- `http://[::1]/` IPv6
- `http://2130706433/` decimal IP
- `http://0x7f000001/` hex IP
- `http://localhost.attacker.com/` — DNS trick
- URL redirect via open redirect to internal
- `http://0177.0.0.1/` octal IP
- `http://127.1/` shorthand
- `http://127.0.0.1.xip.io/` xip.io bypass
- `http://127.0.0.1.nip.io/` nip.io bypass
- `http://localtest.me/` localtest.me bypass

---

## 2. Advanced Web Techniques

### 2.1 HTTP Request Smuggling
- CL.TE (Content-Length vs Transfer-Encoding)
- TE.CL (Transfer-Encoding vs Content-Length)
- TE.TE (Transfer-Encoding vs Transfer-Encoding)
- HTTP/2 request smuggling
- HTTP/2 CONTINUATION flood
- HTTP/2 header field flooding
- Cache poisoning via request smuggling
- Request queue poisoning
- Backend connection abuse
- Method tunneling
- Downgrade attacks

### 2.2 Cache Poisoning
- Web Cache Deception attack
- Cache poisoning via HTTP headers
- Cache poisoning via request smuggling
- Cache key confusion
- Cache stampede attacks
- Cache decoy attacks
- Cache poisoning via XSS
- Cache poisoning via open redirect
- Cache poisoning via parameter pollution
- Cache poisoning via HTTP/2

### 2.3 Host Header Injection
- Password reset poisoning
- Cache poisoning via Host header
- Open redirect via Host header
- XSS via Host header
- SQL injection via Host header
- Server-side template injection via Host
- Business logic abuse via Host
- Access control bypass via Host
- CSRF bypass via Host
- Session fixation via Host

### 2.4 DOM-Based Attacks
- DOM clobbering
- DOM XSS via postMessage
- DOM XSS via location.hash
- DOM XSS via document.referrer
- DOM XSS via document.cookie
- DOM XSS via localStorage
- DOM XSS via sessionStorage
- DOM XSS via IndexedDB
- DOM XSS via Web Workers
- DOM XSS via Service Workers

### 2.5 Prototype Pollution
- Prototype pollution to XSS
- Prototype pollution to RCE
- Prototype pollution to DoS
- Prototype pollution to bypass WAF
- Prototype pollution to CSRF bypass
- Prototype pollution to authentication bypass
- Prototype pollution to privilege escalation
- Prototype pollution in merge functions
- Prototype pollution in JSON parsers
- Prototype pollution in query parsers

### 2.6 WebSocket Security
- WebSocket hijacking
- WebSocket injection
- WebSocket XSS
- WebSocket CSRF
- WebSocket DoS
- WebSocket authentication bypass
- WebSocket authorization bypass
- WebSocket message manipulation
- WebSocket protocol downgrade
- WebSocket connection flooding

### 2.7 GraphQL Security
- GraphQL injection — all types
- GraphQL batching attack — rate limit bypass
- GraphQL introspection disclosure
- GraphQL field suggestion abuse
- GraphQL alias abuse
- GraphQL directive abuse
- GraphQL nested query DoS
- GraphQL circular reference DoS
- GraphQL authorization bypass
- GraphQL CSRF

### 2.8 REST API Security
- REST API security testing methodology
- REST API mass assignment
- REST API IDOR
- REST API broken authentication
- REST API broken authorization
- REST API rate limiting bypass
- REST API parameter pollution
- REST API HTTP method override
- REST API content-type bypass
- REST API versioning issues

### 2.9 gRPC Security
- gRPC security testing
- gRPC reflection abuse
- gRPC metadata injection
- gRPC authentication bypass
- gRPC authorization bypass
- gRPC DoS attacks
- gRPC message tampering
- gRPC stream hijacking
- gRPC protocol downgrade
- gRPC compression attacks

### 2.10 WebRTC Security
- WebRTC information leakage
- WebRTC IP leak
- WebRTC STUN server abuse
- WebRTC TURN server abuse
- WebRTC bypass VPN
- WebRTC DNS leak
- WebRTC local network discovery
- WebRTC fingerprinting
- WebRTC DoS
- WebRTC MITM

### 2.11 Browser Extension Security
- Extension XSS
- Extension CSRF
- Extension data theft
- Extension privilege escalation
- Extension persistence
- Extension background page abuse
- Extension content script abuse
- Extension manifest manipulation
- Extension update hijacking
- Extension supply chain attacks

### 2.12 CORS-Based Attacks
- CORS-based data theft chains
- CORS-based CSRF bypass
- CORS-based XSS amplification
- CORS-based credential leakage
- CORS-based session hijacking
- CORS-based cache poisoning
- CORS-based request smuggling
- CORS-based parameter pollution
- CORS-based host header injection
- CORS-based open redirect

### 2.13 Iframe & Frame Security
- Iframe sandbox bypass
- Iframe clickjacking
- Iframe XSS
- Iframe CSRF
- Iframe phishing
- Iframe tabnabbing
- Iframe framebusting bypass
- Iframe same-origin bypass
- Iframe postMessage abuse
- Iframe overlay attacks

### 2.14 CSP Bypass Techniques
- CSP via nonce bypass
- CSP via hash bypass
- CSP via strict-dynamic bypass
- CSP via script-src self bypass
- CSP via data-uri bypass
- CSP via object-src bypass
- CSP via base-uri bypass
- CSP via form-action bypass
- CSP via frame-src bypass
- CSP via plugin-types bypass

---

## 3. API Security

### 3.1 REST API Vulnerabilities
- Mass assignment in API requests
- IDOR in API endpoints
- Broken object level authorization
- Broken user authentication
- Excessive data exposure
- Lack of resources & rate limiting
- Improper assets management
- Security misconfiguration
- Injection in API parameters
- Improper error handling

### 3.2 GraphQL API Vulnerabilities
- Introspection disclosure
- Field-level authorization bypass
- Query depth DoS
- Query complexity abuse
- Circular reference DoS
- Batch query abuse
- Alias abuse
- Directive abuse
- Nested query abuse
- Mutation abuse

### 3.3 Authentication in APIs
- API key leakage
- API key brute force
- API key reuse
- JWT algorithm confusion
- JWT expiration bypass
- JWT signature bypass
- OAuth2 token theft
- OAuth2 scope bypass
- OAuth2 redirect_uri abuse
- OAuth2 state parameter bypass

### 3.4 Authorization in APIs
- Role-based access control bypass
- Attribute-based access control bypass
- Permission creep
- Privilege escalation
- Horizontal privilege escalation
- Vertical privilege escalation
- Missing authorization checks
- Inconsistent authorization
- Authorization header manipulation
- Cookie-based auth bypass

### 3.5 Rate Limiting Bypass
- IP-based rate limiting bypass
- User-based rate limiting bypass
- API key-based rate limiting bypass
- Distributed rate limiting bypass
- Rate limiting via multiple endpoints
- Rate limiting via HTTP methods
- Rate limiting via request size
- Rate limiting via connection pooling
- Rate limiting via CDN bypass
- Rate limiting via proxy bypass

### 3.6 API Versioning Issues
- Versioning via URL path issues
- Versioning via header issues
- Versioning via query param issues
- Deprecated version exposure
- Version-specific vulnerabilities
- Version rollback attacks
- Version confusion attacks
- Version downgrade attacks
- Version mismatch issues
- Version-specific bypasses

---

## 4. GraphQL Security

### 4.1 GraphQL-Specific Vulnerabilities
- Introspection enabled in production
- Query depth not limited
- Query complexity not limited
- Field suggestion enabled
- Debug mode enabled
- Playground enabled in production
- Tracing enabled in production
- Apollo Engine telemetry
- GraphQL batching not rate-limited
- GraphQL alias abuse

### 4.2 GraphQL Injection
- GraphQL query injection
- GraphQL mutation injection
- GraphQL subscription injection
- GraphQL directive injection
- GraphQL fragment injection
- GraphQL variable injection
- GraphQL argument injection
- GraphQL field injection
- GraphQL type injection
- GraphQL schema injection

### 4.3 GraphQL Authorization
- Field-level authorization missing
- Type-level authorization missing
- Query-level authorization missing
- Mutation-level authorization missing
- Subscription-level authorization missing
- Directive-level authorization missing
- Resolver-level authorization missing
- Schema-level authorization missing
- Operation-level authorization missing
- Context-level authorization missing

### 4.4 GraphQL DoS
- Query depth DoS
- Query complexity DoS
- Nested query DoS
- Circular reference DoS
- Alias abuse DoS
- Fragment abuse DoS
- Directive abuse DoS
- Batch query DoS
- Subscription abuse DoS
- WebSocket abuse DoS

---

## 5. WebSocket Security

### 5.1 WebSocket Authentication
- Missing authentication
- Weak authentication
- Authentication bypass
- Session hijacking
- Token theft
- Credential leakage
- Replay attacks
- Man-in-the-middle
- Downgrade attacks
- Protocol confusion

### 5.2 WebSocket Authorization
- Missing authorization
- Authorization bypass
- Privilege escalation
- Resource access
- Message access
- Channel access
- Room access
- User access
- Admin access
- Function access

### 5.3 WebSocket Injection
- Message injection
- Command injection
- SQL injection
- XSS via WebSocket
- CSRF via WebSocket
- Protocol injection
- Header injection
- Origin injection
- Parameter injection
- Content injection

### 5.4 WebSocket DoS
- Connection flooding
- Message flooding
- Large message DoS
- Slowloris for WebSocket
- Memory exhaustion
- CPU exhaustion
- File descriptor exhaustion
- Bandwidth exhaustion
- Resource exhaustion
- Amplification attacks

---

*End of Web Application Security Specification*
