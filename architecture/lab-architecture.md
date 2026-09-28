# SOC Lab Architecture

## Overview

This lab simulates a small Security Operations Center (SOC) environment using Wazuh for security monitoring, threat detection, file integrity monitoring, and automated response.

The environment consists of two Ubuntu virtual machines running on an Apple Silicon Mac using UTM.

## Lab Components

| Component | Role |
|---|---|
| Wazuh Server | SIEM, log analysis, alerting, detection rules, and active response |
| Ubuntu Endpoint | Monitored endpoint running the Wazuh agent |
| UTM | Virtualization platform hosting the lab VMs |
| Wazuh Dashboard | Security monitoring and visualization |

## Network Architecture

```text
                 macOS Host
                     |
                    UTM
                     |
          Shared Virtual Network
             192.168.64.0/24
                     |
          +----------+----------+
          |                     |
          |                     |
   Wazuh Server           Ubuntu Endpoint
   192.168.64.22          192.168.64.23
          |                     |
          | <--- Wazuh Agent ---|
          |
   Wazuh Dashboard
          |
   Security Monitoring
Security Event
      |
      v
Ubuntu Endpoint
      |
      v
Wazuh Agent
      |
      v
Wazuh Manager
      |
      v
Decoder + Detection Rules
      |
      v
Security Alert
      |
      +------------------+
      |                  |
      v                  v
Wazuh Dashboard     Active Response
                         |
                         v
                  Temporary IP Block
