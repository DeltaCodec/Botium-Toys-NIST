## Introduction

This repository is a security audit exercise for [Google's Cybersecurity Course](https://www.coursera.org/google-certificates/cybersecurity-certificate) on a dummy company called "Botium Toys"
> I will try to develop this repository not only on the NIST-CSF perspective as it's asked on the course but also on Brazilian's laws and regulations perspective using the course as an extension to FIB Youth Program that I am participating this year.
## Scenario
Botium Toys is a small U.S. business that develops and sells toys. The business has a single physical location, which serves as their main office, a storefront, and warehouse for their products. However, Botium Toy’s online presence has grown, attracting customers in the U.S. and abroad. As a result, their information technology (IT) department is under increasing pressure to support their online market worldwide. 

The manager of the IT department has decided that an internal IT audit needs to be conducted. She's worried about maintaining compliance and business operations as the company grows without a clear plan. She believes an internal audit can help better secure the company’s infrastructure and help them identify and mitigate potential risks, threats, or vulnerabilities to critical assets. The manager is also interested in ensuring that they comply with regulations related to internally processing and accepting online payments and conducting business in the European Union (E.U.).   

The IT manager starts by implementing the National Institute of Standards and Technology Cybersecurity Framework (NIST CSF), establishing an audit scope and goals, listing assets currently managed by the IT department, and completing a risk assessment. The goal of the audit is to provide an overview of the risks and/or fines that the company might experience due to the current state of their security posture.

> My task is to review the IT manager’s scope, goals, and risk assessment report. Then, perform an internal audit by completing a controls and compliance checklist.

**Scope and goals of the audit**
* **Scope:** The scope is defined as the entire security program at Botium Toys. This means all assets need to be assessed alongside internal processes and procedures related to the implementation of controls and compliance best practices.


* **Goals:** Assess existing assets and complete the controls and compliance checklist to determine which controls and compliance best practices need to be implemented to  improve Botium Toys’ security posture.

  ![f_nist-logo-brand-black](https://github.com/user-attachments/assets/2595068a-65a8-4015-b334-355240a4dc17)

### Optimization for Small Businesses (Small Business Guide)
As the company is a small business (SMB), this audit can be optimized using the [NIST Cybersecurity Framework 2.0: Small Business Quick-Start Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.1300.pdf), a resource provided on NIST's website.
> [!NOTE]
>"This guide provides small-to-medium sized businesses (SMB), specifically those who have modest or no cybersecurity plans
in place, with considerations to kick-start their cybersecurity risk management strategy by using the NIST Cybersecurity
Framework (CSF) 2.0. The guide also can assist other relatively small organizations, such as non-profits, government
agencies, and schools. It is a supplement to the NIST CSF and is not intended to replace it."
<sub>- Purpose, Slide 2, "NIST Cybersecurity Framework 2.0: Small Business Quick-Start Guide"<sub>


The company scored an 8 on the **Risk Score** due the lack of controls and adherence to compliance and best practices, this also qualifies this resource as a useful tool for this audit.

## Identify
> Before you can protect your assets, you need to identify them. Then you can determine the
appropriate level of protection for each asset based upon its sensitivity and criticality to your
business mission.



| Asset                        | Asset's Use                                           | Asset Administrator    | Sensitive Data the Asset has Access To           | Is multi-factor authentication required to access this asset? | Risk to Business if the Asset is Compromised                                                                                         |
|------------------------------|------------------------------------------------------|------------------------|-------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| On-premises equipment         | Company Needs                                        | Unknown                | PII/SPII, Cardholder Data                        | Not Specified                                               | High – Sensitive data exposure, potential non-compliance, financial and reputational risks.                                          |
| Employee equipment            | Employee use, access to internal data                | Unknown                | PII/SPII, Cardholder Data                        | Not Specified                                               | High – Unauthorized access to sensitive data, regulatory penalties, identity theft, and fraud risks.                                |
| Internal Database Server      | Stores customer PII/SPII and cardholder data         | IT Department          | PII, SPII, Cardholder Data                       | No                                                          | Critical – Lack of encryption, risk of data theft, non-compliance with PCI-DSS, GDPR.                                               |
| Firewall                      | Controls network traffic                             | IT Department          | None                                            | N/A                                                         | Moderate – Risk of unauthorized network access if not properly configured.                                                          |
| Antivirus Software            | Protects systems from malware                        | IT Department          | None                                            | N/A                                                         | Medium – A compromised system could spread malware, impacting internal data security.                                               |
| Disaster Recovery System      | Backup and recovery of critical data (not implemented) | IT Department          | Critical Business Data                          | N/A                                                         | High – No backup system in place for data recovery, leading to possible data loss in case of failure or cyberattack.               |
| Password Management System    | Managing passwords across systems                    | IT Department          | PII, SPII, Internal Systems Access               | No (No centralized system)                                    | High – Weak password policies could lead to unauthorized access to sensitive data and systems.                                        |
| Intrusion Detection System (IDS) | Detects potential threats or unauthorized access     | IT Department          | None                                            | N/A                                                         | High – Lack of IDS leaves the network vulnerable to undetected attacks, increasing the risk of a breach.                            |

 > Due to the lack of controls, all employees have access to PII/SPII, making it difficult to quantify anything below high risk when it comes to employee-needed assets. Thus, all employee equipment and assets are classified as high risk due to the sensitive nature of the data they access.

## Protect
> [!TIP]
> When working with an SMB, it is essential to prioritize cost-effective and compatible solutions that align with the business’s specific needs. One of the most significant concerns for any business, regardless of size, is data security. Multi-factor authentication (MFA) is one of the most affordable and effective ways to improve security. It is also quick to implement and requires minimal investment compared to other advanced security measures. MFA implementation is mandatory for most of the company services, therefore, the next subtopic on Protect phase already expects it's presence on our security strategy.

### Protect Phase Controls Table

| **Control Category**         | **Control Name**                     | **Control Type and Explanation**                                                                                                    | **Needs to be Implemented (X)** | **Priority** | **Risk to Business if Not Implemented**                                                                                                                                      |
|------------------------------|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Administrative Controls**   | Least Privilege                      | Preventative; restricts user access to only what is necessary for their role, minimizing the risk of unauthorized access               |            ✔️                    | High         | High: Increases risk of unauthorized access to critical assets or data if employees have unnecessary privileges.                                                          |
|           **Administrative Controls**                   | Disaster Recovery Plans              | Corrective; ensures business continuity in case of disaster, limiting downtime and data loss                                           | ✔️                                | High         | High: Potential loss of critical data and prolonged system downtime can severely impact business operations.                                                               |
|           **Administrative Controls**                   | Password Policies                    | Preventative; establishes rules for creating strong passwords to defend against brute-force attacks                                   | ✔️                                | High         | High: Weak passwords increase the likelihood of unauthorized access or account compromise.                                                                              |
|          **Administrative Controls**                    | Access Control Policies              | Preventative; improves confidentiality and integrity of sensitive data by controlling who can access it                              | ✔️                               | High         | High: Failure to enforce access controls can lead to unauthorized access or data breaches.                                                                                |
|         **Administrative Controls**                     | Account Management Policies          | Preventative; ensures proper management of employee accounts, especially for former or disgruntled employees                          | ✔️                                | High         | High: Failing to manage accounts increases the risk of disgruntled employees retaining access to systems, possibly causing data breaches or damage.                       |
|         **Administrative Controls**                     | Separation of Duties                 | Preventative; ensures no single person has control over critical processes, preventing abuse of power and fraud                      | ✔️                                | High         | High: Potential for fraud, data misuse, or systems being tampered with if an individual has too much access or control.                                                   |
| **Technical Controls**        | Multi-Factor Authentication (MFA)    | Preventative; requires multiple forms of authentication to verify user identity before granting access                               | ✔️                                | High         | High: Without MFA, accounts and systems are more vulnerable to unauthorized access, increasing the likelihood of data theft or breaches.                               |
|            **Technical Controls**                   | Encryption                           | Deterrent; secures sensitive data by encoding it, making it unreadable without the correct decryption key                             | ✔️                                | High         | High: Lack of encryption exposes sensitive data (e.g., credit card information, PII) to unauthorized access or theft, violating compliance regulations.                  |
|            **Technical Controls**                   | Intrusion Detection System (IDS)     | Detective; detects and alerts on unusual or malicious activity on the network to enable rapid response                               | ✔️                                | High         | High: Without IDS, potential intrusions could go undetected, leading to significant data breaches, financial loss, or compromised systems.                               |
|          **Technical Controls**                     | Backups                              | Corrective; ensures that critical data is backed up regularly, allowing restoration in case of data loss                             | ✔️                                | High         | High: Data loss can have severe operational impacts, especially if backups are not available or not functioning properly.                                                  |
|          **Technical Controls**                     | Antivirus Software                   | Corrective; detects and removes malware or other malicious software from the system                                                   | ✔️                                | High         | High: Malware infections can compromise system integrity, steal sensitive data, or disable business operations if antivirus software is not in place.                      |
|           **Technical Controls**                    | Password Management System           | Corrective; streamlines password recovery and reset processes, ensuring compliance with password policies and preventing delays     | ✔️                                | High         | High: Difficulty in managing passwords and access can result in productivity loss, frustration, and potentially unauthorized access to accounts if password reset is delayed. |
|           **Technical Controls**                    | Legacy System Monitoring             | Preventative/Corrective; ensures legacy systems are monitored and any vulnerabilities are addressed in a timely manner                |            ✔️                     | High         | High: Legacy systems are particularly vulnerable to cyberattacks if they are not monitored and patched regularly.                                                          |
| **Physical Controls**         | Time-Controlled Safe                 | Deterrent; restricts physical access to critical assets, reducing the risk of physical theft                                        | ✔️                               | Medium/Low   | Medium: Potential for physical theft or tampering with critical assets, though impact is less significant than a cybersecurity breach.                                     |
|           **Physical Controls**                    | CCTV Surveillance                    | Preventative/Detective; reduces the risk of unauthorized physical access and provides video evidence for investigations               |   ✔️                             | High/Medium | Medium: Physical security risks such as theft or vandalism could increase if CCTV is not maintained or used effectively.                                                   |
|           **Physical Controls**                    | Locking Cabinets (Network Gear)      | Preventative; prevents unauthorized personnel from accessing and tampering with sensitive equipment and network gear                | ✔️                                | High/Medium | High: Unauthorized access to network infrastructure could compromise security and lead to unauthorized changes or data leaks.                                            |
|          **Physical Controls**                     | Locks                                | Preventative; secures physical and digital assets from theft or tampering                                                             | ✔️                                | High         | High: Failure to secure physical assets (e.g., laptops, network gear) can lead to theft or unauthorized access.                                                          |
|          **Physical Controls**                     | Fire Detection and Prevention        | Detective/Preventative; detects and prevents fire hazards in the store and office to protect assets and prevent system damage        | ✔️                                | Medium       | Medium: If fire detection systems are not functional, the business faces significant risk of asset damage or inventory loss due to fire.                                   |


## Controls and compliance checklist
### **Controls Assessment Checklist**

| **Control**                                          | **Before (Current State)** | **After (Improvement Recommendations)** |
|------------------------------------------------------|----------------------------|----------------------------------------|
| Least Privilege                                      | ❌                          | ✔️                                      |
| Disaster recovery plans                              | ❌                          | ✔️                                      |
| Password policies                                     | ❌                          | ✔️                                      |
| Separation of duties                                  | ❌                          | ✔️                                      |
| Firewall                                             | ✔️                          | ✔️                                      |
| Intrusion detection system (IDS)                      | ❌                          | ✔️                                      |
| Backups                                              | ❌                          | ✔️                                      |
| Antivirus software                                    | ✔️                          | ✔️                                      |
| Manual monitoring, maintenance, and intervention for legacy systems | ❌                          | ✔️                                      |
| Encryption                                           | ❌                          | ✔️                                      |
| Password management system                           | ❌                          | ✔️                                      |
| Locks (offices, storefront, warehouse)               | ✔️                          | ✔️                                      |
| Closed-circuit television (CCTV) surveillance         | ✔️                          | ✔️                                      |
| Fire detection/prevention (fire alarm, sprinkler system, etc.) | ✔️                          | ✔️                                      |

---

### **Compliance Checklist**

#### **Payment Card Industry Data Security Standard (PCI DSS)**

| **Best practice**                                    | **Before (Current State)** | **After (Improvement Recommendations)** |
|------------------------------------------------------|----------------------------|----------------------------------------|
| Only authorized users have access to customers’ credit card information. | ❌                          | ✔️                                      |
| Credit card information is stored, accepted, processed, and transmitted internally, in a secure environment. | ❌                          | ✔️                                      |
| Implement data encryption procedures to better secure credit card transaction touchpoints and data. | ❌                          | ✔️                                      |
| Adopt secure password management policies.           | ✔️                          | ✔️                                      |

#### **General Data Protection Regulation (GDPR)**

| **Best practice**                                    | **Before (Current State)** | **After (Improvement Recommendations)** |
|------------------------------------------------------|----------------------------|----------------------------------------|
| E.U. customers’ data is kept private/secured.        | ❌                          | ✔️                                      |
| There is a plan in place to notify E.U. customers within 72 hours if their data is compromised/there is a breach. | ❌                          | ✔️                                      |
| Ensure data is properly classified and inventoried.  | ✔️                          | ✔️                                      |
| Enforce privacy policies, procedures, and processes to properly document and maintain data. | ✔️                          | ✔️                                      |

#### **System and Organization Controls (SOC type 1, SOC type 2)**

| **Best practice**                                    | **Before (Current State)** | **After (Improvement Recommendations)** |
|------------------------------------------------------|----------------------------|----------------------------------------|
| User access policies are established.                | ❌                          | ✔️                                      |
| Sensitive data (PII/SPII) is confidential/private.    | ❌                          | ✔️                                      |
| Data integrity ensures the data is consistent, complete, accurate, and has been validated. | ❌                          | ✔️                                      |
| Data is available to individuals authorized to access it. | ❌                          | ✔️                                      |

## Recomendations

**Implement Least Privilege Access Control**
> Enforce strict access control policies that ensure employees and vendors only have access to the specific data and systems they need to perform their job functions. This can minimize the risk of internal threats and data breaches.

**Develop Disaster Recovery Plans**

>  Establish comprehensive disaster recovery plans that include off-site backups, system redundancy, and business continuity strategies to reduce downtime and minimize operational impact in case of system failures or data loss.

**Enhance Password Policies**

> Update the password policy to require stronger passwords (at least 8 characters, including numbers, letters, and special characters) and implement a centralized password management system to enforce these rules across the company.

**Separate Duties and Responsibilities**

>Implement separation of duties within key processes (e.g., access management, financial transactions) to ensure no single employee has too much control over sensitive systems or data, reducing the risk of fraud or misuse.

**Implement Intrusion Detection System (IDS)**

> Install and configure an intrusion detection system (IDS) to monitor network traffic for potential threats. The IDS should be able to quickly alert the IT team to any suspicious activities and prevent attacks from spreading.

**Implement Full Data Encryption**

> Encrypt sensitive data at rest (in databases) and in transit (e.g., during payment transactions) to ensure confidentiality and integrity, especially for customer credit card information and personal data (PII/SPII).

**Establish Regular Backup and Recovery Procedures**

> Create a backup strategy that includes automatic daily backups, off-site storage, and frequent recovery tests to ensure critical data can be restored quickly in the event of a data loss or disaster.


**Install a Password Management System**

> Implement a centralized password management system to securely store and enforce password policies. This will improve productivity, reduce password reset requests, and enhance overall security.

**Increase Monitoring and Maintenance for Legacy Systems**

>Establish a formal schedule for monitoring, patching, and maintaining legacy systems. Identify and address any vulnerabilities in outdated systems to reduce security risks.

**Improve Physical Security Controls**

> Ensure that physical security measures (e.g., locked cabinets for network gear, CCTV surveillance) are in place to protect critical systems and assets from unauthorized access or tampering.

**Implement Security Awareness Training for Employees**

> Provide regular cybersecurity training to all employees to increase awareness of phishing, social engineering attacks, and best practices for maintaining security in their daily work.

**Develop an Incident Response and Notification Plan for EU Customers (GDPR)**

> Develop a clear and actionable plan to notify EU customers within 72 hours of a data breach as required by GDPR. Include the necessary contact information and procedures to ensure compliance with data protection laws.

**Improve User Access Policies for Compliance with SOC 1 and SOC 2**

> Review and refine user access policies to ensure that only authorized personnel have access to sensitive data and systems. Implement role-based access control (RBAC) to restrict unnecessary access and ensure data confidentiality.

**Ensure Compliance with PCI DSS for Credit Card Data**

> Review the organization's handling of credit card data and implement necessary changes to comply with PCI DSS standards, including encryption, access controls, and secure transmission practices.
