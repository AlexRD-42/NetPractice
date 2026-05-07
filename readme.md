This project has been created as part of the 42 curriculum by <adeimlin>

# Description
• A “Description” section that clearly presents the project, including its goal and a
brief overview.
---


# Instructions
• An “Instructions” section containing any relevant information about compilation,
installation, and/or execution.
• The Instructions section must explain how to run the training interface (e.g.,
using run.sh), how to export configurations, and submission requirements.
---


# Resources
• A “Resources” section listing classic references related to the topic (documen-
tation, articles, tutorials, etc.), as well as a description of how AI was used —
specifying for which tasks and which parts of the project.
• The Resources section must explicitly mention the networking concepts studied,
such as TCP/IP addressing, subnet masks, default gateways, routers and
switches, OSI layers, etc.
---

## Internet Protocols
Internet protocols are standards that define communication between computers (networking). To start, we can define the main categories:
* Physical, Network, Transport and Application

Within these categories, depending on the model chosen there are subcategories within these main categories. The two main models I'll study here are the TCP/IP Cisco model, which differentiates the physical layer from data link, and the OSI model which further differentiates the Application layer in Presentation -> Session -> Application.

This results in seven possible layers:
Physical -> Data Link -> Network -> Transport -> Session -> Presentation -> Application

Data is represented through different abstractions as you go up and down the layers of a network stack. A generic, layer-independent term for this data is a Protocol Data Unit (PDU).
This protocol data unit has a payload (the data itself) and metadata (information about the payload, things like port or IP addresses). This metadata is encapsulated in the form of headers (prepended) and trailers (appended).
Interpreting this metadata (process of receiving a packet) is called decapsulation, and creating this metadata (process of sending a packet) is called encapsulation.

### Transport Layer: Layer 4
Starting at the application layer going to the transport layer, a PDU (Protocol Data Unit) is created. A PDU is composed of protocol-specific metadata (like from, to, host, user-agent, domain name, query type, etc) and user data. 

| **OSI Layer** | **Name of PDU**                        | **Example Protocol**   | **Control Info (Headers)**    |
| ------------- | -------------------------------------- | ---------------------- | ----------------------------- |
| Application   | **Message**                            | HTTP, DNS, SMTP        | e.g., HTTP headers            |
| Transport     | **Segment** (TCP) / **Datagram** (UDP) | TCP, UDP               | e.g., ports, sequence numbers |
| Network       | **Packet**                             | IP                     | e.g., IP addresses, TTL       |
| Data Link     | **Frame**                              | Ethernet, PPP          | e.g., MAC addresses, FCS      |
| Physical      | **Bits**                               | Ethernet (cable level) | No headers — just raw bits    |

The first task of the transport layer is segmentation: to split the PDU received from the application layer into smaller pieces called segments (for TCP) or datagrams (for UDP).

Segmentation is done for security, performance and multiplexing (multiple communications to occur at the same time). Each segment includes source and destination port numbers to identify what application is making the request and what service is going to receive them.
Applications communicate with each other using the transport layer. One acts as a client (sending a request), and the other acts as a server (receiving and responding).

TCP vs UDP

### Network Layer: Layer 3
A network is defined as two or more devices connected together, so here the IP protocol is used to identify the devices on the network. The sender and the receiver's IP address goes into the packet.

### Data Link Layer: Layer 2
This is essentially your intra-network, meaning it operates within a single local network segment, connected by Ethernet or PPP. Here the PDU is described as a frame, and it contains things like MAC addresses.
