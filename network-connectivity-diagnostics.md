# Windows Network Connectivity Diagnostics

## 1. Lab Overview

**Project:** IT Service Desk & Troubleshooting Lab  
**Lab type:** Hands-on Windows network diagnostics  
**Operating system:** Windows 11  
**Tools:** Windows PowerShell, ipconfig, ping, nslookup, tracert, Get-NetAdapter, Get-NetIPConfiguration, Get-NetConnectionProfile, netsh

## 2. Objective

Practice collecting and interpreting Windows network configuration data to assess basic connectivity, DNS resolution, gateway reachability, adapter status, and network interface configuration.

## 3. Tests Performed and Results

### Test 1: IP Configuration

**Command:** `ipconfig /all`

**Results:**
- Primary Ethernet IPv4 address: `10.0.2.15`
- Subnet mask: `255.255.255.0`
- IPv4 default gateway: `10.0.2.2`
- DHCP: Enabled
- DNS servers: `75.75.75.75` and `75.75.76.76`

**Finding:** The primary adapter had an IPv4 address, a default gateway, DNS server entries, and DHCP enabled.

### Test 2: External IP Connectivity

**Command:** `ping 8.8.8.8`

**Results:**
- Packets sent: 4
- Packets received: 4
- Packet loss: 0%
- Average response time: 12 ms

**Finding:** The destination responded to all four ICMP requests.

### Test 3: DNS Resolution

**Command:** `nslookup google.com`

**Finding:** DNS resolution succeeded and returned IPv4 and IPv6 addresses for the hostname.

### Test 4: Hostname Connectivity

**Command:** `ping google.com`

**Results:**
- Packets sent: 4
- Packets received: 4
- Packet loss: 0%
- Average response time: 38 ms

**Finding:** The hostname resolved, and the resulting destination responded to all four ping requests.

### Test 5: Route Tracing

**Command:** `tracert -d 8.8.8.8`

**Finding:** The trace completed, and the destination responded at the first reported hop. This result describes the observed trace and does not establish the complete physical network path.

### Test 6: Default Gateway Reachability

**Command:** `ping 10.0.2.2`

**Results:**
- Packets sent: 4
- Packets received: 4
- Packet loss: 0%

**Finding:** The configured IPv4 default gateway responded to the test requests.

### Test 7: Network Adapter Status

**Command:** `Get-NetAdapter | Format-Table Name, Status, LinkSpeed, InterfaceDescription -AutoSize`

**Results:**
- Ethernet: Up, reported link speed 1 Gbps
- Ethernet 2: Up, reported link speed 1 Gbps

**Finding:** Windows reported both Ethernet adapters as Up. The reported link speed is not a measurement of actual internet throughput.

### Test 8: DNS Server Configuration

**Command:** `Get-DnsClientServerAddress | Format-Table InterfaceAlias, AddressFamily, ServerAddresses -AutoSize`

**Finding:** The primary Ethernet adapter listed IPv4 DNS servers `75.75.75.75` and `75.75.76.76`, along with an IPv6 DNS address. The secondary adapter had different DNS entries.

### Test 9: Extended Connectivity Test

**Command:** `ping -n 20 8.8.8.8`

**Results:**
- Packets sent: 20
- Packets received: 20
- Packet loss: 0%
- Minimum response time: 8 ms
- Maximum response time: 24 ms
- Average response time: 15 ms

**Finding:** The extended test showed no packet loss during the test period.

### Test 10: Consolidated IP Configuration

**Command:** `Get-NetIPConfiguration`

**Findings:**
- Ethernet used IPv4 address `10.0.2.15` and gateway `10.0.2.2`.
- Ethernet 2 used IPv4 address `192.168.56.103` and did not list an IPv4 default gateway.
- Ethernet 2 was identified as an unidentified network.

### Test 11: Windows Network Profiles

**Command:** `Get-NetConnectionProfile`

**Findings:**
- Ethernet reported IPv4 connectivity as Internet.
- Ethernet 2 reported IPv4 connectivity as LocalNetwork.
- Both connections were categorized as Public.

**Finding:** Windows reported different connectivity levels for the two adapters. Network profile settings should be reviewed in context before making changes.

### Test 12: IPv4 Interface Status

**Command:** `netsh interface ipv4 show interfaces`

**Findings:**
- Ethernet: Connected, MTU 1500, metric 25.
- Ethernet 2: Connected, MTU 1500, metric 25.
- Loopback Pseudo-Interface 1: Connected.

**Finding:** Windows reported both Ethernet interfaces as connected.

## 4. Overall Conclusion

The diagnostic tests showed successful DNS resolution, successful connectivity to the tested public IP addresses, successful reachability of the configured IPv4 gateway, and no packet loss during the recorded extended ping test.

Windows reported two Ethernet adapters with different IP configurations and connectivity profiles. The available evidence is consistent with a primary internet-connected adapter and a secondary adapter that has local-network connectivity.

These results describe the system at the time of testing. They do not guarantee that every application or destination is reachable, nor do they establish that intermittent connectivity problems cannot occur.

## 5. Skills Demonstrated

- Windows network configuration review
- IPv4 addressing and subnet-mask interpretation
- DHCP and default gateway identification
- DNS troubleshooting
- Ping and traceroute diagnostics
- Network adapter status inspection
- Windows network profile interpretation
- Technical documentation and evidence collection

## 6. Evidence

Supporting screenshots are available in the [`screenshots/`](screenshots/) folder. They document the Windows network diagnostic commands and their results, providing visual evidence of the troubleshooting activities performed during this lab.

Screenshots were reviewed for potentially sensitive information before publication.

## 7. Limitations

This exercise documents basic connectivity checks on a personal lab system. It does not represent production enterprise troubleshooting, measured internet throughput, or a formal network security assessment.
