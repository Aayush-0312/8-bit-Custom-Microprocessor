# ⚡ 8-Bit Custom Microprocessor 

An 8-bit modular CPU architecture designed, simulated, and executed in **Logisim**. The microprocessor features a hierarchical Arithmetic Logic Unit (ALU), an internal register file, and custom ROM instruction decoding capable of executing dynamic arithmetic/logic calculations while streaming ASCII text to a terminal display interface.

---

## 🛠 Tech Stack & Key Concepts

- **Simulation Engine:** Logisim / Logisim-Evolution
- **Architecture:** 8-Bit Datapath, Multi-Operation ALU, Register File
- **Memory & Encoding:** Hexadecimal Instruction Streams, ASCII Memory-Mapping, Control-Payload Microcode

---

## 🚀 Key Features

* **Modular 8-Bit ALU:** Supports **6 distinct operations**:
  * Arithmetic: `ADD`, `SUB`
  * Bitwise Logic: `AND`, `OR`, `XOR`, `NOT`
* **Dedicated Register File:** Handles temporary operand storage and state management during execution loops.
* **2-Byte Custom Instruction Decoding:** Processes custom hex microcode (`[Control Byte] [Payload]`) loaded from memory files (`Inp_data.txt`).
* **Dynamic Terminal Output:** Streams formatted ASCII headers (up to 23 characters) and outputs live arithmetic calculation results directly to a simulated TTY display module.

---

## 📑 Instruction Set & Memory Mapping

The control unit parses 2-byte hexadecimal sequences to trigger execution cycles and display rendering:

$$\text{Instruction Format} = \text{[ Control Byte ]} \quad \text{[ Payload / ASCII Byte ]}$$

### Example Instruction Pair Breakdown:
| Byte Type | Example Hex | Purpose |
| :--- | :--- | :--- |
| **Control Byte** | `14` / `16` / `30` | Signals control lines (e.g., set row/line, pulse display enable, reset control) |
| **Payload Byte** | `43` (`'C'`) / `41` (`'A'`) | Contains the raw ASCII character hex value or binary data operand |

---

## 📂 Project Structure

```text
.
├── docs/
│   └── ascii_table.png       # Reference ASCII mapping table used for microcode encoding
├── firmware/
│   └── Inp_data.txt          # Raw hexadecimal ROM memory image containing control & text payloads
├── src/
│   ├── ASSI.circ             # 🌟 MAIN CPU SCHEMATIC (Top-Level Entry Point)
│   ├── alu.circ              # Integrated Arithmetic Logic Unit module
│   ├── registers_file.circ   # Multi-register storage unit
│   ├── add.circ              # 8-bit Adder module
│   ├── sub.circ              # 8-bit Subtractor module
│   ├── and.circ              # Bitwise AND module
│   ├── or.circ               # Bitwise OR module
│   ├── xor.circ              # Bitwise XOR module
│   └── not.circ              # Bitwise NOT module
└── README.md
