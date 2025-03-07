# RV32IM-Pipelined-Processor
Design and implementation of a custom 32-bit RISC-V processor supporting the RV32IM instruction set architecture. 

## Supported Instructions

| **Opcode**    | **Instruction**  | **Format** | **Description**                          | **Example**            |
|---------------|------------------|------------|------------------------------------------|------------------------|
| `0110011`     | ADD              | R-Type     | rD = rS1 + rS2                           | `add r3, r1, r2`       |
| `0110011`     | SUB              | R-Type     | rD = rS1 - rS2                           | `sub r3, r1, r2`       |
| `0110011`     | AND              | R-Type     | rD = rS1 & rS2                           | `and r3, r1, r2`       |
| `0110011`     | OR               | R-Type     | rD = rS1 | rS2                           | `or r3, r1, r2`        |
| `0110011`     | XOR              | R-Type     | rD = rS1 ^ rS2                           | `xor r3, r1, r2`       |
| `0110011`     | SLL              | R-Type     | rD = rS1 << rS2                          | `sll r3, r1, r2`       |
| `0110011`     | SLT              | R-Type     | rD = if (rS1 < rS2) return True          | `slt r3, r1, r2`       |
| `0110011`     | SLTU             | R-Type     | rD = if (rS1(uint) < rS2(uint)) return True | `sltu r3, r1, r2`   |
| `0110011`     | SRA              | R-Type     | rD = rS1 >>> rS2                         | `sra r3, r1, r2`       |
| `0110011`     | MUL              | R-Type     | rD = rS1 * rS2                           | `mul r3, r1, r2`       |
| `0110011`     | DIV              | R-Type     | rD = rS1 / rS2                           | `div r3, r1, r2`       |
| `0110011`     | REM              | R-Type     | rD = rS1 % rS2                           | `rem r3, r1, r2`       |
| `0010011`     | ADDI             | I-Type     | rD = rS1 + imm                           | `addi r3, r1, 10`      |
| `0010011`     | SLTI             | I-Type     | rD = if (rS1 < imm) return True          | `slti r3, r1, 0xFF`    |
| `0010011`     | SLTIU            | I-Type     | rD = if (rS1(uint) < rS2(uint)) return True | `sltiu r3, r1, 0xFF`|
| `0010011`     | SLLI             | I-Type     | rD = rS1 << imm                          | `slli r3, r1, 0xFF`    |
| `0010011`     | SRAI             | I-Type     | rD = rS1 >>> imm                         | `srai r3, r1, 0xFF`    |
| `0010011`     | ORI              | I-Type     | rD = rS1 \| imm                          | `ori r3, r1, 0xFF`     |
| `0010011`     | XORI             | I-Type     | rD = rS1 ^ imm                           | `xori r3, r1, 0xFF`    |
| `0000011`     | LB               | I-Type     | Load byte from memory                    | `lb r3, 0(r1)`         |
| `0000011`     | LBU              | I-Type     | Load byte unsigned from memory           | `lbu r3, 0(r1)`        |
| `0000011`     | LH               | I-Type     | Load halfword from memory                | `lh r3, 0(r1)`         |
| `0000011`     | LHU              | I-Type     | Load halfword unsigned from memory       | `lhu r3, 0(r1)`        |
| `0000011`     | LW               | I-Type     | Load word from memory                    | `lw r3, 0(r1)`         |
| `0100011`     | SB               | S-Type     | Store byte to memory                     | `sb r3, 0(r1)`         |
| `0100011`     | SH               | S-Type     | Store halfword to memory                 | `sh r3, 0(r1)`         |
| `0100011`     | SW               | S-Type     | Store word to memory                     | `sw r3, 0(r1)`         |
| `1100011`     | BEQ              | B-Type     | Branch if equal                          | `beq r1, r2, label`    |
| `1100011`     | BNE              | B-Type     | Branch if not equal                      | `bne r1, r2, label`    |
| `1100011`     | BLT              | B-Type     | Branch if less than                      | `blt r1, r2, label`    |
| `1100011`     | BGE              | B-Type     | Branch if greater than or equal          | `bge r1, r2, label`    |
| `1100011`     | BLTU             | B-Type     | Branch if less than (uint)               | `bge r1, r2, label`    |
| `1100011`     | BGEU             | B-Type     | Branch if greater than or equal (uint)   | `bge r1, r2, label`    |
| `1101111`     | JAL              | J-Type     | Jump and link                            | `jal r1, label`        |
| `1100111`     | JALR             | I-Type     | Jump and link register                   | `jalr r1, r2, 0`       |
| `0110111`     | LUI              | U-Type     | Load upper immediate                     | `lui r1, 0x12345`      |
| `0010111`     | AUIPC            | U-Type     | Add upper immediate to PC                | `auipc r1, 0x1000`     |
