# Lab 1: Basic LAN Connectivity

## Objective 
Understand how two PCs communicate through a layer 2 switch.

## Topology
PC1 - SW1 - PC2

## IP Configuration
| Device | IP Address | Subnet Mask |
|--------|------------|-------------|
| PC1 | 192.168.1.10 | 255.255.255.0 |
| PC2 | 192.168.1.20 | 255.255.255.0 |

## Commands used 
- ping: Test connectivity between devices
- arp -a: 

## Why did it work
A switch allows PCs on the same LAN to communicate by forwarding Ethernet frames based on their destination MAC addresses. When a PC wants to send data to another PC in the same subnet, it uses ARP (Address Resolution Protocol) to discover the destination PC's MAC address if it is not already known. The switch learns which MAC addresses are connected to its ports by examining the source MAC addresses of incoming frames and storing them in its MAC address table. It then uses this table to forward frames to the correct destination port.

Because both PCs are in the same subnet, they can communicate directly through the Layer 2 switch without requiring a router.

## What went wrong and how to fix it?
- Used a router instead of a switch, replaced it to fix.