# Fast I/O Code Optimizer
A tool developed in Python to optimize execution time of C++ codes by replacing methods of reading and writing variables. The program is focused on Competitive Programming and could be used to help to solve problems with a tight time limit. This optimizer replaces all cin/cout methods to faster approaches which can optimize until 30% the execution time of the code.

## Motivation
Some competitive programming problems have a tight time limit.  Then, when someone submits a solution, even with the expected complexity, it may get a time limit exceeded verdict. Occasionally, the problem requires Fast I/O methods to speed up the execution time and is very hard to get accepted verdict without making this type of optimization. Consequently, it is needed to replace all default C++ reading and writing methods (cin/cout) to faster approaches.  This tool makes very easy the task of replacing the way of reading and writing variables, and it uses very fast methods which would take very long to type and wouldn't be so efficient.

## How to use

### Website: [fastio.pythonanywhere.com/](http://fastio.pythonanywhere.com/)
After accessing the website, it is needed to insert the code to be optimized in the text field from the left, then click the button Optimize it and it's done, the optimized code will be pasted in the text field from the right.

### Offline tool
Download the project and execute the file in terminal. To execute it just type the following.
```shell
python3 fastio.py nameOfFile.cpp
```
After that, it will be generated a new file named `FastIO-nameOfFile.cpp` in project's directory and the converted code will be printed in terminal.
If the user do not want to create a new file or print the code in terminal, he only needs to go to fastio.py file and modify the variables printInTerminal and printInFile.

## Functions and Commands

### To Be Replaced 
* cin
* cout
* cin.ignore() - 0 parameter
* getline() - Any number of parameters
* cout << setpresision() - 1 parameter and at most 1 call

### To Be Deleted
* cout << fixed
* ios_base::sync_with_stdio()
* ios::sync_with_stdio()

## Important Restrictions and Warnings
* This tool doesn't work with multiple calls of setprecision function.
* Multiline statements are not supported.
* Custom istream is not supported.
* C++ (g++ 4.3.2) and past versions are not supported.
* This tool only supports cin/cout commands.
* C++11 is faster than newer versions.

## Implementation
In order to optimize the code performance, text replacing was the approach chosen. This tool finds all occurrences of cin/cout commands and replaces them with functions. Important auxiliaries commands also are supported and will be described later. Most of the implementation consists of finding patterns in text using regular expressions, and this is very useful to avoid blank characters. Because of the best compatibility with methods applied, Python was the language chosen. There are other approaches available to make the same optimization, but this one was chosen by reason of it is possible to modify easier all commands without creating some specific modification to a certain command. Besides that, it is possible to add support to a big range of things like the use of different namespaces.

### Reading Variables

All cin calls are replaced by READ_VAR function. It is a boolean funcion. It returns 0 if it reads EOF or returns 1 if it reads some content.

#### - Reading Integers
Cin is replaced by getchar() function which is responsible to read each number as a character and convert it to a number.

#### - Reading Strings and Characters 
Cin is replaced by getchar() function which is responsible to read the string, char by char.

#### - Reading Floating Numbers
Cin is replaced by a scanf function.

#### - Reading Booleans and Bitsets
Cin is replaced by getchar() function which is responsible to read each bit as a character and convert it to a bit.

### Writing Variables

All cout calls are replaced by WRITE_VAR function. It is a void function.

#### - Writing Integers
Cout is replaced by putchar() function which is responsible to write each number as a character.

#### - Writing Strings and Characters
Cout is replaced by putchar() function which is responsible to write each character, char by char.

#### - Writing Floating Numbers
Cout is replaced by a printf function. If setprecision(number) method is called, all floating numbers will be written with "number" decimal places. However, this tool only supports one call of setprecision method.  

#### - Writing Booleans and Bitsets
Cout is replaced by putchar() function which is responsible to write each bit as a character.

\* The usage of std:: before a call and the usage of blank characters like tabs and spaces are supported.


## Tests and Comparisons

| | C++ | C++ (FAST IO) | C++11 | C++11 (FAST IO) | C++14 | C++14 (FAST IO) | C++17 | C++17 (FAST IO) |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| [Codeforces - Cloud of Hashtags](https://codeforces.com/problemset/problem/777/D) | - | - | [264 ms](https://codeforces.com/contest/777/submission/50989538) | [62 ms](https://codeforces.com/contest/777/submission/50989575) |[124 ms](https://codeforces.com/contest/777/submission/50989550) | [202 ms](https://codeforces.com/contest/777/submission/50989582) | [140 ms](https://codeforces.com/contest/777/submission/50989556) | [187 ms](https://codeforces.com/contest/777/submission/50989597) |
| [Codeforces - Stars Drawing (Hard Edition)](https://codeforces.com/contest/1015/problem/E2) | - | - | [1606 ms](https://codeforces.com/contest/1015/submission/50987913) | [467 ms](https://codeforces.com/contest/1015/submission/50987973) | [733 ms](https://codeforces.com/contest/1015/submission/50988087) | [998 ms](https://codeforces.com/contest/1015/submission/50988176) | [702 ms](https://codeforces.com/contest/1015/submission/50988090) | [1014 ms](https://codeforces.com/contest/1015/submission/50988172)  |
| [URI - Man, Elephant and Mouse](https://www.urionlinejudge.com.br/judge/en/problems/view/1477) | - | - | 912 ms | 660 ms | - | - | 944 ms | 728 ms |
| [URI - Plantation](https://www.urionlinejudge.com.br/judge/en/problems/view/2772) | - | - | 700 ms | 680 ms | - | - | 916 ms | 896 ms |
| [SPOJ - Binary search](https://www.spoj.com/problems/BSEARCH1/) | TLE | 110 ms | - | - | TLE | 110 ms | - | - |
