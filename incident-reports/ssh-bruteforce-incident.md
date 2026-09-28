# SSH Brute-Force Detection Incident

## Incident Summary

A controlled SSH brute-force simulation was performed against the Ubuntu endpoint in the SOC lab.

Multiple failed authentication attempts using an invalid username were generated to validate the Wazuh detection and automated response capabilities.

## Detection Details

| Field | Value |
|---|---|
| Detection | SSH authentication failures |
| Custom Rule | 100100 |
| Alert Level | 12 |
| Frequency | 3 events |
| Timeframe | 120 seconds |
| MITRE ATT&CK | T1110 - Brute Force |
| Source | SSH client |
| Response | firewall-drop |

## Attack Simulation

The test generated repeated failed SSH authentication attempts against the monitored Ubuntu endpoint.

The activity was intentionally performed in the isolated lab environment for detection and response validation.

## Detection Process

```text
SSH Failed Login Attempts
          |
          v
Wazuh Agent
          |
          v
Wazuh Manager
          |
          v
SSH Decoder
          |
          v
Rule 5710
          |
          v
Custom Rule 100100
          |
          v
Level 12 Alert
60 seconds
1. Failed SSH login generated
        ↓
2. Multiple failures detected
        ↓
3. Rule 5710 matched
        ↓
4. Custom rule 100100 triggered
        ↓
5. Level 12 alert generated
        ↓
6. Active Response executed
        ↓
7. Source IP temporarily blocked
        ↓
8. 60-second timeout expired
        ↓
9. Block automatically removed
