spin_trylock()
---------------

int spin_trylock(spinlock_t *lock);

Tries to acquire given lock;

	If not available, returns zero.

	If available, it obtains the lock and returns nonzero
