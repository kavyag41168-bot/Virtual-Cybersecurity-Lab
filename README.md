# Virtual Cybersecurity Lab — Network Configuration

## 1. Project Overview

This project focuses on setting up a virtual cybersecurity lab using Oracle VirtualBox and Kali Linux. The practical work involves examining network interfaces, understanding IPv4 configuration, and exploring network settings using NetworkManager.

## 2. Tools and Technologies

- **Virtualization Platform:** Oracle VirtualBox
- **Operating System:** Kali Linux
- **Network Management:** NetworkManager
- **Commands Used:** `nmcli`, `nm-connection-editor`

## 3. Network Configuration and Inspection

### Step 1: Inspect Network Connections

I used the following command to inspect the available network connections and their current configuration:

```bash
nmcli
```

The output showed the following details:

| Parameter | Observed Value |
|---|---|
| Network interface | `eth0` |
| Connection profile | `Wired connection 1` |
| IPv4 address | `10.0.0.15/24` |
| Default gateway | `10.0.0.1` |
| DNS server | `192.168.0.1` |
| Virtual network adapter | Intel 82540EM |

### Step 2: Open the Network Connection Editor

I executed the following command to open the graphical network configuration interface:

```bash
nm-connection-editor
```

The Network Connections window opened and displayed the `Wired connection 1` profile. This interface allows network connection settings, including IPv4 configuration, to be reviewed and modified.

### Step 3: IP Address Configuration

The observed IPv4 address was `10.0.0.15/24`. The next step is to review the IPv4 settings and configure the intended IP address according to the VirtualBox network configuration.

The final IP address and connectivity status will be recorded after the configuration is applied and verified.

## 4. Key Learnings

- Learned to inspect network interfaces using `nmcli`.
- Identified the active Ethernet connection and its IPv4 address.
- Learned how to open the graphical NetworkManager connection editor.
- Improved understanding of IPv4 addressing, gateways, and DNS.
- Explored the process of reviewing network configuration in Kali Linux.

## 5. Conclusion

This practical exercise provided hands-on experience with network inspection and configuration in Kali Linux running inside Oracle VirtualBox. It established a foundation for understanding virtual networking and preparing a cybersecurity lab for further authorized testing.


