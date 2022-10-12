# What is the Internet?

## 1. A Nuts-and-Bolts Description
- **internet**: a computer network that interconnects billions of computing devices over the world
- what are the components?

  - **host**: a device connected to the internet = end systems
  - end systems are connected by a network of **communication links** and **packet switches**
    - different(physical) links can transmit data at different rates
    - the sending host segments the data and adds header bytes to each segment = **packets**
      - these packets are assembled into the original data by the receiving host

  - a packet switch
    - takes a packet arriving on one of its incoming communication linkes, and forwards that packet on one of its outgoing communication links
    - **router**: used in the network core
    - **link-layer switch**: used in access networkss

  - **route**/**path**: the sequence of communication links and packet switches traversed by a packet from end to end

  - analogies
    - packet = truck
    - communication link = highways and roads
    - packet switch = intersection
    - end system = building

  - ISP(internet service provider): end systems can access to the internet through ISPs
    - each ISP itself is a network of packet switches and communicational links
    - cable modem, DSL, high-speed local area network access, mobile wireless access
    - providing Internet access to content providers: connecting servers directly to the Internet

    - lower tier vs high tier
    - each ISP is managed independently, runs the IP protocol, and conforms to certain naming and address conventions

- **protocols**
  - **TCP**(transmission control protocol)
  - **IP**(internet protocol): specifies the format of the packets that are sent and received among routers and end systems
  - **TCP/IP**: all the internet protocols collectively referred as 

- internet standards: **RFCs(requests for comments)**

## 2. A Service Description
- **internet**: an infrastructure that provides services to applications
  - **distributed applications**: applications involved in interconnected system of exchanging data
  - an Internet applciation run on end systems(not run in the packet switches in the network core)

- question: how does one program on one end system instruct the Internet to deliver data to another program
running on another end system?
  - **socket interface**: specification of how a program running on one end system asks the Internet infrastructure to deliver data to a specific destination program running on another end system
  - a socket interface is provided to applications by the end system

- the Internet provides multiple services to applications - you need to choose one of them

## 3. What is a Protocol?

### network protocols
- all activities in the Internet that involves two or more communicating remote entities is governed by a protocol
  - HW protocols for the bits passing through NIC(network interface card)
  - congenstion-control protocols, router protocols

- then what is exactly a protocol?
  - the format of messages
  - the order of messages exchanged
  - actions taken on the transmission and/or receipt of a message or any other event
