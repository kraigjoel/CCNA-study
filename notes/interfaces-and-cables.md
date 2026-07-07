# Interfaces and Cables

## Speed Units
Speed is measured in bits per second
kilo = 1000
mega = 1 000 000
giga = 1 000 000 000
tera = 1 000 000 000 000 

rj 45 - standard ethernet connector
Ethernet = collection of standards and protocols
UTP = Unshielded twisted pair
- most common and cheap ethernet cable

## Copper straight through cable
Used between PCs/Routers/Firewalls and switches
- PC <> Switch
- Router <> Switch
- Firewall <> Switch

Reason: 
- PCs, routers and firewalls transmit on pins 1 and 2 and receive on 3 and 6
- Switches do the opposite

## Auto MDIX
Purpose: Allows devices to automatically connect whether a straight through or crossover cable is needed
Result: Crossover cables are rarely needed

## Fiber optic cables
Fiber optic port <- SFP transceiver <- Fiber optic cable

## Key takeaways
- Straight through cables for PC/Router/Firewall <> Switch
- Crossover cables for connecting two same device types
  - Auto MDIX removes the need for this
- Fiber optic cables
  - multi/singlemode
  - SFP transceiver
