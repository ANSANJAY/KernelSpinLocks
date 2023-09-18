Why was there no error?
=======================
	Because no other process tried to take the same spinlock.

For example, 
	thread A acquires a spin lock.
	Thread A will not be preempted until it releases the lock
	 But if thread A sleeps while holding the lock
	thread B could be scheduled to run since the sleep function will invoke the scheduler. 
	And thread B could acquire the same lock as well.
	Deadlock
	


