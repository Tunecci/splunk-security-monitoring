# Splunk SIEM & Security Monitoring Lab

## Project Overview

This project demonstrates how Splunk can be used to investigate authentication logs, identify repeated failed login attempts, and create a basic security monitoring dashboard.

The lab uses simulated authentication events to practise SIEM searches and security investigation techniques.

## Objectives

- Ingest sample authentication logs into Splunk.
- Search and analyse successful and failed login events.
- Identify repeated failed login attempts by username and source IP address.
- Create a basic detection query for repeated failures.
- Build a dashboard to display accounts requiring further investigation.

## Tools Used

- Splunk Cloud
- Splunk Search Processing Language (SPL)
- GitHub

## Lab Environment

The project uses 10 simulated authentication events. The events include successful logins, failed logins, and a logout event.

## Investigation Findings

The sample data contained:

- 7 failed login events.
- 2 successful login events.
- 1 logout event.
- 3 usernames associated with failed login attempts.
- 3 source IP addresses associated with failed login attempts.

The detection query identified two username and source-IP combinations with three failed attempts each:

| Username | Source IP | Failed Attempts |
|---|---|---:|
| admin | 198.51.100.77 | 3 |
| bob | 203.0.113.44 | 3 |

These results represent simulated lab activity, not a confirmed real-world attack. The IP addresses are reserved for documentation and example use.

## Detection Logic

The SPL query groups failed login events by username and source IP, then displays groups with at least three failures.

See `queries/failed-login-detection.spl`.

## Recommendations

- Investigate repeated authentication failures using additional log sources and context.
- Monitor for repeated failures across multiple accounts and source IP addresses.
- Correlate failed logins with successful logins and other security events.
- Consider alerting when the detection threshold is reached.
- Tune detection thresholds to reduce false positives in a real environment.

## Limitations

This project uses a small, simulated dataset. The detection demonstrates a basic investigation technique and does not independently confirm malicious activity.

## Evidence

Screenshots of the detection query and monitoring dashboard will be included in the `screenshots/` directory.

## Skills Demonstrated

- SIEM fundamentals
- SPL searching and aggregation
- Authentication log analysis
- Basic detection logic
- Security monitoring and reporting
- Technical documentation
