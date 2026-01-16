# Bank Production Windows Hardening  
## Risk-Based Vulnerability Management & Network Exposure Reduction

---

## Executive Summary
This project demonstrates how a **misconfigured cloud system and outdated security settings**, if left unaddressed, could expose a financial institution to **millions of dollars in potential loss**, regulatory scrutiny, and reputational damage.

Rather than remediating everything blindly, this engagement focused on:
- Identifying **what posed the greatest business risk**
- Fixing **what could realistically lead to a breach**
- Deferring lower-impact issues that did **not materially increase exposure**

This is how vulnerability management works in real banking environments.

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

## Critical Finding #1: Network Security Group (NSG) Misconfiguration

### What Was Wrong
The system was deployed with inbound network rules that:
- Allowed remote administrative access from **anywhere on the internet**
- Did not restrict who could attempt to connect
- Effectively exposed the system to continuous scanning and brute-force attempts

This is equivalent to:
> Leaving a bank’s back-office systems reachable from the public street.

---

### Why This Is Dangerous (Non-Technical Explanation)
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

This immediately:
- Reduced exposure
- Lowered attack probability
- Brought the system closer to regulatory expectations

---

## Critical Finding #2: Outdated Encryption Protocols (TLS 1.0 / 1.1)

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
- Expose sensitive traf

