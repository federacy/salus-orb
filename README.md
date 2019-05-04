# salus-orb

A CircleCI Orb for Salus

## Parameters

| attribute | description | default | options |
| --------- | ----------- | ------- | ------- |
| active_scanners | Scanners to run | all | Brakeman, PatternSearch, BundleAudit, NPMAudit |
| enforced_scanners | Scanners that block builds | all | Brakeman, PatternSearch, BundleAudit, NPMAudit |
| report_uri | Where to send Salus reports | file://test/salus-report.json | Any URI |
| report_format | What format to use for report | json | json, yaml, txt |
| report_verbosity | Whether to enable a verbose report | true | true, false |

Note: active_scanners and enforced_scanners must be yaml formatted for Salus configuration file.

## Examples

.circleci/config.yml

### blocking scan with all scanners

```
version: 2.1

orbs:
  salus: federacy/salus@dev:0.0.1

workflows:
  main:
    jobs:
      - salus/scan
```

### non-blocking scan with all scanners

```
version: 2.1

orbs:
  salus: federacy/salus@dev:0.0.1

workflows:
  main:
    jobs:
      - salus/scan:
          enforced_scanners: "none"
```

### blocking scan with only Brakeman

```
version: 2.1

orbs:
  salus: federacy/salus@dev:0.0.1

workflows:
  main:
    jobs:
      - salus/scan:
          active_scanners: "\n    - Brakeman"
          enforced_scanners: "\n    - Brakeman"
```
