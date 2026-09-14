# Sunhaven IAM Recovery and Resilience Validation Toolkit

## SIRVT

SIRVT stands for **Sunhaven IAM Recovery and Resilience Validation Toolkit**.

It is an independent cybersecurity technical artefact developed for the fictional **Sunhaven Care** environment.

The purpose of SIRVT is to test whether important Identity and Access Management (IAM) information can be backed up, checked for unexpected change or corruption, and safely recovered after a failure.

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

However, important IAM information could still be:

- accidentally deleted;
- incorrectly modified;
- corrupted;
- incompletely backed up; or
- restored incorrectly after a failure.

A backup should not automatically be accepted for recovery simply because it exists.

---

## Proposed Solution

SIRVT is designed to provide a controlled recovery and resilience validation process for fictional Sunhaven IAM data.

The planned toolkit will:

- create versioned backups of Sunhaven IAM configuration;
- generate SHA-256 hashes for protected files;
- store expected file information in a manifest;
- verify backup integrity before recovery;
- detect modified or missing files;
- stop recovery when integrity verification fails;
- restore a verified backup into an isolated recovery folder;
- check whether the recovered IAM state is complete; and
- generate recovery evidence.

The project uses fictional local data only.

It does not modify the live Microsoft Entra ID tenant used by the wider group project.


---

## Documentation

- [Architecture](docs/architecture.md)
- [Test Plan](docs/test-plan.md)
- [Architecture Diagram](docs/diagrams/sirvt-architecture.png)

---

## Current Status

The current project has completed its initial planning, architecture and fictional IAM data-model stage.

Completed so far:

- recovery problem and project scope defined;
- individual project boundary defined;
- project folder structure created;
- high-level architecture designed;
- architecture diagram created;
- initial architecture documentation created;
- initial test planning created;
- fictional `users.json` dataset created;
- fictional `roles.json` dataset created;
- fictional `groups.json` dataset created; and
- fictional `policies.json` dataset created.

The Python implementation has not yet started.

The next stage is to load and validate the four fictional IAM JSON files before backup functionality is implemented.

---

## Project Boundary

SIRVT is designed as an independent technical artefact.

It does not depend on:

- another team member's source code;
- live Microsoft Entra ID data;
- Joiner-Mover-Leaver scripts;
- Flask application code;
- access-review output;
- workforce compliance results;
- security monitoring logs; or
- shared tenant credentials.

Development and testing use fictional Sunhaven IAM information created specifically for this project.

---

## Safety and Testing

SIRVT is a controlled educational prototype.

It does not perform attacks against real systems and does not contain real passwords, authentication tokens, tenant secrets or resident information.

All recovery testing will be performed locally using fictional data.
