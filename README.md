# Cisco Static Routing Lab

## Project Overview

In this lab, I connected two separate LAN networks using two Cisco routers and static routing. The goal was to bring up the LAN interfaces, 
configure a point-to-point router link, add static routes, and verify end-to-end connectivity between both sites.

## Network Topology

Coffee House LAN: 192.168.42.0/24

Fallout Shelter LAN: 192.168.84.0/24

Point-to-Point Link: 10.8.0.0/30

| Device | Interface | IP Address |
|----------|----------|----------|
| Cafe-RT1 | Ethernet0/0 | 192.168.42.1/24 |
| Cafe-RT1 | Ethernet0/1 | 10.8.0.1/30 |
| Fallout-RT1 | Ethernet0/0 | 192.168.84.1/24 |
| Fallout-RT1 | Ethernet0/1 | 10.8.0.2/30 |

## Configuration Summary

### Cafe-RT1

```bash
interface ethernet0/0
 ip address 192.168.42.1 255.255.255.0
 no shutdown

interface ethernet0/1
 ip address 10.8.0.1 255.255.255.252
 no shutdown

ip route 192.168.84.0 255.255.255.0 10.8.0.2
```

### Fallout-RT1

```bash
interface ethernet0/0
 ip address 192.168.84.1 255.255.255.0
 no shutdown

interface ethernet0/1
 ip address 10.8.0.2 255.255.255.252
 no shutdown

ip route 192.168.42.0 255.255.255.0 10.8.0.1
```

## Verification Commands

```bash
show ip interface brief
show ip route
show ip arp
ping 10.8.0.2
ping 192.168.84.1
```

## Results

The lab was completed successfully by configuring two Cisco routers and establishing connectivity between two separate LANs using static routing.

Both LAN interfaces were configured with their assigned gateway addresses and reached an operational up/up state. 
The point-to-point connection between Cafe-RT1 and Fallout-RT1 was established using the 10.8.0.0/30 network.

Static routes were added on each router to provide reachability to the remote LAN. Connectivity was validated through successful ICMP ping tests between the routers.

Interface statistics were reviewed after implementation and showed no input errors, CRC errors, or packet drops.

## Skills Practiced

- Cisco IOS Configuration
- Static Routing
- IPv4 Addressing
- Interface Configuration
- Router Verification
- Network Troubleshooting
- ICMP Testing
- ARP Verification

## Key Takeaway
This project strengthened my understanding of how routers communicate across different networks using static routes. 
I gained hands-on experience configuring interfaces, verifying connectivity, troubleshooting routing issues, and validating network performance using Cisco IOS commands.

## Screenshots
I also learned how to verify interface status, confirm connectivity, and troubleshoot basic routing issues using Cisco IOS commands.

## Screenshots

### Interface Status and Configuration

![Cafe Router Configuration](screenshots/Screenshot%202026-06-05%20130657.png)

### Point-to-Point Link Configuration

![Point-to-Point Link](screenshots/Screenshot%202026-06-05%20130723.png)

### Fallout Router Configuration

![Fallout Router Configuration](screenshots/Screenshot%202026-06-05%20130757.png)

### Interface Verification

![Interface Verification](screenshots/Screenshot%202026-06-05%20130816.png)
