Skycoin: A New System for Distributed Consensus
Skycoin: 一种新的分布式共识系统
===========

Abstract: 
摘要：
A new cryptographic primitive known as a public broadcast channel is introduced. A new consensus algorithm implementation, Obelisk and new coin Skycoin built upon Obelisk are introduced. Obelisk is not a single algorithm, but an implementation employing multiple techniques to deliver specific security guarantees.
本文介绍了一种称之为公开广播频道的加密原语，并引入一种新的共识算法，Obelisk以及基于Obelisk的Skycoin。Obelisk并不是一种单一算法，而是一整套采用多种技术来实现特定安全保证的方法论。

Bitcoin
=======
Overview Of Bitcoin as a solution to the byzantine generals problem. 
比特币的概述-一种拜占庭将军问题的解决方案。

New transactions are placed into a block, which is appended to the blockchain. Any peer in the Bitcoin network can create new blocks. Each block therefore has a single parent but one or more valid successors (children).  The chains form a tree and the core problem of Bitcoin solves is getting every node in the network to agree on which which of prospective chains in the chaintree is the consensus blockchain.
新的交易被放入区块，然后附加到区块链上。比特币网络的任意节点都能创建区块。每个块因此有一个单一的父节点，但是一个或多个合法的后继（子区块）。多个链形成一棵树，并且比特币解决的核心问题是让网络中的每个节点认同到底区块树的哪个潜在链成为共识的区块链。

Bitcoin uses a technique called Proof-of-Work to determine a unique blockchain. A valid block requires a hash value which is below a target value. Nodes add transactions to a new block and randomly try notches until a valid hash for a block is found.
比特币使用一种称之为工作量证明的技术来决定唯一的区块链。一个合法的区块要求一个低于特定值的哈希值。节点们添加交易到新的区块并且随机的尝试notch直到发现一个具有正确哈希值的区块。

A function is used to create a total ordering of chains in the blocktree. The chain which has the highest difficulty and required the most hashing operations to produce is "the longest chain" and consensus chain. The notion of "block depth" and "difficulty" create a total ordering over all linear chains in the blocktree and we accept the most resource intensive to produce chain as the consensus chain.
一个函数被用来创建区块树中链的总体排序。拥有最高难度并且要求最多哈希运算才能创建的链称为“最长链”和共识链。采用一种包含“区块深度”和“难度”的标识来创建一个对区块树中所有线性链的总体排序，并且我们接受消耗资源最密集的链作为共识链。

Bitcoin nodes connect to each other randomly and each node relays the most difficult chain of blocks that it knows about to its peers. If one node has a more difficult to produce chain than another connected peer, the peer will receive the blocks sequentially. The peer will evaluate the function and decide that received chain is more difficult to produce and therefore switch its consensus to the received chain. The peer will then advertise its new chain to its peers. In this way, consensus is propagated throughout the network and all nodes reach the same consensus.
比特币节点们互相之间随机连接，并且每个节点传递它所知道的难度最大的块链到其它节点。如果一个节点拥有一个比其它节点所知道的产生难度更大的链，其它节点接下来将会接受该链。节点将对函数进行求值，来验证接收到的块链的难度更大，并且随后切换到接收到的该链。节点会随后广播它的新链到其他节点。通过这种方式，通过网络来传播共识，并且所有节点达到同一个共识。

Bitcoin does not assume that nodes have identities and does not assume that nodes are honest. Nodes may send other nodes any data and it cannot affect consensus decisions, because difficulty is something that can be independently verified on its own merit.
比特币并不假定节点拥有标识，并且不假定节点是诚实的。节点能够发送任何数据到其它节点，并且它不能影响共识结果，因为难度是一种能够自己单独验证的设计机制。

Innovation in Bitcoin
比特币的创新
====

Bitcoin has made several innovations that need to be kept in mind:
- a single datastructure that everyone has a copy of (the blockchain)
- storing financial transactions in the blockchain (public ledger for transactions)
- use of PoW and difficulty retargeting to maintain a constant rate of block production
- use of public key hashes as addresses (public keys are not disclosed until used)
- use of "outputs" for balances. Ignores trying to create divisible digital cash: To pay $20 from a $25 output, send $20 to person and $5 back to yourself.
- first use of function (PoW difficulty function and block depth) to define total ordering on block trees
- public ledger circumvents double spending problem in traditional digital cash
比特币已经完成多种需要我们继承的创新：
- 一种每个人都有一份拷贝的单一数据结构
- 存储金融交易在区块链中（公开的交易总帐）
- 使用PoW和重置难度来实现恒定的区块产生速度
- 使用公钥哈希作为地址（公钥直到使用时才会披露）
- 使用“输出”表示余额。放弃创建可划分的数字现金的尝试：为了从$25的输出中支付$20，发送$20到其它人，同时$5到自己。
- 第一次使用函数（PoW难度函数和区块深度）来定义区块树的总体排序
- 公开的记账规避了传统数字现金双花问题

Flaws in the Bitcoin System
比特币系统中的缺陷
============================

The Bitcoin system suffers from these flaws:
比特币系统有如下局限性：
- Consensus decisions in Bitcoin are not final and can be reverted. A person or organization who can rent or buy enough hashing power can revert transactions.
- 比特币中的共识结果并不是最终的，并且能被撤回。一个能够租赁或者买到足够哈希计算能力的人或者组织能够撤销交易。
- Bitcoin achieves network consensus but individual Bitcoin nodes are highly vulnerable to adversaries who control the routers through which packets pass. A router controlling adversary has absolute control over the view of a node of the network and can arbitrarily influence the nodes consensus decisions: Attacking a Bitcoin node used by a bank to execute a double spending attack is easier than attacking the whole network to do a double spending attack.
- 比特币获得了网络共识，但是通过控制通过路由的数据包，每个比特币节点非常容易受到控制。一个控制路由器的攻击者有绝对的控制力并且能够任意影响节点的共识结果：攻击一个银行使用的比特币节点比通过攻击整个网络来实现一次双花攻击更加容易。
- The security of the Bitcoin network depends upon the cost to achieve majority hash rate being too great for an individual or organization that would attack the network. This is not a valid assumption. As Bitcoin grows in success and value, the incentives to attack the network have increased. 
- 比特币网络的安全基于，对于一个想要攻击网络的个人或者组织，获得绝大多数哈希速率的成本太过于昂贵。这并不是一个正确的假定。随着比特币获得成功和价值增长，攻击网络的动机会越来越强。
- Successful attacks can steal incredible sums from exchanges ($400 million in the most recent MtGox attack). An skilled attacker can buy alt coins from an exchange in Bitcoin and then 51% attacks to revert the Bitcoin deposit transaction. The user now has both the Bitcoin and the alt coins and the exchange is insolvent because of liabilities to depositors that cannot be met.
- 成功攻击能够从交易平台偷取巨量的数额（最近MtGox攻击事件中价值$400 million）。一个有经验的攻击者能够从交易平台以比特币购买alt coins，并且51%攻击来撤销比特币充值交易。用户因此同时获得了比特币和alt coins，并且交易平台将因为不能兑现破产。
- Attackers can steal substantial sums from banks and gambling sites. An attacker deposits Bitcoin and then withdraws it. The attacker uses a 51% attack to revert the deposit transaction, while keeping the withdraw transaction. Such an attack is likely to come suddenly, be extremely profitable and affect all Bitcoin operating services, who are not fortified against the possibility.
- 攻击者能够从银行和赌博网站偷取大量数额。一个攻击者存储比特币然后提取出来。攻击者通过51%攻击来撤销存储交易，同时保留提取交易。这种类型的攻击会很突然，并且非常有利可图，从而影响比特币的整个服务，这种可能性并不能被排除。
- As Bitcoin matures, criminals can gain massively by buying options against Bitcoin and attacking the network. In the future, successful attacks on Bitcoin could result in several hundred millions of dollars in profit from options trading. 
- 随着比特币的成熟，买空比特币或者攻击网络的犯罪行为能够获利很多。在将来，对比特币的成功攻击能够导致数以百万美元计的买空收益。
- The cost to achieve majority hash rate may not be high enough to protect against a dedicated attacker. KNC miner has shipped batches of 200 units for $10,000 each, which together achieved majority hashrate. The cost to attack the Bitcoin network is therefore less than 2 million dollars.
- 获得绝大多数哈希算力的成本可能并没有高到足够防止特定攻击者。KNC miner已经一万美元单价发售了200个批次，加起来可以获得绝大多数算力。攻击比特币网络的成本低于两百万美金。
- The cost to attack the Bitcoin network is within the resources of nation states and corporations who may attempt to discredit the security of Bitcoin. Countries with strong capital controls and competing corporations may directly attack the Bitcoin network to protect their financial interests.
- 攻击比特币网络的成本在某些为了抹黑比特币安全性的国家或者公司的资源能力范围之内。对资本控制性强的国家和竞争公司能直接攻击比特币网络来网络他们的经济利益。
- Services which allow "cloud hashing" and rental of 3rd party hash power are increasingly successful. Many large pools now have the ability to rent the hash power for a majority attack.
- “云挖矿”和第三方算力租赁服务正变的越来越成功。很多大的矿池现在拥有租用算力完成绝大多数攻击的能力。
- Hackers can use numerous security holes in routers and networking equipment to steal coins from banks and exchanges. An attacker can control the peers a Bitcoin node is connected to and ensure connections to attacker controlled nodes. An attacker may introduce a deposit transaction to the side chain of a bank and get the bank to issue a withdraw transaction which is then relayed to the main network. 
- 黑客们可以使用路由器和网络设备中的各种安全漏洞来从银行和交易平台窃取比特币。一个攻击者能够控制一个比特币节点连接到的节点，并且确保它连接到黑客控制的节点。一个攻击者可能引入一个存储交易到银行的所在侧链，并且让银行发送一个提取交易到主交易网络。
- Bitcoin cannot offer security at a low cost. The cost to run the Bitcoin network is extremely high. The Bitcoin network is using immense and exponentially growing amounts of electricity and is environmentally irresponsible. Bitcoin's security purposely relies upon creating as much electrical waste as possible. A secure system costs more to attack than defend. In a well designed system, $1 in security costs $1000 to circumvent. In Bitcoin the ratio is $1 to $1.
- 比特币不能低成本的提供安全性。运行比特币网络的成本非常高昂。比特币网络正在使用非常大并且指数增加的电能，并且对环境不负责任。比特币的安全性故意的建立在制造尽可能多的电能浪费之上。一个安全的系统应该让攻击花费多于防守。在比特币中，这个比例是1：1。
- Bitcoin transactions take on average 10 minutes to get included in a block, and more time is required for more security. Bitcoin fundamentally cannot decrease transaction times without compromising security. This hinders Bitcoin adaption at the point of sale.
- 比特币交易需要平均10分钟时间来打包进入一个区块，并且为了更高的安全性需要的时间更多。比特币基本上不能降低交易时间的同时又不降低安全性。这一点从推广角度上妨碍了比特币的接受度。

These are the issues that must be addressed. In light of these issues, Bitcoin should be regarded as embryonic, but not final form of cryptocurrencies. Future currencies will improve significantly on Bitcoin and surpass it in many ways.
这些问题必须被解决。通过这些问题，比特币应该被视为加密货币的胚胎而不是最终形式。未来的货币将显著的改善比特币并且在很多方面超过它。

Desirable Properties For Systems of Distributed Consensus for Financial Ledgers
分布式共识的金融记账系统需要具备的属性
==========

The criteria on which Bitcoin can be improved are:
1. Security
2. Efficiency
3. Speed
4. Transparency
比特币能够被改善的几点是：
1. 安全性
2. 效率
3. 速度
4. 透明度

1. Once a transaction has executed, it should be impossible to revert consensus. Consensus should be irreversible as possible. (no double spending, security)
2. The cost to run a perfectly secure ledger should be extremely low. (efficiency)
3. The system should allow transactions to be confirmed within seconds (speed)
4. It should be easy to audit and identify malicious nodes (transparency)
5. Nodes should be able to detect if their consensus differs from the network (router attack, security)
6. Some security properties should remain intact even if the vast majority of nodes in the network are malicious and colluding
1. 一旦一个交易被执行，它应该是不可能被撤销共识的。共识应该尽可能的不可逆。（没有双花，安全性）
2. 运行一个完美的安全的账本的成本应该是极低的。（效率）
3. 系统应该允许交易在几秒级被确认 （速度）
4. 应该很容易审计和识别恶意节点 （透明度）
5. 节点应该能够检测他们的共识是否不同于网络 （路由攻击，安全性）
6. 一些安全属性应该保证完好，即使网络中的绝大多数节点是恶意和勾结的。
We introduce a system called Obelisk which achieves these objectives.
我们引入一个称之为Obelisk的系统来达成这些目标。

Byzantine Generals Problem In The Real World
现实世界中的拜占庭将军问题
======


The Byzantine Generals Problem is a model used by academics for designing algorithms that allow networks of computers to come to an agreement. A successful consensus algorithm requires all of the honest nodes to come to the same agreement.
拜占庭将军问题是一个学术界用来设计算法来保证计算机网络达成共识的模型。一个成功的共识算法要求所有的诚实节点达到同一个共识。

In the Byzantine Generals Problem, you have N generals sieging a city. The generals can only communicate over faulty communication channels and all must come to the same decision. They must all attack on the same day. To conquer the city, all the generals must either attack or stay put. If one general attacks, all the generals should attack and if one waits, all generals should wait. If one general attacks and the other generals stay put, the siege fails. The generals can only communicate by letter and the letters may not arrive or may arrive late. 
在拜占庭将军问题中，你有N个将军围困一个城市。将军们仅仅能通过通信渠道来通信，并且所有人必须达到同一个决定。他们必须在同一天同时攻击。为了征服这个城市，所有的将军必须同时进攻或者等待。如果一个将军进攻，所有将军应该进攻，并且如果一个等待，所有将军应该等待。如果一个将军进攻并且其他将军们按兵不动，围攻就会失败。将军们仅仅能通过信件通信，并且有可能不到达或者晚到达。

In the academic version of the Byzantine Generals Problem, the failures are benign. Maybe a general does not get a letter. The represents faulty but benign computer servers which should all come to the same state. The real world Byzantine Generals Problem is called the "Adversarial Byzantine Generals Problem". The Adversarial Byzantine Generals problem is what happens when someone has a financial incentive to attack the network.
在拜占庭将军问题的学术版本中，失败是良性的。可能一个将军没有得到信。表述失败但是良性的计算机服务器应该同时到达相同的状态。真实世界的拜占庭将军问题被称之为“对抗拜占庭将军问题”。 对抗拜占庭将军问题发生在当有人能通过攻击网络来获利情况下。

There are dishonest generals and they will do everything possible to ensure that consensus fails. Dishonest generals can lie. They can tell one general one thing and another something else. Dishonest generals can kill the messenger of another general so that a message sent is not received. Dishonest generals can forge messages from other generals. Dishonest generals can change the message an honest general sent. The dishonest generals can collude.
存在一些不诚实的将军，并且他们将不惜一切代价来确保不能达成共识。不诚实的将军们可能撒谎。他们可能告诉一个将军一件事情，对另外一个将军则是不同的事情。不诚实的将军可能杀死另外一个将军的信使，让一个发送的消息不能被接收到。不诚实的将军们可能假冒其他将军的信息。不诚实的将军们能够改变一个诚实将军的信息。不诚实的将军们会互相勾结。

In Bitcoin, they will go even further and engage in bribery and hacking. They will hunt down your employees and hack into the computers of contractors to gain access to your servers. They will manipulate system clocks, compromise routers, use hash collisions, flood the network with hundreds of thousands of bots and exploit signature malleability.
在比特币中，他们甚至走的更远，进行贿赂和破解。他们将猎取你的雇员并且黑进承包商的电脑来获取你的服务器权限。他们将改变系统时钟，攻击路由，使用哈希碰撞，使用数以千计的僵尸网络来拥堵网络并且破解签名延展性。
A secure system must not only protect against every known attack, but be robust enough to evolve and survive all future attacks. Some issues in Bitcoin can be fixed, such as signature malleability. Other issues are fundamental and cannot be addressed without defining an entirely new framework, such as the reliance on Proof of Work and miners.
一个安全的系统必须不仅保护每个已知的攻击，还要足够鲁棒性来进化并且在未来攻击中存活下来。比特币中的一些问题可以被修正，比如签名延展性。其他问题则是基础性的，并且不能被解决，除非定义一个全新的框架，比如对于工作量证明和矿工的依赖性。

Skycoin Security Philosophy:
Skycoin的安全哲学：
========

Security is a process of continuous identification and fortification against threats. A good system achieves "defense in depth", has multiple redundant systems and will survive the complete failure of any individual measure. 
安全性是一种针对威胁进行连续识别和加强的过程。一个良好的系统获得“深度防卫”，拥有多个冗余系统，并且能够在任何单一测度下的完全失效中存活下来。

Good security comes not from the paranoia of protecting against every possible imaginable threat, but upon knowing which threats are existential and which are mere annoyances. 
良好的安全性不仅来自保护来自每个可能的不可预测的威胁的悖论，并且依赖于了解哪些威胁是切实存在的，哪些是仅仅是干扰性的。

Good security achieves a multiplier effect. A dollar that costs an attacker ten dollars in resources to steal is a dollar that is safe.
良好安全性具有乘数效应。需要花费攻击者10美元才能窃取的一美元才是安全的一美元。

No single system could achieve all of the objectives a successor to Bitcoin requires. Skycoin instead takes a modular layered approach and uses different systems to enforce particular guarantees. Skycoin was designed as a fortress with multiple layers of overlapping defense. 
没有一个单一的系统能够获得比特币后继者需要的所有目标。Skycoin采用一个模块化层级的方式，并且使用不同的系统来加强特定的要求。Skycoin被设计为一个具有多层交迭防御的要塞。

Skycoin security is focused on protecting against the existential threats to Bitcoin and the daily threats that day to day users face. Skycoin security attempts to give the highest degree of protection against the class of attacks that would inflict the greatest loses upon its users, stakeholders and institutions. This required a complete redesign of Bitcoin at both ends from wallet generation to blockchain consensus. It requires a vision of what we are trying to achieve and requires fundamental innovation in several areas to get there.
Skycoin安全性重点在于保护所有比特币已知的威胁，并且之后每天使用该系统的用户遇到的威胁。Skycoin安全性试图对于可能造成用户，股份持有者和机构，最大损失的攻击类别给予最高界别的保护。这要求对于比特币的完全重新设计，包括钱包生成到区块共识。它需要具有一定视野，这也是我们一直在努力获得的，并且要求在很多领域实现基础性的创新。

Most of the losses in Bitcoin have been from oversights in design, lack of usability and at the end user rather than fundamental technical attacks on the software or mathematics. A user backs up his wallet, makes some transactions and reformats his computer. He thinks his coins are safe because he has a wallet backup (unlike his stupid friend who lost hundreds of thousands of dollars in Bitcoin because they forgot to make backups). He loads the wallet and half his coins are missing. Bitcoin generates new addresses and sends coins to those addresses as change every transactions, but the new addresses are not in the wallet backup because they were not generated at the time the backup was made.
比特币中的大多数损失来自于设计中的疏忽，缺乏可用性，以及发生在终端用户而不是对于软件或者数学的基础性技术攻击。一个用户备份了它的钱包，进行了一些交易，并且重新格式化了他的电脑。他认为他的币是安全的，因为他有一个钱包备份 （不同于他因忘记备份而丢失数以千计美金的愚蠢朋友）。 他加载了钱包，同时他一半的币丢失了。比特币对每一个交易生成新的地址并且作为找零发送币到这些地址，但是新的地址并不在钱包备份中，因为在进行备份时他们还并没有被生成。

Skycoin must address both the looming existential mathematical threats while addressing the security perils that Bitcoin's incomplete and poorly thought out user experience has created for everyday users. The poor usability and design has forced users to compromise security and even paranoid power users with millions of dollar routinely rely on insecure web wallets. Despite the frequent and massive thefts reported by the media on a daily basis, to date more Bitcoin have been lost to usability issues than all the efforts of criminals to steal Bitcoin.
Skycoin必须同时解决若隐若现的现有的数学威胁，同时解决对日常用户来说，比特币不完善和考虑不周的用户体验造成的安全风险。比较差的可用性和设计迫使用户对安全性妥协，并且甚至让拥有百万美元的重要用户依赖于不安全的在线钱包。尽管每天媒体都有报道频繁和大额的丢失，到今天为止，更多的比特币由于可用性问题丢失，而非偷窃比特币的犯罪行为导致。

As many as half of the total existing Bitcoin have never been moved from their initial addresses and never will be. They are simply lost. Unrecoverable wallet files, lost wallets, misunderstandings of what was actually being backed up in a wallet file. MtGox recently reporting "finding" 200,000 Bitcoin in a wallet they didn't know had Bitcoin in it. The wallet was ignored and easily could have been deleted under the mistake it had no coins in it (which has happened to many) because the software was unable to load the wallet because it was "too old". 
全部现存比特币中超过半数的在它们的初始地址上从未移动过，并且将永远不会。他们仅仅是简单的被丢失了。不可恢复的钱包文件，丢失的钱包，对于文件中真正备份的是什么的误解。MtGox近期报告说在一个他们不知道有比特币的钱包中“发现”了二十万比特币。钱包被忽略，并且因为软件由于钱包“太老”而不能加载钱包文件，认为里面没币而被很轻易的删除 （在很多人身上发生过） 。

Most of the security issues are at that level. They are about usability, end users and exchange security. The rest of this paper covers some of the new techniques we have created to address network level security and secure the Skycoin blockchain.
大多数的安全问题是在于那个层级上。他们是关于可用性，终端用户以及交易安全性。本文余下的部分包含了一些我们创造的新技术来解决网络层级的安全性，并且保护Skycoin的区块链。

We have proven mathematically that our system achieves consensus, has the security properties we want and operates well under normal network conditions. We have some exciting new data-structures that have not been seen in any coin or piece of software before. Now we are prototyping the system for deployment.  The Skycoin development process is iterative. There will be changes, improvements and refinements as we work through the details, address known flaws, test the system and get feedback.
我们已经数学意义上证明我们的系统可以获得共识，拥有我们想要的安全性，并且在正常网络状态下工作正常。我们现有的一些数据结构从未在任何虚拟币或者软件中被见到过。现在我们正在进行可供部署的原型系统开发。Skycoin开发流程是迭代性的。随着我们处理一些细节，解决已知问题，测试系统并获得反馈，将会有一些改动，改进以及重新调整。

Public Broadcast Channels: Personal Blockchains
公开广播频道：个人区块链
==========

In Adversarial Byzantine Generals Problem there are several communication assumptions
- messages may arrive out of order
- messages may not arrive
- dishonest generals may say one thing to one person and another thing to another
- dishonest generals may lie
- dishonest generals may forge signatures of other generals
- dishonest generals may intercept and modify messages from other generals
在对抗拜占庭将军问题中，有如下通信假设
- 消息可能乱序到达
- 消息可能不到达
- 不诚实将军们可能对于不同人说不同的事情
- 不诚实将军们可能撒谎
- 不诚实将军们可能伪造其它将军的签名
- 不诚实将军们可能拦截并修改来自其他将军的消息

We introduce a new cryptographic primitive called a public broadcast channel and describe its implementation. This primitive has the following properties
- you cannot say one thing to A and another thing to B 
- the communication is public
- the communication could not have come from anyone but you (authenticated)
- once publish something, it cannot be easily unpublished
- you cannot backdate a communication without being detected (linked timestamping/hash chain)
- the messages arrive in order
- the message cannot be modified in transmission
我们引入一种称之为公开广播频道的新的加密原语并且描述了它的实现。这个原语具有如下属性：
- 你不能对A说一件事情，对B说另外一件事情
- 通信是公开的
- 通信不能来自除你之外的其他人（认证过的）
- 一旦发布，不能轻易的取消发布
- 你不能回溯一次通信而不被检测到 （链接的时间戳/哈希链）
- 消息顺序到达
- 消息在传输中不能被修改

The public broadcast channel is implemented as a block chain. Everyone can read the chain, but only the owner can mint blocks for it. To be valid for a personal chain, each block must be signed by the owners private key. 
公开广播频道被实现成一个区块链。每一个人可以读取链，但是仅仅拥有者可以对它挖块。为了成为合法的个人链，每个区块必须用拥有者的私钥进行签名。

Each Obelisk node has a personal blockchain and it is the core primitive in the Obelisk system.
每个Obelisk节点具有一个个人区块链，并且它是Obelisk系统的核心部分。

The public broadcast channel imposes several constraints
- Once a block is published, it cannot be unpublished (blocks are replicated peer to peer to all subscribers. Once a block has been published, it spreads to all subscribers. You have to destroy all peers who have received the block to erase it from internet).
- A node cannot publish a different version of an earlier block without detection (blocks are numbered and it would be detected if the node signed two different blocks with the same sequence number)
- A node cannot backdate the time stamp on the receipt of a block, without delaying the publication of a block (timestamps only go up, time stamps increase monotonously with block sequence count)
- A block in the middle of the chain cannot be changed without invalidating every block that comes after it (hashchain, each block header contains a hash of the previous block)
公开广播频道强加了几个约束：
- 一旦发布一个区块，它不能被取消发布 （区块被点对点的复制到所有订阅者。一旦一个区块已经被发布，它将扩散到所有订阅者。你必须销毁所有已经接收到区块的节点来从网络上擦除它）。
- 一个节点不能发布一个之前区块的不同版本而不被检测到 （区块被编号并且如果节点使用同一个序列号签名了两个不同的区块将被检测到）
- 在不延迟区块发布情况下，一个节点对于接收到的区块不能回溯时间戳 （时间戳仅仅增长，时间戳随着区块序列号单调增加）
- 链中的一个区块不能在不报废之后区块情况下被修改 （哈希链，每个区块头部包含之前区块的哈希）

Obelisk: 
=======

Each Obelisk node (Skycoin Consensus Node) has a public key (an identity) and personal blockchain (a public broadcast channel). Consensus decisions and communication happen within the personal blockchains of each Obelisk node. This is a public record of everything a node does. This allows the community to audit nodes for cheating and collusion. It gives the community a way identify nodes which are participating in attacks on the network and it makes public how decisions in the network are being made and which nodes are influencing those decisions.
每个Obelish节点（Skycoin共识节点）拥有一个公钥（一个标识）和一个个人区块链（一个公开广播频道）。共识决定和通信发生在每个Obelisk节点的个人区块链内。这是一个该节点所有事情的公开记录。这让社区可以审计节点是否欺诈和勾结。它给予了社区一种方法识别正在参与网络上攻击的节点并且公开了网络如何进行决定，并且哪些节点正在影响那些决定。

Each node has a list of other nodes that it subscribes to. Nodes with more subscribers are more "trusted" and yield more influence in the network. If the community does not trust the nodes representing them or feels that power within the network is too concentrated (or not concentrated enough) the community is able to collectively shift the balance of power in the network by collectively changing their trust relationships in the network.
每个节点具有一个它所订阅节点的列表。具有更多订阅者的节点可以更加被信任并且在网络中产生更大影响。如果社区不相信代表它们的节点，或者感觉网络内的权利太过于集中（或者集中程度不够），社区能够通过集体的改变他们网络内的信任关系来集体移动网络内权利的平衡。

Node subscription relationships can be random and/or can be formed through web of trust (subscribe to nodes of people you know and people in community you trust).
节点订阅关系可以是随机的，并且/或者通过信任网络形成（订阅你知道的人以及社区内你信任的人的节点）。

When a node receives a new block from a chain it is subscribed to, it publishes the hash of the block it publishes. This is a public acknowledgment of the receipt of the block. Each block is timestamped and counter references blocks from other chains. This creates a dense interlinked chains of block acknowledgments. These chains establish causal relationships and can act as a distributed time stamping system as described in the next section. This allows the network to prove that data did not exist or was not published to the network or establish that particular nodes were active or offline during a particular time interval.
当一个节点从一个它订阅的链接收到一个新的区块，它发布区块所发布的哈希值。这是一种对接收到区块的公开确认。每个区块加上时间戳并且计数器引用了来自其他链的区块。这创造了一个密集的区块互认的互联链。这些链建立因果关系并且可以作为一种如下节所述的分布式的时间戳系统。这使网络可以证明数据并没有存在，或者没被发布到网络过，或者证明那个特定节点在某一个特定时间间隔内曾经活跃过或者离线过。

The current Obelisk consensus algorithm is based upon Ben-Or's randomized consensus algorithm.
当前的Obelisk共识算法基于Ben-Or's随机化共识算法。

A Sybil attack in a random graph (worse case) allows the Sybil nodes to control consensus, but the nodes are unable to revert transactions, removing the only economic incentive to attack the network. In real world graphs the Sybil resistance of the network is actually very high and running a node is moderately costly in terms of bandwidth, which make large botnets prohibitive.
一个在随机图中的Sybil攻击（最坏情况下）使得Sybil节点可以控制共识，但是节点不能撤销交易，从而移除了攻击网络的唯一的经济上的激励。在现实世界的图中，网络的Sybil抵抗能力实际上是非常高的，并且运行一个节点在带宽上成本是比较高的，这防止了大的僵尸网络出现。

Trust relationships are scarce and can be rescinded. In the event of an attack, the network reacts by severing connections to less trustworthy nodes and contracting to a smaller core of trusted nodes. The public record left by each node's personal blockchain makes it very easy to identify the nodes participating in an attack. As attacking nodes are identified individuals sever relationships with those nodes, reducing their influence.
信任关系是稀缺的，并且可以被撤销。在发生攻击事件时，网络通过断绝到可信度低的节点的链接，并且缩小到一个较小的信任节点核心来进行反应。每个节点的个人区块链留下的公开记录使它非常容易来确认参与攻击的节点。随着攻击节点被识别出来，每个人可以限制和这些节点的关系来降低他们的影响。

- Skycoin consensus is democratic and nodes are run by the community. 
- Skycoin node consensus is public
- Every node is accountable to the community and 3rd party audits.
- Influence within the Skycoin consensus system is democratic and transparent (but unequal).
- Skycoin共识是民主的，并且节点由社区来运行
- Skycoin节点共识是公开的
- 每个节点对于社区和第三方审计是可问责的
- Skycoin共识系统内的影响是民主和透明的 （但是不平等）

Simple Binary Consensus Algorithm: Choosing between two blocks
简单的二进制共识算法：在两个区块内选择
====

Each voting decision is a hash pair (A,B). A is the hash of the parent of the block and B is the hash of the block.
每个投票决定是一个哈希对（A,B）。A是父区块的哈希，同时B是区块的哈希。
Each node votes on the next block it believes should be the consensus block. If 40% of the nodes it is subscribed to have the same candidate for consensus, the node changes its consensus to that block. The node flips randomly between candidates until consensus is reached.
每个节点对它认为应该是共识区块的下一个区块投票。如果它所订阅的40%的节点具有同样的共识候选人，节点改变它的共识到那个区块。节点在候选人间随机跳转直到达成共识。

Consensus on Multiple Concurrent Branch Choices:
多个并发分支选择的共识：
====

A more advanced system publishes (A,B, P) Where P is value from 0 to 1. P values across all successors to block would sum to 1. This allows for concurrent consensus decisions on multiple chain branches.
一个更高级的系统发布（A,B,P）,其中P是从0到1的值。block的所有后继者的P值之和为1。这可以实现多个链分支上的并发共识判决。

If the majority of nodes in the network are honest, they will also converge to the same consensus.
如果网络内绝大多数节点是诚实的，他们也将收敛到同一个共识。

Skycoin also has a limited form of Proof of Stake. We bias voting in favor of blocks with a larger transaction fee.
Skycoin同时具有一定形式的股份证明。我们投票偏向于具有更大交易费用的区块。

If there are only two possible consensus choices for given parent and both blocks execute your transaction, then the transaction is effectively executed regardless of which of the two blocks end up chosen by the network.
如果对于给定的父区块和包含你的交易的区块只有两个可能的共识选项，无论两个区块中的哪个被网络选择，交易将被有效执行。

The probability of reversion of an early consensus decision declines exponentially with block depth.
撤销一个早期共识决定的概率随着区块深度指数衰减。

Advanced Topics in Consensus
共识的高级课题
====

By constructing the network link adjacency matrix, we can compute the Eigenvalue centrality measure which measures the influence of each node. We can cluster the graph and find the influential subclusters of nodes and then sampling nodes from the subclusters can determine if global consensus has been reached.
通过构造网络链接邻接矩阵，我们可以计算测量每个节点影响度的特征值中心量度。我们可以把图聚类并且找到有影响力的子集群节点，然后从子集群中的节点采样从而决定全局共识是否已经达到。

The efficiency of the algorithm declines with the number of blocks the network has to choose from in each round. We may use Proof of Work, with no reward and difficulty retarget as a throttle rate on the introduction of new candidate blocks.
算法的有效性随着每一轮中网络必须从中进行选择的区块数目递减。我们可能使用工作量证明，没有奖励并且难度重新调整控制引入新的候选区块速率。

If we could guarantee a single block per decision period, consensus becomes trivial. We can achieve this by imposing a total ordering on the blocks in the consensus round and dropping all but the top. Example: the block with the largest transaction fee that was published within fifteen seconds of the last block. There is no way to do an exact, fair, distributed time stamp everyone will agree one, but any way to construct a total ordering would work.
如果我们可以保证每个判决周期内单一区块，共识会变的很琐细。我们可以在每一个共识周期内引入总体排序，并且只保留顶部区块。举例：在上个区块之后15秒内发布的具有最高转账费用的区块。没有办法完成一个精确的，公平的，每个人都同意的分布式时间戳，但是任何构建总体排序的方式都能工作。

Another method uses a "fair" block lottery to choose the node that will mint the next block. It has to exploit the graph structure so trusted people and not sybil atack nodes get the block minting rights. Its easy to construct if you have the global graph and replicate all chains for each node, but very difficult using only local information available to each node.
另外一种方法使用一个“公平”的区块彩票方式来选择将挖掘下一个区块的节点。它必须利用图结构来使得受信任的人而非sybil攻击节点获得区块开采权利。如果你有全局图并且为每个节点复制所有链，它是非常容易构建的，但是仅仅利用每个节点的本地信息则将非常困难。

In another scheme, you use the consensus to vote a committee of nodes to mint block. The right to mint the next block passes around in circles over a list of elected nodes. Once the system in place, you can try different things. Nodes can be programmed to communicate and act autonomously. People can update their node's program to automatically kick deadbeats off the elected board of block minters. If enough nodes added that script, it would become an enforced rule.
在另外一种框架中，你使用共识来投票成立一个节点委员会来挖掘区块。挖掘下一个区块的权利在一个选举出来的节点列表中循环传递。一旦系统运行起来，你可以尝试不同的方法。节点可以被编程来自动通信和回应。用户可以更新他们节点的程序来把懒人从选举出来的区块矿工委员会中自动剔除。如果足够多的节点添加了那个脚本，它就变成一个强制执行规则。

The personal blockchains act as ballots with scriptable behavior. Individuals can add scripts to their node for detecting bad nodes and severing relationships with them. The network can acquire attack immunity locally, through the actions of individual users choosing the scripts to run on their node instead of from a central patch by the developers.
个人区块链表现为可编程行为的投票。每个人可以添加脚本到他们的节点来检测恶意节点并且和它们断绝联系。网络可以本地化的对攻击获得免疫，通过每个用户选择在他们节点上运行的脚本的行为，而不是采用来自开发者的中心化分发。
We are at an early stage of understanding what is possible with personal blockchains.
我们对于理解个人区块链存在的可能性的理解还处于初级阶段。

Attack Types:
攻击类型：
===

There are four types of attacks
- dominating decisions on block consensus (potential denial of service)
- reverting consensus which had previously become unanimous (double spending)
- delaying consensus (denial of service)
- attacking individual nodes by controlling their view of the network
有四种类型的攻击方式：
- 区块共识的判决被主导 （潜在的拒绝服务）
- 撤销之前已经达到一致的共识（双花）
- 延迟共识（拒绝服务）
- 通过控制网络的视图来攻击单独节点

An adversary who controls the majority of the influence in the network controls the consensus decisions of the network. However, they are unable to easily double spend or 51% attack. A adversary which controls the network can vote for blocks that contain no transactions and other annoyances. Such behavior is easily detected (public behavior) and nodes easily banned if they become disruptive.
控制网络内绝大多数影响力的攻击者控制了网络的共识判决。然而，他们并不能轻易的双花或者51%攻击。一个控制了网络的攻击者可以对仅包含噪声而没有任何交易的区块投票。这种行为能轻易的被检测到（公开行为）并且如果他们变的有破坏性，可以轻易的被节点禁掉。

To revert consensus, requires a majority of nodes to be hostile and collude. The malicious majority must go offline, allow the main network to reach a particular consensus and then resume communication with the rest of the network. Any node which whose connections consist of a majority of attacking nodes will be successfully recruited in the 51% attack (in the naive version). However, If the attacking nodes are less than a majority, the effort will fail.
为了撤销共识，需要绝大多数节点变的恶意和勾结。恶意的大多数必须离线，允许整个网络来到到一个特定的共识，然后恢复和其它网络的通信。任意包含绝大多数攻击节点连接的节点将会成功带入一次51%攻击（原始形式）。尽管如此，如果攻击节点少于绝大多数，这种努力将会失败。

This is the only way to revert transactions. This is the only attack and is extremely easy to detect. Trustworthy nodes quickly sever relationships with attacking nodes. Subgraphs involved in the attack are likely to be densely connected and do not influence the network as much as more tightly integrated subgraphs. It is not enough to have a simple majority of nodes, to revert consensus, an adversary must control nodes which control a majority of scarce subscription and trust relationships. Sybil attack bots have difficulty networking into a human web of trust network.
这是撤回交易的唯一方式。这是唯一的攻击并且非常容易被检测到。受信任的节点快速切断和攻击节点的联系。牵扯到攻击内的子图很有可能被密集的链接一起，并且不如紧密集成的子图一样大的影响网络。简单的拥有绝大多数节点并不足以撤销共识。一个攻击者必须控制了控制绝大多数稀缺节点和信任关系的节点。对于Sybil攻击机器人，聚合人类的信任网络具有一定难度。

In web of trust graphs, influence is highly concentrated with nodes trusted by the community and controlled by Skycoin stakeholders. It is extremely unlikely a majority of trusted community members and institutions would benefit from, or even be able to organize a successfull majority influence attack. Community members participating are publicly identifiable and would suffer severe trust penalities for being associated with an attack attempt.
在信任图网络中，影响力是和被社区信任的节点高度联系的，并且由Skycoin股权持有者控制。绝大多数受信任的社区成员和机构能从中获利，或者甚至组织起一次成功的绝大多数影响力攻击的可能性是非常低的。

Despite the difficulty of double spending under Skycoin, it is possible to prevent the attack entirely through two separate methods. The first method severely restricts the way voting decisions are made, to greatly increase the difficulty of collusion between nodes. The second way uses distributed time stamping to identify attack nodes .
即使Skycoin下的双花难度很大，仍有可能分别通过两种方法来完全防止攻击。第一个方法是严格限制投票判决的方式，来极大的增加节点间勾结的难度。第二种方式使用分布式时间采样来识别攻击节点。

Subverting Individual Bitcoin Nodes: Easier Than Attacking Network
攻击单独的比特币节点：比攻击网络更容易
====

Individual Bitcoin nodes suffers vulnability to attacker who controling the network router. Such an attack can inject reset packets and control who the node can connect to. Victims can be setup for a double spending attack and coins stolen by forking the blockchain of indivial node without needing to attack the Bitcoin network. As the price of Bitcoin rises, these attacks become more likely and profitable.
每个比特币节点容易受到控制网络路由器的攻击者的控制。这种攻击可以插入重置数据包并且控制节点可以连接到谁。受害者节点可能被陷入双花攻击并且通过分叉单个节点的区块链来窃取币，而不用攻击整个比特币网络。随着比特币的价格上升，这些攻击变的可能性更大和更有利可图。

Skycoin introduces a "consensus oracle" to protect banks and exchanges from targeted attacked on individual nodes. The Skycoin consensus oracle verifies an individual node is in sync with global network. The Skycoin consensus oracle takes a list of public keys of user chosen trusted nodes and verifies against the list. Discrepancy result in an alert prompting human action and safeguard measures such as suspending exchange withdrawls before funds can be stolen.
Skycoin引入了一种“共识预报”来保护银行和交易平台防范在特定节点上的目标攻击。Skycoin共识预报采用一个用户选定的信任节点的公钥列表并且根据列表进行验证。结果的不同会触发一个警告提示用户该行为的存在以及防范措施，比如在资金被窃前暂停交易平台提款。

Publicly Verifiable Trusted Computing with Communicating Distributed Deterministic State Machines:
采用分布式判决状态机通信的公开可验证的可信性计算:
=====

We describe a system, where each node performs a computation in public. The computationa can be verified and replicated by any third party. This system consists of deterministic state machines communicating over a public broadcast channel (private blockchains).
我们描述了一个系统，每个节点公开执行一种计算。该计算能被任何第三方验证和重复。这个系统由通过公开广播频道（私有区块链）进行通信的确定性状态机构成。

Consensus decisions published in the block chain become outputs of a deterministic state machine, whose inputs are public data. We require that the output published in a blockchain by a node, are a deterministic function of the block data published by the nodes subscribed to. Any third party can download the public inputs to a node and verify that the output matches exactly the output (the block ) produced and published by the node. 
发布在区块链中的共识结果变为确定状态机的输出，它的输入为公开数据。我们要求，由一个节点在区块链中发布的输出，是一个由它所订阅节点区块数据的确定性函数。任何第三方可以下载一个节点的公开输入并且验证输出和由节点产生和发布的（区块）输出精确匹配。

This approach was developed for and heavily influenced by research into adversarial Paxos. We call the implementation of Paxos on a public broadcast channel "Public Paxos".
这种方法被开发用于并受到关于对抗性Paxos的研究的深刻影响。我们将公开广播频道上的Paxos实现称为“Public Paxos”。

A third party auditor can produce a mathematical proof which can be indepedently verified by third parties, proving cheating by a dishonest node. Such cheating becomes bannable and results in automatic revocation of trust relationships. The node would be severed from the network by honest nodes and unable to influence voting decisions.
一个第三方审计可以产生一个数学证明，并能被第三方独立验证，不诚信节点欺诈证明。这类欺诈可以被禁掉并且导致信任关系的自动撤销。

A practical implementation of this system, requires 
- the implementation of a state machine or well defined virtual machine
- requires that each block contain a hash of the list of peers the node has trust relationships with
- requires a hash of the program that the state machine is running, which determines its output (block produced)
- requires publication of hash of blocks received from peers in the feed
这类系统的一个实际实现要求：
-　一个状态机的实现或者定义良好的虚拟机
-　要求每个区块包含一个有信任关系节点的列表的哈希
-　要求正在运行状态机程序的哈希，决定了它的输出（产生区块）
- 要求在反馈中发布从节点所获得区块的哈希

We augment the personal blockchain with a datastructure containing some rarely changing fixed information, including the state machine's subscription list and program source code. The node publishes the hash of its subscription list and virtual machine source code in each block and publishes the subscription list and program source.
我们采用包含一些很少改变的固定信息的数据结构来增强个人数据链，包括状态机的订阅列表和程序源代码。节点发布它的订阅列表的哈希和每个区块中的虚拟机源代码，并且发布它的订阅列表和程序源代码。

Example:
举例：

Node A is subscribed to the private chains of Node B and Node C. B mints block B1. A receives B1. A publishes a block, which includes the hash of B1 to signify the receipt of the data. The block produced by A, A1 is a deterministic function of B1.  C publishes block C1. A publishes block A1, which include a hash of block C1 in its block acknowledgement list. A2 produces and publishes and signs block A2, which must be a deterministic function of B1,C1.
节点A被节点B和C的私有链订阅。B挖出区块B1。A接收到B1。A发布一个区块，包含了B1的哈希来表示接收到数据。由A产生的区块A1是一个B1的确定性函数。C发布区块C1。A发布区块A1，在它的区块确认列表中包含了区块C1的哈希。A2产生，发布并签名区块A2，必须包含B1，C1的确定性函数。

Note:
- all inputs are public and available to 3rd parties (information published in a public broadcast channel)
- outputs produced by each node are deterministic functions of public input
- any 3rd party can download the same data, run the same program and generate the same output as the node itself
- the state of the machine, which generates the output might be a queue of the last 1024 blocks acknowledged by the node
备注：
- 所有输入是公开的，并且对第三方可查的 （信息发布在一个公开的广播频道）
- 每个节点产生的输出是公开输入的确定性函数
- 任何第三方都能下载同样数据，执行同样程序并且和节点自身生成同样的输出
- 用于产生输出的状态机的状态可能是由节点确认的最近1024区块的队列

Overview:
- you have N state machines
- each state machine communicates over a public broadcast channel
- the state of each machine is a queue of received messages from other state machines
- each state machine when invoked produces an output block published into the machines public broadcast channel
- the output block contains hashes (receipts) of received messages and data
- the output block is a deterministic function of the queue of received messages over the last N blocks, for finite N
概述：
- 你有N个状态机
- 每个状态机通过一个公开广播频道通信
- 每个机器的状态是从其他状态机接收到信息的队列
- 每个被引用的状态机产生一个发布在机器公开广播频道的输出区块
- 输出区块包含接收到信息和数据的哈希 （收据）
- 对于有限N，输出区块是最近N个区块接收到信息队列的一个确定性函数

In this system, nodes are highly constrained. The only leeway nodes receive is twiddling the order that messages are acknowledged. The types of attacks a node can partipate in without detection is severely limited.
在这个系统中，节点是高度受限的。节点唯一的回旋余地在于摆弄所确认消息的顺序。一个节点在不被检测到情况下可以参与的攻击类型是严格受限的。

Thoughts on Distributed Time Stamping:
关于分布式时间戳的想法：
====

The simplest time stamping service is a trusted central server with a known public key and an accurate clock. The server receives hashes and produces a signed timestamp of the hash with its private key. If the server can be trusted, the signed timestamp can be used to prove that data existed at a particular time.
最简单的分布式时间戳服务是一个受信任的具有已知公钥和一个精确时钟的中心服务器。服务器接到到哈希并且用它的私钥对哈希产生一个签过名的时间戳。如果服务器可以被信任，签名时间戳能被用来证明数据在某一个特定时间存在过。

Accurate, trusted digital time stamps have many applications. They can be used to determine if a node was online at a particular time, they can be used to detect and eliminate particular types of attacks which require withholding publications of the data to the network until a later time and then revealing the data suddenly (such as Bitcoin 51% attacks) and can be used to establish a total ordering on blocks. 
精确的，可信任的数字时间戳有很多应用。它们能被用来决定一个节点在某个时间是否在线，他们可以用来检测和消除那些要求先扣留数据一段时间，然后再突然公布数据到网络的特定类型的攻击 （比如比特币51%攻击） 并且能被用来建立区块的总体排序。

For example, Distributed blockchain consensus with a reliable timestamping server is trivial. The rule "Accept the block with the highest fees which was produced within 15 seconds of the previous block" achieves blockchain consensus. This rule uniquely determines a unique successor block. In fact if an accurate and honest timestamping service exists then this simple rule produces a 51% attack network with no mining and extremely low operational overhead.
比如，使用一个可靠的时间戳服务器的分布式区块共识是很琐细的。规则“接受在上个区块之后15秒内产生的具有最高手续费的区块”可以获得区块共识。这个规则唯一的确定了一个唯一的后继区块。事实上，如果一个精确的并且诚实的时间戳服务存在的话，那么这个简单的规则可以不使用挖矿和在非常低操作成本下产生一次51%网络攻击。

The original Obelisk design was based upon constructing a distributed timestamping, but only worked in a fully connected graph.  No distributed time stamping system could achieve provable consensus on the total ordering of events between all nodes in the network using only the local information available to individual nodes. Each node only sees a subset of the network. The fully connected case of a small number of servers is a special case where each node has a "global" view and eventually arrives at the same data and consesus as all other nodes. Public broadcast channels and fully connected graphs make the byzantine generals problem fairly trivial.
原始的Obelish设计是基于构建一个分布式时间戳，但是仅仅在完全连通图中才能工作。仅仅使用对每个节点可用的本地信息，没有分布式时间戳系统能实现可被证明的在网络中所有节点中发生事件的总体排序的共识。每个节点仅仅看到网络的一个子集。比较小数目服务器的完全连通情况是每个节点都有“全局”视野并和其它节点最终到达相同数据和共识的一个特殊情况。公开广播频道和完全连通图让拜占庭将军问题相当琐细。

While time stamp consensus and a full total ordering of events could not be achieved from the local information available to a node, randomized consensus allows provable global consenus from local information for non-pathological graph topologies. However, we were able to prove a weaker result which allows nodes to derive upper and lower bounds (a temporal interval) on events in the network. These bounds are local to each node or subset of nodes in the network and are very useful for detecting and preventing some type of Sybil attacks.
由于从每个节点可用的本地信息不能实现时间戳共识和完全的时间总体排序，对非病态的拓扑结构图，随机化共识可以从本地信息提供可被证明的全局共识。尽管如此，我们之前能提供一个稍弱一点的结果，使得节点推导出网络中事件的上界和下界（一个时间区间）。这些边界对网络中每个节点或者节点子集是本地化的，并且对于检测和防止某些类型的Sybil攻击非常有用。

Distributed Time Stamping:
分布式时间戳：
====

We show how you can create a distributed timestamping authority using the Obelisk public broadcast channel, time stamped blocks and receipts for block acknowledgements.
我们展示了你能如何使用Obelisk公开广播频道，时间戳区块和区块确认收据来创建一个分布式时间戳授权。

We want to create a system that allows us to prove with high certainty
- the publication time of a block 
- to establish that a node was active on the network and communicating 
- to prove that data existed and was published within a particular time interval
- prove that data did not exist at a time, or if it did exist was not published publicly
我们想要创建一个系统，它允许我们高确定性的证明
- 一个区块的发布时间
- 证明一个节点曾经在网络上活跃和通信
- 证明数据存在过并且在某一个特定时间段发布
- 证明数据在某个时间不存在，或者它并没有被公开发布过

Having this information allows us to build detection systems for cheating nodes. We want to show with high probability that a particular node is selectively denying messages, creating invalid time stamps, belongs to a colluding subgraph of the network or is otherwise unreliable and untrustworthy.
拥有这些信息使我们可以构建欺诈节点的检测系统。我们希望以很高概率确认一个特定节点正在选择性的拒绝消息，创建不正确的时间，属于一个勾结的网络子图，或者是不可靠和不值得信任的。

Each node is subscribed to the block chain of a list of other nodes. Every few seconds each node publishes a new block. Each block is time stamped and includes a list of hashes (receipts) of the blocks the node has received since the last block it published. Each published block is cryptographicly signed by the publishing node's private key.
每个节点被其他节点列表的区块链所订阅。每几秒钟，每个节点发布一个新的区块。每个区块加上时间戳并且包含一个节点自从它发布上个区块后已经接收到的区块哈希(收据)列表。每个发布的区块通过发布节点的私钥进行加密签名。

Each node is constantly publishing timestamped blocks and publishing receipts for blocks published by other nodes. This forms a dense, interlinking mesh of timestamps and receipts and counter receipts and make it very difficult for malicious node backdate events without detection.
每个节点一直持续发布时间戳区块并且发布由其他节点发布区块的收据。这形成了一个密集的，互连的时间戳，收据和计数器收据的网孔，并且使得它很难被恶意节点回溯事件而不被检测到。

The public broadcast channel imposes several constraints
- Once a block is published, it cannot be unpublished (blocks are replicated peer to peer to all subscribers. Once a block has been published, it spreads to all subscribers. You have to destroy all peers who have received the block to erase it from internet).
- A node cannot publish a different version of an earlier block without detection (blocks are numbered and it would be detected if the node signed two different blocks with the same sequence number)
- A node cannot backdate the time stamp on the receipt of a block, without delaying the publication of a block (timestamps only go up, time stamps increase monotonously with block sequence count)
- A block in the middle of the chain cannot be changed without invalidating every block that comes after it (linked time stamping, each block header contains a hash of the previous block)
公开广播频道强加了几个约束：
- 一旦发布一个区块，它不能被取消发布 （区块被点对点的复制到所有订阅者。一旦一个区块已经被发布，它将扩展到所有订阅者。你必须销毁所有已经接收到区块的节点来从网络上擦除它）。
- 一个节点不能发布一个之前区块的不同版本而不被检测到 （区块被编号并且如果节点使用同一个序列号签名了两个不同的区块将被检测到）
- 在不延迟区块发布情况下，一个节点对于接收到的区块不能回溯时间戳 （时间戳仅仅增长，时间戳随着区块序列号单调增加）
- 链中的一个区块不能在不报废之后区块情况下被修改 （链接的时间链，每个区块头部包含之前区块的哈希）

Situation:
情况：

A publishes a block. B publishes a block with a receipt for the block published by A. Then A publishes a new block with a receipt of the Block by B.
A发布了一个区块。B发布了一个带有A发布区块收据的区块。然后A发布了一个带有B区块收据的新的区块。

Node A is subscribed to Node B. Node B is subscribed to Node A.
节点A被节点B订阅。节点B被节点A订阅。
Example:
Node A publishes block A1 with time T1
Node B receives block A1
Node B publishes block B2 with time T2. B1 includes hash of block A1.
Node A receives block B2.
Node A publishes block A3 with time T3. A3 includes hash of block B2.
举例：
节点A发布带有时间T1的区块A1
节点B接收到区块A1
节点B发布带有时间T2的区块B2。B1包含区块A1的哈希。
节点A接收到区块B2。
节点A发布带有时间T3的区块A3。A3包含区块B2的哈希。

This is called a "2-cycle". If A trusts themselves and believes that their clock is honest, then A knows that block B2 existed and was published between times T1 and T3.
这称之为“2-cycle”。如果A信任它们自己并且相信它们的时钟是诚实的，那么A知道区块B2存在过并且在时间T1和T2之间发布。

If B2 was published before T1, then B2 could not include the hash of A1, because A1 did not exist yet. The probaility of guessing the hash by luck is 1 in 2^256.
如果B2在T1之前发布，那么B2不能包含A1的哈希，因为A1在那时还不存在。靠运气猜中哈希的概率是1比2^256。

If B2 was published after T3, then A3 could not include the hash of B2, because A3 could not include a hash for a block that did not exist at the time A3 was created.
如果B2在T3之后发布，那么A3不能包含B2哈希，因为A3不能包含在A3被创建时还不存在的一个区块的哈希。

Therefore B2 must have been produced after A1 was published and before A3 was published. Therefore if the clock of Node A is accurate and honest, B2 was created and published between times T1 and T3.
因此B2必须在A1被发布之后被产生并且在A3被发布之前。因此如果节点A的时钟是精确和诚实的，B2在时间T1和T3之间被创造和发布。

Therefore this construction allows us to prove with certainty that events happened on certain temporal intervals with respect to Node A's clock. There are higher order cycles, 3-cycles, 4-cycles and so on in the receipt graph. This establishes a distributed time stamping system with a calculus of temporal intervals.
因此，这种构造让我们可以依据节点A的时钟来确定性的证明事件在某个时间间隔内发生。在收据图中有更高的cycles，3-cycles，4-cycles等等。这建立了一种通过计算时间间隔的分布式时间戳系统。

You can show that, if a block  X1  published at time T, a cycle starting at a honest node and ending on the same honest node ending on T2, that T < T2. This upper bounds the publication time. If we have a receipt for a trusted node of successor block X0 with timestamp T1, T1 < T. The timestamp of the receipt of the previous block (X0) lower bounds the time interval for the publication of X1. This is another way of producing intervals using the monotonously increasing clock assumption.
你可以证明，如果一个区块X1在时间T发布，一个cycle起始于一个诚实的节点并且在时间T2终止于同一个诚实节点T2，T<T2。这上确界了发行时间。如果我们有一个受信任节点的时间戳T1的后续区块X0的收据，T1<T。之前区块（X0）的收据的时间戳下确界了X1发行时间的间隔。这是利用单调增加时钟假设产生时间间隔的另外一种方式。

Some nodes are honest and do not lie. Some nodes try to lie about timestamps and the order messages were received. If we have a cycle between dishonest nodes, the time stamps can be anything, subject to the constraint of the public broadcast channel. However if the cycle of receipts contains at least one honest node then it places a constraint on the timestamps.
有一些节点是诚实的，并且不撒谎。有些节点试图对时间戳以及消息接收到的顺序撒谎。如在不诚实节点间有一个cycle，时间戳可能是任何值，取决于公开广播频道的约束。尽管如此，如果cycle的接收者包含至少一个诚实节点，那么它就会给时间戳放置一个约束。

If we have a cycle of receipts, A -> B, B-> C, we say that the two cycles "interlink". Cycles between receipts within the subgraph of honest nodes interlink broadly. The multiple, interlinking timestamp and receipts form a dense interlinked mesh. If you say something existed at time 3, but did not publish it to network until time 8, all the honest nodes in network will have a timestamp of your block announcing the thing, with time greater than or equal to 8. Only nodes on a subgraph of lying or cheating nodes will have a lower timestamp.
假设我们有一个cycle的接收者，A->B，B->C，我们称这两个cycles“互连”。接收者之间的cycles在诚实节点子图内宽广的互连。多个互联的时间戳和收据形成了一个密集的互联网孔。如果你说在时间3存在什么事情，但是直到时间8之前并没有将它发布到网络，网络中的所有诚实节点对你宣布那件事情的区块有时间戳，时间大约等于8。仅仅撒谎和欺诈的子图上的节点才会有更低的时间戳。

Receipt Cycles Establish a Fair Total Ordering of Events with Respect to the Clock of a Given Node:
收据Cycles对于一个给定节点的时钟建立了一个公平的事件的总体排序：

To prove that a block Z existed by time 5, we can find a sequence of blocks that reference each other by hash, X1 -> Y1 -> Z1 -> X2. If block X2 was published by a trusted/honest node with an accurate clock, the timestamp on block X2 upper bounds the time Z1 was published to the network, even if we do not trust the node that published block Y or the node that published Z. 
为了证明一个区块在时间5之前存在，我们可以找到一个通过哈希互相引用的区块序列，X1 -> Y1 -> Z1 -> X2。如果区块X2由一个时钟精确的受信任/诚实的节点发布，区块X2上的时间戳上确界了Z1发布到网络的时间，即使我们不相信发布区块Y的节点或者发布Z的节点。

Choose a node X. We want to establish a temporal ordering on blocks with respect to X. We enumerate all cycles that originate at X (assume only cycles with one loop, cycles that start at X and end at X and do not pass through X multiple times). Each block will be contained in one or more cycles starting at X and ending at X. We say the time of a block with respect to X for a particular cycle is the time of the receipt produced by X that ends the cycle. For each event we choose the cycle with lowest ending timestamp, for each cycle that contains the event.
选择一个节点X。我们希望根据X建立一个区块的时间排序。我们枚举所有起源于X的cycles（假设一个loop的cycles，起始于X并且终止与X，并且不多次经过X）。每个区块将被包含在一个或多个起始并终结于X的cycles中。对于一个特定cycle，我们说根据X一个区块的时间是终结cycle的由X产生的收据的时间。对于每一个事件，我们选择具有最低终结时间戳的cycle，对于每个cycle则是包含该事件的最低。

So if we have cycles
X1 (t=1) -> Y1 -> X2 (t=3)  (cycle starting at block X1, ending at block X2, timestamp on x1 is 1, x2 timestamp is 3)
X1 (t=1) -> Y1 -> Z1 -> X3 (t=5)
所以如果我们有cycles 
X1 (t=1) -> Y1 -> X2 (t=3)  (cycle起始于区块X1，终结于区块 X2, x1时间戳是1, x2时间戳是3)
X1 (t=1) -> Y1 -> Z1 -> X3 (t=5)

Here, 
- Y is subscribed to X
- X is subscribed to Y
- Z is subscribed to Y
- X is subscribed to Z
其中， 
- Y被X订阅
- X被Y订阅
- Z被Y订阅
- X被Z订阅

We have cycles X->Y->X and X->Y->Z->X.

X produces block X1, which has timestamp t=1. Block Y has hash for block X1 in it, proving Y received the block. 
我们有 cyclesX->Y->X and X->Y->Z->X.

X产生区块X1，时间戳t=1。在区块Y中有区块X1的哈希，以证明Y接收到该区块。

X publishes X2 with block showing receipt for Y1 (which contains receipt for X1)
Z publishes Z1 with receipt for Y1
X publishes X3 (with timestamp t=5) with receipt for Z1
X发布X2包含接收到Y1的收据（其中包含X1的收据）
Z发布Z1包含Y1的收据
X发布X3（时间戳t=5）包含Z1收据

Block Y1 is involved in two cycles of X in this example. If we trust the clock of X, then we know that Y1 existed and was published before t=3 (we take the lower of the two cycles). If Y1 was the successor to block Y0, then we can lower bound the time Y1 was published at the time stamp of the block by X which acknowledges Y0.
在本例中区块Y1被包含在X的两个cycles中。如果我们信任X的时钟，那么我们知道Y1曾经在t=3之前存在和被发布 （我们选择两个cycles中较低的）。如果Y1是区块Y0的后继，那么我们可以降低Y1发布的时间到X确认Y0的区块时间.

This produces a time upper and lower bound for any block that can be reached by a receipt chain from X and which leads back to X. For a well conditioned graph, this will include nearly all blocks. For upper bounds for block publication time we take the least of any cycle ending time. For lower bounds we take the greater of the cycle ending times for the predeceding block.
对于可以通过起始于X的收据链到达的任意区块，这产生了一个时间的上确界和下确界。对于一个well conditioned图，这将近似包含所有区块。对于区块发布时间的上确界，我们选择任意cycle终结时间的最小值。对于下确界，我们选择前置区块cycle终结时间的最大值。

We can generalize this notion from "time with respect to node X" to time with respect to a subgraph of trusted nodes in the network. We take a subset of the network. We assume the nodes in the network have synced clocks and report time accurately. We allow a "cycle" that starts on any node in the subgraph and ends on any other node in the subgraph.
我们可以泛化“依据节点X的时间”这种方法表示到网络中一个受信任节点的子图。我们选择网络的一个子集。我们假定网络内的节点有同步时钟并且精确报告时间。我们允许一个“cycle”起始于子图中的任意节点并且终结于子图中的任意节点。

If nodes publish blocks every fifteen seconds or every minute, we can confidently bound the time interval of an event to a reasonably small time interval. We can show that things either did not exist at a given time or were not published to a causally accessible part of the network.
如果节点每十五秒或者每分钟发布区块，我们能有信心把一个时间的时间间隔限定在一个合理大小的时间间隔内。我们可以展示事情在一个给定时间要么没有存在，或者没有发布到网络内causally可访问的部分。

In a random graph of N nodes, where the block time per node is a constant k (say 15 seconds), the interval to which a random event can reliabily be causally resolved assuming only a single trusted node, grows with an upper bound of  k*log(N). 
在一个N个节点的随机图中，每个节点的区块时间是一个常数k（比如说15秒），假定仅有一个受信任节点，一个随机事件能够可靠的被解析的时间间隔，具有一个增长的上确界k*log(N)。

Methods to Eliminate the 51% Attack:
消除51%攻击的方法：
======

The distributed timestamping system can be used to prevent a 51% attack by even a majority of nodes, simply by rejecting and severing relationships with nodes who disconnect from the network and then reappear with provably backdated consensus decisions for blocks that were provably not published to the network at the claimed time.
分布式时间戳系统甚至能够被用来防止绝大多数节点进行的51%攻击，仅仅通过拒绝和断绝和已从网络断开的节点的关系，并且保证在宣称的时间，对于之前被证明过不可被发布到网络的区块，重新出现可被证明的回溯共识决定。

Similarly, nodes can become automaticly untrusted for remaining connected to the network and spontaneously deciding to attempt to revert previously established consensus for no justifiable reason.
类似的，对于剩余连接到的网络，不需要正当理由，节点能变得自动不受信任并且自发决定尝试撤销之前建立的共识。

In Bitcoin the classical 51% attack, a miner with majority hash power forks the blockchain, keeping his blocks secret. The miner gets ahead of the network in secret and suddenly publishes his longer chain. The network instantly switches to the attackers longer chain. Transactions are reverted and coins may have been stolen from exchanges.
在比特币经典的51%攻击中，一个具有绝大多数算力的矿工分叉了区块链，并且秘而不宣。矿工秘密的超过网络并且突然发布他自己更长的链。网络立即切换到攻击者更长的网络上。交易被撤销并且币可能会已经被从交易平台窃取。

The evil miner deposited Bitcoin in an exchange, bought Litecoin, withdraws the litecoin and uses a 51% attack to revert the deposit transaction and get his Bitcoin back but keeping the Litecoin. Then he uses the Litecoin to buy back cheap Bitcoin after the theft hits the media. The miner further more buys put options on Bitcoin and further magnifies his gains. The evil miner also decides to rob a bank at the same time, by depositing Bitcoin, withdrawling the Bitcoin and then reverting the deposit transaction. He now has both the withdrawn coins and the coins he never deposited from any bank which has not taken extremely difficult security measures.
邪恶矿工充值比特币到一个交易平台，买了莱特币，提取莱特币并使用51%攻击来撤销充值交易以重新获取他的比特币并且同时保留了莱特比。之后当盗窃事件在媒体发布后，他使用莱特币来便宜买回比特币。矿工甚至可以买空比特币来进一步扩大他的收益。邪恶矿工同时决定来抢劫一个银行，通过存入比特币，提取比特币并且然后撤销充值交易。他现在同时有了提取的币以及他从未充值的币，只要银行没有采取极其困难的安全措施。

In Skycoin, the distributed time stamping system allows individual nodes to determine locally that a node witheld information from the network and suddenly published it in a 51% attack attempt. Each node locally evaluates the information and chooses whether to ignore the influence of the potentially malicious node. In this way, a successful attack in a random graph now requires over 80% to 90% of the influential network nodes, not merely a majority. The honest nodes simply detect and ignore the 51% attack attempt.
在Skycoin中，分布式时间戳系统允许每个节点来本地化的决定一个节点之前是否在51%攻击尝试中通过对网络隐藏信息然后突然发布。每个节点本地评估信息然后选择是否忽略潜在恶意节点的影响。通过这种方式，在随机图中一次成功的攻击要求超过80%到90%的有影响力的网络节点，而不仅仅是大多数。诚实的节点可以简单的检测和忽略51%攻击尝试。

If each Node is informed by an indepedent but unreliable oracle for determining global consensus (each node samples consensus of a independent random subgraphs of the network), we believe the probability of a successful attack after a few block confirmations can be made arbritarily close to zero. This approach combines local information with indepedent random sampling of the global network state. Local state is used to determine and negotiate consensus and subgraphs of the global network are sampled to probabilistically determine if global network consensus has been reached and to detect netsplits.
假设每个节点由独立的但是不可靠的oracle通知决定全局共识（每个节点采样一个网络独立随机子图的共识），在几个确认后我们可以使进行一次成功攻击的概率任意接近于0。这种方法结合了本地信息和全局网络状态的独立随机采样。本地状态被用来判定和协商共识，并且采样全局网络的子图来概率意义上判决全局网络共识是否已经达到并且检测网络分叉。

Knowledge about the probability of global consensus on a block can be used to decide whether an attempt to fork an earlier block should be accepted. In the naive approach, if a majority of the nodes subscribed vote for a fork of an earlier block, the node will accept this fork.
区块中对于全局共识的概率知识可以用来决定对较早区块的分叉尝试是否应该被接受。在原始方法中，如果订阅的绝大多数节点投票赞成对较早区块的分叉，节点将接受这个分叉。

With a global consensus oracle, the votes for the fork become weighted by the belief that the purposed changes are a result of the legitimite process through which nodes in the network come into agreement (the network is still arriving at global consensus), or whether agreement has already been reached unanimously a long time ago and this is merely an attack in an attempt to revert previous consensus (for which there is no valid valid after global consensus has become unamimous among the active nodes).
通过全局共识oracle，对分叉的投票被下面的观点所加权，刻意的改变是一个合法过程的结果，指通过网络中哪些节点达成一致（网络仍然到达了全局共识），或者是否一致性在很长时间之前已经无争议的达成，并且这仅仅是一次试图撤销之前共识（如果在活跃节点间全局共识已经无争议之后，这将是不正确的）的攻击尝试。

Another prospective approach uses a hybrid system of Ben Or randomized consensus on a web of trust to vote a commitee of trusted masternodes, who form a fully connected public Quorum which determines block consensus. The commitee election might be daily and more resources can be put into verifying global consensus on the single commitee election than verifying consensus on individual blocks.
另外一种可能的方式可使用一种Ben Or随机化共识的混合系统，它基于信任网络来投票受信任主节点委员会从而形成了一个完全互连的公开的Quorum，用来决定区块共识。

We are looking at several different approaches. Skycoin consensus will change as we develop better algorithms and software infrastructure.
我们正在研究几种不同的方式。Skycoin共识将随着我们开发更好的算法和软件框架而改变。