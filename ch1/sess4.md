# Delays, Loss, and Throughput in Packet-Switched Networks
- **throughput**: the amount of data per sec that can be transfered btw end systems
- in reality, computer networks constrain throughput, so that introduce delays btw end systems, and can actually lose packets

## 1. Overview of Delay in Packet-Switched Networks
- as a packet travels along a path, at each node it suffers from several types of delays

### Types of Delay
- how is a packet travels from router A which is outbound to router B?
  - the link btw A and B is preceded by a queue(buffer)
  - when the packet arrives at A, A examines the packet's header to determine the appropriate outbound link for the packet, and then directs the packet to this link
  - a packet can be transmitted on a link only if there is no other packet currently being transmitted on the link, and if there are no other packets preceding it in the queue
  - otherwise, the packet joins the queue

### Processing Delay
- there are a few parts consisting of this delay
  - the time during which a router examines the packet's header and determine where to direct the packet
  - the time during which a router checks for bit-level errors in the packet that occurred in transmitting the packet's bits from the upstream node
  
### Queuing Delay
- the time during which a packet waits to be transmitted to the next node, in a buffer(queue)
- the number of packets that an arriving packet might expect to find, is a function of the intensity and nature of the traffic arriving at the queue

### Transmission Delay
- the amount of time required to transmit(=push) all of the packet's bits into the link

### Propagation Delay
- the time required for a packet to propagate from one end of the link to another
- the speed depends on the physical medium of the link

### Comparing Transmission vs Propagation Delay
- transmission
  - a function of the packet's length and the transmission rate of the link
  - has nothing to do with the distance btw the two routers

- propagation
  - a function of the distance btw the two routers
  - has nothing to do with the packet's length or the transmission rate of the link

## 2. Queuing Delay and Packet Loss
- the queuing delay can vary from packet to packet: one typically uses statistical measures(average, etc.)
- how much is queuing delay important?
  - `a`: the average rate at which packets arrive at a queue(packets/sec)
  - `R`: the transmission rate = the rate at which bits are pushed out of the queue(bits/sec)
  - `L`: the average bits a packet contains

  - the average rate at which bits arrive at the queue: `La` bits/sec
  - assuming the queue is infinitely large, we call the ratio `La/R` call the **traffic intensity**

- if `La/R > 1`: the average rate at which bits arrive at the queue exceeds the rate at which bits can be transmitted from the queue
  - a golden rule: design a system so that `La/R <= 1`

- if `La/R <= 1`: the nature of the arriving traffic impacts the queuing delay
  - if packets arrive in bursts but periodically, there can be a significant average queuing delay

- typically the arrival process to a queue is random, so `La/R` might not be sufficient to describe the characteristics of the queuing delay statistics

### Packet Loss
- a queue's capacity is finite: if a newly arriving packet finds a full queue, then the router **drop**s the packet(packet loss)
- a lost packet may be re-transmitted on an end-to-end basis in order to ensure that all data are eventually transferred from source to destination

## 3. End-to-End Delay

### Traceroute
- `traceroute <destination>`
- skim through how it works

### End System, Application, and Other Delays
- other types of delays in the end systems
  - an end system wanting to transmit a packet into a shared medium may purposefully delay its transmission as part of its protocol for sharing the medium with other end systems
  - media packetization delay in VoIP(Voice over IP) applications: the sending side must first fill a packet with encoded digitized speech before passing the packet to the Internet

## 4. Throughput in Computer Networks
- **instantaneous throughput** at any instant of time is the rate (in bits/sec) at which the receiving host is getting the data

- example: N-link network with transmission rates `R_{i}` => `F / min{R_{i}}` bits/sec(**bottleneck link**)
  - typically in these days, the constraining factor for throughput in today's Internet is typically the access network

- example2: shared link in the core(intervening traffic) => divide the transmission rates 
