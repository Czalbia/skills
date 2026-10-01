---
name: duopoly
description: Ship the requested change as a draft PR, wait for the preview build, then have Codex QA it. Use when the user ends a request with /duopoly.
---

1. Make the requested change, push it, and open a draft PR.
2. Wait for the preview build to be ready.
3. Run `codex exec -m gpt-6.1-sol "<prompt>"` with this prompt:
   ```
   QA this change on <preview URL> (log in with <login URL / creds>): <one-line summary of the change>.
   Check only these acceptance criteria on the changed screen: <criteria from the request>.
   Do not explore other pages, flows, or edge cases.
   Return a markdown table (Criterion | Result PASS/FAIL | Evidence) and one overall verdict.
   ```
4. Fix and repeat until it passes, then report the PR link and the verdict.
