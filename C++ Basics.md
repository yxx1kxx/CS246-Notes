# C++ Basics

#### Booleans

C/C++ let you treat arithmetirc (including char) and pointer values are having true/false meanings

1. Zero(NULL ptr) means false

2. Non-zero(non-NULL ptr) means true [Not recommended; illegal in Java]

   

#### int VS. insigned int

The variable ui is a 32-bit int in the range: 1...4,294,976,295

The variable i is a 32-bit int in the range: -2,147,483,648 ...2,147,483,648



#### Strings

Do not use string.h or char* in C++

Some useful string API:

```c++
+ string catenation
==, <=, <, etc. compare the standard lexical order
s.length() # of chars in s
s.at(i) returns ith char (checked access)
s[i] returns ith char (unchecked access)
s.c_str() returns the c-style char* that is equivalent of s
s.substr(i,n) substring of n characters starting at index i
s.substr(i) substring that starts at index i and ends at the end of s
s.find(str, pos) return first index of str in s, starting at/after pos **
s.rfind(str, pos) return last index of str in s starting at of before pos**
s.replace(...) replace chars within s
s.insert(...) insert chars within s
```

#### char VS. string

1. You can access individual chracters of a string by:
   + Checked via at method: s.at(2)
   + unchecked like an array access: s[2]

2. chars have a dual nature: both characters and integers:
   + When we use "+" operator on chars, it performs integer addition, not string catenation
   + but when we print a char, you get the character not the integer

**Note:**

Char + char returns integer 

String1+ String2 returns appended string



#### 'a' VS. "a"

They are different entities

- **"a"** is a **string** value of length 1

  ```c++
  string s = "a";
  ```

  s is an instance of the class string; it takes a more storage than a single integer

  (Dw for now)

- **'a'** is a single **char**, that is represented internally as a 1-byte integer

  ```c++
  char c = 'a';
  ```

  

#### s == t?

The C++ string class defines the equality operator "==" to be true iff s and t have the same string value (same chars in same order) unlike Java. 



#### Accessing command line arguments: argc and argc

There are two arguments to main, and their values are accessible inside the program.

```c++
- argc, an int which counts the number of command line args passed to the executable for that run
- argv, an array of char*, one for each arg passed in for that run
- argc and argv can be different each time the same program is run/
```

argc is always at least one; argv[0] contains the name of the command used to call the program:

```bash
% myprog -flurble blat
## argc == 3 
## argv[0] == "myprog"
## argv[1] == "-flurble"
## argv[2] == "blat"
```

 

#### Simple I/O

#include<iostream> gets you three useful "streams":

1. cin (standard input),
2. cout (standard output), and
3. cerr (standard error, i.e., the output stream you should send error messages to)

use these operators: << for output and >> for input

- They have overloaded for you already to work with numbers, chars, and strings
- You can overload them yourself to work with your own classes



***operator>>*** skips initial whitespace when reading in a std::string

***getline*** does not skips initial whitespace when reading in a std::string

***getline*** take an input stream as a parameter

***getline*** can be coerced to return a boolean value such that a value of true indicates success, while false indicates failure or end-of-file.

reading a string can set the fail bit



By default, the `istringstream` separates the words (often called "tokens") by whitespace. (Remember, *whitespace* consists of blanks, tabs, and newlines.) Since the input stream function `std::getline` lets us specify the delimiter to use when reading in lines of input as strings, we can use the same technique to specify a different delimiter to separate our tokens.

**Note that forgetting to have a** `return` **statement when a return type other than** `void` **is specified can lead to your program behaving erratically. Using** `-Wall` **when compiling your program will warn you of this error—let the compiler help you!**

**There is one additional rule of use: if some of your parameters have default values, and some do not, all of those with default values** **must** **come after those without default values in the list of arguments.**





#### Dynamic memory allocation

```c++
* ptr # dereference of a pointer
& ptr # address of a pointer 

int *x=5; ## x is a pointer to 5
int &y=x; ## y is a reference to x

## y is an alias of x, both point to 5
```



#### Call-by-value VS. Pass-by-reference

Call-by-value means we are working on a copy. We simply modify the copy and leave the original unchanged.

