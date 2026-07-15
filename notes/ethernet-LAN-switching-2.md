# Ethernet LAN switching 2

## Ethernet Frame
Preamble SFD Destination Source Type Packet FCS

Preamble and SFD are usually not counted as part of header.

payload has to be minimum 46 bytes, padding bytes of 00000000 will be added to ensure this.

frame has to be minimum 64 bytes exlcuding preamble and SFD

## IP packet
inside frame, there is internet protocol 


## ARP (Address resolution protocl)
ARP is used to find the l2 address (MAC) from a known l3 address (IP)

made up of ARP request: sent by device who wants to know the mac
and ARP reply: the reply of what the MAC address is

ARP request is sent to all hosts on the network and waits for a reply from the correct device

ARP request is unicast; only has one destination node.

**ARP Request has its Dst MAC as FFFF.FFFF.FFFF.FFFF, which the switch knows to send out to all hosts**

run arp -a on terminal to see ARP table

run show arp on Cisco IOS to see ARP table

## Ping
Sends ICMP Echo Request and Reply, but these ICMP Echos requires MAC address of the destination, so ARP is sent out first.
- When pinging, the first ICMP Echo might fail because it may not have the MAC address of the destination, so ARP must be sent first. During the time ARP request and reply were being delivered, the first Ping might have failed.

Ping is just a network utility


## key takeways
run clear mac address-table dynamic interface [interface-id] on Cisco switch to clear all dynamic MAC addresses from MAC table