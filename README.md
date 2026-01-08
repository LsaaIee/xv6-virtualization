# xv6 Virtual Memory Experiments

This repository contains a set of operating system experiments
built on top of the MIT xv6-riscv kernel.

The focus of this project is **virtual memory management** and
**page replacement mechanisms**, implemented as part of an
Operating Systems course.

> Base kernel: MIT xv6-riscv  
> My contribution: Virtual memory subsystem extensions

---

## Implemented Features
- Additional system calls
- Linux EEVDF scheduler
- mmap / munmap system calls
- Page fault handling for file-backed and anonymous mappings
- Lazy allocation (on-demand paging)
- Page-level swapping with Clock (LRU-based) replacement policy

---

## Project Structure
- `xv6-riscv/` : Base kernel with modifications
- `assignments/` : Per-project design and implementation notes
- `docs/` : Architecture and design discussions

---

## Key Learning Outcomes
- Deep understanding of RISC-V page tables
- Handling page faults in a real kernel
- Designing swap systems and replacement policies
- Debugging kernel-level memory bugs
