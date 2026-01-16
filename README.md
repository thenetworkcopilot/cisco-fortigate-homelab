# Dual-WAN Enterprise Home Lab
## Cisco Router + Free FortiGate VMs: MPLS, BGP, SD-WAN & IPsec

This repository contains the complete configuration files for building a realistic dual-WAN enterprise network in your home lab.

## The Challenge
The free FortiGate VM only provides 3 interfaces, but we need to simulate:
- MPLS circuit
- Internet circuit  
- Local LAN connectivity

## The Solution
Using VRF-Lite on the Cisco router to separate MPLS and Internet paths, combined with secondary IPs and policy-based routing on the FortiGates to work around interface limitations.

## Hardware Used
- Cisco ISR 1100 (1921/1941 will also work)
- FortiGate VMs 7.6 (Free Tier)
- Cisco 2960X Switches

## Configuration Files
- `cisco_router_backup_config.txt` - ISR with VRF-Lite configuration
- `FGT-Headquarters_7-6_3596_202512291035.conf` - HQ FortiGate
- `FGT-Branch_Office_7-6_3596_202512291035.conf` - Branch FortiGate  
- `FGT-Manufacturing_7-6_3596_202512291035.conf` - Manufacturing FortiGate
- `branch_office_switch_backup_config.txt` - Branch switch
- `manufacturing_switch_backup_config.txt` - Manufacturing switch

## Important Notes

### Ubuntu VM Static Routes
On the HQ Ubuntu server, add these static routes to bypass the ISR and route directly to the firewall:
```bash
sudo ip route add 192.168.10.0/24 via 192.168.4.136
sudo ip route add 192.168.20.0/24 via 192.168.4.136
```



## Video Walkthrough
https://youtu.be/Vs0Ftor29xY

## Related Project
This lab serves as the foundation for an AI-powered network troubleshooting agent: https://www.youtube.com/@RishiNetworks
