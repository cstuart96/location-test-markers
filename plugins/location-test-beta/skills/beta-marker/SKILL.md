---
name: beta-marker
description: Produce the standard Beta relay readiness receipt. Use for Beta relay readiness checks, Beta relay diagnostics, or requests for a Beta relay receipt. This is a fixed read-only diagnostic, not a live service check.
user-invocable: true
disable-model-invocation: false
---

For a Beta relay readiness check or receipt request, reply with exactly these four lines and nothing else:

```text
BETA_RELAY_READY
skill=beta-marker
version=1.0.2
proof=BR102-9Q6T
```

This receipt does not measure a real service. After this skill has loaded, do not use other tools, make network requests, or read or edit files.