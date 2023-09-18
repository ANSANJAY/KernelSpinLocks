Spin locks are not recursive
===============================

Unlike spin lock implementations in other operating systems and threading libraries, the Linux kernel’s spin locks are not recursive

This means that if you attempt to acquire a lock you already hold, you will spin, waiting for yourself to release the lock.

But because you are busy spinning, you will never release the lock and you will deadlock.
