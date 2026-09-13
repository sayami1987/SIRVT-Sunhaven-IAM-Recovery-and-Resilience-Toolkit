\# SIRVT Architecture



\## Sunhaven IAM Recovery and Resilience Validation Toolkit



SIRVT is a standalone cybersecurity resilience tool developed for the fictional Sunhaven Care environment.



The project focuses on protecting the recoverability and integrity of important Identity and Access Management (IAM) configuration.



\---



\## 1. Sunhaven Care Problem



Sunhaven Care has a high-turnover workforce that includes permanent employees, casual workers and agency workers.



Its IAM environment is responsible for controlling access to sensitive systems and resident information through users, roles, groups and security policies.



The wider Sunhaven project already addresses important access-control problems such as:



\- users joining, changing roles and leaving the organisation;

\- accounts remaining active after workers leave;

\- workers retaining access they no longer require;

\- excessive access to sensitive information;

\- shared-device risks;

\- role-based access control;

\- MFA; and

\- access review and auditing.



However, protecting access is only one part of cybersecurity.



Sunhaven also needs to consider what happens if important IAM configuration is:



\- accidentally deleted;

\- incorrectly modified;

\- corrupted;

\- incompletely backed up;

\- restored from an invalid backup; or

\- only partially recovered after a failure.



For example, a manager role could be accidentally removed, a security group could be modified, or an IAM configuration file could become corrupted.



If Sunhaven cannot identify a trusted recovery point, restoring the wrong information could create additional security problems.



\---



\## 2. Security Gap



Existing IAM controls such as MFA, RBAC and account lifecycle management help prevent unauthorised access.



However, these controls do not answer an important resilience question:



> If Sunhaven's IAM security state is damaged, can a trusted version be safely recovered?



A backup is not automatically trustworthy simply because it exists.



A damaged, incomplete or modified backup should not be restored without verification.



Sunhaven therefore requires a method to:



1\. create a known-good recovery copy of important IAM state;

2\. verify that the backup has not been modified or corrupted;

3\. reject an untrusted backup;

4\. restore only verified information;

5\. confirm that the expected IAM state was recovered; and

6\. produce evidence showing whether the recovery succeeded.



\---



\## 3. Proposed Solution



The proposed solution is the \*\*Sunhaven IAM Recovery and Resilience Validation Toolkit (SIRVT)\*\*.



SIRVT is a local Python-based cybersecurity tool that operates on a fictional Sunhaven IAM dataset.



The toolkit will:



\- create versioned backups of fictional Sunhaven IAM configuration;

\- generate SHA-256 hashes for protected files;

\- create a backup manifest containing expected file information;

\- verify backup integrity before restoration;

\- identify modified, missing or corrupted files;

\- block recovery when a backup cannot be trusted;

\- restore a verified backup into an isolated recovery workspace;

\- compare the recovered state with the expected state;

\- calculate recovery completeness;

\- measure controlled recovery duration; and

\- produce recovery evidence and reports.



SIRVT does not modify the live Microsoft Entra ID tenant used by the group project.



It uses independent fictional data so that development, testing and demonstration can be completed safely without depending on another team member's work.



\---



\## 4. How SIRVT Helps Sunhaven Care



SIRVT adds a cyber-resilience capability to the wider Sunhaven Care cybersecurity project.



\### 4.1 Detects Backup Corruption



SIRVT calculates SHA-256 hashes when a backup is created.



When the backup is later checked, new hashes are calculated and compared against the original values.



If a file has changed unexpectedly, SIRVT reports an integrity failure.



Example:



```text

users.json       PASS

roles.json       FAIL

groups.json      PASS

policies.json    PASS

