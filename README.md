# FIFO Memory Implementation in Verilog

## Project Overview
| Description |
|-------------|
| This project implements a **First-In-First-Out (FIFO) memory** using Verilog. FIFO memory is used to **buffer data** between two processes running at different speeds. This implementation is **parameterizable** with configurable data width and depth and supports **full** and **empty** flags. |

---

## Features
| Feature | Description |
|---------|-------------|
| Configurable DATA_WIDTH and FIFO_DEPTH | Allows adjusting the data width and number of entries in FIFO |
| Circular buffer implementation | Efficient memory usage using wrap-around pointers |
| Full and Empty flag detection | Indicates whether FIFO is full or empty |
| Write block on full | Prevents data overwrite when FIFO is full |
| Read block on empty | Prevents invalid reads when FIFO is empty |
| Easy integration | Can be used in other digital systems |

---

## FIFO Module Ports
| Port Name | Direction | Description |
|-----------|-----------|-------------|
| clk       | input     | Clock signal |
| rst       | input     | Synchronous reset |
| wr_en     | input     | Write enable |
| rd_en     | input     | Read enable |
| din       | input     | Data input |
| dout      | output    | Data output |
| full      | output    | FIFO full flag |
| empty     | output    | FIFO empty flag |

---

## Testbench Overview
| Testbench Action | Description |
|-----------------|-------------|
| Write data      | Writes sequential data into FIFO until full |
| Read data       | Reads data from FIFO until empty |
| Flag check      | Monitors full and empty flags for correct operation |

---

## Simulation Console Output
| Time (ns) | Action        | Data | Full | Empty |
|------------|---------------|------|------|-------|
| 25000      | Write         | A1   | 0    | 0     |
| 45000      | Write         | B2   | 0    | 0     |
| 65000      | Write         | C3   | 0    | 0     |
| 85000      | Write         | D4   | 1    | 0     |
| 95000      | Write Attempt | E5   | 1    | 0     |
| 115000     | Read          | A1   | 0    | 0     |
| 135000     | Read          | B2   | 0    | 0     |
| 155000     | Write         | F6   | 0    | 0     |
| 175000     | Write         | 07   | 1    | 0     |
| 195000     | Read          | C3   | 0    | 0     |
| 215000     | Read          | D4   | 0    | 0     |
| 235000     | Read          | F6   | 0    | 0     |
| 255000     | Read          | 07   | 0    | 1     |

---

## Observations
| Observation | Result |
|-------------|--------|
| Writes blocked when FIFO full | Verified (E5 was not written) |
| Reads blocked when FIFO empty | Verified (last read left FIFO empty) |
| Data order | FIFO order maintained (first-in, first-out) |
| Full & Empty flags | Work correctly |

---

## How to Run on EDA Playground
| Step | Instruction |
|------|-------------|
| 1    | Open [EDA Playground](https://www.edaplayground.com/) |
| 2    | Set **Language**: SystemVerilog |
| 3    | Set **Simulator**: Icarus Verilog |
| 4    | Paste `code` in one file and `testbench` in another |
| 5    | Click **Run** to simulate and view console output |

---

