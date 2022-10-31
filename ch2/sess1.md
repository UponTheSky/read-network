# Principles of Network Applications
- application programs run on different *end systems*, and communicate with each other over the network
- e.g.) web application: browser program(user's host) - web server program(web server host)
- layered architecture of Internet network: you can't write application SW for network-core devices(routers, link-layer switches) 

## 1. Network Application Architectures
- **application architecture**
  - designed by the application developer
  - dictates how the application is structured over the various end systems
  - predominant architectural paradigms used in modern network applications: client-server / peer-to-perr

- **client-server**
  - *client* <-> *server*(always-on-host)
  - clients do not directly communicate with each other
  - the server has a fixed, well-known address(**IP** address): 
    - so a client can always contact the server, by sending a packet to the server's IP address
  - examples: web, ftp, telnet, email

  - it is hard for a single server host to manage all the requests from clients
    - **data center**: houses a number of hosts to create a powerful virtual server

- **P2P**
  - the application exploits direct communication btw hosts without or with minimal reliance on a server
  - peers: not owned by the service provider, but the machines controlled by users
  - **self scalability**: each peer responds to a request by distributing files to other peers
  - cost effective, but security / performance / reliability issuses

## 2. Processes Commnicating
- how processes running on different hosts(with potentially different OSs) communicate?
- creating, sending, and responding to **messages** across the network

### Client and Server Processes
- a network application consists of pairs of processes that send messages to each other over a network
- e.g.) web application: a client browser(labeled as **client**) <-> a web server process(labeld as **server**)
- client: the process that initiates the communication
- server: the process that waits to be contacted to begin the session

### The Interface Between the Process and the Computer Network
- **socket**: the interface btw the application layer and the transport layer within a host
  - the API btw the applicaiton and the network
  - a process sends messages into, and receives messages from, the network through a socket

- the application developer can only control the following parts on the transport layer
  - the choice of transport protocol
  - the ability to fix a few transport-layer parameters(max buffer, segment sizes )

### Addressing Processes
- how to identify a receiving process in the destination host?
  - we need 1)the address of the host and 2)an identifier that specifies the receiving process(receiving socket) in the host
  - 1)=> **IP address**
  - 2)=> **port number**: since a host could be running many network applications

## 3. Transport Services Available to Applications
- many networks provide more than one transport-layer protocol
- when you develop an application, you must choose one of the available transport-layer protocols
- four dimensions of protocol services

### Reliable Data Transfer
- guaranteeing that the data sent by one end of the application is delivered correctly and completely to the other end of the application
- that protocol provides **reliable data transfer**
- the sending process can trust the protocol
- opposite: **loss-tolerant** applications

### Throughput
- the available throughput can fluctuate over time: we need guaranteed available throughput at some specified rate
- **bandwidth-sensitive** applications
- opposite: **elastic** applications can make use of as much or as little throughput as happen to be possible

### Timing
- sent packets must arrive at the receiver's socket on time: important for interactive real-time applications

### Security
- a protocol can encrypt/decrypt data

## 4. Transport Services Provided by the Internet
- the Internet(and TCP/IP networks) provides two protocols: TCP, UDP

### TCP Services
- connection oriented
  - **handshaking procedure**: TCP has the client and server exchange transport layer control information, before the application-level messages begin to flow
  - this alerts the client and server to be prepared for exchanging packets
  - **TCP connection** btw the sockets: this simply means that we have completed a handshaking procedure 
  - **full-duplex**: the two processes can send messages to each other over the connection at the same time
  - when the application finishes sending messages, it must tear down the connection

- reliable data transfer service
  - no missing or duplicated bytes
  - congestion-control mechanism: throttles a sending process when the network is congested btw sender and receiver

### UDP Services
- lightweight, minimal services
- connectionless: no handshaking, unreliable data transfer service, no congestion control

### Services Not Provided by Internet Transport Protocols
- today's Internet can *often* provide satisfactory service to time sensitive applications, but it cannot provide any *timing or throughput guarantees*

## 5. Application-Layer Protocols
- **application-layer protocols**: defines how an application's processes pass messages to each other
  - the types of messages exchanged
  - the syntax of the various message types
  - the semantics of the fields
  - rules for determining when and how a process sends messages and responds to messages

- an application-layer protocol is only one piece of a network application 

## 6. Network Applications Covered in This Book
