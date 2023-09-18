Will spin lock exist on uniprocessor machines?
==============================================

When CONFIG_PREEMPT is not set/kernel preemption disabled
===========================================================

spinlocks are defined as empty operations because critical sections cannot be entered by several CPUs at the same time.

When CONFIG_PREEMPT is set
===========================

	spin_lock  = preempt_disable
	spin_unlock = preempt_enable
