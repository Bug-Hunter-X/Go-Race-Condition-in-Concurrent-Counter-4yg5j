# Go Race Condition in Concurrent Counter

This repository demonstrates a race condition in a Go program that uses goroutines and a mutex to increment a shared counter. The program might produce an incorrect result.  The solution demonstrates how to correctly handle concurrent access to shared resources.

## Bug
The `bug.go` file contains the buggy code. The program initializes a counter and launches 1000 goroutines, each incrementing the counter.  Even though a mutex is used, a race condition can still occur.  This is because the `i` variable in the goroutine is not properly isolated; each goroutine receives a copy of `i` *after* the loop has completed, leading to unexpected behavior.

## Solution
The `bugSolution.go` file provides a corrected version of the code.  The solution addresses the race condition by capturing the correct value of `i` using a closure.