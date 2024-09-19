# Aurory Website Security Overview

This repository contains information about security vulnerabilities discovered on the Aurory website using the OWASP ZAP scanning tool. The findings highlight potential security risks, categorized into different severity levels, and provide recommendations for mitigation.

## Table of Contents

- [Project Overview](#project-overview)
- [Vulnerabilities Discovered](#vulnerabilities-discovered)
  - [Missing Secure or HTTPOnly Cookie Flag](#missing-secure-or-httponly-cookie-flag)
  - [Content Security Policy (CSP) Issues](#content-security-policy-csp-issues)
  - [Cross-Domain JavaScript Source File Inclusion](#cross-domain-javascript-source-file-inclusion)
  - [Strict-Transport-Security (HSTS) Not Set](#strict-transport-security-hsts-not-set)
  - [Information Disclosure](#information-disclosure)
- [Business Impact](#business-impact)
- [Remediation Recommendations](#remediation-recommendations)
- [Proof of Concept (PoC)](#proof-of-concept-poc)
- [Contact](#contact)

---

## Project Overview

Aurory is a play-to-earn, Japanese role-playing game built on the Solana blockchain. This project highlights the security vulnerabilities discovered on the Aurory website through an OWASP ZAP scan, with actionable steps for remediation.

### Scan Details:

- **Tool**: OWASP ZAP
- **Target URLs**:
  - [https://app.aurory.io](https://app.aurory.io)
  - [https://login.live.aurory.io](https://login.live.aurory.io)
- **Date of Scan**: 18th September 2024

## Vulnerabilities Discovered

### 1. Missing Secure or HTTPOnly Cookie Flag

**Severity**: Low  
**Description**: Some session cookies do not have the `Secure` or `HTTPOnly` flag set, leaving them vulnerable to attacks such as session hijacking or cookie theft via cross-site scripting (XSS).  
**Impact**: Attackers can access sensitive cookie data, compromising user sessions.  
**Remediation**: Ensure that all session cookies include the `Secure` and `HTTPOnly` attributes.  

More details can be found in [Missing Secure or HTTPOnly Cookie Flag](#missing-secure-or-httponly-cookie-flag).

### 2. Content Security Policy (CSP) Issues

**Severity**: Medium  
**Description**: The Content Security Policy (CSP) allows unsafe inline and eval JavaScript execution, increasing the risk of XSS attacks.  
**Impact**: Attackers could inject malicious scripts to steal data or perform unauthorized actions.  
**Remediation**: Strengthen the CSP by removing `unsafe-inline` and `unsafe-eval` directives.  

### 3. Cross-Domain JavaScript Source File Inclusion

**Severity**: Low  
**Description**: The website loads JavaScript from external sources that may not be trusted, potentially exposing the site to malicious script injection.  
**Impact**: External JavaScript sources can introduce security risks.  
**Remediation**: Ensure that all JavaScript files are loaded from trusted and secure domains only.

### 4. Strict-Transport-Security (HSTS) Not Set

**Severity**: Low  
**Description**: The website does not enforce the Strict-Transport-Security (HSTS) header, making it vulnerable to protocol downgrade attacks.  
**Impact**: Attackers can intercept traffic by forcing the browser to use HTTP instead of HTTPS.  
**Remediation**: Add the HSTS header with a sufficient `max-age` value to enforce HTTPS.

### 5. Information Disclosure

**Severity**: Low  
**Description**: The server leaks version information via the `Server` HTTP response header, which could be used to craft targeted attacks.  
**Impact**: Attackers can gather information about server software versions.  
**Remediation**: Disable or sanitize server version headers to reduce the risk of targeted attacks.

## Business Impact

These vulnerabilities can lead to:
- Loss of customer trust and reputational damage.
- Session hijacking and unauthorized access to user accounts.
- Data theft and potential exposure of sensitive information.
- Potential financial losses due to exploited vulnerabilities.

## Remediation Recommendations

- **Cookie Security**: Ensure all session cookies use the `Secure` and `HTTPOnly` flags.
- **CSP**: Implement a strict Content Security Policy that disallows unsafe script sources.
- **HSTS**: Configure HTTP headers to enforce HTTPS for all connections.
- **Information Disclosure**: Remove or sanitize headers that leak version or software details.


