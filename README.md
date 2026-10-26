# 🔐 Virtual Cybersecurity Lab Environment Setup

**Building a virtual lab using Oracle VirtualBox and Kali Linux for cybersecurity learning and authorized penetration-testing practice.**

---

## 📌 Project Overview

This project focuses on setting up a virtual cybersecurity laboratory using Oracle VirtualBox and Kali Linux.

The main purpose is to create a controlled environment for learning network configuration, reconnaissance, vulnerability assessment, and penetration-testing fundamentals.

The laboratory uses Kali Linux as the primary security-testing machine. The network configuration and virtual-machine settings are documented to support future cybersecurity exercises and the addition of other virtual machines.

## 🎯 Project Objectives

The main objectives of this project are to:

- Install and configure Oracle VirtualBox.
- Extract the Kali Linux virtual-machine package using WinRAR.
- Import and run Kali Linux as a virtual machine.
- Configure the virtual machine's network adapter.
- Explore network configuration using NetworkManager.
- Configure and verify IPv4 addressing.
- Test network connectivity and DNS resolution.
- Document the setup process using screenshots.
- Create a clean virtual-machine snapshot for recovery.
- Prepare the environment for future authorized cybersecurity exercises.

## 🛡️ Purpose of the Lab

This laboratory provides a controlled environment for cybersecurity education and authorized security testing.

Potential activities include:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web application security testing
- Security-tool experimentation
- Learning Linux networking and troubleshooting

**Ethical use:** Only perform security testing on systems you own or have explicit permission to test. Do not target unauthorized systems.

## 🏗️ Lab Architecture

The laboratory consists of a Windows host system running Oracle VirtualBox, with Kali Linux operating as a guest virtual machine.

The intended network design uses a private virtual network with the `10.0.0.0/24` subnet. Additional virtual machines can be added in future exercises after the network configuration has been verified.

**Basic architecture:**

```text
Windows Host
     |
     v
Oracle VirtualBox
     |
     v
Kali Linux Virtual Machine
     |
     v
Virtual Network
10.0.0.0/24
     |
     v
Future Authorized Target VMs
```

## ⚙️ Lab Configuration

| Component | Configuration |
|---|---|
| Host operating system | Windows |
| Virtualization software | Oracle VirtualBox |
| Guest operating system | Kali Linux |
| Archive utility | WinRAR |
| Network configuration tool | NetworkManager (`nm-connection-editor`) |
| Intended network mode | NAT Network |
| Intended network subnet | `10.0.0.0/24` |
| Intended Kali IPv4 address | `10.0.0.2/24` |
| Intended gateway | `10.0.0.1` |
| Intended DNS server | `8.8.8.8` |
| VM snapshot | Clean Kali - Initial Lab Setup |

**Configuration note:** The intended network values above describe the target lab design. Confirm them against the actual VirtualBox and Kali Linux settings before treating them as verified results.

## 🪜 Lab Setup Procedure

### Step 1: Install WinRAR

WinRAR was used to extract the downloaded Kali Linux virtual-machine archive.

The extracted files were then available for use in preparing the Kali Linux virtual machine.

**Tool:** WinRAR

Resource: https://www.win-rar.com/

### Step 2: Install Oracle VirtualBox

Oracle VirtualBox was installed to provide the virtualization environment required to run Kali Linux as a guest operating system.

VirtualBox allows a guest operating system to run independently of the host operating system while using allocated hardware resources.

Resource: https://www.virtualbox.org/wiki/Downloads

### Step 3: Prepare the Kali Linux Virtual Machine

The Kali Linux virtual-machine package was downloaded and extracted using WinRAR.

The Kali Linux VM was then prepared and launched through Oracle VirtualBox.

The VM's memory allocation, network adapter, and other settings can be reviewed through VirtualBox Manager.

Resource: https://www.kali.org/get-kali/

### Step 4: Configure the VirtualBox Network Adapter

The Kali Linux virtual machine uses a virtual network adapter for network communication.

The intended setup uses a NAT Network so that multiple VMs attached to the same virtual network can communicate with one another while accessing external networks through network address translation.

To inspect the adapter configuration:

1. Open Oracle VirtualBox Manager.
2. Select the Kali Linux virtual machine.
3. Open **Settings → Network**.
4. Check the attachment type and network name.
5. Confirm the selected network matches the intended lab configuration.

**Intended network configuration:**

- Network mode: NAT Network
- Network name: `NatNetwork`
- IPv4 subnet: `10.0.0.0/24`
- Intended gateway: `10.0.0.1`

The actual values should be recorded after checking the settings in VirtualBox.

### Step 5: Configure Kali Linux Networking

Kali Linux networking was accessed using the graphical NetworkManager connection editor.

**Tool:** `nm-connection-editor`

To open the connection editor, run:

```bash
nm-connection-editor
```

The graphical interface allows the user to inspect wired connection settings and configure IPv4 options.

For a static IPv4 configuration, the intended lab values are:

| Setting | Intended value |
|---|---|
| IPv4 method | Manual |
| IP address | `10.0.0.2` |
| Subnet prefix | `/24` |
| Subnet mask | `255.255.255.0` |
| Gateway | `10.0.0.1` |
| DNS server | `8.8.8.8` |

Before applying a static address, confirm that it belongs to the configured virtual network and does not conflict with another device or an address reserved by DHCP.

After saving the configuration, inspect the active network settings using:

```bash
ip a
```

```bash
ip route
```

```bash
nmcli
```

These commands help verify the active IPv4 address, routing table, network connection, and DNS information.

### Step 6: Verify Network Connectivity

Network connectivity should be checked after configuring the network adapter and IPv4 settings.

**Check the IP address:**

```bash
ip a
```

Expected result: The intended Kali IPv4 address appears on the active network interface.

**Check the default route:**

```bash
ip route
```

Expected result: The routing table contains the appropriate route for the configured network and, where applicable, a default gateway.

**Test the gateway:**

```bash
ping -c 4 10.0.0.1
```

**Test external IP connectivity:**

```bash
ping -c 4 8.8.8.8
```

**Test DNS resolution:**

```bash
nslookup example.com
```

**Check Nmap installation:**

```bash
nmap --version
```

Record the actual output of each command. A failed ping does not always indicate that a host or network is unavailable, because ICMP traffic can be blocked.

### Step 7: Create a Clean Virtual Machine Snapshot

A snapshot provides a recovery point for the Kali Linux virtual machine before future experiments.

To create one:

1. Open Oracle VirtualBox Manager.
2. Select the Kali Linux virtual machine.
3. Open the **Snapshots** section.
4. Select **Take Snapshot**.
5. Enter the snapshot name:

   `Clean Kali - Initial Lab Setup`

6. Add a description if required.
7. Save the snapshot.
8. Verify that it appears in the snapshot list.

The snapshot should be created after the initial lab configuration has been checked. It can then be used as a recovery point if later experiments affect the VM.

## 📸 Lab Screenshots

Screenshots provide evidence of the configuration and help other learners understand the setup process.

Recommended screenshots:

1. **VirtualBox Manager:** Kali Linux VM listed in VirtualBox.
2. **Network Adapter Settings:** VirtualBox network attachment and network name.
3. **Kali Linux Desktop:** The running Kali Linux virtual machine.
4. **NetworkManager Configuration:** The IPv4 settings in `nm-connection-editor`.
5. **Network Verification:** Terminal output showing the IP address and connectivity tests.
6. **VM Snapshot:** The created snapshot displayed in VirtualBox.

Use your own screenshots and ensure that they accurately represent the configuration at the time they were captured.

## 🐞 Problems Encountered and Troubleshooting

No specific technical problems are documented in this project section yet. Any problems encountered during setup should be recorded with the symptoms, investigation steps, and verified solution.

Useful commands for network troubleshooting include:

```bash
nmcli
```

```bash
ip a
```

```bash
ip route
```

```bash
cat /etc/resolv.conf
```

These commands help inspect the network connection, assigned IP addresses, routes, and DNS configuration.

If connectivity fails after changing IPv4 settings, check that the IP address, subnet, gateway, DNS configuration, and VirtualBox network mode are consistent.

## 💡 What I Learned

Through this project, I gained practical experience with the following concepts:

### 1. Virtualization

I learned how to use Oracle VirtualBox to run Kali Linux as a guest operating system on a host computer.

### 2. Virtual Machine Networking

I learned that VirtualBox provides different network attachment modes and that the selected mode affects connectivity between virtual machines and external networks.

### 3. Network Configuration

I learned how to access the NetworkManager connection editor and inspect IPv4 settings, including IP addresses, subnet masks, gateways, and DNS servers.

### 4. Network Troubleshooting

I learned how to use Linux commands such as `ip a`, `ip route`, and `nmcli` to inspect network configuration and investigate connectivity issues.

### 5. Virtual Machine Snapshots

I learned how snapshots can preserve a known-good VM state and support recovery before potentially disruptive experiments.

### 6. Technical Documentation

I learned how to document a cybersecurity lab using configuration tables, command examples, screenshots, verification steps, and troubleshooting notes.

## 🔐 Security and Ethical Use

This laboratory is intended for educational purposes and authorized security testing only.

All future scanning, reconnaissance, and vulnerability-assessment exercises must be conducted within the lab or against systems for which explicit permission has been obtained.

## 🔗 Tools and Resources

- **WinRAR:** https://www.win-rar.com/
- **Oracle VirtualBox:** https://www.virtualbox.org/wiki/Downloads
- **Kali Linux:** https://www.kali.org/get-kali/
- **Kali Linux Documentation:** https://www.kali.org/docs/

---

*This project documents the development of a virtual cybersecurity learning environment. Configuration values and verification results should be updated as the lab is tested and completed.*
