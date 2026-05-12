*This project has been created as part of the 42 curriculum by adeimlin*

# NetPractice

## Description

NetPractice is a 42 project designed to introduce the basics of computer networking through practical exercises.

The goal of the project is to fix small simulated networks by configuring the correct IP addresses, subnet masks, routes, and gateways. Each level presents a broken network diagram, and the objective is to make communication between the required devices work properly.

This project focuses on understanding how devices communicate inside and between networks. It covers TCP/IP addressing, subnet masks, default gateways, routers, switches, routing tables, and the role of the different OSI layers in network communication.

There are 10 levels to complete. For each level, the correct configuration must be exported and submitted in the Git repository.

## Instructions

### Running the training interface

1. Download the file attached to the NetPractice project page.
2. Extract the archive into a folder of your choice.
3. Open a terminal in that folder.
4. Run the provided script:

```sh
./run.sh
```

If the script does not have execution rights, run:

```sh
chmod +x run.sh
./run.sh
```

The script starts a local web server and opens the NetPractice interface in a web browser.

If `run.sh` does not work, the interface can also be started manually with:

```sh
python3 -m http.server 49242
```

Then open the following URL in a browser:

```txt
http://localhost:49242
```

Depending on the browser, it may also be possible to open the `index.html` file directly, but using the local server is the recommended method.

### Solving the levels

1. Enter the login `adeimlin` in the training interface.
2. Start level 1.
3. Read the objective displayed at the top of the page.
4. Modify the editable network fields until the configuration is correct.
5. Use the `Check again` button to test the configuration.
6. Use the logs at the bottom of the page to understand errors such as:
   - missing gateway;
   - invalid IP address;
   - wrong subnet mask;
   - destination not reachable;
   - packet not going through the correct route.
7. Once the level is correct, export the configuration before moving to the next level.

### Exporting configurations

For each completed level:

1. Click `Get my config`.
2. Save the exported configuration file.
3. Keep the generated file for submission.
4. Repeat this for all 10 levels.

### Submission requirements

The repository must contain:

- this `README.md` file at the root of the repository;
- 10 exported configuration files, one for each completed level;
- all exported configuration files placed at the root of the repository.

Only the files present in the Git repository will be evaluated.

During the defense, three random levels must be solved again within a limited time. External tools are not allowed during the evaluation. A simple calculator such as `bc` is tolerated.

## Networking concepts studied

This project helped me study and apply the following networking concepts:

### TCP/IP addressing

Each device in a network needs an IP address to identify it. In NetPractice, incorrect or incompatible addresses often prevent packets from reaching their destination.

### Subnet masks

A subnet mask defines which part of an IP address represents the network and which part represents the host.

For example:

```txt
192.168.1.10/24
```

means:

- network part: `192.168.1`
- host part: `10`
- subnet mask: `255.255.255.0`

Understanding subnet masks is necessary to know whether two devices are on the same network or whether they need a router to communicate.

### Default gateways

A default gateway is the router address used when a device needs to send packets outside its own local network.

If a host tries to reach an address that is not in its subnet, it sends the packet to its configured gateway.

### Routers

Routers connect different networks together. They forward packets between networks based on routing information.

In NetPractice, routers often need several interfaces, each belonging to a different subnet.

### Switches

Switches connect devices inside the same local network. Unlike routers, they do not route packets between different IP networks.

### OSI layers

I studied the OSI model to better understand what happens at each level of communication:

| OSI Layer | PDU name | Example protocols / data |
|---|---|---|
| Application | Message | HTTP, DNS, SMTP |
| Transport | Segment / Datagram | TCP, UDP |
| Network | Packet | IP |
| Data Link | Frame | Ethernet, PPP |
| Physical | Bits | Electrical or optical signals |

The project mainly focuses on the Network layer, where IP addressing and routing happen, but it also requires understanding how this layer depends on lower layers such as Data Link and Physical.

### Encapsulation and decapsulation

Data is wrapped with protocol-specific information as it moves down the network stack. This is called encapsulation.

When data is received, each layer reads and removes its corresponding metadata. This is called decapsulation.

Examples of metadata include:

- source and destination ports at the Transport layer;
- source and destination IP addresses at the Network layer;
- MAC addresses at the Data Link layer.

## Resources

The following resources were useful for this project:

- 42 NetPractice subject.
- Notes from the NetPractice training interface.
- RFC 791 — Internet Protocol.
- RFC 950 — Internet Standard Subnetting Procedure.
- Cisco networking documentation and introductory CCNA material.
- Articles and tutorials about:
  - TCP/IP addressing;
  - subnet masks and CIDR notation;
  - routing tables;
  - default gateways;
  - routers and switches;
  - OSI and TCP/IP models;
  - packet encapsulation and decapsulation.

The networking concepts studied include TCP/IP addressing, subnet masks, default gateways, routers, switches, OSI layers, TCP and UDP transport concepts, routing between networks, and local network communication.

### AI usage

AI was used to help structure and rewrite this README.

More specifically, AI was used for:

- organizing the `Description`, `Instructions`, and `Resources` sections;
- improving the wording of my existing notes;
- checking that the README matched the project requirements;