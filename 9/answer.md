Is the kernel preemption disabled when the spinlock is acquired?
=================================================================

Any time kernel code holds a spinlock, preemption is disabled on the relevant processor

Lock/unlock methods disable/enable kernel preemption
