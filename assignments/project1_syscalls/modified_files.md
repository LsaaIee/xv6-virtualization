# Modified Files

## kernel/syscall.h
- Added system call numbers for getnice, setnice, ps, meminfo, waitpid, and getpname
- These identifiers are used by the syscall dspatcher to route system calls

## kernel/syscall.c
- Registered newly added system calls in the syscall dispatch table
- Linked syscall numbers to their corresponding kernel implementations

## kernel/sysproc.c
- Implemented process-related system calls such as getnice, setnice, ps, and waitpid
- Accessed process metadata through the global process table

## user/user.h
- Declared user-level function prototypes for the new system calls

## user/usys.pl
- Added user-level syscall stubs to enable invocation from user programs