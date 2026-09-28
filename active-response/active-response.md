# Wazuh Active Response

## Overview

Wazuh Active Response was configured to automatically respond to the custom SSH brute-force detection rule.

When the custom rule detects three failed SSH login attempts from the same source IP within 120 seconds, Wazuh executes the `firewall-drop` response.

## Detection Rule

```text
Rule ID: 100100
Level: 12
Frequency: 3
Timeframe: 120 seconds
MITRE ATT&CK: T1110 - Brute Force
<active-response>
    <disabled>no</disabled>
    <command>firewall-drop</command>
    <location>local</location>
    <rules_id>100100</rules_id>
    <timeout>60</timeout>
</active-response>
Failed SSH Attempts
        |
        v
Custom Rule 100100
        |
        v
Wazuh Active Response
        |
        v
firewall-drop
        |
        v
Source IP Temporarily Blocked
        |
        v
60-Second Timeout
        |
        v
Automatic Block Removal
