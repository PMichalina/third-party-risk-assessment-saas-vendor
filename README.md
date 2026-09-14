# Third-Party Risk Assessment – SaaS Vendor

## Project Overview

This project presents a simplified third-party security risk assessment of a fictional SaaS vendor providing a project management and collaboration platform.

The scenario was selected because third-party risk is a common area within Governance, Risk and Compliance (GRC), and SaaS providers may process company data, employee information, internal documents, user accounts, and system integrations.

The purpose of the project was to practice identifying relevant risk scenarios, evaluating security controls, assessing control effectiveness, and determining residual risk and appropriate risk treatment.

---

## Scenario

A medium-sized international organization plans to implement a SaaS platform for project management and team collaboration.

The platform will be used by multiple departments and may process:

- employee names and corporate email addresses
- project and client information
- internal company documents
- project tasks, deadlines, and comments
- potentially sensitive attachments

The platform will be accessible via the Internet and may be integrated with Microsoft 365 / Single Sign-On (SSO).

The vendor must therefore undergo a security assessment before full approval.

---

## Assessment Methodology

The assessment follows a simplified risk-based approach:

Risk Scenario → Causes / Weaknesses → Business Impact → Controls → Evidence → Control Effectiveness → Residual Risk → Risk Treatment

A three-level risk scale was used:

- 1 = Low
- 2 = Medium
- 3 = High

Risk Score = Likelihood × Impact

Risk levels:

- 1-2 = Low
- 3-4 = Medium
- 6-9 = High

Inherent Risk represents the level of risk before considering existing controls.

Residual Risk represents the level of risk remaining after considering control effectiveness.

Control effectiveness was assessed as:

- Effective
- Partially Effective
- Ineffective

The project was informed by the NIST SP 800-53 introductory course and its concepts related to security and privacy controls.

AI was used as a learning and review assistant to support terminology understanding, question refinement, and structured documentation. Final risk judgments, control assessments, and treatment decisions were reviewed and made by me.

---

# Risk Register

| Risk Scenario | Inherent Likelihood | Inherent Impact | Inherent Risk | Residual Likelihood | Residual Impact | Residual Risk | Treatment |
|---|---:|---:|---|---:|---:|---|---|
| Data Leakage | 2 / Medium | 3 / High | 6 / High | 2 / Medium | 3 / High | 6 / High | Mitigate |
| Account Compromise | 2 / Medium | 3 / High | 6 / High | 2 / Medium | 2 / Medium | 4 / Medium | Mitigate |
| Service Disruption / Availability Risk | 2 / Medium | 3 / High | 6 / High | 1 / Low | 2 / Medium | 2 / Low | Accept |

---

# 1. Data Leakage

## Possible Causes / Weaknesses

- weak data protection measures
- insufficient security assessment of third-party vendors
- failure to apply the Principle of Least Privilege
- excessive user permissions or poorly managed access rights

## Business Impact

- reputational damage
- loss of customer trust
- financial losses
- regulatory or legal consequences

## Controls Assessed

### Data Encryption – Partially Effective

The vendor uses AES-256 encryption at rest, TLS 1.3 encryption in transit, and encrypted backups.

The implementation is supported by security documentation, an encryption policy, and independent audit evidence.

However, encryption key management has not yet been fully verified.

Further evidence should cover:

- encryption key generation
- secure key storage
- access to encryption keys
- key rotation
- monitoring of key usage

### Access Control – Partially Effective

The vendor implements:

- Role-Based Access Control (RBAC)
- Principle of Least Privilege
- periodic access reviews

Evidence includes an access control policy, role matrix, and recent access review report.

However, the Joiner-Mover-Leaver (JML) process has not yet been fully verified.

### Data Loss Prevention – Partially Effective

DLP controls are implemented and supported by evidence.

However, the full scope of protected data and the preventive capabilities of the DLP solution require further verification.

It should be confirmed whether DLP:

- covers all relevant sensitive data
- only generates alerts
- can also block unauthorized data transfers

### Multi-Factor Authentication – Partially Effective

MFA is enforced for administrative accounts but remains optional for standard users.

Supporting evidence confirming technical enforcement of MFA has not yet been reviewed.

## Risk Treatment

Mitigate.

The vendor should not yet be fully approved without further remediation and verification.

Recommended actions include:

- verify key management controls
- verify the JML process
- confirm full DLP coverage
- enforce MFA for all users
- obtain additional evidence of control effectiveness

---

# 2. Account Compromise

## Possible Causes / Weaknesses

- phishing and credential theft
- weak or reused passwords
- lack of MFA
- insecure password reset or account recovery
- insufficient monitoring of suspicious authentication activity

## Business Impact

- unauthorized access to sensitive company data
- modification or deletion of data
- fraudulent actions performed from the compromised account

## Controls Assessed

### Authentication Security – Partially Effective

MFA is enforced for administrative accounts but not for all standard users.

The vendor provided an authentication policy and account recovery documentation, but evidence confirming technical MFA enforcement is incomplete.

This creates both:

- a control gap
- an evidence gap

### Identity & Access Management – Effective

IAM controls are assessed as Effective because the key access controls are implemented and supported by evidence.

RBAC is documented through the role matrix, Least Privilege is supported by access reviews and the JML process, and privileged accounts are managed through Privileged Access Management (PAM).

### Monitoring & Detection – Partially Effective

The vendor demonstrated that suspicious login detection, authentication logging, and anomalous behavior alerts are implemented.

However, the available evidence mainly confirms implementation rather than operating effectiveness.

Additional evidence is required to verify:

- monitoring coverage
- log retention
- alert handling
- escalation procedures
- consistent operation of monitoring controls

### Response & Containment – Effective

The vendor provided evidence of both implementation and operating effectiveness.

Compromised accounts can be promptly disabled, active sessions revoked, and password resets enforced.

The evidence includes incident response procedures, technical documentation, and records from recent testing.

## Residual Risk Rationale

Residual Likelihood remains Medium because MFA is not enforced for all users and Monitoring & Detection has not been fully verified.

Residual Impact is reduced from High to Medium because effective IAM, RBAC, Least Privilege, PAM, and Response & Containment controls limit the potential damage caused by a compromised account.

## Risk Treatment

Mitigate.

Recommended actions:

- enforce MFA for all user accounts
- obtain stronger evidence of Monitoring & Detection operating effectiveness
- verify alert handling and escalation procedures
- reassess residual risk after remediation

---

# 3. Service Disruption / Availability Risk

## Possible Causes / Weaknesses

- DDoS attack
- infrastructure failure
- insufficient redundancy

## Business Impact

- operational disruption
- project delays
- productivity loss
- financial loss

## Controls Assessed

### High Availability & Redundancy – Effective

The service is deployed across multiple Availability Zones.

Critical components are redundant and automatic failover is implemented.

Architecture documentation, failover documentation, and recent availability and failover testing support the effectiveness of these controls.

### DDoS Protection – Effective

The vendor uses:

- traffic filtering
- rate limiting
- dedicated DDoS mitigation mechanisms

The controls are supported by technical documentation and recent resilience testing demonstrating operating effectiveness.

### Disaster Recovery – Effective

The vendor maintains:

- a documented Disaster Recovery Plan
- regular backups
- defined RTO and RPO
- periodic DR testing

Evidence includes the DR Plan, recent test reports, backup documentation, and remediation records.

### Availability Monitoring & Incident Response – Effective

The vendor provides:

- 24/7 uptime monitoring
- automated availability alerts
- defined incident escalation procedures
- documented incident response roles
- post-incident reviews

Recent incident records and post-incident analysis demonstrate operating effectiveness.

## Residual Risk Rationale

Residual Likelihood is reduced from Medium to Low because High Availability, redundancy, automatic failover, and DDoS protection reduce the probability of major service disruption.

Residual Impact is reduced from High to Medium because Disaster Recovery, monitoring, and Incident Response capabilities reduce the expected duration and business impact of an outage.

## Risk Treatment

Accept.

The remaining Residual Risk is Low and may be accepted if it falls within the organization’s defined Risk Appetite and Risk Tolerance.

---

# Vendor Due Diligence Questions

## Data Encryption

- Are company data encrypted both at rest and in transit, including backups?
- How are encryption keys generated, stored, accessed, rotated, and monitored?

## Access Control

- Do you apply RBAC and the Principle of Least Privilege?
- How is user access provisioned, modified, and revoked throughout the Joiner–Mover–Leaver lifecycle?
- How frequently are access rights reviewed?

## Data Loss Prevention

- What types of sensitive data are covered by your DLP policies?
- Can DLP controls block unauthorized transfers or only generate alerts?

## Authentication Security

- Do you enforce MFA for all user accounts?
- What password policy is in place?
- How is the account recovery and password reset process secured?

## Identity & Access Management

- How is user access managed throughout the account lifecycle?
- How do you manage privileged access?

## Monitoring & Detection

- Do you monitor and detect suspicious login activity?
- Are authentication events logged and monitored?
- Do you generate alerts for anomalous user behavior?

## Response & Containment

- Can active sessions be revoked when suspicious activity is detected?
- Can password resets be enforced following a security incident?
- Can compromised accounts be immediately disabled or locked?

## High Availability & Redundancy

- Is the service deployed across multiple Availability Zones or data centers?
- Do you use automatic failover for critical components?
- Are there any identified Single Points of Failure?

## DDoS Protection

- What controls are in place to detect and mitigate DDoS attacks?

## Disaster Recovery

- Do you maintain a documented Disaster Recovery Plan?
- How frequently is the DR Plan tested?
- What are the defined RTO and RPO?

## Availability Monitoring & Incident Response

- Is service availability continuously monitored?
- What is the escalation process for major outages?
- Are post-incident reviews performed?

## Evidence Request

Please provide relevant evidence supporting the implementation and operating effectiveness of the controls described above, where applicable.

---

# Findings & Recommendations

The assessment identified several areas requiring further verification or remediation.

The main gaps relate to:

- MFA coverage
- encryption key management
- JML verification
- DLP scope
- Monitoring & Detection operating effectiveness

Availability-related controls were assessed as Effective.

The vendor should not yet be fully approved from a security perspective until the identified gaps related to data protection and account security are addressed or sufficiently verified.

Following remediation, the Residual Risk should be reassessed.

---

# Lessons Learned

This project helped me understand how third-party risk assessment works in practice.

I learned to distinguish between Inherent Risk and Residual Risk, assess Control Effectiveness based on evidence, and identify Control Gaps and Evidence Gaps instead of relying only on vendor declarations.

I also learned how Vendor Due Diligence questions should be structured around relevant risk scenarios and security controls, and why controls must be assessed within the defined scope instead of applying a generic checklist.

The project strengthened my understanding of Risk Treatment, Risk Appetite, Remediation, Control Effectiveness, Evidence, Likelihood, Impact, and Residual Risk.
