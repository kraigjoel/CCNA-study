# OSI Model

## Data Encapsulation
PDUS:
data - data
data+L4 header - segment
data+l4 header+l3 header - packet
l2 trailer+data+l4 hedaer+l3 header+l2 header - frame

## Ethernet frame
eth header+packet+eth trailer

eth header
- has preamble
- SFD (Start Frame Delimiter)
- Destination -l2 address of destination
- Source -l2 address that sent the frame
- Type -IPv4 or IPv6 or length

eth trailer
- FCS- Frame check sequence

## preamble and SFD - eth header
Preamble
- 7 bytes (56 bits)
- Purpose: allows devices to sync to receiver clocks

SFD (Start frame delimiter)
- 1 byte (8 bits)
- indicates end of preamble and start of the rest of the frame


## destination and source - eth header
Indicates the sending and receiving device of frame
- uses MAC address (layer 2)
    - 6 bytes

## type/length - eth header
2 byte field
value <= 1500 means its showing length of packet in bytes

value => 1536 shows type of packet 
- 2048 decimalmeans IPv4 packet
- 34525 decimal means IPv6 packet

## FCS - eth trailer
4 bytes (32 bits)
detecs corrupted data via CRC (Cyclic redundancy check) 


## key takeaway
preamble SFD Destination Source Type FCS
7       `1    6       6           2    4
byte length

