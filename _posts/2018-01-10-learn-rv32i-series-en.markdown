---
layout: post
title:  "Learn RISCV RV32I from Scratch Series"
date:   2018-01-10 23:00:00 +0800
categories: blog en-post
---

Hello there! Thanks for your interesting in RISC architecture then reading this blog.

This article would list my experience for building RISCV 32-bit Base Instruction Set (RV32I), which form project [learn-rv32i-asap](https://github.com/watz0n/learn-rv32i-asap) between Nov 2017 to Jan 2018, reference form [RISCV Sodor Project](https://github.com/librecores/riscv-sodor). These topics are talk about how to use UC Berkeley Chisel3, a new hardware description language (HDL), to implement RV32I core. Then, how to setup Verilator Simulator for validating core functionality. Finally, how to use RISCV Front-End Server (FESVR) to send executable binary code through RISCV Debug Module. These documents are not fully finished yet, I would update as soon as it's ready.

This series would introduce topics in below order:
1. What is Chisel3 HDL? How to use it for circuit behavior modeling?
2. What is RISCV Base Instruction Set (RV32I)? How to implement from scratch?
3. What is RISCV Control and Status Register (CSR)? How to add it to RV32I core?
4. What is RISCV Debug Module (DM)? How to connect it to RV32I core?
5. What is RISCV Front-End Server (FESVR)? How it works with Debug Transport Module (DTM) to transfer executable binary code into RV32I core simulator?

New content would update a link in topic list, until all topics are finished.

---

### 1. UC Berkeley Chisel3 HDL Introduction

TBD

---

EX. Learning Materials 
---

These materials are useful for my RV32I implementation, hope it would help your on your walkthrough.

University Courses (Online Data)
===
* Learn Chisel3 by building GCD Module
    * [UC Riverside EECS168](https://github.com/sheldonucr/ucr-eecs168-lab/tree/master/lab4) : Use this simple GCD behavioral model.
    * [MIT 6.884](http://csg.csail.mit.edu/6.884/handouts.html) : The original GCD module design data, use the synthesizable design (cpath/dpath) as reference.
    * [Berkeley CS250 FA09](https://inst.eecs.berkeley.edu/~cs250/fa09/) : Universal GCD module input/output interface for implementation. 
* Implementation RV32I core
    * [Berkeley CS61C SP16](http://inst.eecs.berkeley.edu/~cs61c/sp16/) : Prerequisite course of CS152, worth to study the basic ideas from old RISC architecture. The [CS61C FA17](http://inst.eecs.berkeley.edu/~cs61c/fa17/) use new RISCV textbook.
    * [Berkeley CS150 FA13](http://www-inst.eecs.berkeley.edu/~cs150/fa13/) : 
    This laboratory course has essential concept for ValidIO/Decoupled mechanism.
    * [Berkeley CS152 FA16](http://www-inst.eecs.berkeley.edu/~cs152/fa16/): RISCV in real class, suggest reading all lectures to build your database in mind before implementation.

Online Courses
===
* [MITx 6.004x Series](https://www.edx.org/course/computation-structures-part-1-digital-mitx-6-004-1x-0) : This course enlighten me to Digital Design world, and apply BETA core design experience in this design. If you want to look this course without edX account, here is the [official website](http://computationstructures.org/).
* [MITx 6.005x Series](https://www.edx.org/course/software-construction-java-mitx-6-005-1x) : Understand how to use Java language, and apply Java Exception assignment experience for Chisel3 unit-test framework, scalatest.

Books
===
* [The RISC-V Reader: An Open Architecture Atlas](http://riscvbook.com/) : Great book to understand Privileged Spec. CSR behaviors.
* [Programming in Scala, First Edition](https://www.artima.com/pins1ed/) : Comprehensive Scala introduction book, strong recommendation to read before using Chisel3.

Wiki
===
* [Chisel3 Official Wiki](https://github.com/freechipsproject/chisel3/wiki) : 
Lots of Chisel3 use cases and examples.
* [Chisel Learning Journey](https://github.com/librecores/riscv-sodor/wiki/Chisel-Learning-Journey) : Great content about Sodor implementation since 2017/12 update, especially the [Overview page](https://github.com/librecores/riscv-sodor/wiki/overview) has crucial information about DM module non-standard command 0x44(reset the core).

Projects
===
* [GitHub learn-chisel3-gcd](https://github.com/watz0n/learn-chisel3-gcd) : My Chisel3 learning experience, focus on how to link HDL (Verilog/VHDL) experience with Chisel3 design pattern, and test Chisel3 test-bench fesibility.
* [GitHub learn-rv32i-unittest-alu](https://github.com/watz0n/learn-rv32i-unittest-alu) : The beginning of this projcet, represent the first step for building RISCV Reg-Reg and Reg-Imm datapath form scratch.
* [GitHub learn-rv32i-asap](https://github.com/watz0n/learn-rv32i-asap) : The first milestone for me to simulate 1-stage RISCV-32I core
