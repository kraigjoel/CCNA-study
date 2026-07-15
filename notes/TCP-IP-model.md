# TCP/IP Model

## Protocols
Protocol: a set of rules dictacting how data communicates between devices in a network. it is the languages that computers use to communicate

Standard: an agreed specification describing how protocols/tech should work.

TCP: Transmission Control Protocol
IP: Internet Protocol

IEEE: insitute of electrical and electronics engineers
- ethernet 802.3
- wifi 802.11

IETF: internet engineering task force
- TCP, HTTP DNS...

## layers
- application
- transport- port numbers
- internet- ip addresses
- local network- mac addresses
- physical

## physical layer
This layer sends and receives bits as signals over mediums
This layer defines cables, connectors, signal levels and speeds
- UTP cables, fiber optic, NICs
- low level details

## Local network layer
hop to hop delivery of messages on the network
switches dont count as a hop
a hop is from one router/host to another

This layer uses MAC (Media Access Control) address to identify interface
protocols: ethernet, wifi

## Internet layer
goes across multiple networks

Routers are used in this layer

protocols: IP, ICMP

## Transport layer
process to process/service to service communication is provided by this layer

port numbers are used to identify processes on a host

protocols: UDP (user datagram protocol), TCP(transmission control protocol)

## Application layer
formatting, sending and interpretting of data

protocols: HTTP/HTTPS, FTP, TFTP, SMTP, POP3, IMAP


## Protocol data units PDU
TCP - segments
UDP - datagram

segment/datagram + L3 header is called packet

packet + L2 header/trailer is called a frame

PDU: protocol data unit

segment/datagram = Layer 4 PDU or L4DPU
packet = Layer 3 PDU or L3PDU
frame = Layer 2 PDU or L2PDU

payload: contents of PDU

segment/datagram payload = application data
packet payload = segment/datagram
frame payload = packet

## OSI model
Open Systems interconnection model
goal: international, vendor-neutral networking standards to replcae TCP/IP
results: protocols were too complex so never got as popular TCP/IP. 

- Application
- presentation
- session
- transport
- network
- data link
- physical

# key takeaways
Commonly used layer names are borrowed from OSI model
- Application
- Transport
- Network
- Data link
- physical

encapsulation and decapsulation

PDUs

adjacent and same layer interaction