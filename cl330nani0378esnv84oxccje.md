---
title: "Master Solidity : Break and Continue Statements"
seoTitle: "Master Solidity - Break and Continue Statements"
seoDescription: "Solidity tutorial for beginners. Create smart contracts in solidity and build decentralized applications. Learn the use of break and continue statements."
datePublished: Thu May 12 2022 12:57:58 GMT+0000 (Coordinated Universal Time)
cuid: cl330nani0378esnv84oxccje
slug: master-solidity-break-and-continue-statements
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1652461153557/9RaX-OiSz.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1652362940470/b4JrQpC7u.png
tags: blockchain, ethereum, solidity, web3, thw-web3

---

# **Introduction**

Suppose you are copying files from folder1 to folder2. So you select and copy all the files from folder1 and paste them into folder2. But wait, the pop says that folder2 already has 2 files with the same name as in folder1. So you click on the skip button for the files with same name and rest of the files are copied.

**Well this is what *continue statement* is!**

Or when you are installing a software and while installing, the software doesn't meet some specific requirements and it fails at 99% completion. 

**This is what *break statement* does**

## Overview

Just like other programming languages, Control statements are used to change the execution of the program.

> Control statements : break, continue.

> Let’s look at them one by one.


# Control Statements
Control statements are used when we have to skip/jump some part of the block of code in a loop and start the new iteration or it can terminate the loop without reaching at the end of it.

Therefore to handle the execution of the program solidity provides us the following control statements.
- Break
- Continue


## Break Statement
This statement is used when we have to terminate the loop or switch statements or some block of code in which it is present.
After the break statement, the control is passed to the statements present after the break. 
In nested loops, break statement terminates only those loops which has break statement.
> Break only allowed inside for, while or do-while loops.


**Let us understand this with an Example.**

Here in the contract **breakstatement** , we have a dynamic array named **data**, an unsigned integer variable named **a**, and a function containing the while loop to demonstrate the working of the break statement.

***This program insert the elements in a dynamic array***

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;
/*
Solidity Program to show the use of Break Statement
*/
// Creating a contract
contract breakstatement{

    // Declaring a dynamic array   
    uint[] data; 
    
    // Declaring the state variable
    uint a = 0;
  
// Creating a function with while loop inside it
    function loop(
    ) public returns(uint[] memory){
    while(a < 6) {
        a++;
        if(a==3){
            break;
// when value of a is 3, then it will jump out of the loop
        }
        data.push(a);
     }
      return data;
    }
  //To show the elements of the array
         function getarr() public view returns(uint[] memory){
        return data;  
    }
// To determine the length of the array
    function getlength() public view returns(uint){
        return data.length;
    }
}

``` 

### Working of the Break Statement
In the above contract, an unsigned integer 'a' is initialized 0.
1. As a=0, while(a<6) is true
2. unsigned integer 'a' is incremented to 1 (as a++) i.e. a=1.
3. The if statement check is false, as a=1
4. The value of a is inserted into the dynamic array 'data'.
5. Loop will repeat till a=3.
6. Now the if statement is *true*, thus loop will break.

### Output of the above Smart Contract

- *Before the loop() function execution.*

> Array data =[ ]    //empty

> Array length = 0

![blog1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652341924840/ThJcZdrOI.png align="left")

- *After the loop() function executes.*

> Array data =[1,2]

> Array length = 2

![blog2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652341934759/Boro3lHQ-.png align="left")


## Continue Statement

Continue statement is used when we have to skip/jump the remaining block of code and start the next iteration of the loop immediately. 
When the continue statement is executed, the control is then transferred to the loop check condition, and if the condition is true the next iteration resumes.


**Let us understand this with an Example.**

Here in the contract **continuestate** , we have a dynamic array named **data**, an unsigned integer variable named **j**, and a function containing a while loop to demonstrate the working of the conitnue statement.

***This program insert the elements in a dynamic array***

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;

/*
Program to show the use of Continue Statement
*/

// Creating a contract
contract continuestate{

    // Declaring a dynamic array   
    uint[] data; 

    // Declaring the state variable
    uint a = 0;

// Creating a function with while loop inside it
    function loop(
    ) public returns(uint[] memory){
    while(a < 6) {
        a++;
        if(a==3){
            continue;
// when value of a is 3, then it will skip
        }
        data.push(a);
     }
      return data;
    }
  //To show the elements of the array
         function getarr() public view returns(uint[] memory){
        return data;  
    }
// To determine the length of the array
    function getlength() public view returns(uint){
        return data.length;
    }
}

``` 

### Working of the Continue Statement

In the above contract, an unsigned integer 'a' is initialized 0.
1. As a=0, while(a<6) is true
2. unsigned integer 'a' is incremented to 1 (as a++) i.e. a=1.
3. The if statement check is false, as a=1
4. The value of a is inserted into the dynamic array 'data'.
5. Loop will repeat till a=3.
6. Now the if statement is *true*, thus loop will skip.
7. While loop begins with next iteration.

### Output of the above Smart Contract

- *Before the loop() function execution.*

> Array data =[ ]   //empty

> Array length = 0

![state1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652343691181/nfcumEPTk.png align="left")

- *After the loop() function executes.*

> Array data =[1,2,4,5,6]

> Array length = 5

![state2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652343701278/M5DlB6QTd.png align="left")

> Note : Continue work differently in for, while, do-while loops.

Example : Continue and break in a For Loop

```
// Continue and break in For Loop

//Create Contract
contract looptest { 
      //unsigned integer initialize
    uint result = 0;
// Create function containing For Loop
    function sum() public returns(uint data){
     for (uint i = 0; i < 10; i++) {
            if (i == 4) {
                continue; 
              //when i=4 jump out the statement
            }
            if (i == 5) {
                break; 
             // will break when i=5 and condition check resumes 
            }
        }
      return result;
    }
}
``` 

# Conclusion

> As we saw that while using break statement when the condition check is true for break statement, it breaks/terminates the loop. 

> Whereas in Continue, it is similar to break but instead of terminating the loop, it forces to execute the next iteration of the loop.

> So now we know how both the statement behaves depending on the context which helps to avoid bugs and gas costs.


Thanks for taking the time to read this article! 

**▶Next : [Master Solidity Series](https://manavpaul.hashnode.dev/series/solidity-tutorial)**

**Documenting my journey with Solidity, Blockchain and Web3**

Drop a comment here, share or hit me up on Twitter! ♥


