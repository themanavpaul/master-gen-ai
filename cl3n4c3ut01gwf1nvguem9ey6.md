---
title: "NEO Blockchain : Ultimate Blockchain for Developers"
seoTitle: "Neo Blockchain : Ultimate Blockchain for Developers"
seoDescription: "Neo N3 blockchain is an open-source decentralized blockchain platform that supports its own crypto currency and provides various native infrastructures."
datePublished: Thu May 26 2022 14:36:38 GMT+0000 (Coordinated Universal Time)
cuid: cl3n4c3ut01gwf1nvguem9ey6
slug: neo-blockchain-ultimate-blockchain-for-developers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1653570618132/2Q2TdE6MJ.png
tags: blockchain, ethereum, solidity, web3, thw-web3

---

# Introduction

**Neo** is an open-source decentralized blockchain based platform that supports its own crypto currency and enables the development of digital assets and smart contracts.
Just like Ethereum, one can create crypto transactions and create smart contracts and decentralized applications.

It is the most feature-complete blockchain platform for building decentralized applications. Neo enables developers to digitize and automate the management of assets through smart contracts. It also provides powerful native infrastructures which we will understand more about in the below article.

# Origin

Neo was founded by *Da Hongfei* and *Erik Zhang* in 2014 under the name *Antshares*. The original source code was published to GitHub in July 2015 and the MainNet subsequently launched in October 2016.



![11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653570644521/lXgr47HQw.png align="left")

In 2021, Neo is being upgraded to version 3.0, known as ***N3***. As a project that began in June 2018, the N3 upgrade represents the biggest advancement in Neo’s history since it was largest asset migration in history. It is aimed at bringing the first all-in-one blockchain development experience to the industry, packed with powerful native features. Neo N3 also boasts a simpler and more modular architecture than its predecessors, along with an improved governance and economic model.


Let's understand how NEO N3 is a Smart Economy Chain and not just a Smart Contract Chain as compared to others.

# NEO N3 : Smart Economy Chain



![13.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653570655387/nnm23WZtx.png align="left")

## 1. Multi-Language Support

As we have seen in other blockchains, they support the use of a single programming language.

Example :

> Ethereum - Solidity, 
> Solana - Rust

Whereas, NEO provides support to multiple languages.

Example :

> C#, Python, Go, Typescript, and Java.

Most of the programmers are familiar with these language as their building blocks of learning a programming language.

## 2. Decentralized Storage

Blockchain Technologies other than NEO do not provide a decentralized storage which one can use to store or share data.

For example, if someone wants to store any images/videos on the  blockchain network he/she has to pay a lot of fees/gas. In order to store your media file on blockchain we use **IPFS** (InterPlanetary File System) is a protocol and peer-to-peer network for storing and sharing data in a distributed file system.

On the other hand, Neo provides a native infrastructure known as **NeoFS **or ***Neo File Storage.***

**NeoFS** is a distributed, decentralized object storage network developed by Neo SPCC. NeoFS aims to support the shift away from third-party storage providers, providing users with complete control over their data. Here all files will be stored in strict format so nobody else can read your files.

Nodes are organized in peer-to-peer network that takes care of storing and distributing user's data. Any Neo user may participate in NeoFS network and get paid for providing storage resources to other users or store his data in NeoFS and pay a competitive price for it.

The service is designed to work with Neo smart contracts, allowing for truly decentralized applications, and can also be used as a content delivery network. Users can rent out storage in return for Neo GAS tokens or use GAS to store files in the network.


## 3. External Data Access

**No external data access:**

Suppose you want to create a smart contract that fetches crypto currency prices. Now these prices are external to the blockchain environment. We need to fetch these data from an outside environment. Therefore, in other blockchain networks it is not possible until you have a third party support.

**Neo Native Oracle** : 

*Neo Oracle* solves the problem that blockchain cannot obtain information from the external network. As a gateway for smart contracts to communicate with the outside world, Oracle opens a window to the outside world for blockchain.



![14.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653570668326/THBJNPcAF.png align="left")

Neo Oracle Service is an out-of-chain data access service built into Neo N3.
It allows users to request the external data sources in smart contracts, and Oracle nodes designated by the committee will access the specified data source then pass the result in the callback function to continue executing the smart contract logic.


## 4. Ecosystem Friendly

If we see other blockchain networks, there are not considered ecosystem friendly.
One needs to do a lot of hard work in order to achieve communication between two different blockchains.

Neo is considered to be an ecosystem friendly network.
Neo blockchain provides communication between different blockchains with the help of *poly network*. **Poly Network** is a global cross-chain protocol for implementing blockchain interoperability and building Web3.0 infrastructure. In other words,
poly network helps Neo to interact and with other blockchain networks.

## 5. Block Finality

Before we began, first we need to understand what ***finality*** means?

After getting all the grocery items you went to the cashier and swiped your card to pay for your items. After a few seconds the cashier gives you the receipt as the transaction is successful. The cashier was certain that the transaction went through and it would not be reverted back later. Therefore it is said that the payment was finalized.

In Blockchain, ***finality*** is the confirmation that all well-formed blocks will not be revoked once committed to the blockchain. When users transact, they want to be confident that once their transactions process begins, the transactions cannot be arbitrarily changed or reversed.

**Multi-Block Finality:**

In case of bitcoin for a transaction to be confirmed we need to wait for six block confirmation approx. 1 hour.

**One Block Finality:**

In case of Neo once a transaction is confirmed, it is confirmed. They make sure your funds are actually yours within 1 block. Therefore it helps in saving a lot of time.

So, How does Neo achieve this technique?

It uses a term called ***dBFT consensus (Delegated Byzantine Fault Tolerance)***. The algorithm is meant to facilitate consensus on a blockchain

Let's understand this with A problem called Byzantine Generals Problem.
Imagine a city where a bunch of generals want to attack. Well, they will be successful in their mission.
However some of the generals decided "not to attack". Then those generals who attack, will fail the invasion.

So, How do we trust that all the generals will attack the city at the same time?

Let's say if they do have a messenger acting as a means of communication between them. General 1 will say "not to attack" but the messenger turns out to be an imposter and will convey the message "Attack the city" to General 2.
This will lead in a failed invasion again.

This is the same problem when there is an agreement on blockchain.

Neo Blockchain on the other hand has a solution to this problem by using an algorithm called **dBFT (Delegated Byzantine Fault Tolerance)**.

### **Mechanism of dBFT:**


![12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653570680282/5lRn4VFIY.png align="left")

NEO token holders have the right to vote for delegates (generals). 
From the delegates, a speaker is chosen randomly.
The speaker builds a new block from the transactions that waits to be validated.
Then, the speaker sends the proposal to the elected delegates. They are expected to keep track of all the transactions and record them on the network. 
The proposed block is approved when 66% of the other delegates also approves this block.

## 6. Name Service Facility

Can you write your public address or last smart contract transaction hash? 
Probably No ! Because it is difficult to memorize such huge cryptic addresses and hashes.

Example of an address:

> 0x34872378423784687246f6s83hh2i423f7s930
 
It is a hectic process of copying and pasting the addresses.
In other blockchain you will not find name service facility.

Neo provides NNS (Neo Name Service) which solves this issue.

Example:

> 0x34872378423784687246f6s83hh2i423f7s930

> NNS maps public key or transaction id with a familiar name like

> manav.neo  ( this now act as a public key)

### Usabillity offers:

**Security : **
Shorter address solves security problem as it will be quite obvious and easy for anybody to see if the address has been tampered with.

**Speedy Transactions:**
Well it is easy to write *manav.neo* instead of copying my long address from one page to another to initiate a transaction.

# Why Neo is so special ?


## **Neo Id :** 

*Neo Id *is a set of self-sovereign decentralized identity solution standards.
You have control over your data.
You can control the amount of data to be shared, who you want to or don't want to share that data.
It also prevents you from *Sybil Attack*.


![16.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653572222361/AqR07W-Dn.png align="left")

**Sybil Attack** is a type of attack in which main aim is to gain the majority of influence in the network to carry out illegal actions in the system. A single entity(system) has the capability to create and operate multiple identities(user accounts, IP address based accounts). To outside observers, these multiple fake identities appear to be real unique identities.



## **Neo Best Tooling:**

- Developer friendly platform : Easy to interact and to work with.


![15.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653572315204/Nvf721dwt.png align="left")

- Neo Blockchain toolkit for VS Code : One can achieve Network Development, Testing smart contracts and Debug programs.



***Thanks for taking the time to read this article!***

**▶Next : [Master Solidity: Build decentralized applications.](https://manavpaul.hashnode.dev/series/solidity-tutorial)**

Documenting my journey with Solidity, Blockchain and Web3.

Drop a comment here, share or hit me up on Twitter! ♥



*Sources:*

[Neo Documentation](https://docs.neo.org/docs/en-us/index.html)
[Code Eater](https://www.youtube.com/watch?v=C3Lzsn0rjcY&t=13s)
[Whiteboard Crypto](https://www.youtube.com/watch?v=I_vCOzEbSMI&t=151s)
[GeeksforGeeks](https://www.geeksforgeeks.org/sybil-attack/)

