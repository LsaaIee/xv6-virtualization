# Project 3 – Virtual Memory

## Objective
Extend xv6 to support memory-mapped files and lazy allocation.

## Implemented Components
- mmap() system call
- Page fault handler
- munmap() system call
- freemem() system call

## Key Concepts
- File-backed vs anonymous mappings
- On-demand page allocation
- Permission enforcement (PROT_READ / PROT_WRITE)
