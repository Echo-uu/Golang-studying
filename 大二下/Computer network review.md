## Ch1 Introduction

### Network edge

* TCP : HTTP , FTP , Telnet , SMTP
* UDP : streaming media（流媒体传输) , DNS

**ISP** : Internet Service Provider

### Network core

* Packet(no connection) and Circuit(connection established) Switching
  * Packet : queue delay , packet lost , better sharing bandwidth , (including forwarding table and routing algorithm)
  * Circuit : 预留带宽，TDM , FDM

* Performance: delay, loss and throughput in packet-switched networks
  * Four sources of packet delay : nodal processing delay 节点处理(影响最大吞吐量)，queuing 排队(丢包率)，propagation 传播 和 transmission $L/R$ 传输时延
  * **Throughput** : instantaneous throughput and average throughput
* Protocol layers, service models
  * layers and functions of ISO/OSI reference model (In theory)
  * Data encapsulation process of TCP/IP (In practice) (In five layers) (底层封装高层)



## Ch2 Application layer (message)

### Principles of network applications

* Application layer protocol and Underlying transport protocol(SMTP,POP3(邮件传输),Telnet(网络访问),HTTP,FTP(文件传输))
* Transport service requirements of common apps(应用层协议服务于传输层)

### Web and HTTP

* Function of URL(统一的资源定位符,定位网络层资源)
* What is the transport layer protocol of HTTP (TCP)
* Process of requesting objects by HTTP
  * HTTP client process initiattes a TCP connection to the server. There will be **sockets** in C/S
  *  C send request message to S throuth socket
  * S receive request message through socket, and send response message encapsulated the object 
  * S notify C close connnection
  * C receiver response message and close TCP connection

### Electronic Mail

* SMTP: sending email to the receiver's server(简单邮件的传输协议)
  * user agent and mail server
* POP3 and IMAP: receive email from receiver's server



### DNS

* Functions of DNS: hostname to IP address translation

* not centralize DNS(分布式的结构)

* What are the DNS servers that are queried(in order) to find an specified IP address?
  
  * 客户端向上一级一级的找，分布式的层次结构，用于查询主机对应的IP地址
  
* \1. The same user machine runs the client side of the DNS application.

  \2. The browser extracts the hostname, www.someschool.edu, from the URL and passes the hostname to the client side of the DNS application.

  \3. The DNS client sends a query containing the hostname to a DNS server.

  \4. The DNS client eventually receives a reply, which includes the IP address for the hostname.

  \5. Once the browser receives the IP address from DNS, it can initiate a TCP connection to the HTTP server process located at port 80 at that IP address.



## Ch3 Transport Layer (segment)

### Transport-layer services

* Differences on providing data transmission services
  * network layer: between end-to-end hosts
  * transport layer: between **application processes**
* What are the **reliable(rdt)** , in-order delivery of Electronic Mail
  * congestion control, flow control, connection management

### Multiplexing and demultiplexing

* Meanings of multiplexing and demultiplexing
  * Demultiplexing : datagram transfer to socket (将运输层报文段中的数据交付到套接字)
  * Multiplexing : datagram transfer to network layer(从套接字接收数据块并封装生成报文段，将报文段传递到网络层)
* UDP socket identified by **two-tuple** (dest IP address, dest port number)
* TCP socket identified by **4-tuple** (source and dest address, port number)

### Connectionless transport : UDP

### Principles of reliable data transfer (**rdt**)

* principles of rdt for **GBN** and **SR(selection retransmission)**
  * "window" , ACK(n) , Timeout(n)
* Comparison of the window size for the alternating bit, SR and GBN protocol

### Connection-oriented transport : **TCP**

* TCP segment : header **20 Bytes**
* TCP rdt
* connection management : Three-way handshaking

* TCP congestion control
  * Different from flow control
  * TCP **Slow Start**
    * 低于阈值，慢启动，指数增长
    * 高于阈值，拥塞避免阶段，线性增加
    * 重复ACK (Reno) 阈值减半，拥塞窗口减半
    * 超时(Tahoe) 阈值减半，拥塞窗口减为1



## Ch4 Network Layer (datagram)

### Services of Network-Layer

* Two key functions: **forwarding** and **routing**

### Virtual circuit and datagram networks

* connection and connection-less service
* Characteristics 核心在于datagram networks

### Router

* Input port
* Output port
* Switching fabric
* Routing processor

### IP:

* Interface(路由器接口) and IP address
* Datagram format : header **20 Bytes**
* IP Fragmentation : **MTU** size
* IPv4 addressing--IP address, Subnets and mask, Subnet classification, route aggregation
* ICMP : error reporting and echo request/reply(ping)
* Traceroute and ICMP

### Routing algorithms

* Link state--Dijkstra's algorithm (**LS**)
* Distance Vector algorithm (**DV**)
* Two reasons of **hierarchical routing** for Internets

### Routing in the Internet

* intra-As and outer-As(自制系统内 自治系统间)
  * intra : RIP , OSPF      outer : BGP (eBGP and iBGP)
    * RIP :30s 交换一次 , >180s 死掉 
* main dominant issue for routing among Ases
  * Routing policy



## Ch5 Data Link Layer (frame)

### Data transmission services

* data link layer : between adjacent nodes over a link

### Error detection and correction

* CRC : 

### Multiple access protocols

* Two types of "links" : point-to-point & broadcast(广播电路才有碰撞)
* Collision of broadcast channel
* Data link layer is divided into two sub-layers : LLC(逻辑链路控制) and MAC(介质访问控制)
* Multiple access protocol-three broad classes
  * channel Partition: TDMA、FDMA、...
  * Random Access : ALOHA、CSMA、CSMA\CD、...
  * "Taking turns" : Tokening Ring
* Link-Layer Addressing
  * MAC address : 6段 48位 16进制表示地址 网卡的物理地址
  * **ARP** : Address Resolution Protocol
    * IP address -> MAC address
    * encapsulated in a link-layer broadcast frame
    * process of ARP query and ARP addressing routing to another LAN
* Link-Layer switches
  * Switch-link-layer device: 
    * Features of Switch and creation of Switch table : self-learning (自学习IP地址和MAC地址的对应关系，创建或者更新交换表)

