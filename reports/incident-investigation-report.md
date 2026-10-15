# Authentication Log Investigation Report

## 1. Overview

This investigation used Splunk Cloud to analyse simulated authentication logs and identify repeated failed login attempts.

**Investigation type:** Authentication log analysis  
**Tool:** Splunk Cloud  
**Data source:** Simulated authentication events  
**Status:** Lab investigation completed

## 2. Investigation Objective

The objective was to identify repeated login failures, determine which usernames and source IP addresses were associated with them, and demonstrate a basic detection query.

## 3. Findings

The uploaded sample contained 10 events:

- 7 failed login events.
- 2 successful login events.
- 1 logout event.

The failed-login investigation identified these combinations:

| Username | Source IP | Failed Attempts |
|---|---|---:|
| admin | 198.51.100.77 | 3 |
| bob | 203.0.113.44 | 3 |
| david | 192.168.1.88 | 1 |

## 4. Detection Method

The Splunk search grouped failed login events by username and source IP address. It then filtered for groups with at least three failed attempts.

The query is saved in `queries/failed-login-detection.spl`.

## 5. Assessment

The repeated failures associated with the `admin` and `bob` accounts met the lab's detection threshold and were flagged for further investigation.

Repeated failures can have several explanations, including incorrect passwords or automated login attempts. The sample data alone is insufficient to determine intent or confirm an attack.

The source IP addresses in this dataset are reserved for documentation and example use, not evidence of real attackers.

## 6. Recommended Actions

In a real environment, a security analyst should:

1. Review additional authentication events for the affected accounts.
2. Correlate the events with other available logs and time periods.
3. Check whether successful logins followed the failed attempts.
4. Verify whether the activity matches expected user behaviour.
5. Escalate confirmed suspicious activity according to the organisation's incident response process.

## 7. Limitations

This exercise used a small, simulated dataset. It demonstrates basic SIEM searching and detection logic but does not establish that a real security incident occurred.

## 8. Conclusion

The exercise demonstrated how Splunk can be used to search authentication events, count failed login attempts, group events by username and source IP, and flag repeated failures for further review.
