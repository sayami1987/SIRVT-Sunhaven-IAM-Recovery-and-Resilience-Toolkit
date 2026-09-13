# Sunhaven IAM Recovery and Resilience Validation Toolkit

## SIRVT

SIRVT stands for **Sunhaven IAM Recovery and Resilience Validation Toolkit**.

It is an independent cybersecurity technical artefact developed for the fictional **Sunhaven Care** environment.

The purpose of SIRVT is to test whether important Identity and Access Management (IAM) information can be backed up, checked for corruption and safely recovered after a failure.

---

## Sunhaven Care Problem

Sunhaven Care has a high-turnover workforce that includes permanent staff, casual workers and agency workers.

The wider Sunhaven Care project focuses on Identity and Access Management, including:

- user identities;
- roles and permissions;
- security groups;
- MFA;
- Joiner, Mover and Leaver processes;
- access reviews; and
- audit evidence.

These controls help protect access to Sunhaven systems.

However, another problem must also be considered.

Important IAM information could be:

- accidentally deleted;
- incorrectly modified;
- corrupted;
- incompletely backed up; or
- restored incorrectly after a failure.

A backup should not automatically be trusted just because it exists.

---

## Proposed Solution

SIRVT will provide a simple recovery and resilience validation process for fictional Sunhaven IAM data.

The toolkit will:

- create backups of Sunhaven IAM configuration;
- generate SHA-256 hashes for protected files;
- verify backup integrity;
- detect modified or missing files;
- reject an untrusted backup;
- restore a verified backup into an isolated recovery folder;
- check whether the recovery is complete; and
- generate recovery evidence.

The project will use only fictional local data.

It will not modify the live Microsoft Entra ID tenant used by the wider group project.

---

## How SIRVT Helps Sunhaven

SIRVT adds a recovery and resilience capability to the Sunhaven Care cybersecurity project.

The main question SIRVT addresses is:

> If Sunhaven's IAM state is damaged or corrupted, can a trusted version be safely recovered?


