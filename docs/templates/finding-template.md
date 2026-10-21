# F-XXX: <short title>

<!--
RULES
- A finding is a hypothesis until it is verified by hand. Update Status honestly.
- Never paste secrets, tokens, keys, or real personal data. Use placeholders.
- Findings in code owned by teammates stay PRIVATE until fixed and the owner agrees.
  Do not commit unfixed vulnerabilities to the public repository.
- Only fill Evidence with output you actually produced. Do not write from memory.
-->

| Field | Value |
|---|---|
| ID | F-XXX |
| Date found | YYYY-MM-DD |
| Target | <application, branch, commit hash> |
| Found by | <manual / Semgrep / CodeQL / ZAP / dependency scan / secret scan / LLM> |
| Status | Hypothesis / True positive / False positive / Fixed - pending retest / Fixed - verified / Accepted risk |
| Severity | <Critical / High / Medium / Low / Info> |
| CVSS | <version, vector string, score from the first.org calculator> |

## Description
What is wrong, in plain words. Which mechanism makes it possible.

## Location
File and line, or endpoint and HTTP method.

## Steps to reproduce
1. Exact steps in a local or staging environment.
2. Include the request or command, with secrets replaced by placeholders.

## Impact
What an attacker can do, to which data, and under what conditions.

## Remediation
What was changed (or what should change), and why it closes the weakness.

## Verification evidence
Before: output or test result that shows the weakness.
After: the same test showing it is closed. Name the regression test.

## Verification notes
How this was confirmed by hand. If found by a tool or LLM, say whether it was
a true or false positive and how you decided.

## References
Official documentation, advisories, or standards used (links you actually opened).