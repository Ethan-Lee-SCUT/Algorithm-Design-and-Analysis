# COA Review

### Chanter-01 Introduction

#### 1. Architecture

1. Instruction set
2. Number of bits used for data
3. Addressing techniques

#### 2. Organization

1. Instruction set $\to$ Control signals
2. Number of bits used for data $\to$ Bus width
3. Addressing techniques $\to$ Memory technology

#### 3. Functions

1. Data processing
2. Data storage
3. Data movement
4. Control

#### 3. Family product

* Different in organization but not architecture leads to 'family'






### Chapter-02 Evolution and Performance

#### 1. Stored-program concept (von Neumann/Turing)

1. Data and instruction encoded **in binary**
2. Data and instruction stored **in SAME memory**
3. Can change program **without rewriting**

#### 2. IAS machine (von Neumann/Turing)

pic here

#### 3. IAS Register

1. **MBR** memory buffer register
2. **MAR** memory address register
3. **IR** instruction register
4. **IBR** instruction buffer register
5. **PC** program counter
6. **AC** accumulator
7. **MQ** multiplier quotient





### Chapter-03 Interconnection

#### 1. How the program is executed?

1. Fetch
2. Execute

#### 2. Interrupt

1. What is interrupt
   * A way to improve processing efficiency
2. Instruction cycle with interrupt
   * add pics

#### 3. Multiple interrupts

1. Form
   * sequential
   * nested
2. **Approaches to deal with multiple interrupts (homework)**
   * disable all interrupts while an interrupt is being processed.
   * define priorities for interrupts and to allow an interrupt of higher priority to cause a lower-priority interrupt handler to be interrupted

#### 4. Program execution example

add pics





### Chapter-04 Cache Memory

#### 1. Memory hierarchy

1. Internal memory
   * Inside processor -- register and L1 cache
   * Motherboard -- L2 cache
   * Main memory -- DRAM and L3 cache
2. External memory
   * Peripherals -- disk, tape

#### 2. Cache Memory

* A cache is a small amount of fast memory
* Contains **a copy** of portions of main memory
* When processor read a word, check cache first
  * If yes, deliver to processor
  * If no, a block is read into the cache

#### 3. Cache structure

* Word $=n$ bits
* Address space $=2^n$
* Block size $=K$ words
* Number of blocks in main memory $M=2^n/K$
* Cache contains $C$ lines (blocks), each contains $K$ words, plus a tag uniquely identifying the lines.
* $C<<M$

#### 4. Mapping functions

1. **Direct mapping**

   * Each block of memory maps to only one cache line

   * It is always be found in the same line

   * Multiple blocks are mapped to one cache line

   * $$
     i=j\ mod\ m
     $$

   * $i=$ used cache line

   * $j=$ number of all blocks in main memory

   * $m=$ the number of lines in cache

2. **Associative mapping**

   * A main memory block can be mapped to any line in the cache

3. **Set associative mapping**

   * Cache is divided into a number of sets

   * Each set contains a number of lines

   * A given block can be mapped to any line in a given set

   * $$
     m=v\times k \\
     i=j\ mod\ v
     $$

   * $i=$ used cache line

   * $j=$ number of all blocks in main memory

   * $v=$ number of sets in cache line

   * $k=$ number of lines in a set **($k-$way associative mapping)**

   * $m=$ the number of lines in cache

#### 5. What are the differences among sequential access, direct access, and random access? (homework)

* **Sequential access**: Memory is organized into units of data. Access must be made in a specific linear sequence. 
* **Direct access**: Individual blocks or records have a unique address based on physical location. Access is accomplished by direct access. 
* **Random Access**: Each addressable location in memory has a unique, physically wired-in addressing mechanism. The time to access a given location is independent of the sequence of prior accesses and is constant.



### Chapter-05 Internal Memory

#### 1. Memory type

1. **RAM** random access memory

   Allows reading and writing data through electrical signals

   1. **DRAM**
      * Bits stored as charge
   2. **SRAM**
      * Use flip-flop logic gate

2. **ROM** read only memory

   * Non-volatile, no power is needed
   * Can read, cannot write

3. **PROM** programmable read only memory

   * Non-volatile, written only once

4. **EPROM** erasable programmable read only memory

   * Before write, the storage cells must be erased

5. **EEPROM** electronically erasable programmable read only memory

   * Can be written without erasing prior content

6. **Flash**

   * Intermediate between EPROM and EEPROM in both cost and functionality
   * Entire memory can be erased in a few seconds
   * Possible to erase just blocks of memory rather than an entire chip





### Chapter-07 Input and Output

#### 1. I/O techniques

1. **Programmed I/O**
   * CPU has direct control over I/O
     * Sensing status
     * Read/Write commands
     * Transferring data
   * CPU waits for I/O module to complete operaion
2. **Interrupt driven I/O**
   * I/O module interrupts CPU when ready
   * No repeated CPU checking of device
3. **Direct Memory Access (DMA)**
   1. Additional module take over control for I/O
   2. DMA performs transfer directly with memory while CPU does not use other process
   3. DMA sends interrupt when completed.





### Chapter-08 Operating System

#### 1. OS scheduling

1. Long term scheduling
   * The decision to add to the pool of processes to be executed.
2. Medium term scheduling
   * The decision to add to the number of processes that are partially or fully in main memory
3. Short term scheduling
   * The decision as to which available process will be executed by the processor

#### 2. Process

* A program in execution

#### 3. Paging

1. **Logical address** (Relative)
2. **Physical address**





### Chapter-09 ALU

#### 1. Unsigned multiplication

$$
C\ \ \ \ \ A\ \ \ \ \ Q\ \ \ \ \ M
$$

#### 2. Booth Algorithm

$$
A\ \ \ \ \ Q\ \ \ \ \ Q_{-1}\ \ \ \ \ M
$$





### Chapter-10 Instruction Set

#### 1. Instruction set design: design issue

1. operation repertories
2. data types
3. instruction formats
4. registers
5. addressing mode

#### 2. Number of address

* 3:

$$
c=a+b
$$

* 2:

$$
a=a+b
$$

* 1:
  * implicit second address: process register **(AC)**

$$
AC\leftarrow AC\ OP\ B
$$

* 0:
  * all address implicit: stack

$$
T\leftarrow (T-1)\ OP\ T
$$





### Chapter-11 Instruction Set: Addressing mode and Formats

#### 1.  Addressing mode

1. Immediate

   * operand is part of the instruction

2. Direct

   * address field contains effective address

   $$
   EA=A
   $$

3. **Indirect**

   * address filed refer to the address of a word in memory, which contains an full-length address of an operand

   $$
   EA=(A)
   $$

4. **Register**

   * address field is a register

   $$
   EA=R
   $$

5. **Register Indirect**

   * address field refers to a register and then like indirect addressing

   $$
   EA=(R)
   $$

6. **Displacement**

   * combines capability of direct addressing and register indirect addressing

   $$
   EA=A+(R)
   $$

   1. relative addressing (PC)
   2. base-register addressing (R as base)
   3. indexing (interation)

7. Stack addressing

   * operand is on the top of stack

#### 2. Allocation of Bits

1. Number of addressing modes
2. Number of operands
3. Register versus memory
4. Number of register set
5. Address range
6. Address granularity





### Chapter-12 CPU Structure and Function

#### 1. Instruction pipelining

1. Cycle time

$$
\tau=max\{\tau_i\}+d\ \ \ \ \ 1\le i\le k
$$

1. Time to execute without pipelining

$$
T_1=nk\tau
$$

1. Time to execute with pipelining

$$
T_k=[k+(n-1)]\tau
$$

1. Speedup

$$
S_k=\frac{T_1}{T_k}=\frac{nk}{k+(n-1)}
$$

#### 2. Branch dealt

1. Multiple streams
2. Prefetch branch target
3. Loop buffer
4. Branch prediction
5. Delayed branching











 











