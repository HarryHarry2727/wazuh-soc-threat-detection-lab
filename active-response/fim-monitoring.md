# File Integrity Monitoring (FIM)

## Overview

File Integrity Monitoring (FIM) was configured in Wazuh to monitor changes to a dedicated test directory on the Ubuntu endpoint.

The monitoring was configured with real-time detection so file changes generate security events without waiting for the scheduled scan.

## Monitored Directory

```text
/home/harry/soc-test
<directories realtime="yes">/home/harry/soc-test</directories>
<alert_new_files>yes</alert_new_files>
syscheck.event: added
syscheck.event: modified
syscheck.event: deleted
