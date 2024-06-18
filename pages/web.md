# 🌐 Web

Sources: [OWASP](https://owasp.org/)

## 🏛️ Application Architectures

- Monolytic
- Front/Backend
- Mobile
- Micro Services
- Serveless

## 🪰 OWASP - Open Worldwide Application Security Project

It is a nonprofit foundation that provides guidance on how to develop, purchase and maintain trustworthy and secure software applications.

### TOP 10 Vulnerabilities (2021):

**A01:2021** - Broken Access Control
**A02:2021** - Cryptographic Flaws
**A03:2021** - Injection
**A04:2021** - Insecure Design
**A05:2021** - Security Misconfiguration
**A06:2021** - Vulnerable and Outdated Components
**A07:2021** - Identification and Authentication Failures
**A08:2021** - Software Failures and Data Integrity
**A09:2021** - Logging and Security Monitoring Failures
**A10:2021** - Server-Side Request Forgery

### Broken Access Control

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| Inadequate access and permissions control. | Capture of information to which the user should not have access. | Effective permission controls. |

### Cryptographic Flaws

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| Weak cryptographic algorithms. | Potential leak of confidential data. | Ensure that any confidential information is transmitted over trusted channels and stored correctly. |

### Injection

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| Some part of the application interprets information injected by the user as a command or code. | Execution of malicious code that can break data integrity. | Sanitize all user input before storage. |

### Insecure Design

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| Security aspects were not considered during the development phase. | Break application flows or enter the company environment. | Mapping risks and vulnerabilities and applying good security practices in development. |

### Security Misconfiguration

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| Incorrect configuration, use of default passwords, error handling with information for the attacker. | XSS execution, cookie hijacking, abuse of default passwords. | Secure development, using minimal resources (less is more). |

### Vulnerable and Outdated Components

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| Use of components from dubious sources and no inventory of third-party components allowed. | It depends on the vulnerability. | Remove unused dependencies, only use components from trusted sources, use component inventory, keep them updated. |

### Identification and Authentication Failures

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| Authentication and user session failures. | Account takeover. | Strong passwords, MFA, brute force protection, user session management. |

### Software Failures and Data Integrity

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| No integrity check process in development. | The integrity of the correct application flow fails. | Check the reliability of the sources used, code review. |

### Logging and Security Monitoring Failures

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| There is no recording and monitoring of activities carried out for possible audits. | In an incident, there is not enough data recorded to understand what happened. | Grant logs and monitoring of a system's critical operations. |

### Server-Side Request Forgery

| ⚠️ Cause | 💣 Consequence | 🛡️ Mitigation |
| --- | --- | --- |
| The application interacts with the URL without validation. | Port scanning, captures information from other sources. | Validate inputs, create whitelists, and separate the application environment. |

[Web - Authentication](/pages/web-auth.md)

[Web - Access Control](/pages/web-access.md)