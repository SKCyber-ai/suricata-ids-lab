# Suricata Installation

## Overview

Suricata was deployed on Ubuntu Linux as a Network Intrusion Detection System (NIDS).

The installation was performed using the Open Information Security Foundation (OISF) stable repository.

## System Information

- Operating System: Ubuntu Linux
- Suricata Version: 8.0.7
- Deployment Type: Network IDS
- Capture Method: AF_PACKET
- Network Interface: `wlp2s0`

## Installation

The Suricata stable repository was added and the package was installed using APT.

After installation, the version was verified with:

```bash
suricata -V
```

Expected output:

```text
This is Suricata version 8.0.7 RELEASE
```

## Configuration Validation

Before starting the service, the Suricata configuration was tested with:

```bash
sudo suricata -T -c /etc/suricata/suricata.yaml
```

A successful configuration test returned:

```text
Configuration provided was successfully loaded. Exiting.
```

## Service Verification

The Suricata service was started and checked using:

```bash
sudo systemctl status suricata
```

The service was confirmed to be running successfully.

## Network Interface

The system's network interfaces were inspected using:

```bash
ip -br addr
```

The active wireless interface was:

```text
wlp2s0
```

The interface was subsequently configured as the Suricata AF_PACKET capture interface.

## Result

Suricata was successfully installed and configured as a network IDS.

The service was able to capture traffic from the wireless interface and generate security events.
