# KIWI SEARCH ENGINE MULTITHREADING

This project implements a **multithreaded data storage engine** using **C and pthreads**, focusing on synchronization mechanisms, read–write concurrency, global locking strategies, and performance benchmarking.  
It was developed as part of the **MYY601 – Operating Systems** course at the **University of Ioannina**.  
The final grade of the project is **50 out of 100**.

---

## TABLE OF CONTENTS
1. [Overview](#overview)
2. [Features](#features)
3. [Instructions](#instructions)
4. [Implementation Details](#implementation-details)
5. [Usage](#usage)
6. [License](#license)
7. [Contact](#contact)

---

## OVERVIEW

The **Kiwi Search Engine Multithreading** project focuses on implementing a multithreaded storage engine capable of handling concurrent read and write requests.  
The primary goal is to:

- Improve performance using **thread-level parallelism**  
- Ensure correctness through **synchronization techniques**  
- Support **configurable workloads** through command-line execution  

The engine uses a mixture of global locks, mutexes, read–write mechanisms, and benchmarking tools to evaluate concurrency behavior.

---

## FEATURES

- **Global Synchronization**
  - Implementation of global locks  
  - Mutual exclusion to prevent concurrent write conflicts  

- **Read–Write Concurrency**
  - Multiple readers executing simultaneously  
  - Single-writer locking to ensure safety  
  - Adjustable write percentage for mixed workloads  

- **Multithreaded Execution**
  - Dynamic thread creation  
  - Automatic workload distribution among threads  

- **Performance Evaluation**
  - Execution time measurement  
  - Logging of results for analysis  
  - Benchmarking for read, write, and mixed scenarios  

---

## INSTRUCTIONS

- **Objective:**  
  Implement a synchronized multithreading model for a storage engine using C and pthreads.

- **How to Run:**  
  Compile the program using:
  ```bash
  make all
  ```
- **Execute the benchmark tool using:**
  ./kiwi-bench write <operations>
  ./kiwi-bench read <operations>
  ./kiwi-bench readwrite <operations> <write_percentage> <threads>
  **Feedback:**
  Performance logs and output files are generated to evaluate the correctness and efficiency of the engine.

---

## IMPLEMENTATION DETAILS

- **Global Locking**
  - Peterson’s Algorithm used for mutual exclusion  
  - Prevents concurrent writes and ensures ordering

- **Mutex Protection**
  - Shared structures in `db_add` and `db_get` protected using pthread mutexes

- **Read-Write Mechanism**
  - Condition variables ensure safe reader–writer behavior  
  - Multiple readers allowed; writers wait for exclusive access

- **Thread Management**
  - `thread_maker` function dynamically assigns tasks  
  - Uses `pthread_create()` and `pthread_join()` for thread lifecycle control

- **Benchmark Logging**
  - Execution times recorded for analysis  
  - Output files generated for performance comparison

- **Error Handling**
  - Bus error fixes and read inconsistency reductions by improving locking logic

---

## USAGE

1. **Compile using:**
```bash
make all
```
2. Execute any of the supported benchmark commands:
   - **write only**
     ```bash
     ./kiwi-bench write <operations>
     ```
     - **read only**
     ```bash
     ./kiwi-bench read <operations>
     ```
     - **Mixed read/write**
     ```bash
     ./kiwi-bench readwrite <operations> <write_percentage> <threads>
     ```
3. Review the output logs to analyze performance, locking behavior, and thread efficiency.

---

## LICENSE

This project was developed as part of the  
**MYE031 – Operating Systems** course at the University of Ioannina.

Final implementation by the project creators.

---

## CONTACT

**Christos Gkovaris**  
University of Ioannina – Computer Science and Engineering  
GitHub: https://github.com/ChristosGkovaris

**Maria Spanou**  
University of Ioannina – Computer Science and Engineering  
GitHub: https://github.com/SpanouMaria