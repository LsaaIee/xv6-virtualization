# Project 1 – System calls

## Objective
Extend xv6 by implementing five new system calls that expose process scheduling and system-level information to user space

## Implemented Components
1. getnice: obtains nice value (priority) of a process
2. setnice: updates nice value of a process
3. ps: prints process information for one or multiple processes
4. meminfo: prints available memory in bytes
5. waitpid: suspends execution until a specified process terminates

## Key Concepts
- Default nice value is set to 20 and the lower value has higher priority in scheduling processes
- The range of valid nice value is 0~39
- For ps syscall, if the pid is 0, print all processes' information
    - Otherwise, print corresponding process's information 
    - If there is no process corresponding to the pid, print nothing
- System calls in xv6 are invoked via the `ecall` instruction, transferring control from user space to the kernel trap handler
- Each system call requires updates across multiple layers, including user-level stubs, syscall number registration, and kernel-side implementations
- Process-related system calls operate on the global process table and require careful handling of process identifiers
