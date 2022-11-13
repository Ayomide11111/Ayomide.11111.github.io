## Deeper exploration on Bitwise Operators

 The CPU in addition to standard arithmetic operations support operations that are outside the scope of binary. These `bitwise operations` directly apply the behavior of logic gates to but sequences, which makes them straightforward to implement efficiently in hardware. Unilke addition and subtraction, which programmers use to manipulate a variable's numerical interpretation, programmers use bitwise operators to modify specific bits in a variable. For example, a program might encode a certain bit position in a variable to hold a true/false meaning, and bitwise operations allow the program to manipulate the variable's individual bits to change that specific bit. 

## BITWISE AND
 The bitwise AND operator (`&`) evaluates two input bit sequences. For each digit of the inputs, it outputs a 1 in the corresponding position of the output if both inputs are 1 in that position. Otherwise, it outputs a 0 for the digit. The table below shows the truth table for the bitwise AND of two values, A and B.

 - BITWISE  AND TABLE
 
 | A | B | A & B |
 |---|---| ------ |
 | 0 | 0 | 0 |
 | 0 | 1 | 0 |
 | 1 | 0 | 0 |
 | 1 | 1 | 1 |

 For example,to bitwise  AND `0b011010` with `0b110110`, start by lining up the two sequences. Checking vertically through each digit, set the result of the column to 1 if both digits are 1. So the result will be:
  >     
           011010
   AND     110110
   Result: 010010 

 In c++ programming language, to perform bitwise AND we place the bitwise AND operator `&` between two operand variables. An example is:

- C++ CODE
int x = 26;
int y = 54;
int result = x & y;
std::cout << "The result of the bitwise operation is: " << result << std::endl;
// the result prints 18.

## BITWISE OR
 The bitwise OR operator (`|`) behaves like the bitwise AND operator except that it outputs a 1 for a digit if either or both of the inputs is 1 in the corresponding position. Otherwise, it outputs a 0 for the digit. The below table shows the truth table for the bitwise OR of two values, A and B.

- BITWISE OR TABLE
 | A | B | A|B |
 |---|---| ------ |
 | 0 | 0 | 0 |
 | 0 | 1 | 1 |
 | 1 | 0 | 1 |
 | 1 | 1 | 1 |
 For example, to bitwise OR `0b011010` with `0b110110`, start by lining up the two sequences. Checking vertically through each digit, set the result of the column to 1 if either digit is 1:
 >        011010
   OR      110110
   Result: 111110 
 
 In c++ programming language, to perform bitwise AND we place the bitwise AND operator `|` between two operand variables. An example is:

 - C++ CODE
int x = 26;
int y = 54;
int result = x | y;
std::cout << "The result of the bitwise operation is: " << result << std::endl;
// the result prints 62.

## BITWISE XOR (EXCLUSIVE OR)
 The bitwise XOR operator (`^`) behaves like the bitwise OR operator except that it outputs a 1 for a digit only if exactly one (but not both) of the inputs is 1 in the corresponding position. Otherwise, it outputs a 0 for the digit. The table below shows the truth table for the bitwise XOR of two values, A and B.

- BITWISE XOR TABLE
 | A | B | A ^ B |
 |---|---| ------ |
 | 0 | 0 | 0 |
 | 0 | 1 | 1 |
 | 1 | 0 | 1 |
 | 1 | 1 | 0 |
 For example, to bitwise XOR `0b011010` with `0b110110`, start by lining up the two sequences. Checking vertically through each digit, set the result of the column to 1 if either digit is 1:
 >        011010
   XOR     110110
   Result: 101100 
 
 In c++ programming language, to perform bitwise AND we place the bitwise AND operator `^` between two operand variables. An example is:
 - C++ CODE
int x = 26;
int y = 54;
int result = x ^ y;
std::cout << "The result of the bitwise operation is: " << result << std::endl;
// the result prints 44.

## BITWISE NOT
 The bitwise NOT operator (`~`) operates on just one operand. For each bit in the sequence, it simply flips the bit such that a zero becomes a one or vice versa. Table 4 shows the truth table for the bitwise NOT operator.
 
 - BITWISE NOT TABLE
 | A |!A |
 |---|--- |
 | 0 | 1 |
 | 1 | 0 |

 In c++ programming language, to perform bitwise NOT we place the bitwise AND operator `~` between two operand variables. An example is:

 - C++ CODE
int x = 26;
std::cout << "The result of the bitwise operation is: " << ~x << std::endl;
// the result prints -27.


## BIT SHIFTING
 Another important bitwise operation involves shifting the position of an operand’s bits either to the left (`<<`) or to the right (`>>`). Both the left and right shifting operators take two operands: the bit sequence to shift and the number of places it should be shifted.

## SHIFTING LEFT
 Shifting a sequence to the left by N places moves each of its bits to the left N times, appending new zeros to the right side of the sequence. For example, shifting the eight-bit sequence 0b00101101 to the left by two produces 0b10110100. The two zeros at the right are appended to end of the sequence, since the result still needs to be an eight-bit sequence.

  In the absence of overflow, shifting to the left increases the value of the result because bits move toward digits that contribute larger powers of two to the value of the number. However, with a fixed number of bits, any bits that shift into positions beyond the maximum capacity of the number get truncated. For example, shifting the eight-bit sequence 0b11110101 (unsigned interpretation 245) to the left by one produces 0b11101010 (unsigned interpretation 234). Here, the truncation of the high-order bit that shifted out makes the result smaller.

  To perform a left bit shift in C++, place two less-than characters (<<) between a value and the number of places to shift that value:
  > C++ CODE
  int x = 13; // 13 is 0b00001101 in binary
  std::cout << "The result of doing a left bit shift on 13 is" << `x << 3` << std::endl;

## SHIFTING RIGHT
 Shifting to the right is similar to left shifting — any bits that are shifted out of a variable’s capacity (e.g., off the end to the right) disappear due to truncation. However, right shifting introduces an additional consideration: the new bits prepended to the left side of the result may need to be either all zeros or all ones depending on the type of the variable being shifted and its high-order bit value. Conceptually, the choice to prepend zeros or ones resembles that of sign extension. Thus, there exist two distinct variants of right shifting:
 - A `logical right shift` always prepends zeros to the high-order bits of the result. Logical shifting is used to shift unsigned variables, since a leading 1 in the most significant bit of an unsigned value isn’t intended to mean that the value is negative. For example, shifting 0b10110011 to the right by two using a logical shift yields 0b00101100.
 - An `arithmetic right shift` prepends a copy of the shifted value’s most significant bit into each of the new bit positions. Arithmetic shifting applies to signed variables, for which it’s important to preserve the signedness of the high-order bits. For example, shifting 0b10110011 to the right by two using an arithmetic shift yields 0b11101100.


## REAL USES OF BITWISE OPERATORS
------------------------------------
1. Check for Odd and Even Numbers.
 A trick we can use to achieve bitwise operators is to check if an integer is odd or even.
 ```C++
 # C++ CODE
 -------------------
 #include <iostream>
 int main(){
    int x = 5;
    if(!(x&1)){
        std::cout << "x is even"<< std::endl;
    }else{
        std::cout << " x is odd" << std::endl;
    }
 }
```
2. Swapping variables without using a third variable
 The swapping of two variables without involving a third variable can be achieved without the bitwise operators, but since you already know bitwise operators, why not?
 ```C++
 # C++ CODE
 ----------------------
 #include <iostream>
 int main(){
    int a=3, b=4;
    //before swapping
    std::cout << a << b << std::endl;

          /* a == 0011; b == 0100 */
  a ^= b; /* a == 0111; b == 0100 */
  b ^= a; /* a == 0111; b == 0011 */
  a ^= b; /* a == 0100; b == 0011 */
  
  //after swapping
  std::cout << a << b << std::endl;
  return 0;
 ```

3. Converting text casing
```C++
  C++ CODE
  ---------------------
  #include <iostream>
  int main(){
    char word[8]= "bITwiSe";
    char *wordptr = &word[0];
    while(wordptr < &word[7]){
        // converts the char into uppercase regardless of current casing
        std::cout << "UPPERCASE: " << *wordptr & '_' << std::endl;
        // converts the char into lowercase regardless of  current casing
        std::cout << "LOWERCASE: " << *wordptr | '_' << std::endl;
        wordptr++;
    }
    return 0;
  }
```

## REFERENCES
---------------------
- Dive into Systems by  Suzanne J. Matthews, Tia Newhall, Kevin C.Webb.
- Real World Uses of Bitwise Operators by Sreedev Kodicath.
