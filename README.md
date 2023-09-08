# ARMv8-Computer-Architecture-and-ARMv8-Assembly

# Background: two computer architectures

Two main computer architecures are x86(x64) and ARM. x86-based CPUs running complex instruction set computers (CISC) instructions. It has a very rich instruction set. A single instruction can complete an entire calculation (like multiplication) or move a chunk of data directly from one place in memory to another. This might not sound like much, but multiplication and moving data between places in memory requires a lot of instructions at this low level. With x86 computers, this complex series of operations can be executed with a single cycle. However, the powerful instructions in a CISC computer mean that it needs more transistors, which eat up space and power.

On the other hand, the complexity of CISC computer ultimately led to the design of reduced instruction set computer (RISC) processors. RISC processors have an instruction set where each instruction represents only a simple operation using lower power. This makes the assembly language programmer’s job more complex, but simplifies the processor’s job. With RISC processors and advanced RISC machines, complex operations are performed either by running multiple instructions or by pushing the complexity over to the compiler rather than the CPU core. ARM is the most porpular and successful RISC-based computer architecture.

RISC architecture was inspired by a need to make smaller chips with better performance for smaller computers—or microcomputers—which eventually became PCs. Since ARM processors are integrated as a SoC, the emphasis has long been on overall resource management, including low energy consumption and lower heat production. For example, ARM architectures (like ARMv8) tend not to have simplified cooling systems (no fans on a cell phone). 

While both CPU designs can still have high performance (both ARM- and x86-architecture supercomputers compete for the fastest in the world), ARM designs tend to focus on smaller form factors, battery life, size, eliminating cooling requirements, and—perhaps most importantly—cost. This is why ARM processors dominate small electronics and mobile devices like smartphones, tablets, and even Raspberry Pi systems. x86 architectures are more common in servers, PCs, and even laptops where there is a preference for speed and flexibility in real time, and fewer constraints on cooling and size.

# Porpose:
The purpose of this repository is to about ARMv8 computer architecture, ARMv8 assembly language programming, and testing strategies. It includes the following tasks:

# 1. A Word Counting Program in Assembly Language
The GNU toolset contains a program named wc (word count). In its simplest form, wc reads characters from stdin until end-of-file, and writes to stdout a count of how many lines, words, and characters it has read. A word is a sequence of characters that is delimited by one or more white space characters.

In this step, a mywc.c file contains a C program that implements the subset of the wc command described above. The task is to translate that program into ARMv8 assembly language, thus creating a file named mywc.s. The mywc.s program must be an accurate translation of mywc.c. In particular, note that the given mywc.c program uses global variables, and so your mywc.s must use global variables too. That is, your mywc.s program must store data in the DATA and/or BSS sections.

To test the assembly language, compose data files that, when read by your mywc.s program, perform boundary tests, statement tests, and stress tests of that program. Name each test file such that its prefix is mywc and its suffix is .txt. Thus, the command ls mywc*.txt must display the names of all test files, and only those files.

Note that the logic implemented by your mywc.s program must be identical to the logic implemented by the given mywc.c program. So, for the sake of simplicity, let's assume that any test file that boundary/statement/stress tests mywc.c also boundary/statement/stress tests mywc.s.

# 2. Beat the Compiler with Optimized Assembly Language

Many programming environments contain modules to handle high-precision integer arithmetic. For example, the Java Development Kit (JDK) contains the BigDecimal and BigInteger classes.

The Fibonacci numbers are used often in computer science. See http://en.wikipedia.org/wiki/Fibonacci_number for some background information. Note in particular that Fibonacci numbers can be very large integers.

This part of the assignment asks you to use assembly language to compose a minimal but fast high-precision integer arithmetic module, and use it to compute large Fibonacci numbers.

Step 1. Add BigInt Objects Using C Code

Suppose you must compute Fibonacci number 250000, that is, fib(250000)... 

You are given a C program that computes Fibonacci numbers. It consists of two modules: a client and a BigInt ADT.The client consists of the file fib.c. The client accepts an integer x as a command-line argument, where x must be a non-negative integer. The client computes and writes fib(x) to stdout as a hexadecimal number. Then it writes to stderr the amount of CPU time consumed while performing the computation. Finally the client performs some boundary condition and stress tests, writing the results to stdout. The client module delegates most of the work to BigInt objects.

Step 2. Add BigInt Objects Using C Code Built with Compiler Optimization

Suppose you decide that the amount of CPU time consumed is unacceptably large. You decide to instruct the compiler to optimize the code that it produces...

Build the fib program using optimization. Specifically, build with the -D NDEBUG option so the preprocessor disables the assert macro, and with the -O (that's an upper case letter, not a digit) option so the compiler generates optimized code. Run the resulting program to compute fib(250000). In your readme file note the amount of CPU time consumed.

Step 3: Profile the Code

Suppose you decide that the amount of CPU time consumed still is too large. You decide to investigate by doing a gprof analysis to determine which functions are consuming the most time...

Perform a gprof analysis of the executable binary file from Part 2b. Save the textual report in a file named performance. Don't delete the file; as described later in this document, you must submit that file.

Step 4. Add BigInt Objects Using Assembly Language Code

Suppose, not surprisingly, your gprof analysis shows that most CPU time is spent executing the BigInt_add function. In an attempt to gain speed, you decide to code the BigInt_add function manually in assembly language...

Manually translate the C code in the bigintadd.c file into ARMv8 assembly language, thus creating the file bigintadd.s. Do not translate the code in other files into assembly language.

Your assembly language code must store all parameters and local variables defined in the BigInt_larger and BigInt_add functions in memory, on the stack.

Note that assert is a parameterized macro, not a function. (See Section 14.3 of the King book for a description of parameterized macros.) So assembly language code cannot call assert. When translating bigintadd.c to assembly language, simply pretend that the calls of assert are not in the C code.

This project is a COS217 assignment. https://www.cs.princeton.edu/courses/archive/spr23/cos217/asgts/05assemlang/

A complete code is a private repository and it is available upon request only for employment purpose.
