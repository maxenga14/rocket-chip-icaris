# Rocket Core Detailed Reference

## Introduction
The Rocket Core is a high-performance, in-order processor designed for various applications ranging from embedded systems to general-purpose computing. This document provides a comprehensive overview of the Rocket Core's in-order pipeline implementation, detailing each stage, its functionalities, and the supporting components integral to its operation.

The purpose of this document is to serve as a reference for engineers and developers involved in designing, implementing, and verifying Rocket Core pipelines. By exploring the architecture, SystemVerilog code examples, and practical implementation guidance, readers will gain insights into optimizing and utilizing the Rocket Core design efficiently.

## Complete 5-Stage Pipeline Architecture

The Rocket Core employs a classical 5-stage instruction pipeline, which enhances instruction throughput and overall performance by allowing multiple instructions to be processed simultaneously. The stages of the pipeline include:

1. **Instruction Fetch (IF)**
   - The IF stage retrieves the next instruction from memory. It utilizes an instruction cache (I-Cache) to minimize access latency. The program counter (PC) holds the address of the instruction to be fetched, and a branch predictor may be employed to speculate on control flow.

2. **Instruction Decode (ID)**
   - In this stage, the fetched instruction is decoded into control signals, and operands are read from the register file. The ID stage also handles immediate value extraction, operand forwarding, and hazard detection.

3. **Execute (EX)**
   - The EX stage performs the necessary calculations based on the operation specified by the instruction. It involves arithmetic logic unit (ALU) operations, address calculations for memory access, and branch target calculations.

4. **Memory Access (MEM)**
   - This stage manages data memory reads and writes. If the instruction is a load or store, the address generated in the EX stage is used to access the data cache (D-Cache).

5. **Write Back (WB)**
   - The final stage writes the results of the computation back to the register file, completing the instruction execution process. This stage ensures that the register file is updated with the latest output from the preceding stages, allowing future instructions to access the most current data.