# Bank Production Windows Hardening – Credentialed Vulnerability Remediation

## Project Overview
This project simulates a real-world **banking environment vulnerability management workflow**.  
The objective was to identify, remediate, and validate security weaknesses on a Windows production system using **credentialed vulnerability scanning**, **network access controls**, and **operating system hardening**.

The focus of this engagement was **reducing cryptographic risk and external exposure**, two areas that are heavily scrutinized in regulated financial environments.

---

## Business Context (Why This Matters)
Financial institutions are frequent targets for:
- Credential abuse
- Lateral movement
- Weak cryptographic configurations
- Compliance violations

Even configuration-level weaknesses — such as deprecated TLS protocols — can:
- Violate regulatory requirements
- Increase breach impact
- Lead to audit findings
- Expose customer data

This project demonstrates how **small, targeted changes** significantly reduce risk while maintaining business functionality.

---

## Scope of Work
- Environment: Azure-hosted Windows 11 virtual machine
- Scan Type: **Credentialed vulnerability scan**
- Scanner Access: Restricted to a known internal scanner IP
- Objective:
  - Identify insecure cryptographic protocols
  - Remediate OS-level vulnerabilities
  - Validate fixes through rescanning
  - Maintain least-privilege network access

---

## Initial Findings (Pre-Remediation)
The initial scan identified the following **Medium-severity findings**:

- TLS Version 1.0 Protocol Enabled
- TLS Version 1.1 Deprecated Protocol Enabled
- SSL Certificate Cannot Be Trusted
- SSL Self-Signed Certificate

From a banking risk perspective, **TLS 1.0 and 1.1 posed the highest concern**, as they:
- Are cryptographically weak
- Are explicitly disallowed by modern security standards
- Increase exposure to downgrade and interception attacks

---

## Risk Assessment
The presence of deprecated TLS protocols represents:
- **Confidentiality risk** to encrypted communications
- **Regulatory non-compliance**
- **Increased attack surface** for man-in-the-middle techniques

In regulated environments, these configurations are typically classified as:
- High audit priority
- Required remediation items
- Policy violations if left unaddressed

---

## Remediation Actions Taken

### 1. Network Security Group (NSG) Hardening
Inbound access was restricted to:
- Administrative RDP access from a single trusted IP
- Credentialed scanner access from an internal scanner IP

All other inbound traffic remained **explicitly denied by default**.

This enforced:
- Least privilege network access
- Reduced external attack surface
- Separation of management and scanning traffic

---

### 2. Operating System Hardening (SCHANNEL)
Deprecated cryptographic protocols were disabled at the OS level using Windows SCHANNEL configuration:

- TLS 1.0 – Disabled (Server-side)
- TLS 1.1 – Disabled (Server-side)

This ensures:
- The system cannot negotiate insecure encryption
- Applications inherit secure defaults
- Configuration persists across reboots

A system restart was performed to fully apply changes.

---

## Validation & Verification
After remediation:
- A **follow-up credentialed vulnerability scan** was executed
- TLS 1.0 and TLS 1.1 findings were **fully remediated**
- No regressions or service disruption were observed

Remaining findings were reviewed and categorized as:
- Informational (expected in credentialed scans)
- Low risk
- Accepted risk pending future architectural changes

---

## Regulatory & Compliance Alignment
This remediation aligns with common financial industry requirements, including:

- **PCI DSS**
  - Requirement 4: Strong cryptography and secure protocols
- **NIST SP 800-52**
  - Guidelines for TLS usage
- **NIST SP 800-53**
  - System and communications protection controls
- **FFIEC Cybersecurity Assessment Tool**
  - Secure configuration management
- **ISO/IEC 27001**
  - Technical vulnerability management

Disabling deprecated TLS protocols is a **baseline expectation** for regulated financial systems.

---

## Key Takeaways
- Vulnerability management is not just scanning — it is **risk-based decision making**
- Credentialed scans provide deep visibility but require careful interpretation
- Small configuration changes can eliminate significant compliance risk
- Validation is as important as remediation

---

## Skills Demonstrated
- Credentialed vulnerability analysis
- Risk prioritization in regulated environments
- OS-level hardening
- Network access control design
- Remediation validation
- Security documentation and reporting

---

## Final Outcome
This project successfully:
- Reduced cryptographic attack surface
- Improved compliance posture
- Demonstrated a repeatable vulnerability management workflow
- Maintained operational stability

---

*This project reflects real-world vulnerability management practices expected in financial institutions and regulated enterprises.*
