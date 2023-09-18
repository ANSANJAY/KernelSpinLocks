Problem with atomic instructions:
=================================

        Can only work with CPU word and double word size.
        Cannot work with shared data structures of custom size.


In real life, critical regions can be more than one line. And these code paths such execute atomically to avoid race condition.

To ensure atomicity of such code blocks locks are used.



Spinlocks
==============

The most common lock in the Linux kernel is the spin lock.

Spinlocks are used to protect short code sections that comprise just a few C statements and are therefore
quickly executed and exited.

A spin lock is a lock that can be held by at most one thread of execution.

When the thread tries to acquire lock which is already held?
--------------------------------------------------------------
        The thread busy loops/spins waiting for the lock to become available.

When the thread tries to acquire lock which is available?
--------------------------------------------------------------
        The thread acquires the lock and continues.

