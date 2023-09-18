Can i use spinlock when the resource is shared between kernel control path in process context vs interrupt context
==================================================================================================================

	1. Your driver is executing and has taken a lock.

	2. Device the driver is handling issues a interrupt.

	3. Interrupt handler also obtains the same lock.

	
Problem: Happens when the interrupt handler runs in the same processor which driver code with lock is running

	Interrupt handler will spin forever, as the non interrupt code will not be able to run to release the lock


Solution:

	Disable interrupts before acquiring the spin lock

	Enable them back after releasing the spin lock.

The kernel provides an interface that conveniently disables interrupts and acquires the lock.

DEFINE_SPINLOCK(my_lock);
unsigned long flags;

spin_lock_irqsave(&my_lock, flags);
/* critical region ... */
spin_unlock_irqrestore(&my_lock, flags);

Why additional argument of flags is needed
============================================

What if the interrupts were disabled before you acquire a spinlock, if we don't have flags, we will enable them after unlocking.

spin_lock_irqsave()saves the current state of interrupts, disables them locally, and then obtains the given lock.

Conversely, spin_unlock_irqrestore() unlocks the given lock and returns interrupts to their previous state.


If you always know before the fact that interrupts are initially enabled, there is no need to restore their previous state

DEFINE_SPINLOCK(mr_lock);
spin_lock_irq(&mr_lock);
/* critical section ... */
spin_unlock_irq(&mr_lock);

Use of spin_lock_irq() is not recommended, as it is hard to ensure interrupts are always enabled in any kernel code path

	
