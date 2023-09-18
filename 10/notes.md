Important Points with Spinlocks
===============================

1. If a lock is acquired but no longer released, the system is rendered unusable.

	All processors— including the one that acquired the lock — sooner or later arrive at a point where they must enter the critical region.

	They go into the endless loop to wait for lock release, but this never happens and deadlocks.

2. On no account should spinlocks be acquired for a longer period because all processors waiting for lock release are no longer available for other productive tasks.

3. Code that is protected by spinlocks must not go to sleep.
	it must also be ensured that none of the functions that are called inside a spinlocked region can go to sleep!
	Ex: kmalloc with GFP_KERNEL.


	
