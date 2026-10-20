# Network Troubleshooting Documentation

## Cisco Enterprise Multi-Site Network Lab

This document records network issues encountered and resolved during the implementation and testing of a Cisco Packet Tracer enterprise network.

### Case 1: Router Interface Connectivity Issue

**Problem:** Router-to-router connectivity was unsuccessful during initial network configuration.

**Troubleshooting:**
- Checked interface status using `show ip interface brief`.
- Verified neighboring devices using `show cdp neighbors`.
- Compared interface IP assignments with physical cable connections.

**Resolution:** Corrected the router interface configurations to match the actual physical connections.

**Skills Demonstrated:** Layer 3 troubleshooting, Cisco Discovery Protocol (CDP), interface verification.

### Case 2: Engineering VLAN Connectivity Issue

**Problem:** The Engineering PC could not communicate with its VLAN gateway.

**Troubleshooting:**
- Verified VLAN membership and switchport configuration.
- Checked 802.1Q trunk settings.
- Reviewed router subinterface configuration.
- Checked the Engineering PC IP address and subnet mask.

**Resolution:** Corrected the Engineering PC IP configuration to match the Engineering VLAN subnet.

**Skills Demonstrated:** VLAN troubleshooting, router-on-a-stick, IPv4 subnetting.

### Case 3: HSRP Failover Connectivity Issue

**Problem:** During a simulated R1 failure, the Engineering PC could reach the HSRP virtual gateway but could not communicate with the Branch network.

**Troubleshooting:**
- Verified HSRP operation and backup router connectivity.
- Checked OSPF routes between R3 and R2.
- Tested connectivity from R3 to the Branch network.
- Inspected the Engineering PC default gateway using `ipconfig /all`.

**Root Cause:** The Engineering PC was using R1's physical IP address (`192.168.30.1`) instead of the HSRP virtual IP (`192.168.30.254`) as its default gateway.

**Resolution:**
1. Changed the Engineering PC default gateway to `192.168.30.254`.
2. Verified connectivity through R3 while R1 was powered off.
3. Updated the DHCP gateway configuration.
4. Renewed the Engineering PC DHCP configuration.

**Result:** Engineering-to-Branch communication succeeded through the backup router during the simulated primary router failure.

**Skills Demonstrated:** HSRP, OSPF, DHCP troubleshooting, routing verification, network redundancy.

## Key Lessons Learned

- Physical interface mapping must be verified before troubleshooting Layer 3 connectivity.
- VLAN assignments, trunk configurations, and IP addressing must be consistent.
- HSRP clients must use the virtual IP address as their default gateway.
- Dynamic routing and gateway redundancy work together to support network failover.
- End-to-end connectivity testing is essential for validating redundancy.
