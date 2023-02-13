# C++ Concurrent Programming

In a situation where three threads are waiting on a std::condition_variable and notify_one() is invoked, one of the waiting threads will be unblocked. Which thread is unblocked is determined by the implementation, and it is not specified in the standard.

Typically, implementations use some kind of queue to keep track of the waiting threads, and the first thread in the queue will be the one that is unblocked. However, the order in which the threads are added to the queue and the order in which they are unblocked can depend on various factors, such as the scheduling policy of the operating system and the performance characteristics of the hardware.

It's important to note that the other two threads will continue to wait on the condition variable until they are unblocked, either by another call to notify_one() or by a call to notify_all(). The behavior of the waiting threads and the synchronization mechanisms you are using is critical to ensure that the shared data protected by the mutex is in a consistent state and that the threads behave as expected.

# Once notified or once rel_time has passed, the function unblocks and calls lck.lock(), leaving lck in the same state as when the function was called. Then the function returns (notice that this last mutex locking may block again the thread before returning).
