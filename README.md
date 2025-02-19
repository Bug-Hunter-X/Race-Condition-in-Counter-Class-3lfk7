# Race Condition in a Simple Counter

This repository demonstrates a classic race condition bug in Java.  The `Counter` class uses an integer variable to keep track of a count which is incremented by multiple threads simultaneously.  Because of a lack of proper synchronization, the final count is usually less than the expected 20000 (10000 increments from each of two threads). 

## Bug Description

The `increment()` method is not atomic. Multiple threads can interleave their execution, leading to lost updates of the `count` variable. The problem stems from the fact that `count++` is not a single, indivisible operation; it involves multiple steps: read, increment, write.  If multiple threads are executing this simultaneously, some increments might be overwritten.

## Solution

The solution involves using synchronization mechanisms to ensure thread safety.  Various synchronization techniques can be implemented to resolve this, including using the `synchronized` keyword, `AtomicInteger`, or locks.