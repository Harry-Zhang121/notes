#  Mobile communication systems and networks MT

### Describe the basic challenges of mobile communications and solution areas (mobility, radio channel).
1. endpoints (terminals, user devices) are mobile

	- can go to anywhere in the network
	- can access the network anywhere
	- this motion should be supported while having an ongoing communications
	- this motion should be supported while the terminal is idle, that is it does not have an active communications
	- the mobile should be able to initiate a communication session (voice or
	video call, data upload or download) any time, anywhere
	- the mobile should be able to receive a communication session

	- the position of the terminal does not prove its right to communicate. Unlike fixed access, where the endpoint is associated to the premises of the customer. Therefore authentication mechanism is needed, to ensure that a terminal has rights to access the network

2.  The physical medium to be used is radio channel
	- it is a shared medium, namely any terminal can listen to it or transmit over it (interferece)


### Outline the properties of radio channels.
- thermal noise is always present
- channel attenuation is very high and is dependent on multiple factor
- multi-path propagation
- each path has random delay and attenuation and the sum signal arrives to the receiver
- received signal level is random and has very sudden random changes

### Outline Shannon's formula, describe the parameters in it and its consequences.
Shannon\`s formula $$ R \leq W*log_2( 1+ \frac{P_{signal}}{P_{noise}} ) $$
where 
- $R$: achievable bitrate at the receiver, bits/second
- $W$: bandwidth of the channel (Hz)
- $P_{signal}$: power of the received signal
- $P_{noise}$: power of the noise

**Consequences**:
- the bitrate scales linearly with bandwidth -> for high bitrate, high bandwidth is needed
- the bitrate scales logarithmically with power: it is not as useful to increase the power


### How to correct transmission errors in the radio channel (FEC, ACK, interleaving)?
Forward Error Correction, FEC:

- error detection: existence false bits (wrongly received) can be detected, like Cyclyc Redundancy Check (CRC)
- with given clever coding erroneous bits also can be corrected -> error correction coding
- this needs adding redundancy to the information: not just the useful bits, but redundancy also has to be transmitted
- the probability of receiving a bit wrongly is increased if the SNR decreases
- so for bad (low) SNR -> stronger error correction coding -> more redundancy -> less useful bits -> less bitrates

- some coding used in mobile systems: convolutional coding, turbo coding, Reed-
Solomon coding

Acknowledgement/retransmission:

- upon reception of packets or frames, the receiver sends ACKnowledgement to the
sender
- if erroneous packet received, NegativeACKnowledgement, or no acknowledgement is
sent
- the transmitter then retransmits
- this is the other method for error correction


### Sketch the basic structure of mobile networks. Describe the principle of frequency reuse:

### presentation of the basic idea through an example. Outline why mobile networks are based on radio cells.
> Lecture note 01 page 34


### Describe the main functionalities of the first four layers of the OSI layered model.
| Network layer | functionalities |
|---|---|
| Application | Application to network interaction |
| Presentation | Compression and data sequence |
| Session | Manages Opening/Closing Connection |
| Transport | Port destination encapsulation |

### Describe the basic properties of circuit switched and packet switched communications.
> Lecture note 02 page 9

#### Circuit switching
- Signalling phase to establish the connection 
- A fixed path along nodes
- Continues data flow
- Path is dedicated to one connection.
#### Packet switching
- No signalling phase
- Network nodes forward the packets
- Packets may take different path and may arrive in different order
- Path can be shared 
### Digital transmission: binary data, basic element, frames, parts of a frame.
> Lecture note 02 page 04

In digital transmission, data are transmitted in binary format. Basic element is bits, 8 bits is 1 byte.
The data is organized into frames or packets which contains **headers** and **body**.



### What are real time/quasi real time and non-real time services?
#### real time service
- the information should be transmitted when it is created (or with minimum latency)
- packet loss: tolerable

#### "quasi" real time
- streaming voice and video
- latency can be seconds

#### non-real time service
- latency is not a concern (second - tens of second)
- data loss is not permitted

### Describe a typical communication network hierarchy (access, aggregation, and core)?
**Access network**: The segment that reaches subscribers
**Aggregation network**: Local area switches. disctrict, town
**Core network: regional**: country wide network

### What is the geographic scale of comm. networks (PAN, LAN, MAN, WAN)?
- Personal Area Network (PAN)
- Local Area Network (LAN)
- Metropolitan area network (MAN)
- Wide Area Network (WAN)

### Describe the Internet Protocol's addressing and routing!
Addressed by IP address which is 4 8bit numbers. The IP address is used to indentify a connection interface.

The router will forward the packet to the next node according to a routing table and thedestination address.



### What is the Internet Protocol's packet format? What is IP tunneling?
> Lecture note 02 page 59



Packet contains headers with version, TTL, Source address and destination address information. And the body it self.

**Tunneling**:
- put a new IP header before the original IP packet
- new header contain source/destination address which are endpoints of the tunnel



### Describe the ICMP (with an example)!
ICMP Internet Control Message Protocol
- control messages at IP layer, in the payload of IP packets
- signalling of errors, messages for discovering routes, paths

example: traceroute
[Check this article](https://www.cloudflare.com/learning/ddos/glossary/internet-control-message-protocol-icmp/)



### What are the main differences between IPv4 and IPv6?
A lot more address: $2^{128}$
eight groups of four hexadecimal numbers


### Summarize IPv6 addressing, packet format and protocol features?
Features:
- Larger Address Space
- End-to-end Connectivity
- Simplified Header:
- Faster Forwarding/Routing
	- the information contained in the first part of the header is adequate for a router to take routing decisions
- Mobility
	- this feature enables hosts (such as mobile phone) to roam around in different geographical area and remain connected with the same IP address

### Describe the TCP transport protocol!
Refer to Informatics 2 lecture notes ^_+

### Describe the UDP transport protocol!
Refer to Informatics 2 lecture notes ^_+

### What is the DNS Domain Name System?
[Check this article](https://www.cloudflare.com/learning/dns/what-is-dns/)

### Describe Ethernet protocol (addressing, switching and speeds)!

Addressing:
- MAC address (often called physical address) of the interface
- 6 bytes, source address, destination address

Switching:
- based on destination address, similar to how it is in IP router
- does not consider anything beyond the Ethernet header
- switch learns MAC addresses

