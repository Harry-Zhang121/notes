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
- reveiced signal level is random and has very sudden random changes

### Outline Shannon\`s formula, describe the parameters in it and its consequences.
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
- the probavility of receiving a bit wrongly is increased if the SNR decreases
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
lecture note 01 page 34


### Describe the main functionalities of the first four layers of the OSI layered model.
