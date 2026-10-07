# Suricata Monitoring and Detection

## EVE JSON Monitoring

Suricata was configured to generate events in EVE JSON format. The EVE log provides structured information about detected events and network traffic.

## Network Interface

Suricata was configured to capture traffic from the active wireless interface:

`wlp2s0`

The local network was configured as `192.168.1.0/24`.

## Packet Capture Statistics

Suricata statistics indicated approximately 91,000 kernel packets were captured.

Relevant statistics included:

`kernel_drops: 0`
`errors: 0`
`pkt_too_small: 6`

The value for `kernel_drops` was zero, indicating that no packets were reported as dropped by the kernel capture mechanism.

The small number of `pkt_too_small` events was recorded but did not by themselves provide evidence of an attack.

## Observed Alerts

Suricata detected several low-priority events during the lab. Examples include:

1. `ET INFO Observed DNS Query to Cloudflare Developer Domain (workers.dev)`
   - Priority: 3
   - Category: Information/Misc Activity

2. `SURICATA IPv4 packet too small`
   - SID: 2200000
   - Severity: 3
   - Action: Allowed

## File and Log Monitoring

EVE JSON events can be reviewed with:

`sudo tail -f /var/log/suricata/eve.json`

For a quick view of alerts, the log can be searched with:

`sudo grep 'type": "alert' /var/log/suricata/eve.json`

## Result

Suricata was confirmed to be capturing network traffic from `wlp2s0` and generating EVE JSON events.

The observed low-priority events were recorded for analysis. The capture statistics showed zero kernel packet drops and zero capture errors.
