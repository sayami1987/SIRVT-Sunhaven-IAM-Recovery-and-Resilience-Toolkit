# SIRVT Test Plan

## Sunhaven IAM Recovery and Resilience Validation Toolkit

## 1. Purpose

This test plan defines how the Sunhaven IAM Recovery and Resilience Validation Toolkit (SIRVT) will be tested as implementation progresses.

The purpose of testing is to confirm that SIRVT can:

- create a valid backup of the fictional Sunhaven IAM state;
- verify backup integrity;
- detect modified, missing or unexpected files;
- prevent recovery from a backup that fails integrity verification;
- restore a verified backup into an isolated recovery workspace;
- verify that recovery is complete;
- measure recovery results; and
- generate useful recovery evidence.

All tests use fictional Sunhaven Care data.

No real Microsoft Entra ID accounts, passwords, authentication tokens, tenant secrets or resident information are used.

---

## 2. Test Scope

The following planned SIRVT components will be tested:

1. Source IAM data loading and validation
2. Backup creation
3. Manifest generation
4. SHA-256 integrity verification
5. Corruption detection
6. Missing-file detection
7. Unexpected-file detection
8. Restore protection
9. Restore operation
10. Recovery completeness
11. Recovery metrics
12. Report generation

Optional encryption testing may be added later only if encryption is implemented.

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
```

---

## 4. Current Test Data

The current fictional IAM test state contains:

```text
data/
├── users.json
├── roles.json
├── groups.json
└── policies.json
```

These files provide the controlled source state for future backup and recovery tests.

The dataset is intentionally small so that changes can be identified and explained clearly during testing.

---

## 5. General Pass and Fail Rules

A test will be marked **PASS** when the actual result matches the expected result.

A test will be marked **FAIL** when:

- the expected condition is not detected;
- invalid data is incorrectly accepted;
- a required file is missed;
- recovery proceeds after integrity verification has failed;
- a verified backup cannot be restored as expected; or
- recovered data is incomplete without being reported.

---

## 6. Planned Core Test Cases

| ID | Test | Expected Result | Priority |
|---|---|---|---|
| SIRVT-T01 | Load valid IAM data | All four required JSON files load successfully | High |
| SIRVT-T02 | Missing source file | Missing required file is reported | High |
| SIRVT-T03 | Invalid JSON | Invalid JSON is rejected with a clear result | High |
| SIRVT-T04 | Create valid backup | Versioned backup contains required IAM files | High |
| SIRVT-T05 | Verify unchanged backup | All protected files pass integrity verification | High |
| SIRVT-T06 | Modify one backup file | Modified file is detected | High |
| SIRVT-T07 | Remove one backup file | Missing file is detected | High |
| SIRVT-T08 | Add unexpected backup file | Unexpected file is reported | Medium |
| SIRVT-T09 | Restore backup that failed verification | Restore is blocked | High |
| SIRVT-T10 | Restore verified backup | Files are restored into the isolated recovery workspace | High |
| SIRVT-T11 | Validate complete recovery | Expected recovery state is reported as complete | High |
| SIRVT-T12 | Detect incomplete recovery | Missing recovered data is reported | High |
| SIRVT-T13 | Measure recovery duration | Recovery duration is recorded | Medium |
| SIRVT-T14 | Generate JSON evidence | Structured JSON result is produced | Medium |
| SIRVT-T15 | Generate CSV evidence | CSV summary is produced | Medium |
| SIRVT-T16 | Generate HTML evidence | Readable HTML recovery report is produced | Medium |

These test cases describe the intended test coverage. Their implementation status will be updated as the corresponding SIRVT features are developed.

---

## 7. Priority Demonstration Scenarios

### Scenario A – Valid Backup

### Scenario B – Modified Backup

### Scenario C – Successful Recovery



These scenarios are intended to form the core of the final SIRVT demonstration.

---

## 8. Evidence to Retain

Testing evidence should include, where applicable:

- terminal output;
- automated test output;
- backup folder contents;
- manifest files;
- integrity PASS/FAIL results;
- restore-blocking evidence;
- recovery results;
- screenshots; and
- generated JSON, CSV or HTML reports.

---

## 9. Current Test Status

The test approach and fictional test data have been defined.

The Python implementation and automated test suite have not yet been created.

Testing will begin with source IAM data loading and validation before backup creation is implemented.
