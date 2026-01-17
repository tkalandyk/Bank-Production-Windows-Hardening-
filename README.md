
<img width="1536" height="1024" alt="ChatGPT Image Jan 16, 2026, 07_14_00 PM" src="https://github.com/user-attachments/assets/89db7596-85f9-42dc-ba4c-6d7f9126e3ed" />


# Bank Production Windows Hardening  
## Risk-Based Vulnerability Management & Network Exposure Reduction

---

## Executive Summary
This project demonstrates how a **misconfigured cloud system and outdated security settings**, if left unaddressed, could expose a financial institution to **millions of dollars in potential loss**, regulatory scrutiny, and reputational damage.

Rather than remediating everything blindly, this engagement focused on:
- Identifying **what posed the greatest business risk**
- Fixing **what could realistically lead to a breach**
- Deferring lower-impact issues that did **not materially increase exposure**


---

## Business Context (Why Leadership Should Care)
Banks operate under constant threat from:
- Unauthorized access
- Credential abuse
- Regulatory audits
- Public trust erosion

In this case, two major risk areas were identified:
1. **Severely misconfigured network access controls**
2. **Outdated encryption protocols still enabled**

Either issue alone could lead to a serious incident.  
Together, they significantly increased the likelihood of compromise.

---

## Critical Finding #1: Network Security Group (NSG) Extremely Misconfigured

### What Was Wrong
The system was deployed with inbound network rules that:
- Allowed remote administrative access from **anywhere on the internet**
- Did not restrict who could attempt to connect
- Effectively exposed the system to continuous scanning and brute-force attempts
- As well as an ICMP Protocol rule that was irrelevant 

<img width="1562" height="305" alt="Screenshot 2026-01-16 at 4 18 46 PM" src="https://github.com/user-attachments/assets/62a63a9b-885c-43f0-b29d-3a5cb6bfed23" />


This is equivalent to:
> Leaving a bank’s back-office systems reachable from the public street.

---

### Why This Is Dangerous 
An open management port:
- Gives attackers unlimited chances to guess credentials
- Enables automated attack tools to operate 24/7
- Increases the probability of account compromise over time

Even if passwords are strong, **constant exposure multiplies risk**.

In regulated environments, this type of configuration is often flagged as:
- A **high-risk audit finding**
- A **policy violation**
- An unacceptable external attack surface

---

### What Was Done
Inbound access was redesigned to follow **least privilege principles**:
- Administrative access limited to a **single trusted IP**
- Vulnerability scanning allowed only from a **known internal scanner**
- All other inbound traffic explicitly denied by default

  <img width="1012" height="253" alt="Screenshot 2026-01-16 at 5 42 04 PM" src="https://github.com/user-attachments/assets/9f495ac3-a521-4777-8499-c2d71068bc09" />


This immediately:
- Reduced exposure
- Lowered attack probability
- Brought the system closer to regulatory expectations

---

## Critical Finding #2: Outdated Encryption Protocols (TLS 1.0 / 1.1)

<img width="795" height="372" alt="Screenshot 2026-01-16 at 7 25 25 PM" src="https://github.com/user-attachments/assets/65a2e7df-97ed-41be-8f4d-32b230f190b0" />


<img width="685" height="548" alt="Screenshot 2026-01-16 at 6 12 48 PM" src="https://github.com/user-attachments/assets/e21a906c-9111-4d3f-892d-e7bfe06b837f" />


### What Was Found
The system still supported older encryption methods that:
- Are no longer considered secure
- Are explicitly disallowed by modern banking standards
- Increase the risk of data interception

---

### Why TLS Was Prioritized
From a business risk perspective:
- Encryption protects **customer data and credentials**
- Weak encryption undermines **trust and compliance**
- Regulators expect outdated protocols to be disabled

Leaving these enabled could:
- Violate compliance frameworks
- Expose sensitive traffic
- Create audit and legal exposure

As a result, **TLS 1.0 and TLS 1.1 were fully disabled at the operating system level**.

---

## Why SSL Certificate Findings Were NOT Immediately Remediated

### This Was a Deliberate Decision
The scan also reported:
- Self-signed certificates
- Certificates that could not be externally trusted

While these findings appear serious, context matters.

---

### Business Reasoning
In this environment:
- The certificates were used internally
- No public-facing customer services relied on them
- No sensitive data was being transmitted externally using these certificates

Remediating certificates would have:
- Required architectural changes
- Introduced potential service disruption
- Delivered **minimal risk reduction** compared to other actions

---

### Risk-Based Conclusion
The SSL findings were:
- Documented
- Acknowledged
- Accepted as **lower priority risk**

---

## Validation & Results
After remediation:

<img width="797" height="274" alt="Screenshot 2026-01-16 at 7 31 41 PM" src="https://github.com/user-attachments/assets/b04d3ae4-c7de-40ce-9bb5-e93af58cd614" />


<img width="610" height="591" alt="TLS" src="https://github.com/user-attachments/assets/524debd0-0c86-4782-9021-51e34bbd2d0b" />



- Network exposure was significantly reduced
- Deprecated encryption protocols were fully removed
- Follow-up credentialed scans confirmed remediation success
- No operational downtime occurred

---

## Regulatory & Compliance Alignment
Actions taken align with expectations from:
- PCI DSS (secure communications)
- NIST security frameworks
- FFIEC guidance for financial institutions
- ISO/IEC 27001 vulnerability management principles

More importantly, they align with **how banks actually balance security and business continuity**.

---

## Key Takeaways
- Not all findings are equal
- Exposure matters more than volume
- Risk must be reduced without breaking the business
- Good vulnerability management is about **judgment**, not just fixes

---

## Final Outcome
This engagement:
- Eliminated unnecessary external exposure
- Reduced cryptographic risk
- Demonstrated real-world prioritization
- Reflected how vulnerability management is performed in regulated environments

---

*This project showcases practical vulnerability management decision-making expected of analysts supporting financial institutions.*

