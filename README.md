# 590-59-ASSIGMENT2

# Dining Philosophers – Java Threads

## Team Members

* Jimena Luna




## How to Compile and Run

From the project root directory:

### Compile

```bash
javac -d out src/dining/*.java
```

### Run

```bash
java -cp out dining.DiningPhilosophers
```



## Design Overview

This program simulates the classic Dining Philosophers problem using Java threads. Each philosopher runs in its own thread and alternates between thinking and eating. Forks are shared resources protected by locks. A semaphore acts as a waiter to control how many philosophers may attempt to eat simultaneously.

Console output shows when philosophers are thinking, picking up forks, eating, and putting forks down.

## Representation

* **Philosopher** → Implemented as a `Runnable` executed by a `Thread`
* **Fork** → Object containing a fair `ReentrantLock`
* **Table** → Represented by an array of forks and a shared semaphore
* **Thinking Phase** → Thread sleeps for a random short time
* **Eating Phase** → Philosopher acquires two forks, eats, then releases them



## Deadlock Prevention

Two techniques are used:

1. A semaphore initialized to `N - 1` ensures that at most `N - 1` philosophers may try to pick up forks at once.
2. Forks are always picked up in a consistent global order (lower‐ID fork first).

Together, these eliminate circular waiting and prevent deadlock.

---

## Starvation

Both the semaphore and fork locks are created as **fair**, meaning waiting threads are served in order. This greatly reduces the chance of starvation.



## Race Conditions

Fork access is protected by locks so only one philosopher may hold a fork at a time. This prevents multiple threads from modifying or using the same fork simultaneously.


## Notes

Deadlock is prevented by design. Starvation is extremely unlikely under fair scheduling. The program continuously runs and prints philosopher activity to demonstrate correct synchronization.
