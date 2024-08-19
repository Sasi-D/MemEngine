# MemoryEngine
This project implements a memory management engine that handles paging and virtual memory. The system simulates a computer's memory management unit, dealing with both main memory and virtual memory, and executes various commands related to process management and memory operations.

## Features

- Memory allocation for processes
- Paging system implementation
- Virtual memory management
- Process execution simulation
- Memory swapping (swap-in and swap-out operations)
- Page table management
- LRU (Least Recently Used) replacement algorithm


## Key Components

1. **Memory Initialization**: Sets up main memory and virtual memory based on input parameters.
2. **Process Management**: Handles loading, running, and killing processes.
3. **Paging System**: Implements page tables and manages page allocation.
4. **Virtual Memory Handling**: Manages swapping between main memory and virtual memory.
5. **Command Interpreter**: Processes user commands for system operation.


## Supported Commands

- `load <filename1> <filename2> .. <filenameN>`: Load executables into memory
- `run <pid>`: Execute a program
- `kill <pid>`: Terminate a program
- `listpr`: List all processes in memory
- `pte <pid> <file>`: Print page table entries for a process
- `pteall <file>`: Print all page table entries
- `swapout <pid>`: Move a process to virtual memory
- `swapin <pid>`: Move a process to main memory
- `print <memloc> <length>`: Print values in physical memory
- `exit`: Terminate the system


## Implementation Details

- Written in C/C++
- Uses LRU algorithm for page replacement
- Handles both main memory and virtual memory
- Simulates process execution with basic arithmetic operations


## Usage
**Compiling :** 

```sh
g++ -o memoryEngine main.cpp Process.cpp MemoryManager.cpp
```
**Executing :**
```bash
./memoryEngine -M <main_memory_size> -V <virtual_memory_size> -P <page_size> -i <input_file> -o <output_file>
```

## Input and Output Files

### Input Files

1. **Executable Files**: 
   - Contains programs to be loaded and executed by the memory management system.
   - Format:
     - First line: Size of the executable in KB
     - Subsequent lines: Commands to be executed
   - Supported commands in executables:
     - `add x, y, z`: Add contents of addresses x and y, store in z
     - `sub x, y, z`: Subtract contents of address y from x, store in z
     - `print x`: Print value at address x
     - `load a, y`: Store value 'a' at address y

2. **System Command Input File**:
   - Contains a sequence of system commands to be executed by the memory manager.
   - Supported system commands:
     - `load <filename1> <filename2> .. <filenameN>`
     - `run <pid>`
     - `kill <pid>`
     - `listpr`
     - `pte <pid> <file>`
     - `pteall <file>`
     - `swapout <pid>`
     - `swapin <pid>`
     - `print <memloc> <length>`
     - `exit`

### Output Files

1. **Main Output File**:
   - Contains the results and messages from executing the system commands.
   - Includes:
     - Process loading confirmations
     - Execution results of programs
     - Error messages
     - Listings of processes in memory
     - Results of memory print commands

2. **Page Table Entry Files**:
   - Generated by `pte` and `pteall` commands.
   - Contains page table information for specified processes.
   - Format includes:
     - Date and time of the command execution
     - Process ID
     - Logical page numbers and corresponding physical page numbers
