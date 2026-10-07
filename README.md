# Suricata IDS Lab

A practical cybersecurity lab documenting the deployment, configuration,
monitoring, and troubleshooting of Suricata IDS on Ubuntu Linux.

## Project Overview

This project documents my hands-on experience deploying Suricata as a
Network Intrusion Detection System (NIDS).

The lab covers:

- Suricata installation
- Network interface configuration
- HOME_NET configuration
- AF_PACKET capture configuration
- Suricata rule management
- EVE JSON logging
- IDS alert monitoring
- Packet capture statistics
- Troubleshooting configuration and service issues
- Basic network security analysis

## Environment

| Component | Configuration |
|---|---|
| Operating System | Ubuntu Linux |
| Suricata Version | 8.0.7 |
| Network Interface | wlp2s0 |
| HOME_NET | 192.168.1.0/24 |
| Capture Method | AF_PACKET |
| Logging | EVE JSON |

## Project Status

- [x] Suricata installed
- [x] Suricata configuration validated
- [x] HOME_NET configured
- [x] Network interface configured
- [x] Suricata service running
- [x] Network traffic captured
- [x] IDS alerts observed
- [x] Packet statistics reviewed
- [ ] Add detailed configuration documentation
- [ ] Add troubleshooting documentation
- [ ] Add sanitized configuration examples
- [ ] Add screenshots

## Key Results

Suricata was successfully configured to monitor the wireless network
interface `wlp2s0`.

The configured local network is:

```text
192.168.1.0/24
