# CCNA Lab 2: Ethernet Switching, MAC Learning and ARP

**Level:** Beginner  
**Platform:** Cisco Packet Tracer  
**Status:** Conceptual questions completed; Packet Tracer observations to be added

## Objectives

- Understand how switches learn source MAC addresses.
- Explain known unicast forwarding and unknown unicast flooding.
- Distinguish ARP caches from switch MAC address tables.
- Explain why ARP is not required for every ping.
- Understand dynamic MAC address aging and MAC moves.

## Proposed topology

One Cisco 2960 switch connected to three PCs using copper straight-through cables.

```text
PC0 (192.168.1.10) --- Fa0/1 [SW1] Fa0/2 --- PC1 (192.168.1.20)
                                  |
                                Fa0/3
                                  |
                         PC2 (192.168.1.30)
```

| Device | IPv4 address | Subnet mask | Switch interface |
|---|---|---|---|
| PC0 | 192.168.1.10 | 255.255.255.0 | Fa0/1 |
| PC1 | 192.168.1.20 | 255.255.255.0 | Fa0/2 |
| PC2 | 192.168.1.30 | 255.255.255.0 | Fa0/3 |

No default gateway is required because all three PCs are in the same IPv4 subnet and VLAN.

![topology](diagrams/lab2a.png)

## Commands

On the switch:

```text
enable
show mac address-table
```

On a PC (Packet Tracer Command Prompt):

```text
arp -a
ping 192.168.1.20
arp -a
```

To inspect packet exchanges, switch Packet Tracer to **Simulation** mode, filter for **ARP** and **ICMP**, and use **Capture/Forward**.

![before switching](diagrams/lab2b.png)
![after switching](diagrams/lab2c.png)

## Key concepts

### 1. MAC address learning

A switch learns a device's MAC address by inspecting the **source MAC address** of a frame arriving on an interface. It associates that address with the incoming interface and VLAN.

**Memory rule:** Source MAC = learning; destination MAC = forwarding decision.

### 2. Known unicast forwarding

If the destination MAC address is in the switch's MAC address table, the switch normally forwards the frame only through the associated outgoing interface (assuming that interface differs from the incoming one and forwarding is permitted).

### 3. Unknown unicast flooding

If the destination is a unicast MAC address that the switch has not learned, it floods the frame out other forwarding interfaces **in the same VLAN**, excluding the interface on which the frame arrived. It does **not** change the destination MAC address to the broadcast address.

Example: PC0 sends to PC2, but the switch does not know PC2's port. The frame arrives on Fa0/1 and is flooded out Fa0/2 and Fa0/3. PC1 discards the frame because the destination MAC is not its own; PC2 accepts it.

### 4. ARP and repeated pings

For IPv4 communication on the same subnet, a PC needs the destination's MAC address. If the mapping is not already in its ARP cache, it sends an **ARP Request** using the Ethernet broadcast destination `FF:FF:FF:FF:FF:FF`. The target normally responds with an ARP Reply. The sender caches the mapping.

A second ping shortly afterward generally uses the cached MAC address, so another ARP broadcast is unnecessary. The ICMP Echo Request itself is carried in a **unicast Ethernet frame** once the MAC address is known.

For off-subnet destinations, the host resolves the MAC address of its next-hop gateway instead of the remote host.

### 5. ARP cache vs MAC address table

| Device | Table | Mapping | Purpose |
|---|---|---|---|
| PC | ARP cache | IPv4 address → MAC address | Determine the destination MAC for local Ethernet delivery |
| Switch | MAC address table | MAC address + VLAN → interface | Determine where to forward Ethernet frames |

These tables age independently. A PC can retain an ARP entry even if the switch has forgotten the corresponding MAC-to-port mapping. In that situation, the switch can flood an **unknown unicast** without the PC needing another ARP exchange.

### 6. Learning from replies

If the switch's MAC address table starts empty, receiving PC0's frame on Fa0/1 teaches it PC0's source MAC address. When PC1 replies from Fa0/2, the switch learns PC1's source MAC address and can forward the reply directly to Fa0/1 because PC0's location is already known.

### 7. MAC aging and moving devices

On a Cisco 2960, the default dynamic MAC aging time is typically **300 seconds (5 minutes)**. Dynamic entries can expire after inactivity.

If PC1 moves from Fa0/2 to Fa0/3 and transmits a frame, the switch can update its MAC-to-port association immediately from the source MAC address. It does not have to wait five minutes for the old entry to expire.

## Conceptual checkpoint: completed

- **Unknown unicast:** Identified that the switch floods the frame when it does not know the destination port.
- **Flooding scope:** Clarified that the incoming interface is excluded and that the frame remains unicast-addressed.
- **Reply forwarding:** Explained that the switch learned PC0's location from the original frame, so it can forward PC1's reply directly.
- **MAC move:** Explained that a frame arriving from PC1 on a new interface updates the switch's learned association.

## Practical verification checklist

- [ ] Build the three-PC topology in Packet Tracer.
- [ ] Record `show mac address-table` before generating traffic.
- [ ] Ping PC1 from PC0 and record the updated MAC address table.
- [ ] Inspect `arp -a` on PC0.
- [ ] In Simulation mode, observe ARP Request, ARP Reply, and ICMP packets.
- [ ] Repeat the ping and check whether another ARP Request occurs.
- [ ] Record screenshots and actual command outputs.

## Reflection

The central lesson is that switches **learn from source MAC addresses** and **forward based on destination MAC addresses**. Flooding is a forwarding action, not the same thing as changing a frame into a broadcast. ARP resolves IPv4-to-MAC mappings at the host, while the switch's MAC address table tracks MAC-to-interface mappings.

## Next lab

**Lab 3: VLANs and network segmentation** — place PCs into different VLANs and observe why sharing a physical switch does not guarantee Layer 2 connectivity.
