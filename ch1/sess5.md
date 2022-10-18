# Protocol Layers and Their Service Models

## 1. Layered Architecture
- a packet is shipped from host to destination host in the Internet
- each layer represents some functionality(service)
- why layer?: modularity(easy to change the implementation of the service provided by the layer)

### protocol layering
- network protocols are organized in layers(with SW and HW implementing such protocols)
- we are focusing on the services that a layer offers to the layer above(**service model**)
  - performs certain actions within that layer
  - uses the services of the layer directly below it

- a layer is implemented in SW, in HW or in a combination of the two
- a layer n protocol is distributed among the end systems, packet switches, and other components that make up the internet

- possible drawbacks
  - one layer may duplicate lower-layer functionality
  - functionality at one layer may need information that is present only in another layer: violates the goal of separation of layers

- **protocol stack**: the collection of the various layer protocols
  - application / transport / network / link / physical
  - ATNLP

### application layer
- where network applications and their application-layer protocols reside
- HTTP, SMTP, FTP, DNS
- distributed over multiple end systems
- **message**: a packet of information at the application layer

### transport layer
- transports application-layer messsages btw application endpoints
- TCP
  - provides a connection-oriented service to its applications
  - guaranteed delivery of application-layer messages to the destination, and flow control
  - breaks long messages into shorter segments, and provides a congestion-control mechanism
    - a source throttles its transmission rate when the network is congested
- UDP
  - provides a connectionless service to its applications
  - no reliability, no flow control, no congestion control

- **segment**: a packet at the transport-layer

### netwokr layer
- **datagram**: a packet at the network layer
- a source host: passes a *segment*(from its transport layer) and a destination address to the network layer
- the network layer: then provides the service of delivering the segment to the transport layer in the destination host

- IP
  - defines the field in the diagram, and how the end systems and routers act on these fields
  - there is only one IP protocol
  - all the internet components having a network layer must run the IP protocol

- routing protocols
  - determine the routers that datagrams take between source and destination
  - the Internet has many routing protocols

### link layer
- to move a packet from one node(host or router) to the next node in the route, the network layer relies on the services of the link layer
  - at each node, the network layer passes the datagram down to the link layer, which delivers the datagram to the next node along the route
  - at this next node, the link layer passes the datagram up to the network layer

- the services provided by the link layer depend on the specific link-layer protocol that is employed over the link
  - protocol examples: Ethernet, WiFi, DOCSIS
  - a datagram may be handled by different link-layer protocols at different links along its route

- **frame**: a packet at the link layer

### physical layer
- moves the individual bits within a frame from one node to the next
- protocols depending on: link, transmission medium of the link

## 2. Encapsulation
- routers, link-layer switches: not implementing all of the layers in the protocol stack
  - typically only the bottom layers
- hosts implement all five layers

- **encapsulation** of packets: header fields + **payload field**(a packet from the layer above)
  - message + transport-layer header = **transport-layer segment**: meta info, erorr-detection bits
  - segment + network-layer header = **network-layer datagram**: source, destination addresses
  - datagram + link-layer header=  **link-layer frame**
