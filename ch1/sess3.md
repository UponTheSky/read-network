# The Network Core
- the Internet's network core: packet switches and linkes connecting between the edge systems
- two fundamental approaches to moving data through a network of links and switches
  - **packet switching**
  - *circuit switching**

## 1. Packet Switching
- end systems exchange messages: control functions or some data
- the source breaks long messages into smaller chuncks(**packets**)

- packet switches: **routers**, **link-layer switches**
- a link with its full transmission rate(R bits/sec): packets are transmitted over this communication link at this rate

### Store-and-Forward Transmission
- most packet switches use **store-and-forward** transmission at the inputs to the links
  - the packet switch must receive the entire packet before it can begin to transmit the first bit of the packet onto the outbound link
  - why?: routers need to receive, store, and process the entire packet before forwarding

### Queuing Delays and Packet Loss
- each packet switch has multiple links attached to it
  - for each attached link, the packet switch has an **output buffer**(**output queue**) that stores packets that the router is about to send into that link
  - if an arriving packet needs to be sent through that link but if the link is busy with transmitting another packet, the arriving packet must wait in the output buffer

- so in addition to the *store-and-forward* delays, packets suffer output buffer **queuing delays** 
  - moreover, if the buffer is full, packet loss might occur

### Forwarding Tables and Routing Protocols
- how does the router determine which link it should forward the packet onto?
  - packet forwarding could be done in various ways, in various types of computer networks

- in the Internet, the source includes the destination's IP address in the packet's header
  - when a packet arrives at a router, the router examines a portion of the packet's destination address, and forwards the packet to an adjacent router
  - each router has a **forwarding table** that maps destination addresses(or portions) to that router's outbound links

- how do forwarding tables get set?: the Internet has a number of special **routing protocols** that are used to automatically set the forwarding tables

## 2. Circuit Switching
- in circuit switched networks, the resources needed along a path to provide for communication btw the end systems are *reserved* for the duration of the communication session btw the end systems
  - resource: buffers, link transmission rate, etc.
  - traditional telephone networks
  - **circuit**: such a reserved network connection btw end systems
  - transmission rate is reserved: the sender can transfer the data to the receiver at the guaranteed constant rate

- when two host wants to communicate, the network establishes a dedicated **end-to-end connection** between the two hosts

### Multiplexing in Circuit-Switched Networks
- how is a circut in a link implemented?

- **frequency division multiplexing**(FDM)
  - the frequency spectrum of a link is divided up among the connections established across the link
  - the link dedicates a frequency band to each connection for the duration of the connection
  - **bandwidth**: the width of a band (eg: 88MHz ~ 108MHz)

- **time division multiplexing**(TDM)
  - time is divided into frames of fixed duration, and each frame is divided into a fixed number of time slots
  - when the network establishes a connection across a link, the network dedicates one time slot in every frame to this connection

- downside of circuit switching
  - some dedicated circuits are idle during silent periods
  - establishing end-to-end circuits and reserving transmission capacity is complicated, requiring complex signaling SW to coordinate the operation of the switches

- transmission time is independent of the number of links

### Packet Switching vs Circuit Switching
- skim through this part
- currently the trend is packet switching

## 3. A Network of Networks
- the access ISPs are interconnected to form a large *network of networks*

- network structure 3
  - customer: access ISPs / provider: global transit ISPs
  - heirarchy of ISPs
    - access ISPs
    - regional ISPs(could be multiple levels)
    - global transit ISPs(tier-1)

- network structure 4
  - **points of presense(PoPs)**
    - exist at all levels but access ISPs
    - a group of one or more routers(at the same location) in the provider's network, where customer ISPs can connect into the provider ISP

  - **multi-home**: connecting to two or more provider ISPs
    - good for reliability
  
  - **peer**: two ISPs at the same level directly connect their networks together, so that all the traffic btw them passes over the direct connection rather through upstream intermediaries

  - **Internet Exchange Point**(IXP): a meeting point where multiple ISPs can peer together

- network structure 5
  - **content-provider networks**: a network constructed by a certain enterprise(e.g. Google)
  - all the data centers are privately interconnected, so that it can bypass the upper tiers of the Internet by peering with lower-tier ISPs