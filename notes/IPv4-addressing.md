# IPv4 Addressing 

## Layer 3 - Network Layer
IPv4 address is 32 bits long

## IPv4 address classes
A - /8 octet 1-126
B - /16 octet 128-191
C - /24 octet 192-223

## subnet masks 
to find subnet mask from CIDR (the /8, /27 etc at the end of an IP address):
1. write 32 bits
2. fill 1s according to number on CIDR left to right
3. convert each octet to decimal
Example: /8 > 11111111.00000000.00000000.00000000 > 255.0.0.0


## maximum number of hosts
2^n-2
where n is number of host bits (0)

## first and last usable address
make the last host bit of network address (all 0s) to 1, thats your first usable address

make last host bit of broadcast address (all 1s) to 0, thats your last usable address
example: 
172.16.0.0/16

host bits = 32-16 = 16
network address: 00000000.00000000
turn last one into 1: 00000000.00000001
therefore first usable address is 172.16.0.1

broadcast address: 11111111.11111111
turn last one into 0: 11111111.11111110
therefore last usable address is 172.16.255.254 (convert last octet to decimal)

## show ip interface brief
run in privileged EXEC mode on a CISCO router

status column - layer 1 status
protocol column - layer 2 status

shows interfaces and their ip addresses. ip addresses might be unassigned

## interface configuration mode
run interface gigabitethernet0/0 or whatever the name of interface is
in is short for interface

g0/0 is short for gigabitethernet0/0
- g is short for gigabitethernet even though there are other g options

## configuring ip address in CLI
run ip address [ip address] [subnet mask (in dotted decimal)]

## other commands
show interfaces [interface]

show interfaces description
- shows status and protocol status of interfaces
- has third column for description, where you can add your own descriptions by going into an interfaces' configuration mode, and running description [write your description]
  
## worked example
pc ip addr: 43.109.23.12/8

that means
network address = 43.0.0.0
max no of hosts = 2^(32-8)-2
network broadcast address = 