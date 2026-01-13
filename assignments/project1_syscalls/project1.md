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
- System calls in xv6 are initiated via the `ecall` instruction, transferring control from user space to the kernel trap handler
- Each system call requires updates across multiple layers, including user-level stubs, syscall number registration, and kernel-side implementations
    - a system call number is passed through a designated register and used by the kernel to dispatch the call to the appropriate handler
- Adding a new system call requires defining a user-level interface, including function prototypes and system call numbers, so that user programs can invoke the kernel functionality
- On the kernel side, the system call must be registered in the syscall dispatch table and implemented in the appropriate kernel source file, allowing controlled access to kernel data structures
- This layered structure enforces a clear boundary between user space and kernel space, preventing direct access to kernel internals while still allowing controlled interaction through system calls
- Process-related system calls operate on the global process table and require careful handling of process identifiers
