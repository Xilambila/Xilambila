# Incident response: suspicious identity activity

**Type:** synthetic tabletop exercise. **Status:** documented scenario; no live incident, tenant, user or containment action. All timestamps, identities, assets and addresses below are fictional.

## Problem and business context

A lab identity with access to a fictional reporting service triggers an unusual sign-in alert. The response objective is to determine whether access was unauthorized while preserving evidence and minimizing unnecessary service interruption.

## Evidence supplied

The [timeline.csv](timeline.csv) contains six synthetic events. Addresses use documentation space. It is a teaching fixture, not an export from a SIEM or cloud provider.

| UTC time | Synthetic observation | What it supports |
|---|---|---|
| 09:00 | Successful sign-in from a baseline lab source | A comparison point; not proof of legitimate ownership |
| 09:11 | Successful sign-in from a different source and new device | A reason to investigate; IP change alone is insufficient |
| 09:12 | Risk alert for that session | A detector signal that needs supporting evidence |
| 09:14 | Application access request denied | The requested action did not succeed in this event |
| 09:17 | User reports not recognizing the new session | Corroboration from a trusted contact process, assumed for this tabletop |
| 09:20 | Containment decision recorded | A simulated decision, not proof that revocation worked |

## Investigation and competing hypotheses

1. Check source timestamps, time zones, event identifiers and collection gaps. Preserve originals in an access-controlled evidence store and hash exports when an actual case requires them. Do not modify original events during normalization.
2. Compare device registration, authentication methods, session context and user confirmation through a known channel.
3. Consider legitimate travel, a new device, approved remote access, stolen session material or compromised credentials. A source address or risk label does not resolve these alternatives alone.
4. Correlate authorized identity logs, endpoint signals, mailbox/application audit events and recent privilege changes. Record unavailable evidence as a gap.
5. The supplied fixture supports suspicion and a response decision; it does not establish malware, data exfiltration, initial access mechanism or full scope.

## Response decisions

| Decision point | Action if supported and authorized | Verification |
|---|---|---|
| User denies session and corroborating evidence indicates unauthorized access | Revoke sessions, require approved credential recovery, preserve relevant evidence | Test that the suspect session can no longer reach protected resources; account for token lifetime and application behavior |
| Privileged identity or active harmful behavior | Escalate to incident lead and asset owner; apply scoped containment | Check denied access and impact on service dependencies |
| Evidence remains ambiguous | Increase monitoring and collect missing context using the response policy | Record rationale, owner and a reassessment time |
| Recovery approved | Restore permitted access after identity and endpoint checks | Observe fresh authorized sessions and watch for recurrence |

Do not infer that every token is immediately invalidated by one revocation action. Recovery and containment depend on the identity platform, application and token type.

## Detection design to validate

Proposed correlation: a successful sign-in on a new device, followed by risky application activity and a user denial, within a defined investigation window. Separate each observation from the analyst conclusion. Tune against approved device onboarding, remote access, travel and service accounts.

This is detection logic in prose, not an installed or tested detection rule. Required validation includes known-good activity, simulated unauthorized sessions, late events, missing events and duplicate ingestion. Measure false positives, time to triage, time to contain and successful recovery from actual test runs; no measured improvements are claimed here.

## Lessons

Identity context and business impact determine the response. Useful observability needs reliable timestamps, actor/session correlation, access decisions and clear ownership. Closure requires evidence that the selected controls worked, alongside a record of remaining uncertainty.
