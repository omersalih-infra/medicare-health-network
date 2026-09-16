# MediCare Health Network

A fully redundant, three-site hospital enterprise network — designed, built, troubleshot, and verified end-to-end in Cisco Packet Tracer.

## Overview

MediCare Health Network simulates a hospital system with a main site and two community clinics:

- **HQ-Central** — main hospital, data center, Internet edge, 7 servers, 5 access switches
- **BR-North** — north community clinic, 3 access switches
- **BR-South** — south community clinic, 2 access switches

Every major claim in this project is backed by real CLI evidence — pings, DHCP leases, SSH logins, and ACL match counters — not just configuration that looks correct on paper.

## What's built

- **Redundant Layer 3 core** at every site — dual Catalyst switches with HSRP first-hop redundancy
- **OSPF backbone** tying all three sites into one dynamically-routed domain
- **Centralized DHCP + DNS**, proven working across the WAN at every site
- **ASA firewall with NAT/PAT**, giving all three sites real Internet reachability
- **Guest VLAN isolation** via ACL, verified with live traffic and hit counters
- **Wireless** — staff (WPA2-PSK) and guest (open) SSIDs across 6 access points
- **Centralized management** — SSH with RADIUS/AAA and local fallback, Syslog, SNMP, and NTP across all 19 manageable devices
- **Full end-user population** — PCs, IP phones, laptops, and printers across every site

## Repository contents

| File | Description |
|---|---|
| `MediCare_Health_Network.pkt` | The Packet Tracer project file |
| `MediCare_Health_Network_Report.docx` | Full project report — design, implementation, testing evidence, and a documented list of real defects found and fixed |
| `MediCare_All_Devices_Running_Config.txt` | Combined running-configuration export for every device in the topology |

## Documented limitations

Three genuine Cisco Packet Tracer simulator limitations were identified and documented separately from configuration defects (see Section 7 of the report):

1. GRE backup tunnel, HQ ↔ BR-North — a persistent stuck interface that resists all standard fixes
2. GRE backup tunnel, HQ ↔ BR-South — the router's expansion module only provides Layer-2 switchports, with no BVI support in this IOS image
3. NTP synchronization never completes, despite correct configuration and proven reachability
4. Cisco 7960 IP phones stall indefinitely mid-registration, consistent with the simulator expecting a Call Manager server that this design does not include

## Author

Built by Omer, Computer Science student specializing in Network & Telecommunications Technology, INES-Ruhengeri University.
