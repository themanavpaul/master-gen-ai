---
title: "Master Solidity : Arrays (Advance)"
datePublished: Fri Dec 30 2022 20:04:28 GMT+0000 (Coordinated Universal Time)
cuid: clcay1f0j000908mi240vduho
slug: master-solidity-arrays-advance
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1654112561680/baPVYCo4b.png
tags: tutorial, blockchain, array, solidity, web3

---

# What are Arrays ?

Arrays are data structures that store the fixed collection of elements of the same data type. Each element has a specific location called Index.

In Solidity, an array is an ordered list of items that is indexed numerically, starting at 0.

# Types of Arrays

In this section, we provide two types of arrays:

1. *Fixed-size arrays* and *Dynamic size arrays*
    
2. *One Dimensional arrays* and *Multi-Dimensional Arrays*
    

## **Fixed Size Arrays**

Size of the array is predefined. Total number of elements should not exceed the size of the array created.

Syntax

```sql
uint[3] public arr;
```

Initialization

```sql
uint[3] public numfixed = [1,2,3];
```

Note

```sql
uint[3] public numfix = [1,2,3,4];
```

> // This will not compile -&gt; Type Error

> // As the number of elements is greater than size of the array

Example

```sql
contract Array
{
  uint[4] public arr = [10,20,30]
  function setter (uint index, uint value) public
   {
       arr[index]= value;
    }
   function length() public view return(uint)
   {
     return arr.length;
    }
}
```

*Explanation*

Here in ***arr\[index\] = value*** inside setter function, you can check the element by typing its index position as well as change the element in that respective position.

## Dynamic Size Array

Size of the array is not predefined when declared. Size of the array changes as the elements are added. At runtime, size of the array is determined.

Syntax

```sql
uint[] public arrayname;
```

Inintialization

```sql
uint[] public arr = [1,2,3];
```

If you want to initialize dynamically-sized arrays, you have to assign the individual elements

```sql
contract Begins {
    function f() public pure {
        uint[] memory x = new uint[](3);
        x[0] = 1;
        x[1] = 3;
        x[2] = 4;
    }
}
```

---

One dimensional and multidimension arrays is a topic that are fundamentals of a programming language. In Solidity, it works in a similar manner but not exactly. Would highly recommend this article from [Jean Cvllr](https://jeancvllr.medium.com/solidity-tutorial-all-about-array-efdff4613694) if you want to learn the in-depth working of one-dimensional and multi-dimensional arrays. For now I have summarized the concept for better understanding.

## One Dimensional

One Dimensional and Multi-Dimensional arrays can be both of Fixed-Size or Dynamic-Size.

> T\[k\] : One Dimensional, Fixed-size
> 
> T\[\] : One Dimensional, Dynamic-size

## Multi-Dimensional arrays

Multi-dimensional arrays are essentially nested arrays (An array that contain other arrays).

> T\[k\]\[k\] : Two-Dimensional, Fixed-size
> 
> T\[ \]\[ \] : Two-Dimensional, Dynamic-size
> 
> T\[ \]\[k\] or T\[k\]\[\] : Two-Dimensional, Mixed-size

\*\* Multi-dimensional arrays can have any level of nesting \*\*

> T\[2\]\[2\]\[2\] : Three-Dimensional, Fixed-Size (all k are the same)
> 
> T\[2\]\[8\]\[4\]\[12\] : Four-Dimensional, Fixed-Sizes ( k‘s are of different values)
> 
> T\[ \]\[ \]\[ \]\[ \]\[ \] : Five-Dimensional, Dynamic-Size
> 
> T\[ \]\[3\]\[2\]\[ \]\[9\]\[ \] : Six-Dimensional, Mixed-Size

\*\*Note \*\*

* You cannot have different types within nested arrays
    
* The maximum level of nesting for nested arrays is 15. If you try to create a variable with 16 nested arrays, you will get a ‘stack too deep’ error. As stack pointer in the EVM cannot access a slot in the stack that is deeper than is 16th element (top down).
    

If you want to know more about **Stack too deep error** I will highly recommend you this article by [Aventus Network](https://medium.com/coinmonks/stack-too-deep-error-in-solidity-608d1bd6a1ea)

> // 15 level of nesting : working

uint\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \] public nesting\_limit; \`\`\`

> // 'Stack too deep' error

uint\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \]\[ \] public over\_limit; \`\`\`

## Defining One-Dimensional arrays

> // (One-Dimensional array, fixed size)

string\[4\] players\_room; \`\`\`

> //(One-Dimensional array, Dynamic Size)

string\[ \] have\_voted; \`\`\`

## Defining Two-Dimensional arrays

**Example 1**

```sql
string[2][ ] crypto_names;
```

Here, the fixed-size 2 refers to the second level of nesting, not the first.

```sql
contract CryptoNames {
    string[2][ ] public crypto_names;
 
    constructor() public {
        crypto_names.push([“Alice”, “Bob”]);   
        crypto_names.push([“Carol”, “Dave”]);  
        crypto_names.push([“Eve”, “Frank”]);   
        crypto_names.push([“Grace”, “Heidi”]); 
    }
}
```

As we see there are fixed number of columns that is 2. Though rows can be extended to any number.

What if we add three names instead of 2. Let's see what happens

```sql
function invalidPush() public {
     crypto_names.push(["Ivan", "Judy", "Mallory"]);
}
```

This will give us a Type Error.

> Invalid type for argument in function call.  
> Invalid implicit conversion from string memory\[3\] memory to string storage ref\[2\] storage ref requested.

**Example 2**

```sql
string[ ][6] names_A_to_F;
```

Similarly in the following example, there can be any number columns but the rows must be 5. ( Since last index of the array with 6 elements will be 5 i.e. 6 - 1 = 5)

## Access elements within multi-dimensional arrays.

```sql
contract NamesAlphabet {
    
    string[][6] public names_A_to_F;
    
    constructor() public {
        names_A_to_F[0] = ["Alice"];
        names_A_to_F[1] = ["Bob"];
        names_A_to_F[2] = ["Carol", "Carlos", "Charlie", "Chuck", "Craig"];
        names_A_to_F[3] = ["Dan", "Dave", "David"];
        names_A_to_F[4] = ["Erin", "Eve"];
    }
    
    function getAliceName() public view returns (string memory) {
        return names_A_to_F[0][0];
    }
    
    function getBobName() public view returns (string memory) {
        return names_A_to_F[1][0];
    }
    
    function getEveName() public view returns (string memory) {
        return names_A_to_F[4][1];
    }
    
    function getChuckName() public view returns(string memory) {
        return names_A_to_F[2][3];
    }
    
}
```

---

# Array Operations/Members

These are several operations/members that can be performed on an array.

## **1\. Push**

When a new element is to be added in dynamic array. The new element is added to the last position.

## **2\. Get/Access the Element**

Elements of array are accessed by index. To access *i* th element you have to access the *(i-1)* th element.

## **3\. Update**

Update the element in an array using the index position.

## **4\. Delete**

Delete/clear the element in given index position and changes to the default value. Default value of uint is 0. The length of the array remains the same.

## **5\. Pop**

Removes the last elements of the dynamic array. Size of the array changes(reduces)

## **6\. Length**

Length of the array is used to check the numbers of element present in the array. Size of memory array is fixed when they are declared, while incase of dynamic array is defined at runtime so for manipulation length is required.

*Example*

```sql
contract Array
{
   uint[] public nums = [1,2,3];
   function examples() external
{
  nums.push(4);   // [1,2,3,4]
uint x = nums[1];   //x access the index position
nums[2] = 777;   //[1,2,777,4]
delete nums[1];  //1,0,777,4]
nums.pop();   //[1,0,777]
uint len = nums.length;   // returns length of array

// Lets create an array in memory
  uint[] memory a = new uint[] (5);    //fixed size of 5
a.pop();   //will not worked since fixed size
a.push();  //will not worked since fixed size
a[1] = 123;   //You can get or update the value of an array in the memory
}

// Function that returns an array
//memory is used to copy state variable nums into memory, then return it
function return external view returns ( uint[] memory)
{
  return nums;
}

}
```

Note

> Returning an array from function is not recommended. It is said to keep the For Loop small. Bigger array results in lot of gas consumption. Thus, unusable.

> Increasing the length of a storage array by calling **push()** has constant gas costs because storage is zero-initialised, while decreasing the length by calling **pop()** has a cost that depends on the “size” of the element being removed. If that element is an array, it can be very costly, because it includes explicitly clearing the removed elements similar to calling **delete** on them.

> If an array is returned by a function, the data location specified always have to be memory .

# Allocating Memory Arrays

Memory arrays with dynamic length can be created using the ***new*** operator. As opposed to storage arrays, it is not possible to resize memory arrays (e.g. the .push member functions are not available). You either have to calculate the required size in advance or create a new memory array and copy every element.

As all variables in Solidity, the elements of newly allocated arrays are always initialized with the default value.

> The “**default values**” of variables are the typical “**zero-state**” of whatever the type is.

> For example, the default value for a **bool** is false. The default value for the **uint** or **int** types is 0. For statically-sized arrays and **bytes1** to **bytes32**, each individual element will be initialized to the default value corresponding to its type.

> For dynamically-sized arrays, **bytes** and **string**, the default value is an empty array or string. For the **enum** type, the default value is its first member.

*Example*

```sql
contract Begins {
    function f(uint len) public pure {
        uint[] memory a = new uint[](7);
        bytes memory b = new bytes(len);
        assert(a.length == 7);
        assert(b.length == len);
        a[6] = 8;
    }
}
```

# Array Literals

An array literal is a comma-separated list of one or more expressions. They do not get assigned to a variable right away.

> For example \[1, a, f(3)\].

It is always a statically-sized memory array whose length is the number of expressions.

The base type of the array is the type of the first expression on the list such that all other expressions can be implicitly converted to it. It is a type error if this is not possible. Only condition is that one of the elements has to be of that type.

In the example below, the type of \[1, 2, 3\] is uint8\[3\] memory, because the type of each of these constants is uint8. If you want the result to be a uint\[3\] memory type, you need to convert the first element to uint.

```sql
contract Literals {
    function f() public pure {
        func([uint(1), 2, 3]);
    }
    function func(uint[3] memory) public pure {
        // some code....
    }
}
```

---

# Fixed Size Byte Arrays

We can define variables by using the keyword **bytesX**.

**X** -&gt; represents the sequence of bytes. X can be from 1 up to 32.

> Example- bytes1, bytes2, bytes3

*Example*

```sql
contract Array 
{
   bytes2 public b2;  // 2 bytes array -> 0x0000
   bytes2 public b3;  // 3 bytes array -> 0x000000

   function setter() public 
  {
     b2 = 'ab';   //0x6162
     b3 = 'abc';  //0x616263
  }
}
```

**Note**

> * According to ASCII Table, Hex value of a = 61, b= 62, c = 63.
>     

> * 1 byte = 8 bits
>     

> * 1 Hexadecimal = 4 bits
>     

> * 1 byte = 2 Hexadecimals
>     

> * If b2 = 'a'; //0x6100
>     

> * If b3 = 'abc'; and b3\[0\] ='d';  
>     Type Error -&gt; cannot be modified in fixed byte
>     

**Important Points**

* Bytes array cannot be modified.
    
* Padding of 0 is added at the end if the value does not occupy the entire space.
    
* They can be passed between contracts since fixed size.
    

# Dynamically-Size Byte Arrays

Variables of type **bytes** and **string** are special arrays. A **bytes** is similar to **byte\[ \]**, but it is packed tightly in *calldata* and *memory*. **string** is equal to **bytes** but does not allow length or index access.

**Bytes** Use bytes for arbitrary-length raw byte data. The term bytes in Solidity represents a dynamic array of bytes.

You should use bytes over byte\[ \] because it is cheaper, since byte\[\] adds 31 padding bytes between the elements.

Because bytes are treated as array is Solidity code, it can have a length of zero and you can do things like append a byte to the end.

However, bytes is not a value type !

You can push, pop, get and length

**String** use string for arbitrary-length string (UTF-8) data

*Example*

```sql
bytes32 var = "stringliteral";
```

This string literal is interpreted in its raw byte form when assigned to a bytes32 type.

However, strings can’t be passed between contracts because they are not fixed size variables.

Solidity does not have string manipulation functions, but there are third-party string libraries.

If you can limit the length to a certain number of bytes, always use one of the value types bytes1 to bytes32 because they are much cheaper.

**Example**

```sql
contract Array 
{
   bytes public b1 = 'abc';   // 0x616263

//Push
   function pushElement() public 
   {
     b1.push('d');   // 0x61626364
   }
//Get
   function getElement(uint i) public view returns(bytes 1)  
  {
    return b1[i];   //when i = 1 -> 0x62
  }
//Length   
  function getLength() public view returns(uint)  
  {
    return b1.length;   // 3
  }
}
```

---

# Remove an Element from an Array

Lets see how we can remove an element from an array using array operations. As we have read from the topic Array Operation/Members that **delete** operation is used to clear the element in the given index position and changes to its default value i.e. 0.

*Example*

> We have an array nums = \[1,2,777,4\]
> 
> ```sql
> delete nums[1];
> ```
> 
> The result will be \[1,0,777,4\]

As we can see, the length of the array remains the same.

When we call the delete operation, it does ont remove the number from the array. It just removes the value of that index and switches it to the default value i.e. 0.

Thus, **delete** is not the right operation.

**But what about pop ?**

Well we know that pop operation removes the last elements of the dynamic array resulting reduction in array size.

> We have an array nums = \[1,0,777,4\]
> 
> ```sql
> nums.pop();
> ```
> 
> The result will be \[1,0,777\]

We see that **pop** operation removes the last element from the array.

***What if we want to remove an element present between an array?***

---

# Remove an array element by Shifting keeping the array in Order

It is basically removing an array element by shifting elements from right to left and keeping the array in order.

What we want to achieve is this:

> \*\* \[1,,2,3\] -&gt; remove(1) -&gt; \[1,3,3\] -&gt; \[1,3\]\*\*

> Here,

> \[1,,2,3\] -&gt; original array

> remove(1) -&gt; index position

> \[1,3,3\] -&gt; element copied from right

> \[1,3\] -&gt; remove last element

**Steps**

1. Create a function with index as a parameter.
    
2. Index should be less than length of the array. If not then "out of bound" show message.
    
3. For loop with incrementation, with **a\[i\] =a\[i+1\]**.
    
4. Pop or eliminate the last element from array.
    

Now to implement the above steps

```sql
function ArrayShift(uint index) public{
    for(uint i = index; i < arr.length-1; i++){
      arr[i] = arr[i+1];      
    }
    arr.pop();
  }
```

Here we used one **for loop** where we defined *i* as an **index** that will iterate until the array’s second last element. We defined this with **(arr.length-1)**. We have changed the index of the array with the logic **(arr\[i\] = arr\[i+1\])**. At last, we used the **pop()** method to remove the last empty element from the array.

*Example*

```sql
contract ArrayShift {

uint[] public arr;

    function remove(uint _index) public {
        require(_index < arr.length, "index out of bound");

        for (uint i = _index; i < arr.length - 1; i++) {
            arr[i] = arr[i + 1];
        }
        arr.pop();
    }

    function test() external {
        arr = [1, 2, 3, 4, 5, 6];
        remove(3);   // [1, 2, 4, 5, 6] 
        assert(arr[0] == 1);
        assert(arr[1] == 2);
        assert(arr[2] == 4);
        assert(arr[3] == 5);
        assert(arr[4] == 6);
        assert(arr.length == 5);

    }
    function getarr() public view returns (uint[] memory) {
        return arr;
    }
}
```

**Note**

> Returning an array from function is not recommended. It is said to keep the For Loop small. As bigger array results in lot of gas consumption. Thus, unusable.

Transaction of the above smart contract

![shift1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654106743933/YjIF0PYDf.png align="left")

> Here, element 4 present at the 3rd index position of the array is now shifted and the new element at that position is 5.
> 
> Also, the original array i.e. \[1,2,3,4,5,6\] is now \[1,2,3,5,6\].

> Element is removed -&gt; Length is reduced -&gt; Array is in order.

It is also important that there are more steps involved in this process. So naturally, it will consume a lot of gas. Thus, less gas efficiency. That’s why we should use this method only when keeping the elements of the array in order is absolutely required.

# Remove an array element by Replacing keeping the array Unordered

It is basically removing an array element by replacing that element with the last element and keeping the array unordered.

What we want to achieve is this:

> \*\* \[1,,2,3,4\] -&gt; remove(1) -&gt; \[1,4,3\] \*\*

> Here,

> \[1,,2,3,4\] -&gt; original array

> remove(1) -&gt; index position

> \[1,4,3,4\] -&gt; element copied from last

> \[1,4,3\] -&gt; remove last element

**Steps**

1. Create a function with index as a parameter.
    
2. Index should be less than length of the array. If not then "out of bound" show message.
    
3. Replacing the element to remove i.e. **arr\[i\] = arr\[arr.length - 1\]**.
    
4. **Pop** or eliminate the last element from array.
    

**Now to implement the above steps**

```sql
function ArrayReplace(uint index) public{
    arr[index] = arr[arr.length - 1];
    arr.pop();
  }
```

Last element is defined this with **(arr.length-1)**. Then we used the **pop()** method to remove the last empty element from the array.

*Example*

```sql
contract ArrayReplaceFromEnd {
    uint[] public arr;

    // Deleting an element creates a gap in the array.
    // One trick to keep the array compact is to
    // move the last element into the place to delete.

    function remove(uint index) public {
        // Move the last element into the place to delete
        arr[index] = arr[arr.length - 1];

        // Remove the last element
        arr.pop();
    }

    function test() public {
        arr = [1, 2, 3, 4];

        remove(1);
        // [1, 4, 3]
        assert(arr.length == 3);
        assert(arr[0] == 1);
        assert(arr[1] == 4);
        assert(arr[2] == 3);
/*
       // further removing element present at index 2
        remove(2);
        // [1, 4]
        assert(arr.length == 2);
        assert(arr[0] == 1);
        assert(arr[1] == 4);
*/
    }

    function getarr() public view returns (uint[] memory) {
        return arr;
    }
}
```

Notice how this method used only two steps. Replace the element to remove and pop the last element.

Since iteration is not there, there is more efficiency in terms of gas costs.

Here, the order of the array is changed. Whereas in shifting method, the order remains the same.

***Thanks for taking the time to read this article!***

**▶Next :** [**Master Solidity Series**](https://manavpaul.hashnode.dev/series/solidity-tutorial)

**Documenting my journey with Solidity, Blockchain and Web3**

Drop a comment here, share or hit me up on Twitter! ♥