# Feedback Workflow

This document explains what happens after someone reports a Viandly bug or requests an
improvement. The public issue is the durable record of the user's experience and the status of the
response. Application source code and implementation work remain in Viandly's private engineering
repository.

## Status Labels

An open issue carries at most one `status:` label:

- `status: needs-triage` - the report has not yet been reproduced or classified.
- `status: needs-info` - progress requires more information from the reporter.
- `status: confirmed` - the behavior has been reproduced or otherwise established as a defect.
- `status: in-progress` - implementation work is underway.
- `status: ready-for-release` - the fix is complete and tested but not yet live.
- `status: awaiting-verification` - the fix is live and reporter confirmation would be useful.

Area labels such as `import`, `ai`, `cooking-mode`, `cookbooks`, `baking`, `mobile`, `account`, and
`help` describe the affected product surface. They do not replace the status label.

## Bug Lifecycle

1. **Intake**
   - Acknowledge the report and check it for private information.
   - Apply the relevant area labels.
   - Ask the reporter to remove credentials, private recipes, private share links, or personal data
     if any were included.
2. **Triage**
   - Reproduce the behavior against the current production release when practical.
   - Record the affected Viandly version, device, browser, and shortest known reproduction path.
   - Use `status: needs-info` when the report cannot be evaluated without more context.
3. **Confirmation and prioritization**
   - Apply `status: confirmed` once the defect is established.
   - Explain the observed behavior publicly without exposing private implementation or operational
     details.
   - Assign a release milestone only when the issue is accepted for that release.
4. **Implementation**
   - Apply `status: in-progress`.
   - Implement and test the change in the private application repository.
   - Add regression coverage appropriate to the failure and update relevant design or Help
     documentation.
5. **Release preparation**
   - Apply `status: ready-for-release` when the fix is complete but not deployed.
   - Keep the issue open. A source commit is not the same as a fix available to beta testers.
6. **Production verification**
   - Deploy through Viandly's tagged release process.
   - Verify the affected production workflow.
   - Comment with the deployed version and concise retest instructions.
   - Use `status: awaiting-verification` when confirmation from the reporter would add confidence.
7. **Closure**
   - Close as **Completed** after production verification or reporter confirmation.
   - Close as **Not planned** only with a concise explanation.
   - Reopen the issue if the behavior recurs.

Feature requests follow the same intake and communication principles, but confirmation means the
underlying user need is understood rather than that a defect was reproduced. Acceptance and
scheduling remain separate decisions.

## Security and Privacy

Potential security vulnerabilities do not follow the public workflow. Report them privately using
[SECURITY.md](./SECURITY.md). If a public report contains sensitive material, preserve only the
minimum sanitized context needed for tracking and move the investigation to the private security
process.

Account-specific investigations, production records, logs, credentials, private recipe content,
and reusable exploit details must never be copied into this repository.
