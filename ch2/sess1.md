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

### Reliable Data Transfer

### Throughput

### Timing

### Security

## 4. Transport Services Provided by the Internet

### TCP Services

### UDP Services

### Services Not Provided by Internet Transport Protocols

## 5. Application-Layer Protocols

## 6. Network Applications Covered in This Book
