## Overview of Security Auditing
- Security auditing is a systematic process of evaluating and verifying the security control measures in place within an organization to ensure they are effective and appropriate.
- It involves reviewing various aspects of the organization's information systems, networks, applications, and operational procedures to identify vulnerabilities, weaknesses, and areas for improvement.

## Essential Terminology

| Term | Definition | Importance |
|---|---|---|
| Security Policies | Formal documents that define an organization's security objectives, guidelines, and procedures to protect information assets. | Establishes the framework for implementing and enforcing security controls. |
| Compliance | Adherence to regulatory requirements, industry standards, and internal policies related to security and data protection. | Ensures that the organization meets legal obligations and best practices. |
| Vulnerability | A weakness in a system or process that can be exploited to gain unauthorized access or cause harm. | Identifying vulnerabilities is crucial for assessing and improving security measures. |
| Control | A safeguard or countermeasure implemented to mitigate risks and protect information assets. | Controls are designed to prevent, detect, or respond to security threats and weaknesses. |
| Risk Assessment | The process of identifying, analyzing, and evaluating risks to an organization's information assets. | Helps prioritize security measures based on the likelihood and impact of identified risks. |
| Audit Trail | A chronological record of events and activities that provides evidence of actions taken within a system. | Supports accountability and traceability during security audits and investigations. |
| Compliance Audit | An examination of an organization's adherence to regulatory requirements and industry standards. | Validates whether the organization meets the necessary compliance criteria and identifies areas for improvement. |
| Access Control | Measures and mechanisms used to regulate who can access specific information or systems and what actions they can perform. | Protects sensitive information from unauthorized access and misuse. |
| Audit Report | A formal document that presents the findings, conclusions, and recommendations resulting from a security audit. | Communicates audit results and provides guidance for improving security practices. |

## Security Auditing Process/Lifecycle

### 1. Planning and Preparation
- **Define Objectives and Scope**: Determine the goals of the audit and the specific systems, processes, and controls to be evaluated.
- **Gather Relevant Documentation**: Collect policies, procedures, network diagrams, and previous audit reports.
- **Establish Audit Team and Schedule**: Assemble the audit team and set a timeline for the audit activities.

### 2. Information Gathering
- **Review Policies and Procedures**: Examine the organization's security policies, procedures, and standards.
- **Conduct Interviews**: Interview key personnel to understand security practices and identify potential gaps.
- **Collect Technical Information**: Gather data on system configurations, network architecture, and security controls.

### 3. Risk Assessment
- **Identify Assets and Threats**: List critical assets and potential threats to those assets.
- **Evaluate Vulnerabilities**: Assess existing vulnerabilities in systems and processes.
- **Determine Risk Levels**: Assign risk levels based on the likelihood and impact of identified threats and vulnerabilities.

### 4. Audit Execution
- **Perform Technical Testing**: Conduct technical assessments such as vulnerability scans, penetration tests, and configuration reviews.
- **Verify Compliance**: Check adherence to relevant regulations and standards.
- **Evaluate Controls**: Assess the effectiveness of security controls and practices.

### 5. Analysis and Evaluation
- **Analyze Findings**: Review data collected during the audit to identify security weaknesses and areas for improvement.
- **Compare Against Standards**: Measure the organization's security posture against industry standards and best practices.
- **Prioritize Issues**: Rank findings based on their severity and potential impact on the organization.

### 6. Reporting
- **Document Findings**: Create a detailed report outlining audit findings, including identified vulnerabilities, non-compliance issues, and ineffective controls.
- **Provide Recommendations**: Offer actionable recommendations to address identified issues and enhance security.
- **Present Results**: Share the audit report with relevant stakeholders and discuss key findings and recommendations.

### 7. Remediation
- **Develop Remediation Plans**: Work with the organization to create plans for addressing the audit findings.
- **Implement Changes**: Assist in implementing recommended changes and improvements.
- **Conduct Follow-Up Audits**: Schedule follow-up audits to ensure that remediation efforts have been completed and are effective.
- **Monitor and Update**: Continuously monitor the organization's security posture and update security measures as needed.

## Types of Security Audits

| Security Audit | Objective | Importance | Example |
|---|---|---|---|
| Internal Audits | Conducted by the organization's internal audit team or security professionals to evaluate the effectiveness of internal controls and compliance with policies. | Internal audits provide insight into the organization's self-assessment of its security posture and highlight areas that may require more in-depth testing. | An internal audit might review user access controls to ensure that only authorized personnel have access to sensitive data. |
| External Audits | Performed by independent third-party auditors to provide an unbiased evaluation of the organization's security measures and compliance with external standards. | External audits often serve as benchmarks for compliance and security effectiveness. Penetration testers can use these findings to guide their testing efforts. | A company undergoing a PCI DSS compliance audit might hire an external auditor to validate its security controls and ensure they meet the required standards. |
| Compliance Audits | Focus on verifying that the organization complies with specific regulatory requirements and industry standards (e.g., GDPR, HIPAA, PCI DSS). | Compliance audits help identify regulatory gaps that penetration testers can address through targeted testing. | A healthcare provider might undergo a HIPAA compliance audit to ensure that patient data is protected according to federal regulations. |
| Technical Audits | Focus on assessing the technical aspects of the organization's IT infrastructure, including hardware, software, and network configurations. | Technical audits provide a detailed view of the technical controls in place, highlighting areas where penetration testing can uncover vulnerabilities. | A technical audit might involve a thorough review of firewall configurations to ensure they are properly securing the network perimeter. |
| Network Audits | Assess the security of the organization's network infrastructure, including routers, switches, firewalls, and other network devices. | Network audits can reveal vulnerabilities in network design and configurations that penetration testers can exploit to assess network security. | A network audit might identify insecure protocols being used for data transmission, prompting penetration testers to test for potential exploits. |
| Application Audits | Evaluate the security of software applications, focusing on code quality, input validation, authentication mechanisms, and data handling. | Application audits highlight security flaws in applications that penetration testers can exploit to demonstrate real-world attack scenarios. | An application audit might reveal vulnerabilities such as SQL injection or cross-site scripting (XSS) in a web application. |

## Security Auditing & Penetration Testing

| | Security Audit | Penetration Test |
|---|---|---|
| **Purpose** | Evaluate an organization's overall security posture by assessing compliance with policies, standards, and regulations. It focuses on the effectiveness of security controls, processes, and practices. | Simulate real-world attacks to identify and exploit vulnerabilities in systems, networks, or applications. It focuses on technical weaknesses and how they can be exploited by attackers. |
| **Scope** | Comprehensive, covering various aspects such as policies, procedures, technical controls, physical security, and compliance with regulations. | Specific to the systems, networks, or applications being tested. The scope is defined to focus on particular areas of interest. |
| **Methodology** | Typically involves reviewing documentation, conducting interviews, performing technical assessments, and evaluating compliance with security standards. | Involves using various tools and techniques to attempt to breach systems, exploit vulnerabilities, and assess the effectiveness of security defenses. |
| **Outcome** | Identifies gaps in security policies, procedures, and controls. Provides recommendations for improving overall security and ensuring compliance. | Provides a detailed assessment of vulnerabilities and potential attack vectors. Offers recommendations for mitigating identified risks and improving security defenses. |
| **Frequency** | Often performed on a regular basis (e.g., annually or biannually) or as required by compliance regulations. | Typically performed as needed, such as after significant changes to systems, on a regular schedule, or as part of compliance requirements. |

## Governance, Risk & Compliance (GRC)

- Governance, Risk, and Compliance (GRC) is a comprehensive framework used by organizations to manage and align their governance practices, risk management strategies, and compliance with regulatory requirements.
- This holistic approach helps organizations maintain transparency, accountability, and resilience in an increasingly complex regulatory environment.

### Governance
Governance refers to the framework of policies, procedures, and practices that ensure an organization achieves its objectives, manages its risks, and complies with legal and regulatory requirements.

**Components:**
- **Policy Development**: Creating clear, comprehensive security policies.
- **Roles and Responsibilities**: Defining roles and responsibilities for security management.
- **Accountability**: Establishing accountability mechanisms for security performance.

### Risk
Risk management involves identifying, assessing, and mitigating risks that could negatively impact an organization's assets and operations.

**Components:**
- **Risk Identification**: Recognizing potential threats and vulnerabilities.
- **Risk Assessment**: Evaluating the likelihood and impact of identified risks.
- **Risk Mitigation**: Implementing measures to reduce or eliminate risks.

### Compliance
Compliance ensures that an organization adheres to relevant laws, regulations, and industry standards.

**Components:**
- **Regulatory Requirements**: Meeting legal obligations such as GDPR, HIPAA, or PCI DSS.
- **Internal Policies**: Adhering to internal security policies and procedures.
- **Audits and Assessments**: Conducting regular reviews to ensure compliance.

## Frameworks, Standards and Guidelines

- **Frameworks**: Provide a structured approach to implementing security practices, often flexible and adaptable to various organizations and industries.
- **Standards**: Set specific requirements and criteria that must be met to achieve compliance; often mandatory in regulated industries.
- **Guidelines**: Offer recommended practices and advice to improve security; generally not mandatory but considered best practices.

### Frameworks

**NIST Cybersecurity Framework (CSF)**
- Overview: A set of guidelines and best practices developed by the National Institute of Standards and Technology (NIST) to help organizations manage and reduce cybersecurity risk.
- Key Focus: Core functions include Identify, Protect, Detect, Respond, and Recover.

**COBIT (Control Objectives for Information and Related Technologies)**
- Overview: A framework for developing, implementing, monitoring, and improving IT governance and management practices.
- Key Focus: Aligning IT goals with business objectives, managing IT risks, and ensuring compliance with regulations.

### Standards

**ISO/IEC 27001**
- Overview: An international standard for information security management systems (ISMS) that outlines best practices for managing and protecting sensitive information.
- Key Focus: Establishing, implementing, maintaining, and continually improving an ISMS.

**PCI Data Security Standard (PCI DSS)**
- Overview: A set of security standards designed to protect payment card information and ensure secure processing of credit card transactions.
- Key Focus: Requirements for protecting cardholder data, maintaining a secure network, and implementing robust access control measures.
- Legal Requirement: Required for organizations that handle credit card transactions.

**HIPAA (Health Insurance Portability and Accountability Act)**
- Overview: A U.S. law that sets standards for protecting sensitive patient information and ensuring privacy and security of health data.
- Key Focus: Privacy Rule, Security Rule, and Breach Notification Rule.
- Legal Requirement: Required for healthcare providers, health plans, and other entities handling protected health information.

**GDPR (General Data Protection Regulation)**
- Overview: A regulation in the European Union that governs data protection and privacy for individuals within the EU and the European Economic Area (EEA).
- Key Focus: Data protection principles, rights of data subjects, and obligations for data controllers and processors.
- Legal Requirement: Required for organizations processing personal data of individuals within the EU/EEA.

### Guidelines

**CIS Controls (Center for Internet Security Controls)**
- Overview: A set of best practices and actionable steps to help organizations improve their cybersecurity posture.
- Key Focus: Foundational and advanced security controls organized into categories such as basic, foundational, and organizational controls.

**NIST SP 800-53**
- Overview: A publication by NIST that provides a catalog of security and privacy controls for federal information systems and organizations.
- Key Focus: Security controls for federal information systems, including controls for risk management and information security.
- Legal Requirement: Required for U.S. federal agencies and organizations handling federal data.

## From Audit to Pentest — Case Study

### Background
- **Company**: SecureTech Solutions

### Description
- SecureTech Solutions is a fictitious cybersecurity consultancy that specializes in securing IT infrastructure for various clients.
- In this example, we will be demonstrating the process of developing a security policy for Linux servers, performing a risk assessment using the NIST SP 800-53 framework, performing a security audit, and testing the remediations.
- This example will guide you through the entire process, from initial policy creation to auditing and penetration testing, highlighting the importance of compliance with industry standards.

### Phase 1 - Developing a Security Policy

**Security Policy Development Process: Requirements Gathering**
- **Purpose**: Define the purpose and scope of the security policy.
- **Access Control**: Outline user account management, authentication methods, and privilege management.
- **Audit and Accountability**: Specify logging requirements and log review procedures.
- **Configuration Management**: Define baseline configurations, software update practices, and change management.
- **Identification and Authentication**: Enforce strong password policies and unique user identification.
- **System and Information Integrity**: Implement malware protection, security monitoring, and vulnerability management.
- **Maintenance**: Outline controlled maintenance and approved maintenance tools.

**Simple Security Policy for Linux Servers Aligned with NIST SP 800-53**

| Policy Area | Control ID | Policy Statement |
|---|---|---|
| Access Control (AC) | AC-2, AC-5 | User Accounts: Only authorized personnel shall be granted access to Linux servers. Each user must have a unique user account; shared accounts are prohibited. Inactive accounts must be disabled or removed within 30 days. |
| Access Control (AC) | IA-2, IA-5 | Authentication: Enforce strong password policies: minimum length of 12 characters, including upper/lower case letters, numbers, and special characters. Use SSH key-based authentication where possible; disable password-based SSH access. Implement two-factor authentication (2FA) for privileged accounts. |
| Audit and Accountability (AU) | AU-2, AU-3 | System Logging: Enable and configure system logging to capture critical events. Use rsyslog or journald for centralized logging. |
| Audit and Accountability (AU) | AU-6, AU-7 | Log Review: Regularly review logs for suspicious activities. Retain logs for at least 90 days. |
| Configuration Management | CM-2 | Configuration Baseline: Maintain a secure baseline configuration for all Linux servers. Use configuration management tools (e.g., Ansible, Puppet) to enforce configurations. |
| Configuration Management | CM-3, CM-5 | Software Updates: Keep the system and installed software up to date. Apply security patches within 30 days of release. |
| Identification and Authentication (IA) | IA-5 | Password Management: Enforce password complexity and expiration policies. Use password managers to securely store and manage passwords. |
| Identification and Authentication (IA) | IA-4 | User Identification: Ensure all users are uniquely identified. |
| System and Information Integrity (SI) | SI-3 | Malware Protection: Implement malware detection and prevention measures. Regularly scan servers for malware. |
| System and Information Integrity (SI) | SI-4 | Security Monitoring: Monitor systems for security breaches or anomalies. Use tools like Lynis to perform regular security audits. |
| Maintenance (MA) | MA-2 | Controlled Maintenance: Perform regular maintenance on servers according to documented procedures. |
| Maintenance (MA) | MA-3 | Maintenance Tools: Use only approved maintenance tools and ensure they are secure. |

### Phase 2 - Developing a Security Policy (continued)

**Objectives:**
- Establish a baseline security policy for Linux servers that aligns with NIST SP 800-53 guidelines, ensuring that servers are configured and managed securely.
- This policy should ensure that Linux servers are secure and protected from unauthorized access, vulnerabilities, and other security threats.
- It will be used to establish baseline security requirements for configuring, maintaining, and monitoring Linux servers within the organization, aligned with NIST SP 800-53.

## Security Auditing With Lynis

- Download it first from their website.
- Don't be shy to visit the Lynis security controls page for a full list of available control codes.

```bash
./lynis audit system
# Run a full Lynis security audit on the local system

./lynis audit system --tests "<control_code>"
# Run only a specific test/control by its code

./lynis audit system --auditor "<auditor_name>"
# Run the audit, tagging the report with the given auditor's name

./lynis audit system --quick --auditor "<auditor_name>"
# Run the audit without prompting for confirmation between sections (skips the "press enter to continue" prompts)
```

## Conduct Penetration Testing

```bash
hydra -l root -P <path> ssh://$IP:22 -t 2 -v
# Brute-force the root SSH password using a wordlist, with 2 parallel tasks and verbose output
```

- **Remediation**: disable SSH password-based authentication (enforce key-based authentication instead).