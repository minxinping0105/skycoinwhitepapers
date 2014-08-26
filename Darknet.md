

Darknet Plan
Darknet计划
============

The Skycoin Darknet is a high performance, privacy preserving routing protocol inspired by cjdns. Users receive skycoin for contributing resources to the network and expend resources for using network resources.
Skycoin Darknet是一个受cjdns启发的高性能，具有隐私保护的路由协议。用户通过贡献资源到网络来获取skycoin并且未使用网络资源而付出资源。

The protocol is designed to operate over legacy internet and nodes physically connected by wifi. The long term objective is to create long distance point-to-point wifi connections which bypass existing internet providers.
这个协议被设计用来在传统互联网上运行，并且节点通过wifi物理性连接。长期目标是创建远程点对点wifi链接而绕过现有的互联网供应商。


Skywire Meshnet Whitepaper
Skywire Meshnet白皮书
===========================

Implementation details
实现细节

https://docs.google.com/document/d/1_rPNMTokwmBPFel1pZfLbTtTkooSWtGKrTLB3RbXIrI

User Stories: Link Aggregation
用户案例：链路聚合
===============================

Bob has a 2 Mb/s internet connection. It takes Bob minutes to load Youtube videos. Bob and has five neighbors with 2 Mb/s connections. They install Skycoin nodes. Bob's Skycoin node connects to his neighbors through wifi and aggregates the bandwidth, giving Bob a 12 Mb/s connection.
Bob有一个2 Mb/s的互联网连接。它需要花费Bob几分钟来加载Youtube视频。Bob有五个有2 Mb/s链接的邻居。他们安装Skycoin节点。Bobi的Skycoin节点链接通过wifi连接到他的邻居并且聚合带宽，给Bob带来了12 Mb/s连接。

Bob receives Skycoin for relaying traffic and expends Skycoin for using network resources.
Bob接受Skycoin用于传递流量并且为了使用网络资源而花费Skycoin。

Notes:
- Bob's IPv4 traffic tunneled over the Darknet enters the normal internet at a local server on a network backbone
- Bob's Skycoin connection appears as a VPN connection on his computer
- Bob's traffic may take multiple routes between his home and the IPv4 Gateway node
- With $150 in equipment, Bob can connect to nodes up to five miles away at 40 Mb/s
- With $1500 in equipment, Bob can connect to nodes up to 15 miles away at 1.4 Gb/s
备注：
- Bob的IPv4流量通过Darknet隧道进入本地服务器的普通的互联网
- Bob的Skycoin链接作为他电脑上的VPN链接出现
- Bob的流量可能经过多个他家和IPv4网管节点间的路由器
- 花费$150设备费用，Bob可以40 Mb/s连接到最多五英里外的节点
- 话费$1500设备费用，Bob可以1.4 Gb/s连接到最多十五英里外的节点

User Stories: Backhaul
用户案例：回程
======================

Alice lives in a large city, 2 miles from a colocation center with terabytes per second of fiber optic backbone.
Alice住在一个大城市，离每秒T级骨干光纤托管中心2英里。

Alice's internet speed is 2 Mb/s.
Alice的网速是 2 Mb/s。

Alice had cheaper, faster internet, before the FCC stuck down the common carrier access rules. Now, Alice only has one choice for internet. Alice's national ISP is the only ISP after the merger of the two largest cable companies in America.
Alice在FCC搞定公共运营访问规则前有更便宜更快的互联网。现在，在美国两个最大的有线公司合并之后，Alice仅仅有一个ISP。

After the merger the CFO stated "people dont want faster internet", raised prices and put in place bandwidth caps. Alice pays $0.30 per GB for going over her 100 GB bandwidth cap.
合并后CFO表示“人们并不想要更快的互联网”，提高价格并且设置带宽上限。Alice超过100 Gb带宽上限后每GB付费$0.30。

Alice's ISP has been getting worse after net neutrality was struck down by a secret backdoor international trade agreement, that even members of congress were not allowed to see or vote on before it was signed.
自从网络中立性被秘密的，甚至国会议员在被签署前并不被允许看到或者投票的后门国际协定搞定了之后，Alice的ISP正变的越来越糟。

Alice's Youtube and Netflix videos are loading slower than ever before. Alice's ISP has started throttling Netflix, Youtube and Bitorrent while publicly denying it. 
Alice的Youtube和Netflix视频比之前加载更慢。Alice的ISP已经开始限制Netflix，Youtube和Bittorrent，并且公开拒绝它。

Alice's ISP has begun tracking every website she visits, recording her personal information and selling it to the NSA and marketing companies. Alice's ISP has been stealing revenue from the websites Alice visits, by replacing the website's ads with its own advertisements. Alice's ISP is starting to blacklist websites it doesnt like.
Alice的ISP开始跟踪她访问的每个站点，记录她的个人信息并且卖给NSA和营销公司。Alice的ISP已经开始从Alice访问的网站窃取回报，把网站的广告替换成它自己的。Alice的ISP开始黑名单他不喜欢的网站。

Alice hears about Skycoin, finds another Skycoin user with an office in the colocation center. Alice pays $1500 and installs 1.4 Gb/second Ubiquity airFiber antenna on her roof to bridge the distance between her and the fiber backbone.  Alice's connection acts as the backhaul for her neighborhood's local Skycoin mesh.
Alice听说了Skycoin，发现另外一个Skycoin用户有一个托管中心的办公室。Alice在她的房顶花了$1500并且安装了1.4 Gb/秒的Ubiquity airFiber天线来桥接她和骨干光纤的距离。Alice的网络作为她的邻居们本地Skycoin mesh的回程。

Alice cancels her internet service.
Alice取消了她的网络服务。

User Story: Internet Kill Switch
用户案例：互联网杀死交换
=================================

<todo>

Hardware
硬件
========

For development, we are using the following
在开发中，我们使用如下：

Platforms:
- Debian
- Raspberry PI / Beagle Boards
平台：
- Debian
- 树莓派/Beagle开发板

Wifi Devices:
- Edimax EW-7811Un (good linux support)
- TP-LINK TL-WN722N (external antenna support for long distance directional links)
Wifi设备：
- Edimax EW-7811Un (良好的Linux支持)
- TP-LINK TL-WN722N (外部天线支持远程方向性链接)

Directional Antenna:
- TP-LINK TL-ANT2424B 24dBi 60 cm Directional Grid Parabolic Antenna. Up to 10 mile range for line of sight.
- see: http://fabfi.fabfolk.com/
方向性天线:
- TP-LINK TL-ANT2424B 24dBi 60 cm 方向性网格抛物线天线。 直线无遮挡下最高10英里范围。
- 参见: http://fabfi.fabfolk.com/

Future:
未来：
- RONJA (see http://en.wikipedia.org/wiki/RONJA )
- HackRF http://kck.st/1eb5z2R
- Li-Fi http://en.wikipedia.org/wiki/Li-Fi

Technical Objectives
技术目标
====================

Implementation:
- prototype in Golang
- extremely simple
- minimal number of dependencies
实现：
- Go语言原型
- 非常简单
- 最小化的依赖关系

Design Goals:
- Privacy preserving
- coin incentives for provisioning bandwidth, storage and backhaul
- Open Access Wifi mesh networks
- Designed to bridge last mile between the network backbone and home
- "zeroconf". Plug in and runs, no configuration
- difficult to detect and throttle
设计目标:
- 隐私保护
- 提供贷款，存储和回程给予虚拟货币激励
- 开放访问的Wifi mesh网络
- 设计用来桥接骨干网络和家之间最后一英里
- "零配置"。即插即用,无需配置
- 很难被检测到或者限制

Protocol v0.2
协议 v0.2
==============

The protocol is
- simple
- fast
- secure

协议应该
- 简单
- 快速
- 安全

Link Layer:
- Open TCP socket to remote host. Using ECDH with curve secp256k1 to establish ChaCha20 symmetric key session key.
- You now have bidirectional connection to node for sending and receiving data

Routing v0.1:
- At each node, a "path" is established. For each node in route, the next node is registered and associated by 4 byte int. The 4 byte int prefixed on packet determines the node packet will be forwarded to.
- Each node decodes the packet, pops off first 4 bytes to determine next node to transport packet to. Simple lookup table. Routing decisions pushed to origin.
- traffic is one way

Routing v0.2:
- At each node, a "path" is established. For each node in route, the next node is registered and associated with 8 byte int determined by originator. Originator receives 8 byte salt. Salt is hashing or compression function (ex. XOR).
- each node reads the first 8 bytes of packet, hashes in these 8 bytes with the salt function and gets Salt(S, H). Node looks up this value in routing table to get node packet will be forward to.
- if P1 is the 8 byte int denoting packet prefix from incoming node, S is the salt, P2 is int denoting prefix on packets in transit to next node, then the next node is denoted Salt(P1, S). Return path is Salt(S,P2).
- Salt is chosen by transit nodes to avoid collision with other paths through node. Salt may be chosen to avoid collisions in router hash table for constant look up time. Hash table lookup should have randomization internally to prevent information leakage.
- If D is prefix on packet, Salt(P2, D) is forward route and Salt(P1, D) is backwards route. Xor or non-invertable compression function may be used for salt.
- If XOR is used for salt function, there is one seed per node. If non-invertable compression function is used, both forward and backward paths may require seperate values. Symmetric key ciphers only require one salt per node. Non-invertable functions require two.
- two way traffic. destination can communicate back to origin without knowing salt values or return path. Fixed 8 bytes for route information.

Payment for Transport:
- Nodes keep track of how much traffic goes each way for the route
- The person intiating route makes an escrowed "confidence payment" with a 120 byte off block chain Skycoin Transaction.
- The origin node clears payment with the node every few minutes

Note:
- route is determined by origin of traffic
- the destination can communicate back to origin but cannot identify origin node
- payment overhead is 120 bytes per payment
- per hop overhead is 4 bytes (exercise for reader: make it constant)
- public keys are never exposed as plaintext in protocol
- cannot communicate with node without node public key
- 32 bit route path prefix information should be obfuscated by shared secret with node
- packets should be fixed length or multiple of power of 2 for secure applications to resist traffic analysis
- the pubkey a node is sending from can be thrown away. Destination pubkey hash acts as network address for routing. Destination pubkey only decrypts, never signs. Sucessful decryption of session key is proof of private key possession and identity.

Todo:
- this is transport layer protocol. protocol layer over this layer sends traffic over multiple paths to the destination, using fountain coding.
- since origin determines path, origin can optimize for latency or throughput and other criteria
- traffic and handshake should be disguised as SSL protocol to deter throttling by ISPs

Privacy
=======

A user operating a Skycoin Wifi access point allows any user in range to connect through that access point. The access point operator cannot determine the nature of the traffic passing through the access point because it is encrypted. The recipient of the traffic is unable to determine that the path of the traffic passed through the access point.

This effectively removes legal liability for operating public access points. The operator neither has any information about the traffic being relayed nor can the recipient of traffic identify the operator of the network entry point.

Furthermore, with the addition of a mandatory hop (a "guard node") it is impossible for ISPs to easily identify that Skycoin Darknet traffic from a particular public access point has been relayed through a particular cable modem.

Summary:
- Skycoin Darknet Wifi access points are public by default
- Access point operators cannot see contents of traffic through the access point
- Access point operators cannot see destination of traffic routed through the access point
- The recipient of traffic cannot determine the origin or path the data traveled through the network
- Using "guard nodes" ISPs cannot determine that traffic from a particular access point is being relayed through a particular terminating connection (cable modem)

Tradeoffs
=========

The Skycoin Darknet protocol is low latency, high throughput and offers a greater degree of privacy than previous systems. However to achieve these goals, several tradeoffs were necessary.

1. Routing decisions are pushed to the origin node instead of the network
2. Rasberry PIs can only forward 150 Mb/s of second of traffic due to encryption overhead. FGPA hardware could accelerate this to GB/s.
3. The network has the best performance and lowest overhead for large, latency insensitive transfers. Torrents will do very very well over network.
4. Real time applications sending many small packets will function over network, but incur larger overhead than TCP/IP. The theoretical latency and "jitter" in latency is lower than for TCP/IP, but with higher bandwidth requirements for real time applications such as VOIP.
5. Bandwidth microtransaction pollute the blockchain. Therefore we are relying on trusted third parties for low overhead off-blockchain microtransactions for bandwidth confidence payments.
6. Since routing decisions are pushed back to the origin client, clients must maintain routing tables or rely upon 3rd party servers for routing information.
7. Store and Forward operation increases network throughput and reliability, but degrades quality of service for real time applications. Store and Forward operation introduces additional ram and storage requirements on nodes, which may tax the capacity of traditional routers.
8. Nodes that interface between the Skycoin Darknet and traditional internet may suffer the same problems as Tor exit nodes. Most tor exit nodes are blacklisted for editing wikipedia or creating user accounts on websites due to spam issues. To maintain a high quality of service, exit nodes may require trust relationships, payment or user registration to prevent abuse.
