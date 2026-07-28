# ⚡ 8-Bit Custom Microprocessor

An 8-bit modular CPU architecture designed and simulated in **Logisim**(`main.circ`). The system features a hierarchical ALU, a multi-register file, and custom opcode decoding that parses hexadecimal instruction streams (`Inp_data.txt`) to execute arithmetic/bitwise operations and render ASCII output on a TTY terminal display.

---

## 🛠 Tech Stack

- **Simulator:** Logisim / Logisim-Evolution
- **Architecture:** 8-Bit Datapath, Multi-Operation ALU, Register File
- **Concepts:** Custom ISA, Hexadecimal Microcode Encoding, ASCII Memory-Mapping.

---

## 🚀 Key Features

* **Modular 8-Bit ALU:** Supports 6 distinct operations (`ADD`, `SUB`, `AND`, `OR`, `XOR`, `NOT`).
* **Dedicated Register File:** Manages temporary operand storage (`Reg A`, `Reg B`).
* **Custom ISA Decoding:** Decodes nibble-mapped microcode loaded from ROM memory images (`Inp_data.txt`).
* **TTY Terminal Output:** Renders formatted ASCII text headers and live calculation results.

---

## 🎬 Simulation Demo

![Microprocessor Execution Demo](./docs/demo.gif)
<img width="800" height="418" alt="ezgif-5481b6bd05e811b5" src="https://github.com/user-attachments/assets/f32fe1d8-04b2-4ae0-aebd-ea65bf83afe8" />

---

## 📑 Instruction Set Architecture (ISA)

The control unit parses 8-bit hexadecimal bytes from ROM (`Inp_data.txt`), using the high-nibble as the **Opcode** and the low-nibble as the **Operand / Data Parameter**
:

$$\text{Instruction Format (Hex)} = \text{[ Opcode (4-bit) ]} \quad \text{[ Operand / Data (4-bit) ]}$$

### Opcode Mapping (`0x1` – `0x0A`):

| Opcode (Hex) | Action | Description |
| :---: | :--- | :--- |
| **`1`** | `LOAD REG A` | Loads 8-bit operand into **Register A** |
| **`2`** | `LOAD REG B` | Loads 8-bit operand into **Register B** |
| **`3`** | `OUTPUT DISPLAY` | Sends contents of **Reg A** and **Reg B** to display terminal |
| **`4`** | `LOAD ALU REG E` | Loads target value into ALU internal Register E |
| **`5`** | `ALU ADD` | Executes **Addition** on `Reg A` and `Reg B` |
| **`6`** | `ALU SUB` | Executes **Subtraction** on `Reg A` and `Reg B` |
| **`7`** | `ALU AND` | Executes Bitwise **AND** on `Reg A` and `Reg B` |
| **`8`** | `ALU OR` | Executes Bitwise **OR** on `Reg A` and `Reg B` |
| **`9`** | `ALU XOR` | Executes Bitwise **XOR** on `Reg A` and `Reg B` |
| **`A`** | `ALU NOT` | Executes Bitwise **NOT** on `Reg A` |

---

## 📂 Project Structure

```text
.
├── docs/
│   ├── ascii_table.png       # Reference ASCII mapping table used for microcode encoding
│   └── demo.gif              # Simulation execution clip
├── data/
│   └── Inp_data.txt          # Raw hexadecimal ROM memory image containing control & text payloads
├── circuit/
│   ├── main.circ             # Main CPU schematic (Top-Level Entry Point)
│   ├── alu.circ              # Integrated ALU module
│   ├── registers_file.circ   # Register storage unit (Reg A, Reg B)
│   ├── add.circ              # 8-bit Adder module
│   ├── sub.circ              # 8-bit Subtractor module
│   ├── and.circ              # Bitwise AND module
│   ├── or.circ               # Bitwise OR module
│   ├── xor.circ              # Bitwise XOR module
│   └── not.circ              # Bitwise NOT module
└── README.md
