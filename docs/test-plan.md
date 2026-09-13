# SIRVT Test Plan

## Sunhaven IAM Recovery and Resilience Validation Toolkit

## 1. Purpose

This test plan defines how the Sunhaven IAM Recovery and Resilience Validation Toolkit (SIRVT) will be tested.

The purpose of testing is to confirm that SIRVT can:

- create a valid backup of the fictional Sunhaven IAM state;
- verify backup integrity;
- detect modified, missing or unexpected files;
- prevent recovery from an untrusted backup;
- restore a valid backup into an isolated recovery workspace;
- verify that recovery is complete;
- measure recovery results; and
- generate useful recovery evidence.

All tests use fictional Sunhaven Care data.

No real Microsoft Entra ID accounts, passwords, authentication tokens, tenant secrets or resident information are used.

---

## 2. Test Scope

The following SIRVT components will be tested:

1. Backup creation
2. Manifest generation
3. SHA-256 integrity verification
4. Corruption detection
5. Missing-file detection
6. Unexpected-file detection
7. Restore protection
8. Restore operation
9. Recovery completeness
10. Recovery metrics
11. Report generation

Optional encryption testing may be added later if encryption is implemented.

---

## 3. Test Environment

The initial test environment will use:

- Windows development computer;
- Python 3;
- fictional Sunhaven IAM JSON files;
- local backup directory;
- isolated recovery directory; and
- automated Python tests where practical.

Project folders used during testing:

```text
data/
backups/
recovery/
reports/
tests/
