# Marker Plugin Tests

This marketplace contains a read-only diagnostic plugin, not a live service checker. Keep its source separate from the consumer repository. The test marker is public test data, not a secret or a security boundary.

## Automatic Selection

Start a fresh session in the consumer repository with Beta enabled and send only:

```text
Run a Beta relay readiness check and return its standard diagnostic receipt.
```

The prompt intentionally does not name a skill, a plugin, a tool, a file path, or the expected receipt. A pass requires the trace to show normal invocation of `beta-marker` and the response to match the four-line receipt in the installed skill. Manual filesystem lookup, Git-history lookup, a guessed receipt, or an availability claim is not a pass. Confirm the receipt version is 1.0.2; the earlier one-line marker does not pass this version's test.

## Explicit Invocation Control

If automatic selection fails, use a separate fresh session with the same configuration:

```text
Invoke the registered beta-marker skill and follow its instructions exactly. Normal skill loading is allowed. Do not manually locate the skill file. If invocation fails, report the exact error.
```

An explicit pass with an automatic-selection failure distinguishes selection behavior from registration/invocation. It does not by itself identify why selection failed.

## Workspace Isolation

Run the automatic-selection test with the qualified `location-test-beta@location-test-markers` entry true, then false, in fresh sessions. For cloud tests, commit and push each configuration and start from that exact branch/revision. Repeat in another repository without the enablement entry, keeping global Beta off.

For the off cases, verify the registry or invocation error shows the skill is unavailable. A missing receipt alone is inconclusive. An off-case invocation means isolation failed. Record the client, configuration revision, installed plugin version, invocation trace, and response. Check slash-command autocomplete separately; it is not equivalent to automatic model selection.