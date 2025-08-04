# Computer Networks

### OSI vs TCP/IP Model

The **OSI (Open Systems Interconnection)** and **TCP/IP (Transmission Control Protocol/Internet Protocol)** models are conceptual frameworks that describe the functions of a networking system.

**OSI Model (7 Layers):**

1.  **Physical Layer:**
    * **Function:** Transmits raw bit streams over a physical medium.
    * **PDU (Protocol Data Unit):** Bit.
    * **Protocols/Devices:** Ethernet cable, Wi-Fi, hubs.
2.  **Data Link Layer:**
    * **Function:** Provides error-free transfer of data frames from one node to another over the physical layer. Handles physical addressing (MAC addresses).
    * **PDU:** Frame.
    * **Protocols/Devices:** Ethernet, switches, MAC addresses.
3.  **Network Layer:**
    * **Function:** Handles logical addressing (IP addresses) and routing of data packets from source to destination across different networks.
    * **PDU:** Packet.
    * **Protocols/Devices:** IP, routers.
4.  **Transport Layer:**
    * **Function:** Manages end-to-end communication, providing reliable or unreliable data transfer. It segments data and reassembles it at the destination.
    * **PDU:** Segment (TCP) or Datagram (UDP).
    * **Protocols/Devices:** TCP, UDP.
5.  **Session Layer:**
    * **Function:** Establishes, manages, and terminates sessions between applications. It provides synchronization and checkpointing.
    * **PDU:** Data.
    * **Protocols/Devices:** NetBIOS, RPC.
6.  **Presentation Layer:**
    * **Function:** Handles data formatting, compression, and encryption to ensure that data is in a format that the receiving application can understand.
    * **PDU:** Data.
    * **Protocols/Devices:** JPEG, GIF, SSL/TLS.
7.  **Application Layer:**
    * **Function:** The layer closest to the end user. It provides an interface for network applications to access network services.
    * **PDU:** Data.
    * **Protocols/Devices:** HTTP, FTP, SMTP, DNS.

**TCP/IP Model (4 Layers):**

1.  **Network Access Layer (or Link Layer):**
    * **Function:** Combines the functions of the OSI Physical and Data Link layers. Handles hardware details of interfacing with the network.
    * **PDU:** Frame.
    * **Protocols:** Ethernet, Wi-Fi.
2.  **Internet Layer:**
    * **Function:** Corresponds to the OSI Network layer. Handles logical addressing and routing of packets across the internet.
    * **PDU:** Packet.
    * **Protocols:** IP, ARP.
3.  **Transport Layer:**
    * **Function:** Same as the OSI Transport layer. Provides end-to-end communication services.
    * **PDU:** Segment or Datagram.
    * **Protocols:** TCP, UDP.
4.  **Application Layer:**
    * **Function:** Combines the functions of the OSI Session, Presentation, and Application layers. Contains protocols for specific user applications.
    * **PDU:** Data.
    * **Protocols:** HTTP, FTP, SMTP, DNS.

The TCP/IP model is a more practical and widely used model in the real world, while the OSI model is a more theoretical and detailed reference.

---

### What happens when you type a URL in a browser?

This is a simplified, step-by-step overview of the process:

1.  **DNS Lookup:** The browser checks its cache for the IP address of the domain name (e.g., `www.google.com`). If not found, it queries a DNS server to resolve the domain name to an IP address.
2.  **TCP/IP Connection:** The browser opens a TCP socket connection to the web server's IP address on the default HTTP port (port 80) or HTTPS port (port 443). This involves the **TCP 3-way handshake**.
3.  **HTTP Request:** The browser sends an HTTP request to the web server, which includes:
    * The type of request (`GET` or `POST`).
    * The path of the resource (`/`).
    * The host name (`www.google.com`).
    * Other headers (e.g., user-agent, cookies).
4.  **Server Processing:** The web server receives the request, processes it, and retrieves the requested resource (e.g., an HTML file).
5.  **HTTP Response:** The server sends an HTTP response back to the browser, which includes:
    * A status code (e.g., `200 OK`).
    * Headers (e.g., content-type).
    * The body of the response (e.g., the HTML content).
6.  **Browser Rendering:** The browser receives the HTML content and begins to parse and render it. It may find other resources to load (e.g., CSS files, JavaScript, images) and will repeat the process (steps 1-5) for each of them.
7.  **Connection Closure:** Once all resources are loaded, the browser closes the TCP connection.

---

### What is DNS and how does it work?

**DNS (Domain Name System)** is a hierarchical and decentralized naming system for computers, services, or any resource connected to the Internet or a private network. It translates human-readable domain names (e.g., `www.example.com`) into machine-readable IP addresses (e.g., `93.184.216.34`).

**How it works:**

1.  **User Request:** A user enters a domain name into their browser.
2.  **Recursive DNS Server:** The request is sent to a **recursive DNS server** (usually provided by the ISP). This server is responsible for finding the IP address. It first checks its own cache. If it has the IP address, it returns it immediately.
3.  **Root Server:** If the IP address isn't in the cache, the recursive server sends a request to one of the **root name servers**. The root server doesn't know the IP address, but it knows which server is responsible for the top-level domain (TLD), like `.com`. It returns the IP address of the `.com` TLD server.
4.  **TLD Server:** The recursive server then sends a request to the `.com` TLD server. This server knows which server is responsible for the specific domain (`example.com`). It returns the IP address of the **authoritative name server** for `example.com`.
5.  **Authoritative Name Server:** The recursive server sends a request to the authoritative name server. This server holds the actual DNS records for the domain. It finally returns the IP address of `www.example.com`.
6.  **Response to User:** The recursive server caches this IP address and returns it to the user's browser, which can now connect to the website.

---

### TCP vs UDP – Differences and Use Cases

TCP and UDP are the two main protocols in the Transport Layer of the TCP/IP model.

| Feature | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
| :--- | :--- | :--- |
| **Connection** | Connection-oriented; establishes a connection before sending data. | Connectionless; sends data without establishing a connection. |
| **Reliability** | Reliable; guarantees delivery of data. Re-transmits lost packets. | Unreliable; no guarantee of delivery or order. No re-transmission. |
| **Order** | Guarantees that packets are delivered in the correct order. | Does not guarantee order. Packets may arrive out of order. |
| **Speed** | Slower due to overhead of connection setup, error checking, and acknowledgment. | Faster and more lightweight due to less overhead. |
| **Header Size** | Larger (20 bytes) | Smaller (8 bytes) |
| **Flow Control**| Yes; manages the rate of data transfer to prevent the receiver from being overwhelmed. | No. |
| **Congestion Control**| Yes; reduces the rate of data transfer when the network is congested. | No. |

**Use Cases:**

* **TCP:** Used when data integrity and reliability are paramount.
    * **Examples:** Web Browse (HTTP/HTTPS), email (SMTP/IMAP), file transfer (FTP), and secure shell (SSH).
* **UDP:** Used when speed is more important than reliability.
    * **Examples:** Streaming media (video/audio), online gaming, Voice over IP (VoIP), and DNS lookups.

---

### What is IP? IPv4 vs IPv6?

**IP (Internet Protocol)** is the main protocol in the Internet Layer of the TCP/IP model. It is responsible for logical addressing and routing packets of data from a source host to a destination host across networks. Every device on a network that uses IP is assigned a unique IP address.

**IPv4 vs IPv6:**

| Feature | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Address Size** | 32-bit | 128-bit |
| **Address Format** | Four decimal numbers separated by dots (e.g., `192.168.1.1`). | Eight groups of four hexadecimal digits separated by colons (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`). |
| **Address Space**| $2^{32}$ (approx. 4.3 billion) addresses. Critically scarce. | $2^{128}$ (approx. $3.4 \times 10^{38}$) addresses. Vastly larger. |
| **Header** | Larger and more complex (20-60 bytes). | Simpler and more efficient (40 bytes), but with optional extension headers. |
| **Security** | Security features (IPsec) were an add-on and not mandatory. | IPsec is built into the protocol and is mandatory for full IPv6 compliance. |
| **Configuration**| Manual or DHCP required for configuration. | Can be configured automatically using stateless address auto-configuration (SLAAC). |
| **Checksum** | Header checksum is included. | No header checksum; transport layer protocols handle error checking. |

IPv6 was developed to replace IPv4 primarily because of the exhaustion of IPv4 addresses. It also offers other improvements like enhanced security, better routing efficiency, and auto-configuration capabilities.

---

### What is ARP and how does it work?

**ARP (Address Resolution Protocol)** is a protocol used in the Internet Layer (or Network Layer) to map an IP address to a physical MAC address. It's a crucial component for devices to communicate on a local network.

**How it works:**

1.  A device (Host A) wants to send an IP packet to another device (Host B) on the same local network, but it only knows Host B's IP address. It doesn't know the MAC address.
2.  Host A first checks its **ARP cache** (a local table of IP-to-MAC address mappings). If the mapping for Host B is found, it uses that.
3.  If the mapping is not in the cache, Host A sends an **ARP request** as a broadcast message to all devices on the local network. The request says, "Who has the IP address `192.168.1.2`? Please tell `192.168.1.1`." The request includes Host A's own IP and MAC address.
4.  All devices on the network receive the broadcast. They check if the IP address in the request matches their own. Only Host B finds a match.
5.  Host B sends a unicast **ARP reply** directly back to Host A, saying, "I am `192.168.1.2`, and my MAC address is `AA-BB-CC-DD-EE-FF`."
6.  Host A receives the reply, adds the IP-to-MAC address mapping to its ARP cache, and can now send the IP packet directly to Host B's MAC address.

---

### What is a MAC address?

A **MAC (Media Access Control) address** is a physical address that uniquely identifies a network interface controller (NIC) on a network. It is assigned by the manufacturer and is a globally unique identifier.

* **Format:** A 48-bit (6-byte) address, typically represented as a series of 12 hexadecimal digits (e.g., `00:1A:2B:3C:4D:5E`). The first six digits identify the manufacturer, and the last six digits are the unique serial number of the NIC.
* **Layer:** It operates at the **Data Link Layer** of the OSI model.
* **Function:** It is used for local communication within a network segment (LAN). When a device wants to send a frame to another device on the same LAN, it uses the destination's MAC address.
* **Immutability:** MAC addresses are "burned" into the hardware and are typically considered to be permanent and unchangeable, though they can be spoofed in software.

---

### Explain 3-way Handshake in TCP

The **TCP 3-way handshake** is the process used by the TCP protocol to establish a reliable connection between a client and a server. It ensures that both sides are ready to send and receive data before the actual data transfer begins.

The three steps are:

1.  **SYN (Synchronize):** The client sends a `SYN` packet to the server. This packet contains a random sequence number and a request to establish a connection.
    * **Client State:** `SYN_SENT`.
2.  **SYN-ACK (Synchronize-Acknowledge):** The server receives the `SYN` packet and, if it accepts the connection, sends a `SYN-ACK` packet back to the client. This packet contains:
    * An acknowledgment number, which is the client's sequence number plus 1.
    * The server's own random sequence number.
    * **Server State:** `SYN_RECEIVED`.
3.  **ACK (Acknowledge):** The client receives the `SYN-ACK` packet and sends an `ACK` packet back to the server. This packet contains an acknowledgment number, which is the server's sequence number plus 1. The connection is now established, and data transfer can begin.
    * **Client State:** `ESTABLISHED`.
    * **Server State:** `ESTABLISHED`.

This process ensures that both the client and server know that the other party is ready and that the initial sequence numbers are synchronized, which is essential for reliable data transfer.

---

### What are Ports? Why are they needed?

A **port** is a number (a 16-bit integer) assigned to a specific process or application running on a computer. It is used in conjunction with an IP address to uniquely identify a specific application on a specific device on the internet.

* **Role:** While an IP address identifies the *host* (the computer), the port number identifies the *application* or *service* on that host.
* **Need:** When a computer receives a packet, the IP address tells it which machine the packet is for. The port number tells the OS which application on that machine should receive the packet. Without ports, the OS wouldn't know whether to give an incoming packet to the web server, the email client, or the game server.
* **Port Numbers:** Ports are numbered from 0 to 65535.
    * **Well-known ports (0-1023):** Reserved for common services (e.g., HTTP is port 80, FTP is port 21, SSH is port 22, HTTPS is port 443).
    * **Registered ports (1024-49151):** Assigned to specific applications by the IANA.
    * **Dynamic/Private ports (49152-65535):** Can be used by clients for temporary connections.

---

### What is NAT? Types of NAT?

**NAT (Network Address Translation)** is a method used by routers to modify network address information (IP addresses) in the header of IP packets while they are in transit across a traffic routing device. It allows a single public IP address to be shared by multiple devices on a private network, addressing the scarcity of IPv4 addresses.

**How it works:** A router with a single public IP address is connected to the internet. All devices on the private network have private IP addresses. When a device from the private network wants to access the internet, the router's NAT function replaces the device's private IP address with its own public IP address in the packet header. When the response comes back, the router translates the public IP address back to the correct private IP address, using a translation table it maintains.

**Types of NAT:**

1.  **Static NAT:**
    * **Principle:** A one-to-one mapping between a private IP address and a public IP address. Every private IP has a dedicated public IP.
    * **Use Case:** For a server on a private network that needs to be accessible from the internet.

2.  **Dynamic NAT:**
    * **Principle:** Maps private IP addresses to a pool of public IP addresses. When a device requests to access the internet, it is assigned the next available public IP from the pool.
    * **Use Case:** In organizations with a fixed number of public IP addresses and a dynamic number of devices that need internet access.

3.  **Port Address Translation (PAT) / NAT Overload:**
    * **Principle:** This is the most common type of NAT. It maps multiple private IP addresses to a single public IP address by using different **port numbers**. The router keeps a translation table that maps the private IP and port number to the public IP and a unique port number.
    * **Use Case:** This is what most home and small office routers use to allow many devices to share a single public IP address.

NAT is a key technology for the continued use of IPv4, as it helps to conserve the limited number of available public IP addresses.

### What is DHCP? How does it assign IPs?

**DHCP (Dynamic Host Configuration Protocol)** is a network protocol used to automatically assign IP addresses and other network configuration parameters to devices on a network. Without DHCP, a network administrator would have to manually configure each device, which is time-consuming and prone to errors.

**How it assigns IPs (DORA process):**

1.  **Discover:** When a client device (e.g., a laptop) boots up, it doesn't have an IP address. It broadcasts a **DHCP Discover** message on the network to find any available DHCP servers.
2.  **Offer:** Any DHCP server that receives the Discover message and has an available IP address sends a **DHCP Offer** message back to the client. This message contains a proposed IP address, subnet mask, default gateway, and DNS server information.
3.  **Request:** The client receives one or more Offer messages. It chooses one offer and broadcasts a **DHCP Request** message, formally requesting the IP address from the chosen server. This also informs the other DHCP servers that their offers were not accepted.
4.  **Acknowledge:** The chosen DHCP server receives the Request message and sends a final **DHCP Acknowledge (ACK)** message to the client. This message confirms the IP address lease and all other configuration details. The client can now use the assigned IP address to communicate on the network.

The IP address is leased for a specific period. The client must renew the lease with the DHCP server before it expires.

---

### What is Subnetting?

**Subnetting** is the practice of dividing a single large network into smaller, more manageable subnetworks (subnets). This is done by borrowing bits from the host part of an IP address and using them for the network part, which is identified by a **subnet mask**.

**Why is it used?**

* **Efficiency:** It reduces network traffic by confining broadcasts to a smaller subnet.
* **Performance:** Routers can route traffic more efficiently because they only need to know how to reach the subnets, not every individual host.
* **Security:** It provides a way to isolate network segments, allowing for better security control.
* **Organization:** It helps to logically organize a network based on departments, locations, or functions.

For example, an IP address `192.168.1.0/24` (where `/24` is the CIDR notation) has a subnet mask of `255.255.255.0`. The first 24 bits are for the network part, and the last 8 bits are for the host part. Subnetting would involve changing the subnet mask to use more bits for the network, thus creating more, smaller subnets.

---

### What is CIDR notation?

**CIDR (Classless Inter-Domain Routing)** notation is a compact way to represent an IP address and its associated routing prefix. It was introduced to replace the old class-based system (A, B, C) and to help slow down the exhaustion of IPv4 addresses.

* **Format:** It is written as an IP address followed by a slash (`/`) and a number. The number is the **subnet mask length** (also known as the prefix length).
    * **Example:** `192.168.1.0/24`
        * `192.168.1.0` is the network address.
        * `24` indicates that the first 24 bits of the IP address are the network part, and the remaining 8 bits are the host part. This is equivalent to a subnet mask of `255.255.255.0`.

* **Key Advantage:** CIDR allows for more flexible subnetting. Instead of being restricted to fixed subnet masks, you can have subnets of varying sizes, which helps to conserve IP addresses.

---

### What is a Socket?

A **socket** is an endpoint for communication between two programs over a network. It is a software construct that acts as a handle or a file descriptor for network communication. A socket is an essential component of a network connection.

* **Key Information:** A socket is defined by a combination of the IP address of the host and a port number.
* **Client-Server Model:** In a typical client-server application:
    * The **server** creates a **listening socket** that is bound to a specific IP address and port number. It then listens for incoming connections.
    * The **client** creates a socket and connects to the server's socket using the server's IP address and port number.
* **Communication:** Once the connection is established, data can be sent and received through the sockets using standard read/write operations, similar to how data is handled with files.
* **Types:** There are two main types of sockets, corresponding to the transport layer protocols:
    * **Stream Sockets (TCP):** Provides a reliable, connection-oriented service.
    * **Datagram Sockets (UDP):** Provides an unreliable, connectionless service.

---

### Difference between HTTP and HTTPS

* **HTTP (Hypertext Transfer Protocol):**
    * **Security:** Data is transmitted in plaintext. It is not encrypted, making it vulnerable to eavesdropping and man-in-the-middle attacks.
    * **Protocol:** Uses TCP on port 80 by default.
    * **Layer:** Operates at the Application Layer.
* **HTTPS (Hypertext Transfer Protocol Secure):**
    * **Security:** Uses an underlying encryption protocol, either **SSL (Secure Sockets Layer)** or its successor, **TLS (Transport Layer Security)**. Data is encrypted before being sent and decrypted upon arrival.
    * **Protocol:** HTTP is layered on top of TLS/SSL, using TCP on port 443 by default.
    * **Authentication:** Requires a digital certificate from a Certificate Authority (CA) to verify the identity of the web server. This ensures that you are communicating with the genuine website.
    * **Indicator:** Browsers display a padlock icon and the "https://" prefix in the address bar to indicate a secure connection.

The primary and most significant difference is the **security** provided by HTTPS, which is essential for e-commerce, banking, and any website that handles sensitive user data.

---

### What are GET, POST, PUT, DELETE in HTTP?

These are the most common **HTTP methods** (or verbs), which define the type of action a client wants to perform on a resource identified by a URL.

* **GET:**
    * **Purpose:** To retrieve data from a server. It's the most common method.
    * **Characteristics:**
        * Data is sent in the URL's query string.
        * Idempotent: Multiple identical requests have the same effect as a single request.
        * Can be cached and bookmarked.
        * Should not be used for sensitive data.
* **POST:**
    * **Purpose:** To submit data to be processed to a specific resource (e.g., creating a new resource).
    * **Characteristics:**
        * Data is sent in the body of the HTTP request.
        * Not idempotent: Sending the same request multiple times can create multiple resources.
        * Cannot be easily cached or bookmarked.
        * Used for submitting forms, uploading files, etc.
* **PUT:**
    * **Purpose:** To update an existing resource or create a new resource if it doesn't exist at a specific URL.
    * **Characteristics:**
        * Idempotent: Sending the same `PUT` request multiple times will have the same effect.
        * The request body contains the complete, updated representation of the resource.
* **DELETE:**
    * **Purpose:** To delete a specific resource at a given URL.
    * **Characteristics:**
        * Idempotent: Deleting a resource that has already been deleted will not change the state of the system (it's still deleted).
        * Should be used with caution, as it permanently removes a resource.

---

### What is Latency, Bandwidth, and Throughput?

These are key metrics used to measure the performance of a network.

* **Latency:**
    * **Definition:** The time delay it takes for a single bit of data to travel from its source to its destination. It's a measure of time.
    * **Analogy:** The time it takes for a car to travel from one city to another.
    * **Measurement:** Milliseconds (ms).
    * **Factors:** Physical distance, network congestion, number of hops.
* **Bandwidth:**
    * **Definition:** The maximum amount of data that can be transmitted over a communication channel in a given amount of time. It's a measure of capacity.
    * **Analogy:** The width of a highway (e.g., a 2-lane vs. a 6-lane highway).
    * **Measurement:** Bits per second (bps), megabits per second (Mbps).
    * **Factors:** The physical medium of the network.
* **Throughput:**
    * **Definition:** The actual amount of data successfully transferred over a communication channel in a given amount of time. It's a measure of the effective rate.
    * **Analogy:** The actual number of cars that travel from one city to another on the highway.
    * **Measurement:** Bits per second (bps), Mbps.
    * **Relationship:** Throughput is always less than or equal to bandwidth. It's affected by latency, network errors, and congestion.

---

### Explain CSMA/CD and CSMA/CA

These are two different protocols used at the Data Link Layer to handle collisions on a shared network medium.

* **CSMA/CD (Carrier Sense Multiple Access with Collision Detection):**
    * **Protocol:** Used in wired Ethernet networks.
    * **Process:**
        1.  **Carrier Sense:** A device checks if the medium is busy before transmitting.
        2.  **Multiple Access:** If the medium is free, the device transmits its data. Multiple devices can attempt to transmit at the same time.
        3.  **Collision Detection:** While transmitting, the device listens to the medium. If it detects a collision (i.e., another device is also transmitting), it immediately stops transmission.
        4.  **Jam Signal:** The device sends a "jam" signal to notify all other devices of the collision.
        5.  **Backoff:** All devices wait for a random amount of time (a backoff period) before attempting to re-transmit.
    * **Limitation:** It is not effective for wireless networks because it's difficult for a device to "listen" for collisions while it's transmitting.

* **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance):**
    * **Protocol:** Used in wireless networks (e.g., Wi-Fi).
    * **Process:**
        1.  **Carrier Sense:** A device listens to the medium to check if it's busy.
        2.  **Request-to-Send (RTS)/Clear-to-Send (CTS):** If the medium is free, the device sends a small `RTS` frame to the access point. The access point responds with a `CTS` frame, which tells the sending device that it can transmit and tells all other devices to hold off.
        3.  **Transmission:** The device transmits its data.
        4.  **Acknowledgment:** The receiving device sends an acknowledgment (`ACK`) frame upon successful reception.
        5.  **Backoff:** If an `ACK` is not received, the sender assumes a collision occurred and enters a backoff period before attempting to re-transmit.
    * **Note:** The RTS/CTS mechanism is optional but helps to avoid the "hidden node problem."

---

### What is Packet Switching vs Circuit Switching?

These are two fundamental methods for data communication over a network.

* **Circuit Switching:**
    * **Principle:** A dedicated, end-to-end communication path (a "circuit") is established between the sender and receiver before any data is transmitted.
    * **Process:**
        1.  **Connection Setup:** A connection is established (e.g., dialing a phone number).
        2.  **Data Transfer:** Data is transferred over the dedicated circuit.
        3.  **Connection Teardown:** The circuit is released.
    * **Characteristics:**
        * **Guaranteed Bandwidth:** The entire bandwidth of the circuit is reserved for the duration of the connection.
        * **No Sharing:** The circuit cannot be used by other devices, even if no data is being sent.
        * **Inefficient:** Wastes bandwidth if the circuit is idle.
    * **Example:** Traditional analog telephone networks.

* **Packet Switching:**
    * **Principle:** Data is broken down into small, independently addressed units called **packets**. Each packet can take a different route through the network.
    * **Process:**
        1.  **Packetization:** Data is segmented into packets, each with a header containing source and destination addresses.
        2.  **Routing:** Packets are forwarded by routers based on the destination address.
        3.  **Reassembly:** Packets may arrive out of order and are reassembled at the destination.
    * **Characteristics:**
        * **Efficient:** The network medium is shared among all users, leading to better utilization.
        * **No Guaranteed Bandwidth:** Bandwidth is not reserved, so network congestion can lead to delays.
        * **Resilience:** If one path fails, packets can be rerouted.
    * **Example:** The Internet.

---

### Explain the Structure of a TCP/UDP Header

The header contains control information necessary for the transport layer protocols to function.

* **TCP Header (20 bytes minimum):**
    * **Source Port (16 bits):** The port number of the sending application.
    * **Destination Port (16 bits):** The port number of the receiving application.
    * **Sequence Number (32 bits):** A random number that identifies the position of the first byte of data in the segment.
    * **Acknowledgment Number (32 bits):** The sequence number of the next byte the receiver expects from the sender.
    * **Data Offset (4 bits):** The length of the TCP header in 32-bit words.
    * **Reserved (6 bits):** Always set to zero.
    * **Flags (6 bits):** Control bits for various functions (e.g., `SYN`, `ACK`, `FIN`, `RST`).
    * **Window Size (16 bits):** The amount of data the receiver is willing to accept (for flow control).
    * **Checksum (16 bits):** Used for error-checking the header and data.
    * **Urgent Pointer (16 bits):** Points to the end of the urgent data.
    * **Options (variable):** Optional fields for specific functions.

* **UDP Header (8 bytes fixed):**
    * **Source Port (16 bits):** The port number of the sending application.
    * **Destination Port (16 bits):** The port number of the receiving application.
    * **Length (16 bits):** The total length of the UDP header and data in bytes.
    * **Checksum (16 bits):** An optional field for error-checking the header and data.

The TCP header is much larger and more complex than the UDP header because TCP provides a reliable, connection-oriented service with features like flow control, sequencing, and acknowledgment, all of which require control information in the header. UDP is much simpler, reflecting its connectionless, unreliable nature.

### What is Congestion Control?

**Congestion control** is a mechanism used to prevent a network from becoming overloaded with too much data. Network congestion occurs when the amount of data being sent into the network is greater than what the network can handle, leading to packet loss, increased delays, and degraded performance.

* **TCP's Role:** The TCP protocol, being connection-oriented, includes built-in congestion control mechanisms. It works by dynamically adjusting the rate at which data is sent into the network.
* **Mechanism:** TCP uses a "slow-start" algorithm initially, where it gradually increases the amount of data it sends. If it detects packet loss (e.g., through a missing acknowledgment), it assumes congestion and reduces the sending rate. It then probes the network to see if it can increase the rate again.
* **Goal:** The primary goal is to ensure that the network operates efficiently and reliably without collapsing from excessive traffic.

---

### What is Flow Control?

**Flow control** is a mechanism that prevents a sender from overwhelming a receiver with more data than the receiver can process and store at a particular time. It ensures that data is sent at a rate that the receiver can handle.

* **TCP's Role:** TCP uses a "sliding window" protocol for flow control.
* **Mechanism:** The receiver sends a window size to the sender, indicating how many bytes of data it is willing to receive. The sender can only send data up to that window size. As the receiver processes the data, it sends an updated window size, allowing the sender to send more.
* **Goal:** The goal is to avoid buffer overflow at the receiver, which would lead to dropped packets and inefficient data transfer. Flow control is a point-to-point mechanism, operating between two communicating devices.

---

### What is the role of Routers, Switches, and Hubs?

* **Hub:**
    * **Role:** A simple physical layer device that connects multiple network segments.
    * **Function:** When a hub receives a data frame, it broadcasts it to all other ports. It does not perform any intelligent routing or filtering.
    * **Disadvantages:** Highly inefficient, creates a single collision domain, and is rarely used in modern networks.
* **Switch:**
    * **Role:** A data link layer device that connects devices on a local network (LAN).
    * **Function:** A switch learns the MAC addresses of the devices connected to each of its ports. When a frame arrives, the switch reads the destination MAC address and forwards the frame only to the correct port.
    * **Advantages:** It creates separate collision domains for each port, which improves network performance and security.
* **Router:**
    * **Role:** A network layer device that connects different networks.
    * **Function:** A router reads the destination IP address of a packet and uses a **routing table** to determine the best path to forward the packet. It's responsible for routing traffic between different networks, such as a home network and the internet.
    * **Advantages:** Routers are intelligent and can make complex routing decisions, allowing the internet to function as a network of interconnected networks.

---

### How does SSL/TLS work?

**SSL (Secure Sockets Layer)** and its successor, **TLS (Transport Layer Security)**, are cryptographic protocols that provide secure communication over a computer network. They are what makes HTTPS secure.

**How they work (simplified):**

1.  **Handshake:** A secure connection is established through a handshake process.
    * The client sends a `ClientHello` message to the server, listing its supported SSL/TLS versions and cipher suites.
    * The server responds with a `ServerHello`, choosing the best version and cipher suite and sending its digital certificate. The certificate contains the server's public key.
    * The client verifies the server's certificate with a trusted Certificate Authority (CA).
    * The client generates a symmetric session key, encrypts it with the server's public key, and sends it to the server.
    * The server decrypts the session key using its private key.
2.  **Symmetric Encryption:** Both the client and the server now have the same session key. All subsequent data transmitted between them is encrypted using this session key with a fast symmetric encryption algorithm.
3.  **Authentication:** The digital certificate ensures that the client is communicating with the genuine server.
4.  **Integrity:** The handshake also establishes message integrity checks to ensure that data has not been altered in transit.

---

### What are Firewalls? Types?

A **firewall** is a network security system that monitors and controls incoming and outgoing network traffic based on a set of predetermined security rules. Its primary purpose is to protect a private network from unauthorized access from the internet.

**Types of Firewalls:**

1.  **Packet-Filtering Firewall:**
    * **Principle:** The simplest type. It inspects each packet's header (source/destination IP address, port numbers) and decides whether to allow it or deny it based on a predefined set of rules.
    * **Disadvantages:** Cannot inspect the content of the packets; easily bypassed.
2.  **Stateful Firewall:**
    * **Principle:** It keeps track of the state of active connections. It only allows incoming traffic that is part of an established, legitimate session.
    * **Advantages:** Much more secure than packet-filtering firewalls as it can block unauthorized incoming traffic more effectively.
    * **Use Case:** Most modern firewalls are stateful.
3.  **Application Gateway (Proxy Firewall):**
    * **Principle:** Acts as a proxy between a client and a server. It inspects traffic at the application layer, understanding the protocols like HTTP or FTP.
    * **Advantages:** Provides a very high level of security by inspecting the actual content of the data.
    * **Disadvantages:** Can introduce latency and is more complex to configure.
4.  **Next-Generation Firewall (NGFW):**
    * **Principle:** Combines the capabilities of stateful firewalls with deeper packet inspection, intrusion prevention systems (IPS), and application control.
    * **Advantages:** Provides comprehensive security by identifying and controlling applications and content.

---

### Explain Proxy vs. Reverse Proxy

* **Proxy Server (Forward Proxy):**
    * **Role:** A server that sits between a client and the internet.
    * **Function:** A client makes a request to the proxy server, which then forwards the request to the internet on the client's behalf. The response from the internet is sent back to the proxy, which then forwards it to the client.
    * **Purpose:**
        * **Anonymity:** Hides the client's identity from the internet.
        * **Security:** Can be used to block access to certain websites.
        * **Caching:** Can cache web content to speed up future requests.
    * **Analogy:** A "middleman" for the client.

* **Reverse Proxy:**
    * **Role:** A server that sits in front of one or more web servers.
    * **Function:** A client makes a request to the reverse proxy. The reverse proxy then forwards the request to one of the backend web servers. The response from the web server is sent back to the reverse proxy, which then forwards it to the client.
    * **Purpose:**
        * **Load Balancing:** Distributes incoming requests among multiple servers.
        * **Security:** Hides the backend servers and can provide a layer of security.
        * **SSL Termination:** Can handle the SSL/TLS encryption, offloading this CPU-intensive task from the backend servers.
        * **Caching and Compression:** Can cache content and compress responses to improve performance.
    * **Analogy:** A "gatekeeper" for the web servers.

---

### What is ICMP? Use Cases?

**ICMP (Internet Control Message Protocol)** is a protocol used by network devices, like routers, to send error messages and operational information. It is part of the Internet Layer of the TCP/IP model. ICMP messages are encapsulated within IP packets.

**Use Cases:**

* **Error Reporting:**
    * **Destination Unreachable:** A router sends an ICMP message back to the sender if it can't deliver a packet.
    * **Time Exceeded:** A router sends this message if a packet has exceeded its maximum hop count (Time To Live).
* **Network Diagnostics:**
    * **`ping`:** The `ping` utility sends an ICMP Echo Request message to a host. The host replies with an ICMP Echo Reply message. This is used to test connectivity and measure round-trip time.
    * **`traceroute`:** The `traceroute` utility uses ICMP Time Exceeded messages to map the path a packet takes from a source to a destination.

ICMP is a fundamental protocol for network maintenance and troubleshooting.

---

### What is Traceroute?

**Traceroute** is a network diagnostic tool used to track the path a data packet takes from a source computer to a destination host. It provides information about the IP addresses of the routers (hops) that the packet traverses and the time it takes to travel between each hop.

**How it works:**
* **TTL (Time To Live):** Traceroute works by sending a series of packets (usually UDP or ICMP Echo Requests) with an increasing TTL value.
* **Process:**
    1.  The first packet is sent with a TTL of 1. When it reaches the first router, the router decrements the TTL to 0 and sends an ICMP "Time Exceeded" message back to the source.
    2.  The second packet is sent with a TTL of 2. It reaches the first router, which decrements the TTL to 1 and forwards it. It then reaches the second router, which decrements the TTL to 0 and sends an ICMP "Time Exceeded" message back.
    3.  This continues until a packet reaches the destination host, which sends an ICMP "Echo Reply" (if using ICMP) or an ICMP "Port Unreachable" (if using UDP), indicating the end of the path.
* **Output:** The output of `traceroute` is a list of the routers (hops) along the path, along with the round-trip time for each hop. This helps in identifying where network delays or outages are occurring.

---

### What are VPNs? How do they work?

A **VPN (Virtual Private Network)** is a service that allows a user to securely and privately access a network over a public network, such as the internet. It creates a "tunnel" between the user's device and the VPN server, encrypting all traffic within the tunnel.

**How they work:**
1.  **Client-Server Connection:** A client device connects to a VPN server.
2.  **Authentication:** The client and server authenticate each other.
3.  **Encryption:** A secure, encrypted tunnel is established between the client and the VPN server.
4.  **Encapsulation:** All the client's network traffic is encapsulated in encrypted packets.
5.  **Traffic Forwarding:** The encrypted traffic travels through the internet to the VPN server.
6.  **Decryption:** The VPN server decrypts the packets.
7.  **Internet Access:** The VPN server, now acting on the client's behalf, sends the unencrypted traffic to its final destination on the internet.
8.  **Response:** When a response is received, the VPN server encrypts it and sends it back to the client through the tunnel. The client's device then decrypts it.

**Benefits:**
* **Privacy:** Hides the user's IP address and location from the internet.
* **Security:** Encrypts data, protecting it from snooping on public Wi-Fi networks.
* **Access Control:** Allows users to bypass geo-restrictions and access content that is not available in their region.

---

### What is a CDN?

A **CDN (Content Delivery Network)** is a geographically distributed network of servers that work together to provide fast delivery of internet content. CDNs are used by websites to improve performance and availability.

**How it works:**
* **Edge Servers:** A CDN consists of multiple servers placed at various locations around the world, called **Points of Presence (PoPs)**. These servers are closer to end-users than the origin server where the website's content is originally hosted.
* **Caching:** When a user requests content (e.g., an image, a video, a CSS file), the CDN directs the request to the nearest edge server. The edge server checks if it has a cached copy of the content.
* **Delivery:** If the content is in the cache, it is served directly to the user. This is much faster as the data has to travel a shorter distance. If the content is not in the cache, the edge server fetches it from the origin server, caches it, and then delivers it to the user.
* **Benefits:**
    * **Reduced Latency:** Content is delivered from a server closer to the user.
    * **Improved Performance:** Reduces the load on the origin server and increases the website's responsiveness.
    * **High Availability:** If one CDN server goes down, another can take over.
    * **DDoS Protection:** CDNs can absorb large amounts of traffic, helping to mitigate DDoS attacks.

---

### Explain Load Balancing

**Load balancing** is the process of distributing network traffic and workload across a group of servers (a server farm). It is used to improve the performance, reliability, and availability of applications and websites.

**How it works:**
* **Load Balancer:** A load balancer is a device or software that acts as a reverse proxy. It sits between the client and the backend servers. All client requests are sent to the load balancer's IP address.
* **Distribution Algorithms:** The load balancer uses a specific algorithm to decide which backend server should receive the request. Common algorithms include:
    * **Round Robin:** Distributes requests sequentially to each server in the group.
    * **Least Connections:** Sends the request to the server with the fewest active connections.
    * **IP Hash:** Distributes requests based on a hash of the client's IP address, ensuring that a single client's requests always go to the same server.
* **Benefits:**
    * **High Availability:** If one server fails, the load balancer stops sending traffic to it and redirects requests to the remaining healthy servers.
    * **Scalability:** Allows a website to handle a large number of requests by adding more servers to the farm.
    * **Improved Performance:** Prevents a single server from becoming overwhelmed.

---

### What is DNS Spoofing?

**DNS spoofing** (or DNS cache poisoning) is a type of cyberattack where an attacker introduces corrupted DNS data into a DNS resolver's cache. This causes the DNS resolver to return an incorrect IP address for a legitimate domain, redirecting users to a malicious website.

**How it works (simplified):**
1.  An attacker targets a DNS server or a user's local DNS cache.
2.  The attacker sends a forged DNS response to the server/user, providing a fake IP address for a popular website (e.g., a banking site).
3.  The DNS server/user's cache is "poisoned" with this fake information.
4.  When a user tries to access the legitimate website, the DNS resolver returns the fake IP address.
5.  The user's browser connects to the attacker's server, which may look identical to the real website, allowing the attacker to steal the user's login credentials or other sensitive information.

**Mitigation:**
* Using a DNSSEC-enabled DNS resolver, which cryptographically signs DNS records to verify their authenticity.
* Clearing DNS cache.
* Using a secure DNS provider.
* Using HTTPS, which provides authentication and will warn the user if a website's certificate does not match its domain.

### What is Port Forwarding?

**Port forwarding** is a network technique that redirects a communication request from a port on one network address to another port on another network address. It's most commonly used to allow external computers to connect to a specific computer or service on a private network.

**How it works:**
1.  A router on a private network has a public IP address and acts as a gateway to the internet.
2.  Port forwarding rules are configured on the router. These rules specify that incoming traffic arriving on a specific public port should be redirected to a specific private IP address and a specific private port on the local network.
3.  For example, if you want to host a web server on a private network, you could configure port forwarding to redirect incoming traffic on the public port 80 to the private IP address of the web server on port 80.
4.  This allows a user from the internet to access the web server by connecting to the router's public IP address and port 80, which the router then forwards to the correct device on the local network.

---

### What is ARP Poisoning?

**ARP poisoning** (or ARP spoofing) is a type of cyberattack where an attacker sends forged ARP messages onto a local area network. This links the attacker's MAC address with the IP address of another device, such as the default gateway (router).

**How it works:**
1.  On a local network, devices use ARP to find the MAC address associated with an IP address. The results are stored in an ARP cache.
2.  An attacker sends fake ARP replies to other devices on the network. For example, the attacker might send a message to all devices claiming that the router's IP address (`192.168.1.1`) is associated with the attacker's MAC address.
3.  The devices' ARP caches are poisoned with the fake information.
4.  All network traffic intended for the router is now sent to the attacker's machine instead.
5.  The attacker can then either drop the packets (denial of service) or forward them to the real router, all while eavesdropping on the traffic. This allows them to perform a **man-in-the-middle** attack.

---

### How does HTTPS establish a secure connection?

HTTPS (HTTP over TLS/SSL) establishes a secure connection through a process called the **TLS/SSL Handshake**. The goal of this handshake is to:
1.  Authenticate the server.
2.  Establish a secure, symmetric session key.

The process involves public-key cryptography and digital certificates:
1.  **Client Hello:** The client sends a message to the server, listing its supported TLS versions and cryptographic algorithms.
2.  **Server Hello:** The server responds, choosing the best TLS version and algorithm and sending its digital certificate. The certificate contains the server's public key and is issued by a trusted **Certificate Authority (CA)**.
3.  **Certificate Verification:** The client checks the certificate's validity and verifies that it was issued by a trusted CA. This authenticates the server's identity.
4.  **Key Exchange:** The client generates a random, symmetric session key. It encrypts this key using the server's public key (from the certificate) and sends it to the server.
5.  **Session Key Decryption:** The server is the only one with the corresponding private key, so it can decrypt the message to get the session key.
6.  **Secure Communication:** Both the client and the server now have the same session key. All subsequent data transmitted between them is encrypted using this fast symmetric key, ensuring confidentiality, integrity, and authenticity.

---

### Explain TCP Congestion Control Algorithms

TCP congestion control algorithms are a set of strategies used to regulate the rate of data transmission to prevent network congestion. They are a core part of the TCP protocol.

* **AIMD (Additive Increase/Multiplicative Decrease):**
    * **Principle:** When the network is not congested (no packet loss), TCP increases its congestion window size linearly (e.g., adds a fixed number of segments per round-trip time). This is the "Additive Increase."
    * When congestion is detected (e.g., through packet loss), it assumes the network is saturated and reduces the window size multiplicatively (e.g., halves it). This is the "Multiplicative Decrease."
    * **Goal:** To probe for the maximum available bandwidth and then back off gracefully when congestion occurs.
* **Slow Start:**
    * **Principle:** A TCP connection starts with a very small congestion window. It then doubles the window size for every round-trip time (RTT) until it reaches a pre-defined threshold.
    * **Goal:** To quickly find the network capacity without overwhelming the network initially.
* **Congestion Avoidance:**
    * **Principle:** After slow start, once the congestion window reaches a certain threshold, the window size increases linearly (AIMD) instead of exponentially.
    * **Goal:** To avoid causing congestion once the network capacity is known.
* **Fast Retransmit/Fast Recovery:**
    * **Principle:** If the sender receives three duplicate acknowledgments, it assumes a packet was lost (but that the network isn't congested). It immediately re-transmits the lost packet without waiting for a timeout.
    * **Goal:** To improve performance by recovering from minor packet loss more quickly.

---

### What are Cookies and Sessions?

* **Cookies:**
    * **What they are:** Small text files stored on a user's computer by a web browser.
    * **Purpose:** To store small pieces of information about the user, such as login status, user preferences, or items in a shopping cart.
    * **Mechanism:** When a user visits a website, the server can send a cookie to the browser. The browser stores it and sends it back to the server with every subsequent request.
    * **Stateless Protocol:** Cookies help make the stateless HTTP protocol "stateful" by allowing the server to recognize and remember a user across multiple page requests.

* **Sessions:**
    * **What they are:** A server-side mechanism to store information about a user's interaction with a website.
    * **Purpose:** To track a user's journey through a website, maintain their login status, and store more complex data than what can be put in a cookie.
    * **Mechanism:** When a user first visits a website, the server creates a unique session ID and sends it to the user's browser, typically in a cookie. The server then stores the session data (e.g., user's ID, cart contents) associated with that session ID. With every subsequent request, the browser sends the session ID, allowing the server to retrieve the correct session data.
    * **Key Difference:** A session stores data on the server, while a cookie stores data on the client.

---

### What are WebSockets?

**WebSockets** are a communication protocol that provides a full-duplex, persistent connection between a client (e.g., a web browser) and a server. Unlike HTTP, which is a request-response protocol, WebSockets allow for real-time, two-way communication.

* **How they work:**
    * **Handshake:** A WebSocket connection is initiated with a standard HTTP handshake. The client sends a special HTTP request to the server, and if the server supports WebSockets, it responds with a WebSocket-specific response.
    * **Persistent Connection:** After the handshake, the connection is upgraded to a WebSocket connection, and it remains open.
    * **Full-Duplex:** Both the client and the server can send data to each other at any time, without needing a new request-response cycle.
* **Advantages:**
    * **Low Latency:** Eliminates the overhead of creating a new TCP connection for every message.
    * **Efficiency:** Uses a more lightweight header than HTTP.
    * **Real-time Communication:** Ideal for applications that require live data updates, such as live chat, online gaming, and stock tickers.

---

### What is QoS in Networks?

**QoS (Quality of Service)** is a set of techniques used to manage and prioritize network traffic to ensure that certain types of data get the resources they need to function properly.

* **Goal:** To provide a predictable level of service, especially for applications that are sensitive to delays (latency), jitter, and packet loss.
* **How it works:** QoS mechanisms can:
    * **Prioritize Traffic:** Give higher priority to critical or delay-sensitive traffic (e.g., VoIP calls) over less critical traffic (e.g., file downloads).
    * **Bandwidth Reservation:** Reserve a certain amount of bandwidth for a specific application or type of traffic.
    * **Traffic Shaping:** Control the rate at which traffic is sent to prevent congestion.
* **Use Cases:**
    * **VoIP and Video Conferencing:** These applications require low latency and jitter. QoS can prioritize this traffic to ensure a smooth, high-quality experience.
    * **E-commerce and Financial Transactions:** QoS can prioritize this traffic to ensure that transactions are processed quickly and reliably.

---

### Explain Connectionless vs Connection-Oriented Protocols

* **Connection-Oriented Protocols (e.g., TCP):**
    * **Principle:** A logical connection is established between the sender and receiver before any data is sent.
    * **Reliability:** Highly reliable. It guarantees that data will be delivered in the correct order, without loss or duplication. It uses acknowledgments and re-transmissions to achieve this.
    * **Overhead:** Has a higher overhead due to the 3-way handshake and the mechanisms for reliability, sequencing, and flow control.
    * **Use Cases:** Web Browse, email, file transfers—any application where data integrity is more important than speed.

* **Connectionless Protocols (e.g., UDP):**
    * **Principle:** Data is sent as independent packets (datagrams) without establishing a connection. Each packet is routed individually.
    * **Reliability:** Unreliable. It does not guarantee delivery, order, or duplication-free transmission.
    * **Overhead:** Has a very low overhead because there is no connection setup or complex reliability mechanisms.
    * **Use Cases:** Live streaming, online gaming, DNS lookups—any application where speed and low latency are more important than 100% data integrity.

---

### How do you secure a network?

Securing a network is a multi-layered process that involves both hardware and software. Key strategies include:
1.  **Firewalls:** Use firewalls to filter and control network traffic, protecting a private network from unauthorized access.
2.  **Access Control:** Implement strong access control policies, such as using strong passwords, multi-factor authentication (MFA), and role-based access control (RBAC).
3.  **VPNs:** Use VPNs to provide secure, encrypted access to the network for remote users.
4.  **Network Segmentation:** Divide the network into smaller, isolated segments (VLANs). This contains the impact of a security breach.
5.  **Intrusion Detection/Prevention Systems (IDS/IPS):** An IDS monitors network traffic for suspicious activity, while an IPS actively blocks it.
6.  **Encryption:** Encrypt data both in transit (e.g., using HTTPS, IPsec) and at rest (e.g., disk encryption).
7.  **Patch Management:** Regularly update and patch all network devices, operating systems, and applications to fix security vulnerabilities.
8.  **Physical Security:** Secure network devices (routers, switches, servers) in a physically locked location.
9.  **User Education:** Train users to identify phishing attempts and other social engineering attacks.
10. **Monitoring:** Continuously monitor network traffic and logs for unusual activity.

---

### What are Public/Private IPs?

* **Private IP Address:**
    * **Principle:** An IP address reserved for use within a private network (e.g., a home or office network). They are not routable on the public internet.
    * **Address Ranges:** Specific address ranges are reserved for private use: `10.0.0.0` to `10.255.255.255`, `172.16.0.0` to `172.31.255.255`, and `192.168.0.0` to `192.168.255.255`.
    * **Function:** Used for communication between devices on the same local network.
    * **NAT:** Devices with private IPs can access the internet through a router that uses **NAT** (Network Address Translation) to map their private IP to a single public IP.

* **Public IP Address:**
    * **Principle:** A unique IP address that is globally routable on the internet. It is assigned to a device by an ISP.
    * **Function:** It is used to identify a device on the public internet.
    * **Examples:** A web server has a public IP address so that it can be accessed from anywhere in the world. A home router has a public IP address that is visible to the internet.

---

### What is IP Fragmentation?

**IP fragmentation** is the process of breaking down an IP packet into smaller pieces (fragments) to be transmitted over a network that has a smaller **MTU (Maximum Transmission Unit)** than the original packet size.

* **Why it happens:** The MTU is the largest size of a packet that a network can handle. Different network technologies have different MTUs (e.g., Ethernet has an MTU of 1500 bytes). If an IP packet is larger than the MTU of a network link it has to cross, the router on that link will fragment the packet.
* **How it works:** The router splits the large packet into smaller fragments. Each fragment is a separate IP packet with its own header, containing information that allows the destination host to reassemble the original packet.
* **Disadvantages:**
    * **Overhead:** Fragmentation adds overhead because each fragment has its own header.
    * **Performance:** The reassembly process at the destination consumes CPU resources and can lead to performance degradation.
    * **Packet Loss:** If even a single fragment is lost, the entire original packet cannot be reassembled and must be re-transmitted.
* **Mitigation:** Modern networks often use **Path MTU Discovery** to find the smallest MTU along a path and send packets of that size to avoid fragmentation.

---

### What is a Broadcast Domain vs. Collision Domain?

* **Collision Domain:**
    * **Definition:** A collision domain is a network segment where data packets can collide with one another. If two devices in the same collision domain transmit at the same time, a collision occurs.
    * **Devices:** Devices like hubs and repeaters operate at the Physical Layer and simply broadcast data, so all connected devices are in the same collision domain.
    * **Resolution:** Ethernet uses CSMA/CD to manage collisions within a collision domain.
    * **Modern Networks:** Switches and routers create separate collision domains for each port, which significantly improves network performance.

* **Broadcast Domain:**
    * **Definition:** A broadcast domain is a network segment where a broadcast message sent by one device is received by all other devices.
    * **Devices:** Devices like switches and hubs operate within a single broadcast domain. A router, however, separates broadcast domains.
    * **Function:** Broadcast domains are essential for protocols like ARP and DHCP, which rely on broadcast messages to discover devices.
    * **Modern Networks:** A router is used to connect different broadcast domains. Virtual LANs (VLANs) can also be used to create separate broadcast domains within a single switch.

---

### How is Routing done in the Internet?

Routing on the internet is a hierarchical and distributed process.

1.  **Autonomous Systems (AS):** The internet is made up of thousands of individual networks, called Autonomous Systems. An AS is a collection of IP networks operated by a single entity (e.g., an ISP, a university, a large corporation). Each AS has a unique number.
2.  **Routing Protocols:** Routing is handled by protocols that allow routers to exchange information and build routing tables.
    * **Interior Gateway Protocols (IGP):** Used for routing *within* an Autonomous System. Examples include **OSPF** and **RIP**. These protocols are designed to find the best path within a single, trusted network.
    * **Exterior Gateway Protocols (EGP):** Used for routing *between* Autonomous Systems. The primary protocol is **BGP (Border Gateway Protocol)**. BGP is the "glue" that holds the internet together.
3.  **Process:**
    * A packet travels from a source host within an AS.
    * An IGP (e.g., OSPF) guides the packet to the edge of the AS.
    * At the edge, a border router uses BGP to determine the next AS that the packet should be sent to.
    * The packet is then routed between ASes using BGP until it reaches the destination AS.
    * Finally, an IGP guides the packet from the edge of the destination AS to the final host.

---

### Explain BGP and OSPF Briefly

* **BGP (Border Gateway Protocol):**
    * **Type:** Exterior Gateway Protocol (EGP).
    * **Function:** The protocol that powers routing on the internet. It's a path-vector protocol that manages the exchange of routing information between different Autonomous Systems (ASes).
    * **Decision Making:** BGP makes routing decisions based on complex path attributes, policies, and rules set by network administrators, not just on the shortest path. This allows for policy-based routing (e.g., choosing a cheaper or more reliable path).
    * **Scalability:** BGP is highly scalable and is the backbone of the internet.

* **OSPF (Open Shortest Path First):**
    * **Type:** Interior Gateway Protocol (IGP).
    * **Function:** A link-state routing protocol used for routing *within* a single Autonomous System.
    * **How it works:** Each router running OSPF maintains a complete map of the network topology. It uses Dijkstra's algorithm to calculate the shortest path to all other nodes. When a change occurs, it floods a link-state advertisement (LSA) to all other routers to update their maps.
    * **Efficiency:** It converges quickly after a network change and is efficient in its use of bandwidth.
    * **Use Cases:** Used in large corporate networks and by ISPs to manage routing within their own network.
