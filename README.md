# ✅ NTU Sorting Tool – Algorithms Fall 2024 Programming Assignment 1

## 📄 Introduction
This project implements six sorting algorithms as part of NTU's Algorithms Fall 2024 course. The program reads unsorted data from an input file and outputs sorted results using the selected sorting algorithm. The tool is performance-monitored and produces CPU time and memory usage reports.

## 📚 Table of Contents
- [Introduction](#-introduction)
- [Installation](#-installation)
- [Usage](#-usage)
- [Sorting Algorithms](#-sorting-algorithms)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Input and Output Format](#-input-and-output-format)
- [Example](#-example)
- [Visualization](#-visualization)
- [Performance](#-performance)
- [Compilation Notes](#-compilation-notes)
- [Troubleshooting](#-troubleshooting)
- [License](#-license)

## 🛠️ Installation

### Requirements
- C++ compiler (tested with `g++`)
- `make` utility
- Linux environment (EDA Union server recommended)
- gnuplot (optional, for visualization)

### Build Instructions
```bash
ulimit -s 262144        # Set stack size limit
make                    # Compile optimized version
make dbg                # Optional: Compile debug version
```

## 🚀 Usage
```bash
./bin/NTU_sort -[IS|MS|BMS|QS|RQS|HS] <input_file> <output_file>
```

### Options
- `-IS`  : Insertion Sort  
- `-MS`  : Merge Sort (Top-down)  
- `-BMS` : Bottom-up Merge Sort  
- `-QS`  : Quick Sort  
- `-RQS` : Randomized Quick Sort  
- `-HS`  : Heap Sort (optional, not graded)

## 📌 Sorting Algorithms
Implemented in `sort_tool.cpp`:
- Insertion Sort
- Merge Sort (Top-Down)
- Bottom-Up Merge Sort
- Quick Sort
- Randomized Quick Sort
- Heap Sort (structure provided)

## 🌟 Features
- Handles large datasets (up to 1 million entries)
- Measures CPU time and peak memory usage
- Custom I/O format parsing
- Support for six sorting methods
- Visualization support using `gnuplot`

## 📁 Project Structure
```
PA1/
├── bin/                # Compiled binary (NTU_sort)
├── doc/                # Contains report.pdf
├── inputs/             # Input test cases (excluded in submission)
├── outputs/            # Output sorted files
├── src/                # Source code (main.cpp, sort_tool.cpp, sort_tool.h)
├── lib/                # tm_usage library for timing/memory
├── utility/            # Result checker, gnuplot scripts
├── makefile            # Build instructions
└── report.pdf          # Report comparing sort performance
```

## 📄 Input and Output Format

**Input File (`*.in`)**
```text
# 5 data points
# index number
0 16
1 13
2 0
3 6
4 7
```

**Output File (`*.out`)**
```text
# 5 data points
# index number
0 0
1 6
2 7
3 13
4 16
```

## 💡 Example
```bash
./bin/NTU_sort -IS inputs/1000.case1.in outputs/1000.case1.out
```

## 📊 Visualization (gnuplot)
```gnuplot
set xrange [0:5]
set yrange [0:20]
plot "5.case1.in" using 1:2 with lines
plot "5.case1.out" using 1:2 with lines
```

To save as PNG:
```gnuplot
set terminal png
set output "5.case1.out.png"
replot
```

## 📈 Performance
Refer to `report.pdf` for:
- CPU time & memory comparisons
- Log-log plots of sorting complexity trends
- Explanation of best/worst/average cases for each algorithm

## ⚙️ Compilation Notes

From `makefile`:
```bash
g++ -O2 -c src/main.cpp -Ilib -o main_opt.o
g++ -O2 -c src/sort_tool.cpp -o sort_tool_opt.o
g++ -O2 sort_tool_opt.o main_opt.o -ltm_usage -Llib -o bin/NTU_sort
```

Debug build:
```bash
make dbg
```

## 🐞 Troubleshooting

| Problem                              | Solution                                      |
|--------------------------------------|-----------------------------------------------|
| Memory usage not shown               | Run on EDA Union server                       |
| Stack overflow (QuickSort crash)     | Set `ulimit -s 262144`                        |
| Checker permission denied            | `chmod +x utility/checkSubmitPA1.sh`          |

## 🪪 License
This project is part of NTU’s Algorithms Course Fall 2024 and is governed by course academic policies. Redistribution of code is not permitted without explicit permission.
