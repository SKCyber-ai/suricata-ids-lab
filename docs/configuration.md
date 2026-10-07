# Suricata Configuration

## HOME_NET Configuration

Suricata uses the `HOME_NET` variable to identify the network that is considered the local or protected network.

During the initial configuration, the active local network was identified as:

```text
192.168.1.0/24
```

The active wireless interface had the address:

```text
192.168.1.143/24
```

## Initial Configuration Issue

The Suricata configuration initially contained an incorrectly named variable:

```yaml
xHOME_NET: "[192.168.1.0/24]"
```

Because Suricata expects the variable to be named `HOME_NET`, the service failed configuration validation with an error indicating that:

```text
Variable "HOME_NET" is not defined in configuration file
```

The problem occurred because `EXTERNAL_NET` was configured to reference `$HOME_NET`.

## Configuration Correction

The configuration was corrected by changing:

```yaml
xHOME_NET: "[192.168.1.0/24]"
```

to:

```yaml
HOME_NET: "[192.168.1.0/24]"
```

This allowed Suricata to correctly identify the local network.

## Configuration Validation

After making the correction, the configuration was tested with:

```bash
sudo suricata -T -c /etc/suricata/suricata.yaml
```

The validation completed successfully with:

```text
Configuration provided was successfully loaded. Exiting.
```

## Result

The `HOME_NET` variable was successfully configured for the local `192.168.1.0/24` network.

Suricata was then able to start successfully and operate as a network intrusion detection system.
