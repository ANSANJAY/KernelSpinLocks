How are spinlocks implemented
=============================

Simple Implementation
----------------------
	
	A spinlock is a mutual exclusion device that can have only two values:
		Locked
		Unlocked

	It is usually implemented as a single bit in an integer value.

	Code wishing to take out a particular lock tests the relevant bit.
		If the lock is available, the "locked" bit is set and the code continues into the critical section		   If, instead, the lock has been taken by somebody else, the code goes into a tight loop where it repeatedly checks the lock until it becomes available.
		 This loop is the "spin" part of a spinlock.


Real Implementation
--------------------

The "test and set" operation must be done in an atomic manner so that only one thread can obtain the lock, even if several are spinning at any given time. 

Spinlocks are built on top of hardware-specific atomic instructions.

The actual implementation of spinlock is different for each architecture the linux supports.




