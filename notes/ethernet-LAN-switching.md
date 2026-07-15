# Ethernet LAN Switching

## MAC Address
the l2 physical address of a device
6 bytes (48 bit)
first 3 bytes = OUI (Organizationally Unique Identifier)
last 3 bytes = unique to device

## Unicast Frame
a frame with one target device

## Unkown unicast frame
if switch doesnt know how to reach destination, switch will foward to all of its interfaces, except the orignal sender.
**This is called flood**

when destination MAC address doesnt match receipient, the node ignores packe

## Known unicast frame
when the switch has the destination of frame, it forwards straight to the destination node

## MAC address table
dynamic MAC address
The table fills up dynamically by looking at the device from which the frame was sent from
 - assigns that devices MAC address to an interface

*only nodes which sends data get added to MAC address table.*
*dynamic MAC addresses are removed from the table after 5 minutes of inactivty*


## key takeaways
MAC address table interface column doesnt describe physical connection, just where to find it