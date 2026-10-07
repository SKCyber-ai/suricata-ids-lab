# Suricata Troubleshooting

## 1. Suricata Package Conflict

During the Suricata upgrade, a package conflict occurred involving the `suricata-update` utility.

The system reported a conflict because `/usr/bin/suricata-update` already existed.

The issue was resolved by removing the conflicting `suricata-update` package and repairing the package installation with:

`sudo dpkg --configure -a`

`sudo apt --fix-broken install`

Suricata was then successfully installed and upgraded to version 8.0.7.

## 2. HOME_NET Configuration Error

Suricata initially failed configuration validation because the `HOME_NET` variable was not defined correctly.

The configuration contained:

`xHOME_NET: "[192.168.1.0/24]"`

The variable was corrected to:

`HOME_NET: "[192.168.1.0/24]"`

The configuration was then validated successfully with:

`sudo suricata -T -c /etc/suricata/suricata.yaml`

The validation returned:

`Configuration provided was successfully loaded. Exiting.`

## 3. Incorrect Network Interface

The initial AF_PACKET configuration referenced:

`eth0`

However, the active network interface on the system was:

`wlp2s0`

The interface was identified using:

`ip -br addr`

The Suricata AF_PACKET configuration was updated to use `wlp2s0`.

After the correction, Suricata successfully captured traffic from the wireless interface.

## 4. Low-Priority Decoder Alerts

Suricata generated several low-priority events during monitoring, including:

`SURICATA IPv4 packet too small`

and:

`SURICATA STREAM Packet with invalid timestamp`

These events had low severity and were allowed by the configured detection policy.

Such decoder events should be investigated in context but should not automatically be interpreted as evidence of a successful attack or system compromise.

## 5. Packet Capture Verification

Suricata statistics showed approximately 91,000 kernel packets captured.

Important statistics included:

`kernel_drops: 0`

`errors: 0`

`pkt_too_small: 6`

The zero value for `kernel_drops` indicated that the kernel capture mechanism did not report dropped packets during the observed monitoring period.

## Result

The troubleshooting process demonstrated several important Suricata deployment checks:

- Verify package dependencies and conflicts.
- Validate `HOME_NET` and other configuration variables.
- Confirm the correct network interface.
- Test the configuration before starting the service.
- Review alerts and decoder events in context.
- Monitor packet capture statistics for dropped packets and errors.

These checks helped establish a functioning Suricata IDS deployment on Ubuntu.
