# Multithreading-with-Condition-Variables
Multithreading with Condition Variables
## Get familiar with Wait and Signal
In this folder https://github.com/remzi-arpacidusseau/ostep-code/tree/master/threads-cv, there are different C programs 
### Fork/Join Problem
- `join_spin.c`: Working solution but wastes CPU.
- `join_no_lock.c`: What happens when you don't put a lock around the state change and signal
- `join_no_state_var.c`: What happens if you don't have a state variable
- `join.c`: A working solution
- `join_modular.c`: A modularized version
### Producer/Consumer Problem
- `pc_single_cv.c`: What happens if you only use one condition variable
- `pc.c`: A working solution

In the terminal, type `make` to compile the C programs and run the executables in the following order:
- `./join_spin`
- `./join_no_state_var`
- `./join_no_lock`
- `./join`
You will see that `join_spin` works but wastes CPU and thus slow. `join_no_state_var` and `join_no_lock` don't work (parent sleep forever since signal is lost).
`join` is a working solution and `join_modular` is a modularized version.

## Problem 1: 
Write a program where the main default thread spawns N threads. When started, thread i should
sleep for a random interval between 1 and 10 seconds, print the message “I am thread i” to screen,
and exit. Without any synchronization between the threads, the threads will print their messages
in any order. Add suitable synchronization using condition variables such that the threads print
their messages in the order 1, 2, ..., N. You may want to start with N = 2 and then move on to
larger values of N. Note that you must solve all these exercises using condition variables, and not
just inefficient busy waiting, for synchronization.
Submit to Canvas screenshots without synchronization and with synchronization using condition variables.

## Problem 2:
Write a program with N threads. Thread i must print number i in a continuous loop. Without any
synchronization between the threads, the threads will print their numbers in any order. Now, add
synchronization to your code such that the numbers are printed in the order 1, 2, ..., N, 1, 2, ...,
N, and so on. You may want to start with N = 2 and then move on to larger values of N.
