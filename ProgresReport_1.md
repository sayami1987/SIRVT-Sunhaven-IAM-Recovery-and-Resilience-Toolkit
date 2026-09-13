# SIRVT Progress Report 1

## Sunhaven IAM Recovery and Resilience Validation Toolkit

**Project:** AC-2 – Sunhaven Care Workforce IAM  
**Technical Artefact:** SIRVT – Sunhaven IAM Recovery and Resilience Validation Toolkit  
**Student:** Loojaw Manandhar  
**Student ID:** 12228795  

---

## 1. Progress Focus

The work completed so far has focused on defining the SIRVT problem clearly before beginning implementation.

The main reason for this approach was to avoid building a generic backup program with no clear connection to the Sunhaven Care cybersecurity problem.

SIRVT has therefore been positioned as a recovery and resilience component for the fictional Sunhaven IAM environment.

Its main security question is:

> If important IAM information is damaged, modified, deleted or corrupted, can Sunhaven identify a trusted recovery point and restore it safely?

This gives SIRVT a clear purpose that is different from normal user provisioning, role assignment, access review or monitoring.

---

## 2. Why Recovery and Resilience Was Chosen

The wider Sunhaven Care project already addresses operational identity and access management problems such as user lifecycle management, role-based access, MFA, access review and account control.

A second technical artefact needed to add value without reproducing those functions.

Recovery and resilience was selected because IAM configuration is security-critical. Even when access controls are correctly designed, the environment can still be affected by:

- accidental configuration changes;
- deleted IAM information;
- corrupted files;
- incomplete backup data;
- unsuccessful updates;
- or partial recovery after failure.

The important issue is not only whether a backup exists, but whether that backup can still be trusted.

This led to the central SIRVT design principle:

> A backup should be verified before it is accepted for recovery.

---

## 3. Architecture Decisions

A high-level SIRVT architecture has been designed around a controlled recovery process.

The SIRVT process starts with the fictional Sunhaven IAM state, which is backed up and then checked using SHA-256 integrity verification. If the integrity check fails, the backup is rejected and recovery is stopped. If the check passes, the trusted backup is restored, the recovered data is validated for completeness, and the final result is recorded in a recovery report.



The most important design decision is the placement of integrity verification before restoration.

This was done because restoring data first and checking it later would defeat the purpose of a trusted recovery process.


This creates a clear security boundary between a backup that merely exists and a backup that has been validated.

The architecture was also deliberately kept small and understandable. A complex cloud recovery platform was not required for the prototype. The goal is to demonstrate the security logic clearly and produce evidence that can be explained during the final demonstration.

---

## 4. Fictional IAM Data Model

A small fictional Sunhaven IAM dataset has been created using four JSON files:

- `users.json`
- `roles.json`
- `groups.json`
- `policies.json`

The reason for creating a local fictional dataset was to make SIRVT fully independent from the live Microsoft Entra environment and from other team members' implementation work.

This also makes recovery testing safe because files can later be deliberately changed, deleted or corrupted without affecting the real group project.

### Users

The user data represents different types of Sunhaven workers such as nurses, care workers, agency workers, managers, auditors and IAM administrators.

This gives the recovery tool a realistic identity dataset rather than using meaningless test values.

### Roles

Roles were added because IAM recovery should include access-control definitions, not only user records.

If role information is modified or lost, the meaning of a user's access can change.

### Groups

Groups were included to represent another layer of IAM configuration.

They provide a relationship between organisational functions and role assignments.

This also creates useful future recovery scenarios, such as a group definition being unexpectedly modified.

### Policies

Policies were added because security settings are also part of the IAM state that may need to be protected.

The fictional policies cover areas such as:

- privileged access MFA;
- least privilege;
- leaver account disablement;
- agency access expiry;
- and periodic access review.

These files provide enough structure to demonstrate a meaningful recovery process without creating an unnecessarily large dataset.

---

## 5. Why the Dataset Was Kept Small

The objective of SIRVT is not to recreate the complete Sunhaven Microsoft Entra tenant.

A small dataset makes the project easier to validate and explain.

It also allows individual failures to be demonstrated clearly.

For example, if `roles.json` is modified after a backup is created, the future integrity checker should identify that the current file no longer matches the trusted hash stored for that backup.

This provides a direct and understandable security demonstration.

---

## 6. Test Planning Decisions

Initial test planning has been started before implementation.

This was done so that the expected security behaviour is defined before the code is written.

The most important behaviours identified for testing are:

- a valid backup should pass verification;
- a modified backup file should fail verification;
- a missing required file should be detected;
- an untrusted backup should not be restored;
- a valid backup should be recoverable;
- and the recovered state should be checked for completeness.


---

## 7. Separation From Other Sunhaven Work

SIRVT has been deliberately kept separate from the existing operational IAM work.

It does not perform:

- Joiner-Mover-Leaver automation;
- live Entra user management;
- role provisioning;
- access review;
- Flask application blocking;
- compliance checking;
- event monitoring;
- context-aware access decisions;
- or shared-device session testing.

Those areas are already part of the wider team work or other individual technical artefacts.

SIRVT instead owns its own:

- fictional IAM state;
- backup format;
- integrity checking process;
- recovery process;
- recovery validation;
- and recovery evidence.

This separation is important because it keeps the individual contribution clear and avoids technical duplication.

---


## 8. Current Technical Status

The planning and design foundation for SIRVT is now established.

Completed work includes:

- defining the recovery problem;
- defining the individual project boundary;
- designing the recovery architecture;
- creating the architecture diagram;
- documenting the security reasoning;
- creating the initial test approach;
- and creating the fictional IAM dataset.

The Python implementation has not yet started.

This is intentional because the source data, recovery logic and expected security behaviour were defined first.

The project is now ready to move into implementation.

---

## 19. Next Step

The next step is to make SIRVT safely load the four IAM JSON files.

The first implementation should only:

1. locate the required files;
2. load each JSON document;
3. confirm that the JSON is valid;
4. report any missing file;
5. and display a clear success or failure result.


Backup creation should only begin after the source dataset can be loaded and validated correctly.

---



The project now has a clear security objective, defined input data, a simple architecture and expected test behaviour.

This provides a controlled starting point for the implementation of backup creation, SHA-256 verification, safe restore and recovery validation.

