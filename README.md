# latest_val

A demo project to show how to use library written in Rust from C/C++.

In many cases you need to poll some information periodically. You don't mind the latency of the information, but you also definitely don't want this IO operation to block "the hot loop". In this case, you can use a thread to poll the information and use a lock-free queue to pass the information to the main thread.


1. Call `latest_val`, maybe get a `None`
2. In the background, a thread is polling the information
3. When the information is ready, the thread will put it into a lock-free queue
4. Next time you call `latest_val`, you will get the information


We will need to export this library to C/C++, as a dynamic/static library.



