# SOC Incident Report — VPN Authentication Investigation

## 1. Incident Overview

- **Incident Type:** Potential Brute Force Activity
- **Affected User:** Simon
- **Source IP:** `172.201.60.191`
- **Source Country:** Canada
- **Preliminary Severity:** Medium
- **Status:** Escalated to SOC L2
- **Environment:** TryHackMe Training Lab

## 2. Executive Summary

During the investigation of VPN authentication logs, suspicious activity associated with user Simon was identified.

A total of 278 events were recorded for this user and source IP. The activity included 274 failed events (`failed`) and 4 established connection events (`built`).

A cluster of failed events was observed between approximately 07:28 and 07:33. The first subsequent `built` event occurred at approximately 07:35.

This pattern may indicate a potential brute-force attempt followed by an established VPN connection. However, unauthorized access or account compromise has not been confirmed.

## 3. Evidence Collected

| Indicator | Observed value |
|---|---|
| Total events | 278 |
| Failed events | 274 |
| `built` events | 4 |
| Username | Simon |
| Source IP | `172.201.60.191` |
| Source country | Canada |

## 4. Timeline of Events

- **07:28–07:33:** Cluster of failed VPN events.
- **07:33:** Last observed failed event in the investigated sequence.
- **07:35:** First subsequent `built` event.

The established connection event was recorded approximately two minutes after the last observed failed event.

## 5. Analyst Assessment

The high number of failed VPN events associated with one user and one source IP, followed by an established connection, represents suspicious authentication activity.

Potential explanations include:
- Brute-force activity followed by successful access.
- Repeated authentication errors by a legitimate user.
- Other authentication or connectivity issues.

The available VPN logs are insufficient to determine which explanation is correct.

## 6. Recommended L2 Investigation

1. Verify whether Simon initiated or authorized the connection.
2. Check whether the source IP and connection location are expected.
3. Review authentication history and relevant account activity.
4. Examine endpoint telemetry for suspicious processes or activity.
5. Investigate network and account activity following the established VPN connection.

## 7. Final Disposition

**Decision:** Escalate to SOC L2 for further investigation.

**Reason:** Suspicious authentication pattern with a subsequent established VPN connection. Additional contextual and endpoint evidence is required to determine whether the activity was legitimate or malicious.

**Conclusion:** Potential brute-force activity identified. Account compromise remains unconfirmed.
