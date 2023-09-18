Spinlock Methods
=====================

Header File: <linux/spinlock.h>
	

Data Structure: spinlock_t


Methods
------------

DEFINE_SPINLOCK(my_lock);   == spinlock_t my_lock = __SPIN_LOCK_UNLOCKED(my_lock);

From <linux/spinlock_types.h>:
#define DEFINE_SPINLOCK(x)      spinlock_t x = __SPIN_LOCK_UNLOCKED(x)

//To lock a spin lock
void spin_lock(spinlock_t *lock);

//To unlock a spin lock
void spin_unlock(spinlock_t *lock);
