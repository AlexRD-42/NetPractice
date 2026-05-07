## Networking Protocols
Networking protocols are standards that define communication between computers (networking). This communication is done through several layers, of which there are several models that describe them in differing levels of detail.

These are the main models:

```text
  TCP/IP             CISCO               OSI
─────────────────────────────────────────────────────
Application	─────▶Application ┬────▶Application
                               ├────▶Presentation
                               └────▶Session

Transport ───────▶Transport ───────▶Transport

Network ─────────▶Network ─────────▶Network

Physical ┬───────▶Data Link ───────▶Data Link
         └───────▶Physical ────────▶Physical
```

The layer indexing goes from 1 to 7, with 7 being the Application layer and as you go lower, you get closer to Physical. When a layer is referred to by index, it generally assumes the OSI model layout.

Data is represented through different abstractions as you go up and down the layers of a network stack. 

Going up the stack is the process of sending a packet, and is called encapsulation. Encapsulation is the process of encoding metadata so that the receiving layer knows how to propagate the data forward, and possibly encrypt the data so it can't be read by someone other than the intended target (depends on which layer)

Going down the stack is the process of receiving a packet, and is called decapsulation, which is basically the reverse of Encapsulation, where it interprets the metadata.

Layers each have a unique name to the data they process. A generic, layer-independent term for this data is a Service Data Unit (SDU). Each layer then adds their own metadata to this SDU, forming a Protocol Data Unit (PDU).

This protocol data unit has a payload (the data itself, SDU) and metadata (information about the payload, things like port or IP addresses). This PDU is encapsulated in the form of headers and trailers, like so:

PDU = headers | SDU | trailers

And an SDU is nothing more than the previous layers PDU, so for example, HTTP → TCP → IP → Ethernet:

| **Layer** | **Header** | **SDU** | **Trailers** |
| -- | -- | -- | -- |
TCP			| TCP header | HTTP message | --
IP			| IP header | TCP header, HTTP message  | --
Ethernet	| Ethernet header | IP header , TCP header , HTTP message | Ethernet trailer

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

There are two internet protocols, IPv4 (32-bits) and IPv6 (128-bits)

IPv4: 



### Data Link Layer: Layer 2
This is essentially your intra-network, meaning it operates within a single local network segment, connected by Ethernet or PPP. Here the PDU is described as a frame, and it contains things like MAC addresses.



### Examples:

