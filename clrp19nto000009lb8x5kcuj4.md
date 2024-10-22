---
title: "ERC-20 Tokens : A Complete Guide"
seoTitle: "ERC20 Token Guide"
datePublished: Mon Jan 22 2024 14:39:13 GMT+0000 (Coordinated Universal Time)
cuid: clrp19nto000009lb8x5kcuj4
slug: erc-20-tokens-a-complete-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1654234842714/jQzx2EQtz.png
tags: blockchain, crypto, ethereum, solidity, erc20

---

# Introduction

As we know Vitalik Buterin founded Ethereum in 2014. An open-source platform for launching decentralized applications. Main idea kept in mind for the creation of a new blockchain was to provide solutions that Bitcoin protocol faces that is lack of flexibility.

In this article we will learn about ERC-20 standards and why is it an inspiration to the other blockchain standards like Binance Chain's BEP-2.

Before we began with ERC-20 standard, we need to understand what a token is?

# **What is a Token ?**

Tokens, basically, are non-mineable digital units of value that exist as registry entries in blockchains.

Issued by companies using existing third-party blockchains such as the Ethereum blockchain

Tokens can represent virtually anything in Ethereum:

* reputation points in an online platform
    
* lottery tickets
    
* financial assets like a share in a company
    
* a fiat currency like USD
    
* an ounce of gold
    
* and more...
    

---

# What is the ERC-20 standard ?

An ERC is an Ethereum Request for Comments. These are technical documents that outline standards for programming on Ethereum. ERCs aim is to establish easier interaction between applications and contracts.

> **ERC-20** : Ethereum Request for Comments 20

It was proposed by *Vitalik Buterin* and *Fabian Vogelsteller* in November 2015, is a Token Standard that implements an API for tokens within Smart Contracts.

Once new ERC-20 tokens are created, they’re automatically interoperable(system can interact with other systems) with services and software supporting the ERC-20 standard (software wallets, hardware wallets, exchanges, etc.).

It should be noted that the **ERC-20** standard was developed into an *Ethereum Improvement Proposal* or **EIP** (specifically, EIP-20). This happened a couple of years after the original proposal due to its widespread use. However, even years later, the name **ERC-20** has stuck.

If you want to know more about [EIPs](https://ethereum.org/en/eips/).

# Brief intro to Ethereum Tokens

In Ethereum, unlike ETH, ERC-20 tokens aren’t held by accounts.

Tokens only exist inside a contract, which is a self contained database. It specifies the rules for the tokens (i.e., name, symbol, divisibility) and keeps a list that maps user's balances to their Ethereum addresses.

To move tokens, users must send a transaction to the contract asking it to allocate some of their balance elsewhere.

**Example**

If Priya wants to send 1,000 BAT tokens to Anshu.

> 1. She calls a function inside the BAT smart contract asking it to do so.
>     
> 2. Her call is store inside a regular Ethereum transaction that pays 0 ETH to the token contract.
>     
> 3. The call is included in an additional field in the transaction, which specifies what Priya wants i.e. to transfer tokens to Anshu.
>     
> 4. Priya isn't sending ether but she must still pay a fee for her transaction to be stored in a block. For that she needs some ETH before transferring the tokens.
>     

Here's a real-world example of the above on Etherscan : Transaction for an **ERC-20** token, *Tether USD (USDT)*

![trans.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654236137922/W695ZV7Pj.png align="left")

So now you know what ERC-20 tokens are and how they are different from ETH and their process transactions. Now lets understand the architecture of ERC-20 Tokens.

---

# How are ERC-20 tokens created?

\*ERC-20 token's architecture consists of 6 mandatory functions : \*

> totalSupply, balanceOf, transfer, transferFrom, approve, and allowance.

In addition, you can specify optional functions, such as *name*, *symbol*, and *decimal*.

### 1\. totalSupply()

```sql
function totalSupply() public view returns (uint256)
```

When called by a user, the above function returns the total supply of tokens that the contract holds.

> Total Supply - It is the sum of coins that were already mined (or issued) minus the total of coins that were burned or destroyed.

### 2\. balanceOf()

```sql
function balanceOf(address _owner) public view returns (uint256 balance)
```

Unlike *totalSupply*, *balanceOf* takes a parameter (an address). When called, it returns the balance of that address’s token holdings. Since accounts on the Ethereum network are public, so you can query any user’s balance provided you know the address.

### 3\. transfer()

```sql
function transfer(address _to, uint256 _value) public returns (bool success)
```

***transfer*** aptly transfers tokens from one user to another. Here, you provide the address you want to send to and the amount to transfer.

When called, ***transfer*** triggers something called an **event** (event transfer), which basically tells the blockchain to include a reference to it.

### 4\. transferFrom()

```sql
function transferFrom(address _from, address _to, uint256 _value) public returns (bool success)
```

The ***transferFrom*** function is a good alternative to transfer that enables a bit more control over programs in decentralized applications.

Like ***transfer***, it’s used to move tokens, but those tokens may or may not to belong to the person calling the contract. In other words, you can authorize someone – or another contract – to transfer funds on your behalf.

\*Example \*

> Subscription based services like Netflix where program function is to deduct the payments automatically every week/month/year as per your choice.

This function triggers the same event as ***transfer***.

### 5\. approve()

```sql
function approve(address _spender, uint256 _value) public returns (bool success)
```

***approve*** can limit the number of tokens that a smart contract can withdraw from your balance. It prevents the risk of the contract malfunctioning (or being exploited) and stealing all of your funds.

When called, ***approve*** triggers the approval **event**. Like the ***transfer*** event, it writes data to the blockchain.

***Example***

> Lets take Netflix's example. Suppose that you have a huge amount of X tokens, and chose to setup up weekly payment option. You don't have time to take manual transactions.
> 
> You have a huge balance of X tokens, which is lot more than the subscription. To prevent Netflix to used all of X tokens, you can set a limit with ***approve***.
> 
> Subscription costs = one *X token per week*.

> You limit the approved value at = *twenty X tokens*

> Subscription will be paid automatically for = *5 months*.
> 
> ( 4 weeks = 1 month ; 4 tokens/month ; 20 tokens = 5 months. )
> 
> So, if one day Netlfix attempts to withdraw all your funds or if a bug is found, you can only lose *twenty tokens*.

### 6\. allowance()

```sql
function allowance(address _owner, address _spender) public view returns (uint256 remaining)
```

***allowance*** can be used in conjunction with ***approve***. When you’ve given a contract permission to manage your tokens, you might use this to check how many it can still withdraw.

For example, if Netflix has used up twelve of your twenty approved tokens, calling the allowance function should return a total of eight. (refer to the above example for better understanding)

## The Optional Functions

The previously-discussed functions are compulsory. On the other hand, ***name, symbol, and decimal*** don’t need to be included, but they can make your ERC-20 contract a bit prettier.

### name

Returns the name of the token - e.g. "ManavPaul".

### symbol

Returns the symbol of the token. E.g. “MPX”.

### decimals

Returns the number of decimals the token uses - e.g. 8, means to divide the token amount by 100000000 to get its user representation.

---

# ERC-20 Smart Contract

```sql

/*
Implements EIP20 token standard: https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md
.*/


pragma solidity ^0.4.21;

import "./EIP20Interface.sol";


contract EIP20 is EIP20Interface {

    uint256 constant private MAX_UINT256 = 2**256 - 1;
    mapping (address => uint256) public balances;
    mapping (address => mapping (address => uint256)) public allowed;
    /*
    NOTE:
    The following variables are OPTIONAL vanities. One does not have to include them.
    They allow one to customise the token contract & in no way influences the core functionality.
    Some wallets/interfaces might not even bother to look at this information.
    */
    string public name;              //Any name: eg Manav Paul
    uint8 public decimals;           //How many decimals to show.
    string public symbol;            //An identifier: eg MPX

    function EIP20(
        uint256 _initialAmount,
        string _tokenName,
        uint8 _decimalUnits,
        string _tokenSymbol
    ) public {
        balances[msg.sender] = _initialAmount;          // Give the creator all initial tokens
        totalSupply = _initialAmount;                   // Update total supply
        name = _tokenName;                              // Set the name for display purposes
        decimals = _decimalUnits;                       // Amount of decimals for display purposes
        symbol = _tokenSymbol;                          // Set the symbol for display purposes
    }

    function transfer(address _to, uint256 _value) public returns (bool success) {
        require(balances[msg.sender] >= _value);
        balances[msg.sender] -= _value;
        balances[_to] += _value;
        emit Transfer(msg.sender, _to, _value); //solhint-disable-line indent, no-unused-vars
        return true;
    }

    function transferFrom(address _from, address _to, uint256 _value) public returns (bool success) {
        uint256 allowance = allowed[_from][msg.sender];
        require(balances[_from] >= _value && allowance >= _value);
        balances[_to] += _value;
        balances[_from] -= _value;
        if (allowance < MAX_UINT256) {
            allowed[_from][msg.sender] -= _value;
        }
        emit Transfer(_from, _to, _value); //solhint-disable-line indent, no-unused-vars
        return true;
    }

    function balanceOf(address _owner) public view returns (uint256 balance) {
        return balances[_owner];
    }

    function approve(address _spender, uint256 _value) public returns (bool success) {
        allowed[msg.sender][_spender] = _value;
        emit Approval(msg.sender, _spender, _value); //solhint-disable-line indent, no-unused-vars
        return true;
    }

    function allowance(address _owner, address _spender) public view returns (uint256 remaining) {
        return allowed[_owner][_spender];
    }
}
```

# Can ERC-20 tokens be mined ?

One can mine ETH, but not the tokens. They are ***not mineable***, though we say they are ***minted*** when new ones are created.

Mine vs Mint in Crypto

> Crypto **mining** uses a ***Proof of Work (PoW)*** protocol.
> 
> Crypto ***minting*** uses a ***Proof of Stake (PoS)*** protocol.

Developers distribute fixed amount tokens when a contract is launched.

It is achieved via an Initial Coin Offering (ICO), Initial Exchange Offering (IEO), or Security Token Offering (STO). Investors send ETH to contact address and receive new tokens. Collected money is used to fund further development on the project. Users can use their tokens resell them for a profit.

> Initial Exchange Offering (IEO) - here fundraising will be conducted on a well-known exchange’s fundraising platform
> 
> Security Token Offering (STO) - enable asset tokenization, digital funding, while still complying with government regulations.
> 
> Initial Coin Offering (ICO) - here funds are raised for a new cryptocurrency venture where the project team themselves conduct the fundraising.

# Merits of ERC-20 Tokens

**Fungible**

ERC-20 tokens are fungible – each unit is interchangeable with another. They are identical in nature like cash or gold.

**Flexible**

ERC-20 tokens are highly customizable and can be tailored to many different applications. The token is user-friendly.

**Popularity**

Widely used token standard and supported by a majority of exchange and wallets. Thus, it is commonly adopted.

# Demerits of ERC-20 Tokens

**Dependability**

The ERC-20 tokens or any other tokens are based and built on top of Ethereum. This poses a threat, since Ethereum is itself undergoing frequent changes at most times.

**High Gas Costs**

Sending a transaction in peak times will result in higher gas fees and delays. Therefore, the traffic on the network effects its usability.

**Scams**

Since it is easy to create a simple ERC-20 token, meaning that anyone could do it – for good or for bad. Since there are many fake projects on blockchain, one must be aware before investing.

***Thanks for taking the time to read this article!***

**▶Next :** [**Master Solidity Series**](https://manavpaul.hashnode.dev/series/solidity-tutorial)

**Documenting my journey with Solidity, Blockchain and Web3**

Drop a comment here, share or hit me up on Twitter! ♥