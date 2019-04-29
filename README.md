# salus-orb
A CircleCI Orb for Salus

## Example

.circleci/config.yml

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

See more examples in the orb.yml
