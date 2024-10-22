---
title: "Master Solidity : Conditional Statements"
seoTitle: "Master Solidity : Conditional Statements"
datePublished: Sun Nov 13 2022 12:20:12 GMT+0000 (Coordinated Universal Time)
cuid: clafbrbyc000508l0gmkhhblj
slug: master-solidity-conditional-statements
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1653665619921/MzXTjuVXW.png
tags: data-structures, blockchain, ethereum, solidity, web3

---

# Introduction

If solidity is not your first language then you might be familiar with these conditional statements. If you are a beginner, I'll recommend you to read the article from the start for a better understanding.


> For those searching for Advance Smart Contracts, kindly skip to the topic "*NFT based Smart Contracts*".

A **conditional statement** will select the block of statements that will execute based on the given condition. The result of the program depends on the condition. These conditional statements are often referred as If Else Statements.

# If-Else Statements

The **if-else** statement executes a block of code if a specified condition is *true*. 
If the condition is false, program execution jumps and another block of code can be executed.

> Note : Conditional statements follow the principle of control flow i.e. execution of statements in an order.

Syntax :

> **if :** to specify a block of code to be executed, if a specified condition is true.


```
if (condition) {
  // block of code to be executed if the condition is true
}
``` 

> **else if :** to specify a new condition to test, if the first condition is false.


```
if (condition1) {
  // block of code to be executed if condition1 is true
} else if (condition2) {
  // block of code to be executed if the condition1 is false and condition2 is true
} else {
  // block of code to be executed if the condition1 is false and condition2 is false
}
```



> **else :** to specify a block of code to be executed, if the same condition is false.


```
if (condition) {
  // block of code to be executed if the condition is true
} else {
  // block of code to be executed if the condition is false
}
``` 

## Let's build a smart contract to understand this

*Example *

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;

// 1. if a is less 10, value will return 1
// 2. if a is less 20, value will return 2
// 3. Any number above 20 will return 3

contract Conditions {
   function checks(uint a) public pure returns(uint){
      if(a<10)
      {
           return 1;
       } 
       else if (a < 20)
         {
           return 2; 
         } 
       else     //it can also work without else statement
        return 3;
   } 
}
   
``` 
## Output of the above Smart Contract

1. **When a = 55**

![a3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653652663886/37TlmWP32.png align="left")

2. **When a = 19**

![a4'.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653652674487/lZvi2RdI_.png align="left")

3. **When a = 5**

![a6.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653652682869/4uAIPC_9Z.png align="left")

> Note : When a < 0, like -5 or -45. There will be not effect on the value since the variable a is an unsigned integer which can hold 0 and positive integers.

# Ternary/Conditional Operator 

The conditional operator is kind of similar to the if-else statement as it does follow the same algorithm but the conditional operator takes less space and helps to write the if-else statements in the shortest way possible.
Less space means fast execution and less transaction fees or gas. So you should know when to use either of them.

*Below is an example of if-else statement compared to conditional/ternary operator.
*

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;

contract Conditions {
   function checks(uint a) public pure returns(uint){

     if (a<10) {
         return 1;
        }
         return 2;

      return a< 10 ? 1 : 2;
   }
}
          

``` 
***Can be written in one line***

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;

contract Conditions {
   function checks(uint a) public pure returns(uint){

      return a < 10 ? 1 : 2;
   }
}
          

``` 


**Again, If you are a beginner kindly read the whole article for better understanding.**

# NFT based Smart Contracts:

## CryptoKitties 😻


![n.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653657862121/-YcDsHGHS.png align="left")

[CryptoKitties](https://www.cryptokitties.co/) is a Blockchain based play-to-earn game where people can collect and trade kitties. They can even breed two kitties to get a new kitty. One can earn ETH by selling their kitties or rent them for breeding.

The most interesting thing is that these child kitties share a mix of parents genes. Since theses kitties do not have any gender, it creates endless possibilities for breeding.

[Click here to watch CryptoKittes video. ](https://www.youtube.com/watch?v=3PTstAK-cH8&t=10s)

There's a lot more to this amazing games but for now we will discuss how does these conditional statements play great role in their smart contract for *Breeding Kitties*.

This is how a CryptoKittes can be created by breeding:

Here, a *matron* : (similar to “female”)

Here, a *sire* : (similar to “male”)

Note : Not every matron and sir can be breed together otherwise the uniqueness behind the NFTs is compromised.

You can find this Contract here [KittyBreeding.sol](https://github.com/dapperlabs/cryptokitties-bounty/blob/79cb69e7aadfc68fc116cd82dcc21f4336cc744c/contracts/KittyBreeding.sol#L117-L162)



*KittyBreeding.sol.*

```

pragma solidity ^0.4.18;

import './ExternalInterfaces/GeneScienceInterface.sol';
import './KittyOwnership.sol';


/// @title A facet of KittyCore that manages Kitty siring, gestation, and birth.
/// @author Axiom Zen (https://www.axiomzen.co)
/// @dev See the KittyCore contract documentation to understand how the various contract facets are arranged.
contract KittyBreeding is KittyOwnership {


/// @dev Internal check to see if a given sire and matron are a valid mating pair. DOES NOT
    ///  check ownership permissions (that is up to the caller).
    /// @param _matron A reference to the Kitty struct of the potential matron.
    /// @param _matronId The matron's ID.
    /// @param _sire A reference to the Kitty struct of the potential sire.
    /// @param _sireId The sire's ID
    function _isValidMatingPair(
        Kitty storage _matron,
        uint256 _matronId,
        Kitty storage _sire,
        uint256 _sireId
    )
        private
        view
        returns(bool)
    {
        // A Kitty can't breed with itself!
        if (_matronId == _sireId) {
            return false;
        }

        // Kitties can't breed with their parents.
        if (_matron.matronId == _sireId || _matron.sireId == _sireId) {
            return false;
        }
        if (_sire.matronId == _matronId || _sire.sireId == _matronId) {
            return false;
        }

        // We can short circuit the sibling check (below) if either cat is
        // gen zero (has a matron ID of zero).
        if (_sire.matronId == 0 || _matron.matronId == 0) {
            return true;
        }

        // Kitties can't breed with full or half siblings.
        if (_sire.matronId == _matron.matronId || _sire.matronId == _matron.sireId) {
            return false;
        }
        if (_sire.sireId == _matron.matronId || _sire.sireId == _matron.sireId) {
            return false;
        }

        // Everything seems cool! Let's get DTF.
        return true;
    }

``` 

Okay, Now understand if else with the above smart contract.

**If Statatement :**

[*See KittyBreeding.sol, line 134.*](https://github.com/dapperlabs/cryptokitties-bounty/blob/79cb69e7aadfc68fc116cd82dcc21f4336cc744c/contracts/KittyBreeding.sol#L134)

Matron and the Sire cannot have same ID as kittens cannot breed with themselves. 
Therefore, . So if the matron is the same as the sir, it is not a valid mating pair. 

> *Condition : A kitty can't breed itself*
        
> if (_matronId == _sireId) {            
>     return false;        
> }

**Condition one not true then jump to another one :**

[*See the KittyBreeding.sol, line 139.*](https://github.com/dapperlabs/cryptokitties-bounty/blob/79cb69e7aadfc68fc116cd82dcc21f4336cc744c/contracts/KittyBreeding.sol#L139)

According to the condition kitties cannot breed with their parents. Thus making the pair invalid if true.

Here we see the use of Logical Operator || inside the condition. 
(The logical OR operator (||) returns the boolean value true if either or both operands is true and returns false otherwise.) 
Therefore, If at least one of the two conditions evaluates to true, the code inside the if block will run.


> *Condition : Kitties can't breed with their parents. *       

> if (_matron.matronId == _sireId || _matron.sireId == _sireId) {        
>     return false;        
> }
> if (_sire.matronId == _matronId || _sire.sireId == _matronId) {            
>     return false;        
> }


# Conclusion

Conditional statements should be used according to the number of conditions inside a smart contract. As it would not be wise to use if-else statement where one can use ternary operator which might effect in transaction fees/gas, storage, and speed efficiency.


***Thanks for taking the time to read this article!***

**▶Next : [Master Solidity Series](https://manavpaul.hashnode.dev/series/solidity-tutorial)**

**Documenting my journey with Solidity, Blockchain and Web3**

Drop a comment here, share or hit me up on Twitter! ♥

