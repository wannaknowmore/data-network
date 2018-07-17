# Episode 1: Basics

## Some Definition
A data network allows nodes to communicate and share information with each other.
The nodes interact through various physical media and protocols.

## Layering and the OSI model
The Open Systems Interconnection model (OSI model) is a conceptual model that
characterizes and standardizes the communication functions of a telecommunication system.
The model partitions a communication system into abstraction layers.

Originally, the OSI defined 7 layers:
- Layer 7: Application Layer
- Layer 6: Presentation Layer
- Layer 5: Session Layer
- Layer 4: Transport Layer
- Layer 3: Network Layer
- Layer 2: Data Link Layer
- Layer 1: Physical Layer

In a TCP/IP stack, the layering is simplified to 5 layers:
- Layer 5: Application Layer (HTTP)
- Layer 4: Transport Layer (TCP/UDP)
- Layer 3: Network Layer (IP)
- Layer 2: Data Link Layer (Ethernet)
- Layer 1: Physical Layer (Media/Wiring/Connectors)

Note: There is a concept known as "convergence layer" which defines the ability to
place layers over other layers, in a form of encapsulation.
For example, placing Ethernet over UDP (as with [VXLAN](https://tools.ietf.org/html/rfc7348))

Note2: Implementations may optimize and peek in lower layers data in order to make better
desicions with the cost (in most cases) of complexity.

**Wanna know more?**
- An interesting RFC that touches internet architecture: https://tools.ietf.org/html/rfc3439

## Physical Layer
- Media: twisted-pair/coax, fiber, wifi/satellite/radio
- Connectors & Transivers: Standards like RJ45, GBIC, SFP.
- Throughput (10/100/1G/10G/40G/100G)

## Ethernet

Here is the ethernet frame format, not including CRC and other sync bits.

+---------+---------+----------+------+---------+
| MAC dst | MAC src | 802.1Q*  | Type | Payload |
+-----------------------------------------------+
| 6 octets| 6 octets| 4 octets |  2   | 46:1500 |
+------------------------------+------+---------+

The 802.1Q 4 octets field is optional, used for VLAN and priority tagging.
16 bits are reserved for the tag type (0x8100), the VLAN tag has 12 bits and the priority 3 bits.
(1 bit is reserved for other uses)

