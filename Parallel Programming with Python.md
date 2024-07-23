## Parallel Computing Hardware
<details>
	<summary>
	<b> 1.1. Sequential vs. Parallel Computing </b>
	</summary>
This chapter introduces the concept of sequential and parallel computing, using the analogy of cooking a salad. Here's a summary of the main points:

| Topic| Summary|
| :---------------- | :------: |
|Sequential Computing       |   Described as a single cook making a salad, this is a traditional method of programming where tasks are executed one after another. It's easy to understand but has limitations in terms of speed and efficiency.| 
| Parallel Computing          |   Compared to having multiple cooks preparing the salad together, this method breaks down tasks into independent parts that can be executed simultaneously. This increases the overall throughput of a program and allows for large tasks to be accomplished faster.|
| Challenges in Parallel Computing   |  The challenges include the need for coordination and communication between different "processors" (the cooks), and potential waiting times if one task depends on the completion of another.| 
	
 * Sequential computing is like a single cook preparing a salad, executing tasks one after another.
 * Parallel computing is like multiple cooks preparing the salad together, executing tasks simultaneously.
 * Parallel computing can increase the overall throughput of a program, allowing for larger tasks to be accomplished faster.

The challenges of parallel computing include the need for coordination and communication between tasks, and potential waiting times for dependent tasks.

</details>
<details>
	<summary>
	<b> 1.2. Parallel Computing Architectures </b>
	</summary>

This chapter delves into the different types of parallel computing architectures using Flynn's Taxonomy. Here's a summary of the main points:
| Topic| Summary|
| :---------------- | :------: |
|Flynn's Taxonomy	|This is a system used to classify multiprocessor architectures based on the number of instruction streams and data streams. It distinguishes four classes: SISD, SIMD, MISD, and MIMD.|
|SISD (Single Instruction, Single Data)	|This is the simplest class, representing a sequential computer with a single processor unit. It executes one series of instructions and acts on one data element at a time.|
|SIMD (Single Instruction, Multiple Data)	|This is a type of parallel computer with multiple processing units. All processors execute the same instruction at any given time, but each operates on a different data element. It's suitable for tasks that perform the same operations on a massive set of data elements, like image processing.|
|MISD (Multiple Instruction, Single Data)	|In this architecture, each processing unit executes its own series of instructions, but all operate on the same single stream of data. It's not commonly used because it doesn't make much practical sense.|
|MIMD (Multiple Instruction, Multiple Data)	|In this architecture, every processing unit can be executing a different series of instructions, and each can be operating on a different set of data. It's the most commonly used architecture in Flynn's Taxonomy.|

The chapter also introduces two parallel programming models, SPMD (Single Program, Multiple Data) and MPMD (Multiple Program, Multiple Data), which are subdivisions of the MIMD architecture.

Key Takeaways:
* Flynn's Taxonomy classifies parallel computer architectures into SISD, SIMD, MISD, and MIMD.
* SISD is the simplest form of computing, while SIMD and MIMD are forms of parallel computing. MISD is not commonly used.
* SPMD and MPMD are subdivisions of the MIMD architecture and represent different parallel programming models.

From my end:
* The examples used in the chapter are interesting and help to illustrate the concepts. For instance, the SISD architecture is compared to chopping a single carrot, while SIMD is likened to chopping different vegetables (data elements) with the same instruction. MIMD is represented by performing different instructions on different vegetables.
* The mention of image processing as a suitable application for SIMD architecture is important as it gives a practical context for these concepts.
The distinction between SPMD and MPMD, and the mention of their use cases, helps to deepen the understanding of parallel programming models.
</details>
<details>
	<summary>
	<b> 1.3 Shared vs. Distributed Memory </b>
	</summary>
	
This chapter explores the two main memory architectures used in parallel computing: shared memory and distributed memory. Here's a summary of the main points:
| Topic| Summary|
| :---------------- | :------: |
|Shared Memory	|In this system, all processors have access to the same memory as part of a global address space. If one processor changes a memory location, all other processors will see that change. It's further divided into Uniform Memory Access (UMA) and Non-Uniform Memory Access (NUMA).|
|UMA (Uniform Memory Access)	|All processors have equal access to the memory. The most common type of UMA is Symmetric Multiprocessing (SMP), where two or more identical processors are connected to a single shared memory.|
|NUMA (Non-Uniform Memory Access)	|This system is often made by physically connecting multiple SMP systems together. Some processors will have quicker access to certain parts of memory than others, hence the access is non-uniform.|
|Distributed Memory	|In this system, each processor has its own local memory with its own address space. All processors are connected through a network. Changes in local memory are not automatically reflected in the memory of other processors.|

Key Takeaways:
* Shared memory systems are easier to program but can face scalability issues.
* Distributed memory systems are more scalable and cost-effective for building large systems, but require explicit definition of how and when data is communicated between nodes.

From my end:
* The chapter provides a good understanding of how memory access and organization can impact parallel computing performance.
* The distinction between UMA and NUMA within shared memory systems is important as it impacts how quickly processors can access memory.
The challenges of maintaining cache coherency in shared memory systems and the need for explicit data communication in distributed memory systems highlight the complexity of parallel programming.

</details>

## Thread and Processes
<details>
	<summary>
	<b> 2.1 Thread vs. Process </b>
	</summary>

This chapter discusses the concepts of processes and threads, which are fundamental to understanding parallel computing. Here's a summary of the main points:
| Topic| Summary|
| :---------------- | :------: |
|Process	|A process is an instance of a program executing. It consists of the program's code, its data, and information about its state. Each process is independent and has its own separate address space and memory.|
|Thread	|A thread is a smaller sub-element within a process and is an independent path of execution through the program. Threads are the basic units that the operating system manages. Threads belonging to the same process share the process's address space, giving them access to the same resources and memory.|
|Inter-Process Communication	|vProcesses exist in their own separate address space, so sharing resources between separate processes is not as easy as sharing between threads in the same process. Inter-process communication mechanisms are needed to share data between processes.|
|Choosing Between Threads and Processes	|The choice depends on the specific task and the environment. If the application is going to be distributed across multiple computers, separate processes may be needed. However, threads are generally more lightweight and require less overhead to create and terminate than processes.|

Key Takeaways:
* A process is an instance of a program executing, while a thread is a smaller sub-element within a process.
* Threads within the same process share the process's address space and memory, allowing for easy resource sharing.
* Inter-process communication mechanisms are required to share data between separate processes.
* Threads are generally more lightweight and require less overhead than processes, making them a preferred choice for many tasks.

From my end:
* The chapter uses the analogy of cooking in a kitchen to explain the concepts of processes and threads, which is quite helpful for understanding these concepts in a practical context.
* The discussion about the challenges of inter-process communication and the comparison between the overheads of threads and processes provide valuable insights into the complexities of parallel programming.

</details>
<details>
	<summary>
	<b> 2.2 Concurrent vs. Parallel Execution </b>
	</summary>

This chapter distinguishes between concurrency and parallelism, two concepts that are often confused. Here's a summary of the main points:
| Topic| Summary|
| :---------------- | :------: |
|Concurrency	|This refers to the ability of a program to be broken into parts that can be executed out of order or partially out of order, without affecting the end result. It's about the structure of a program and the composition of independently executing processes.|
|Parallelism	|This refers to the simultaneous execution of multiple things at once. It requires parallel hardware, like multi-core processors or computer clusters.|
|Concurrent vs. Parallel	|While concurrent programming structures a program to deal with multiple things at once, parallel execution actually carries out multiple things at once. A concurrent program can execute in parallel given the necessary hardware, but it's not inherently parallel.|
|Use Cases for Concurrency and Parallelism	|Concurrent programming is useful for I/O-dependent tasks, like graphical user interfaces, allowing the UI to remain responsive while other operations are executed in separate threads. Parallel processing is useful for computationally-intensive tasks, like large mathematical operations, where parts can be executed simultaneously on separate processors to speed up processing.|

Key Takeaways:
* Concurrency is about structuring a program to handle multiple things at once, while parallelism is about actually doing multiple things at once.
* Concurrent programming enables a program to execute in parallel, given the necessary hardware.
* Concurrent programming is particularly useful for tasks where responsiveness is important, such as user interfaces, while parallel processing is useful for speeding up computationally-intensive tasks.

From my end:
* The chapter uses the analogy of chopping vegetables to explain the concepts of concurrency and parallelism, which helps to visualize these concepts in a practical context.
* The discussion about the different use cases for concurrency and parallelism provides a clear understanding of when to use each approach.
* The emphasis on the need for parallel hardware for parallel execution is important as it highlights the dependency of parallelism on the underlying hardware.

</details>
<details>
	<summary>
	<b> 2.3 Global Interpreter Lock: Python demo </b>
	</summary>

This chapter provides an overview of the Global Interpreter Lock (GIL), a unique feature in Python that affects how threads execute in the language.
| Topic| Summary|
| :---------------- | :------: |
|Global Interpreter Lock (GIL)	|GIL is a mechanism in Python that prevents multiple Python threads from executing simultaneously. It ensures thread-safe memory management in CPython by allowing only one Python thread to execute at a time.|
|CPython	|The most widely used Python interpreter is CPython, written in a mix of C and Python. Despite proposals to remove the GIL due to its impact on parallel performance, its advantages in most cases outweigh the disadvantages.|
|Alternatives to GIL	|Other Python implementations, like Jython (Java-based), IronPython (.NET-based), and PyPy-STM, do not have the GIL.|
|Multi-threaded Python programs	|Despite the GIL, there's value in writing multi-threaded Python programs, especially for I/O-bound applications. For CPU-bound applications, the GIL can hinder performance, but this can be circumvented using function libraries written in faster languages like C++ or by using Python's multiprocessing package.|
|Python's multiprocessing package	|The multiprocessing package allows the creation of multiple Python processes, each with its own GIL, enabling parallel execution. However, communication between processes is more complicated than between threads, and creating multiple processes uses more system resources.|

Key Takeaways: 
* The Global Interpreter Lock (GIL) is a unique Python feature that prevents multiple threads from executing simultaneously.
* Despite its impact on parallel performance, the GIL remains in CPython due to its advantages in thread-safe memory management.
* For CPU-bound tasks, the GIL's restrictions can be circumvented using function libraries written in faster languages or Python's multiprocessing package.

From my end: 
* The instructor highlights the contentious nature of the GIL in Python, given its impact on parallel performance. However, it's emphasized that the GIL is not a significant bottleneck for I/O-bound tasks.
* The discussion of Python's multiprocessing package as a workaround for the GIL's restrictions provides a practical solution for Python programmers dealing with CPU-intensive tasks.
* The instructor's plan to use Python's threading module for examples in the course, and later switch to the multiprocessing package for CPU-intensive tasks, will provide valuable practical insights into handling concurrent tasks in Python.

</details>
<details>
	<summary>
	<b> 2.4 Multiple threads: Python demo</b>
	</summary>

This chapter covers the topic of Multiple threads: Python demo. Here's a summary of the main points:

| Topic	| Summary |
|------|-------|
| Number of processors	|The computer used in the demonstration has 12 cores and 24 logical processors. Each core supports hyper-threading, which allows them to run two independent applications at the same time.|
|CPU usage	|The CPU usage for all processors is shown in the task manager. The CPU usage for each processor can be seen individually in the resource monitor.|
|Python threads	|A Python program is demonstrated which creates and starts 12 threads. The function 'CPU waster' is defined which has a while loop that will spin forever, continuously using CPU cycles.|
|Global Interpreter Lock (GIL)	 |Python's Global Interpreter Lock (GIL) only allows one thread to execute at any given moment. This means that at most, the program can only utilize one CPU worth of resources.|

Key Takeaways:
	* The computer used in the demonstration has 12 cores and 24 logical processors. Each core supports hyper-threading, which allows them to run two independent applications at the same time.
	* A Python program is demonstrated which creates and starts 12 threads. The function 'CPU waster' is defined which has a while loop that will spin forever, continuously using CPU cycles.
	* Python's Global Interpreter Lock (GIL) only allows one thread to execute at any given moment. This means that at most, the program can only utilize one CPU worth of resources.
	
From my end:
	* The Python threading module is used in the demonstration to create multiple concurrent threads.
	* The task manager and resource monitor are used to monitor the CPU usage of the computer.
	* The Python program demonstrated uses a for loop to start 12 threads and prints out information about the process and threads.
</details>
<details>
	<summary>
	<b> 2.5 Multiple Processes: Python demo </b>
	</summary>


This chapter provides a practical demonstration of using Python's multiprocessing package to create several concurrent processes and investigates their impact on CPU usage.
| Topic| Summary|
| :---------------- | :------: |
|Multiprocessing in Python	|To achieve true parallel execution in Python, one must use multiple processes instead of multiple threads. Python's multiprocessing package makes this straightforward, providing an API for spawning additional processes that is similar to the threading module.|
|Converting Threads to Processes	|To convert a program from using multiple threads to multiple processes, the threading module's Thread class is replaced with the multiprocessing package's Process class. It's also important to enclose the main body of the program in an if statement to check if the special __name__ variable is equal to __main__.|
|CPU Usage with Processes	|After running the program, overall CPU usage rises significantly, as the additional processes created are all executing in parallel.|
|Process Execution	|When a new process is created, it does not directly execute the assigned function. It needs to run through the entire script first to find the function and become aware of any other dependencies.|

Key Takeaways: 
* Python's multiprocessing package allows for the creation of several concurrent processes.
* Converting a program from using multiple threads to multiple processes requires a few changes, including using the Process class from the multiprocessing package and enclosing the main body of the program in an if statement.
* The multiprocessing package allows Python programs to utilize multiple CPUs worth of resources, enabling true parallel execution.

From my end: 
* The demonstration provides a practical look at how Python's multiprocessing module operates and its impact on CPU usage.
* The instructor's explanation of how a new process executes a function provides valuable insight into Python's multiprocessing workings.
* The importance of enclosing the main body of the program in an if statement when using multiprocessing is emphasized, as it prevents processes from uncontrollably spawning more processes.

</details>
<details>
	<summary>
	<b> 2.6 Execution Scheduling  </b>
	</summary>


This chapter covers the topic of execution scheduling in operating systems.
| Topic| Summary|
| :---------------- | :------: |
|Execution Scheduling	|Execution scheduling is the process by which the operating system decides when different threads and processes get their turn to execute on the CPU. This enables multiple programs to run concurrently on a single processor.|
|Ready Queue	|When a process is ready to run, it gets loaded into memory and placed in the ready queue. The operating system cycles through these processes, giving each a chance to execute on the processor.|
|Context Switch	|A context switch occurs when the operating system decides to swap out a currently running process for another one from the ready queue. This involves saving the state of the current process and loading the context of the new process.|
|Scheduler Algorithms	|Schedulers use different algorithms to decide how to assign processor time. Some are preemptive, pausing lower-priority tasks when a higher-priority task is ready. Others allow a process to run for its allotted time. The choice of algorithm depends on the goals of the scheduler, such as maximizing throughput or minimizing latency.|

Key Takeaways:
* The operating system's scheduler controls the execution of threads and processes on the CPU, allowing for concurrent running of multiple programs on a single processor.
* A context switch, which involves saving and loading the state of processes, is a key aspect of execution scheduling.
* The choice of scheduling algorithm depends on the goals of the operating system and can greatly influence system performance.

From my end:
* It's important to note that while understanding scheduling is crucial, developers often don't have control over when parts of their program actually execute. This is handled by the operating system.
* Additionally, it's advisable not to run programs expecting that multiple threads or processes will execute in a certain order, or for an equal amount of time, as the operating system may schedule them differently from run to run.
* The analogy of the scheduler as a head chef in a kitchen, deciding when cooks (processes) get to use the cutting board (processor), can be a helpful way to understand the concept.

</details>
<details>
	<summary>
	<b> 2.7 Execution Scheduling: Python Demo   </b>
	</summary>

This chapter covers the topic of execution scheduling using a Python program as a demonstration. Here's a summary of the main points:
| Topic| Summary|
| :---------------- | :------: |
|Python Program	|A Python program is used to demonstrate scheduling. The program creates two threads named 'Barron' and 'Olivia' that chop vegetables for about one second. The 'vegetable_chopper' function retrieves the name of the current thread and counts the number of vegetables this thread chops.|
|Thread Execution	|The threads 'Barron' and 'Olivia' are started one after the other. The program sleeps for one second before stopping the threads. The threads chop a varying number of vegetables, demonstrating that scheduling is not always fair.|
|Scheduling Variance	|The output shows that even though the threads started and stopped at roughly the same time, they chopped very different numbers of vegetables. Repeated runs of the program yield different results, illustrating that scheduling is not consistent from run to run.|

Key Takeaways: 
* The Python program demonstrates that scheduling can impact execution.
* The threads, although started and stopped at roughly the same time, perform a varying number of operations, indicating that scheduling is not always fair.
* Scheduling is not consistent from run to run, so programs should not rely on it being the same every time.

From my end: 
* This Python demonstration is a practical example of how scheduling works in an operating system. It shows the unpredictable nature of thread execution due to the operating system's scheduling.
* It's crucial for developers to be aware that they cannot rely on scheduling being consistent from run to run. This is an important consideration when developing multi-threaded applications.
* The variance in the number of vegetables chopped by 'Barron' and 'Olivia' in different runs of the program is a clear indication of how the operating system's scheduler can impact the execution of threads.

</details>

<details>
	<summary>
	<b> 2.8 Thread Lifecycle  </b>
	</summary>

This chapter covers the topic of Thread lifecycle. Here's a summary of the main points:

| Topic	| Summary |
|------|-------|
| Main Thread	|The main thread is the primary thread that runs when a program begins. It can spawn additional threads, referred to as child threads, which execute independently to perform other tasks.|
|Thread States	|Over the lifecycle of a thread, it usually goes through four states: new, runnable, blocked, and terminated.|
|New State	|When a thread is created, it begins in the new state. It doesn't run yet and doesn't take any CPU resources.|
|Runnable State	|Once the thread is started, it enters the runnable state. The operating system can schedule it to execute.|
|Blocked State	|When a thread needs to wait for an event to occur, it goes into a blocked state. It doesn't use any CPU resources in this state.|
|Terminated State	|A thread enters the terminated state when it either completes its execution or is abnormally aborted.|

Key Takeaways:
• The main thread can spawn additional threads to perform other tasks.
• Threads usually go through four states: new, runnable, blocked, and terminated.
• A thread doesn't use any CPU resources when it's in the new or blocked state.
• A thread enters the terminated state when it completes its execution or is abnormally aborted.

From my end:
• The concept of thread lifecycle is crucial in understanding how programs execute and manage resources.
• Understanding the different states of a thread can help in optimizing program performance and resource usage.
• The join method can be used to make a thread wait until another thread completes its execution.
</details>
<details>
	<summary>
	<b> 2.9  Thread lifecycle: Python demo </b>
	</summary>

This chapter covers the topic of Thread lifecycle: Python demo. Here's a summary of the main points:

| Topic	| Summary |
|------|-------|
| Thread Creation	|There are two ways to create a thread in Python. One is by putting the code for the thread to execute into a function and passing that function to the thread constructor method as a callable object using the target parameter. The other way is to define a custom subclass that inherits from the thread class and overrides its run method.|
|Thread Initialization	|The init method is used to execute the parent thread class' init method. Python will raise an error if this is not done.|
|Thread Execution	|The run method contains the code to execute when the thread is started. Once the run method is finished, the thread will terminate.|
|Thread Joining	|The join method is used to make a thread wait until another thread has completed its execution.|

Key Takeaways:
	• Threads in Python can be created by defining a custom subclass that inherits from the thread class and overrides its run method.
	• The init method is used to execute the parent thread class' init method.
	• The run method contains the code to execute when the thread is started.
	• The join method is used to make a thread wait until another thread has completed its execution.

From my end:
	• The is_alive method can be used to check if a thread is still running.
	• Even when a thread is sleeping, Python considers it to be alive.
	• After a thread terminates and joins the main method, the is_alive method returns false.

</details>
<details>
	<summary>
	<b> 2.10 Daemon thread </b>
	</summary>
This chapter covers the topic of Daemon thread. Here's a summary of the main points:

| Topic	| Summary |
|------|-------|
| Daemon Thread | A daemon thread is a thread that will not prevent the program from exiting if it's still running. It is often used to perform background tasks like garbage collection. |
| Normal Thread | Normal threads are non-daemon threads. The program will not exit until all normal threads have terminated. |
| Thread Termination | When a process terminates, all its daemon threads are terminated abruptly. This is fine for tasks like garbage collection, but for tasks like IO operations, it could lead to data corruption. |

Key Takeaways:
• Daemon threads are used for background tasks and do not prevent the program from exiting.
• Normal threads must all terminate before the program can exit.
• Abrupt termination of daemon threads can lead to data corruption if they are performing tasks like IO operations.

From my end:
• It's important to carefully consider the potential consequences of abruptly terminating a daemon thread before deciding to use one for a particular task.
• Daemon threads can be very useful for tasks that need to run in the background, but they should be used with caution.
</details>
<details>
	<summary>
	<b> 2.11 Daemon thread: Python demo </b>
	</summary>

This chapter covers the topic of Daemon thread in Python. Here's a summary of the main points:

The instructor demonstrates the use of a daemon thread in Python by defining a function called 'kitchen cleaner'. This function represents a periodic background task like garbage collection. The function uses an infinite while loop to continuously print a message. In the main section of the program, a new kitchen cleaner thread named 'Olivia' is created and started. The main thread then prints a series of messages. However, when the main thread finishes executing, the program doesn't exit because the kitchen cleaner thread is still running. To prevent this, the instructor sets 'Olivia' to be a daemon thread before it gets started. When the main thread is done executing, Olivia's thread is also terminated so the process can exit.

| Topic	| Summary |
|------|-------|
| Daemon Thread	|A daemon thread is a background thread that runs regardless of the main thread. It is used for tasks that need to run continuously in the background.|
|Creating a Daemon Thread	|In Python, a daemon thread can be created by setting the 'daemon' property of a thread object to 'True'. This must be done before the thread is started.|
|Daemon Thread Inheritance	|When a new thread is created, it inherits the daemon status from its parent. The main thread is a non-daemon thread, so by default, any threads that it creates will be non-daemon threads.|
|Daemon Thread Termination	|Daemon threads do not exit gracefully like normal threads. When all of the non-daemon threads in a program are done executing, any remaining daemon threads will be abandoned as Python exits.|

Key Takeaways:
	• Daemon threads are used for background tasks that need to run continuously.
	• A daemon thread can be created by setting the 'daemon' property of a thread object to 'True'.
	• Daemon threads do not exit gracefully like normal threads. They are abandoned when all non-daemon threads are done executing.

From my end:
	• Daemon threads are useful in scenarios where you want a background task to run continuously until the main program is running.
	• It's important to set the 'daemon' property before starting the thread, otherwise Python will raise a runtime error.
	• Daemon threads can lead to abrupt termination of tasks as they do not exit gracefully. Hence, they should be used judiciously.
</details>

## Mutual Exclusion 

<details>
	<summary>
	<b> 3.1 Data Race </b>
	</summary>

This chapter covers the topic of Data Race. Here's a summary of the main points:

Data races are a common problem in concurrent programming, occurring when two or more threads concurrently access the same location in memory and at least one of those threads modifies its value. This can lead to inconsistencies and bugs that are hard to debug due to the unpredictability of thread scheduling. Synchronization techniques can be used to protect against data races.

| Topic	| Summary |
|------|-------|
| Data Race	|A data race occurs when two or more threads concurrently access the same location in memory and at least one of those threads modifies its value.|
|Thread Scheduling	|The unpredictability of when threads get scheduled can sometimes cause data races, leading to inconsistencies and bugs.|
|Synchronization Techniques	| Techniques that can be used to protect against data races, ensuring that threads do not interfere with each other.|

Key Takeaways:
• Data races are a common problem in concurrent programming.
• The unpredictability of thread scheduling can sometimes cause data races.
• Synchronization techniques can be used to protect against data races.

From my end:
• Understanding the concept of data races is crucial for writing efficient concurrent programs.
• Debugging data races can be challenging due to their unpredictable nature.
• Proper use of synchronization techniques can help in avoiding data races.
 
</details>

<details>
	<summary>
	<b> 3.2  Data race: Python demo </b>
	</summary>

This chapter covers the topic of Data race: Python demo. Here's a summary of the main points:

The instructor demonstrates a data race in a simple Python program that uses two threads to concurrently increment a shared variable. The variable is a counter for the amount of garlic to buy, initialized to zero. The shopper function represents a shopper adding garlic to the shopping list. It uses a for loop to increment the global count variable. Two shopper threads are created, started, and then the join method is used to wait until they're both done. Finally, the value of the garlic count variable is printed out. 

| Topic	| Summary |
|------|-------|
| Data Race	|A data race occurs when two or more threads in a process access the same memory location concurrently, and at least one of the accesses is for writing, and the threads are not using any exclusive locks to control their accesses to that memory.|
|Python Demo	|The instructor demonstrates a data race in a simple Python program that uses two threads to concurrently increment a shared variable. The variable is a counter for the amount of garlic to buy, initialized to zero. The shopper function represents a shopper adding garlic to the shopping list. It uses a for loop to increment the global count variable. Two shopper threads are created, started, and then the join method is used to wait until they're both done. Finally, the value of the garlic count variable is printed out. |
|Preventing Data Race	|The best defense against data races is a good offense, preventing them from occurring in the first place. Since a data race only occurs when at least one of the concurrent threads is modifying the value of a memory location, pay close attention to anywhere you use an assignment operation, or an operator like the plus equal incrementor that changes a variable's value. If there's a potential for two or more threads to access that variable and make changes to it, then you'll almost certainly need to use some sort of mechanism to protect it.|

Key Takeaways:
• Data races occur when two or more threads in a process access the same memory location concurrently, and at least one of the accesses is for writing, and the threads are not using any exclusive locks to control their accesses to that memory.
• In Python, data races can be demonstrated with a simple program that uses two threads to concurrently increment a shared variable.
• The best way to prevent data races is to pay close attention to anywhere you use an assignment operation, or an operator like the plus equal incrementor that changes a variable's value. If there's a potential for two or more threads to access that variable and make changes to it, then you'll almost certainly need to use some sort of mechanism to protect it.

From my end:
• Data races can be difficult to detect and fix, and can cause unexpected and incorrect results in your program.
• There are tools that exist to help detect data races, but they are specific to different languages and environments.
• It's important to understand the concept of data races and how to prevent them to ensure the accuracy and reliability of your multi-threaded programs.	
</details>


<details>
	<summary>
	<b> 3.3 Mutual Exclusion </b>
	</summary>


This chapter covers the topic of Mutual exclusion. Here's a summary of the main points:

Mutual exclusion, also known as a mutex or lock, is a mechanism used to prevent multiple threads from simultaneously accessing a shared resource, forcing them to take turns. This is particularly important when multiple threads are concurrently reading and writing a shared resource, as it can lead to incorrect behavior such as data erasure. A critical section of code that accesses a shared resource needs to be protected so that it only allows one thread or process to execute in it at a time. The operation to acquire the lock is an atomic operation, meaning it's always executed as a single, indivisible action.

| Topic	| Summary |
|------|-------|
| Critical Section	|A critical section or critical region is part of a program that accesses a shared resource, such as a data structured memory or an external device, and it may not operate correctly if multiple threads concurrently access it.|
|Mutex	|A mutex, short for mutual exclusion, also referred to as a lock, is a mechanism that only allows one thread or process to have possession of the lock at a time. It is used to prevent multiple threads from simultaneously accessing a shared resource, forcing them to take turns.|
|Atomic Operation	|The operation to acquire the lock is an atomic operation, which means it's always executed as a single, indivisible action. To the rest of the system, an atomic operation appears to happen instantaneously, even if under the hood it really takes multiple steps.|

Key Takeaways:
• Mutex is a mechanism used to prevent multiple threads from simultaneously accessing a shared resource.
• The operation to acquire the lock is an atomic operation, meaning it's always executed as a single, indivisible action.
• It's important to keep the section of code protected with the mutex as short as possible to avoid blocking other threads.

From my end:
• Mutex is a crucial concept in concurrent programming to avoid data inconsistency and race conditions.
• Atomic operations are key to ensuring that critical sections of code are executed without interruption.
• Proper use of mutex can significantly improve the efficiency and correctness of multi-threaded programs.	
</details>

<details>
	<summary>
	<b> 3.4 Mutual Exclusion: Python Demo </b>
	</summary>

This chapter covers the topic of Mutual exclusion with a Python demo. Here's a summary of the main points:

The chapter demonstrates how to manually enforce mutual exclusion with locks in Python. It modifies an example program with two shoppers that have a data race as they increment the amount of garlic to buy. The solution involves creating a lock object using the constructor method from Python's threading module. The lock object is acquired before entering the for loop and released immediately after the for loop has finished. This prevents the data race and gives the expected output. The chapter also discusses the scenario where there is a longer I/O operation involved and how to optimize the program by minimizing the critical section to only protect the part of the program that truly requires mutual exclusion.

| Topic	| Summary |
|------|-------|
| Mutual Exclusion	|The concept of ensuring that only one thread can execute a particular section of code at a time.|
|Python's threading module	|Used to create a new lock object to enforce mutual exclusion.|
|Lock object	|Used to prevent multiple threads from modifying a shared variable at the same time.|
|Critical section	|The part of the program that requires mutual exclusion. It should be minimized to improve program efficiency.|

Key Takeaways:
• Mutual exclusion can be enforced in Python using locks from the threading module.
• The lock object is acquired before entering the critical section and released immediately after exiting it.
• Minimizing the critical section can improve the efficiency of the program.

From my end:
• The lock object acts as a gatekeeper, ensuring that only one thread can execute the critical section at a time.
• It's important to release the lock after the critical section to avoid deadlocks.
• The critical section should only include the code that modifies the shared data, not the code that performs other operations.	
</details>

## Locks
<details>
	<summary>
	<b> 4.1  Reentrant Lock </b>
	</summary>

This chapter covers the topic of Reentrant lock. Here's a summary of the main points:

A reentrant lock is a type of mutex that can be locked multiple times by the same process or thread. It keeps track of how many times it's been locked by the owning thread and has to be unlocked an equal number of times before another thread can lock it. This can prevent deadlocks, where a thread tries to lock a mutex that it's already locked, causing it to enter into a waiting list for that mutex, and no other thread can unlock that mutex.

| Topic	| Summary |
|------|-------|
| Mutex	|A mutex is a program object that allows multiple program threads to share the same resource, such as file access, but not simultaneously.|
|Reentrant Mutex	|A reentrant mutex is a particular type of mutex that can be locked multiple times by the same process or thread. Internally, the reentrant mutex keeps track of how many times it's been locked by the owning thread, and it has to be unlocked an equal number of times before another thread can lock it.|
|Deadlock	| If a thread tries to lock a mutex that it's already locked, it'll enter into a waiting list for that mutex, which results in something called a deadlock, because no other thread can unlock that mutex.|
|Recursive Function	| One use case where reentrant locks are really needed is when writing a recursive function. That is a function that calls itself. If the function makes a recursive call to itself from within a locked section, it will lock the mutex multiple times as it repeats itself, and then unlock the mutex an equal number of times as it returns and unwinds.|

Key Takeaways:
• A reentrant lock is a type of mutex that can be locked multiple times by the same process or thread.
• A reentrant lock can prevent deadlocks, which occur when a thread tries to lock a mutex that it's already locked.
• Reentrant locks are particularly useful when writing recursive functions, as the function will lock the mutex multiple times as it repeats itself, and then unlock the mutex an equal number of times as it returns and unwinds.

From my end:
• Reentrant locks can make things easier as you don't need to worry as much about what's already been locked, and they make it easier to retrofit locks into existing code.
• However, if you don't unlock the reentrant mutex the same number of times, you can still end up stuck.
• Different languages use different terms for reentrant locks, but these all basically mean the same thing. They are also often referred to as a recursive mutex or a recursive lock.	
</details>

<details>
	<summary>
	<b> 4.2 Rlock: Python demo </b>
	</summary>

This chapter covers the topic of Rlock: Python demo. Here's a summary of the main points:

The instructor demonstrates the use of a reentrant lock in Python using an example of two shoppers concurrently incrementing the amount of items to buy. The example uses two helper functions, add_garlic and add_potato, which increment the corresponding garlic_count or potato_count variables. These functions acquire and release the same lock object, named pencil, to enforce mutual exclusion and prevent a data race. The shopper function uses a for loop to execute these functions multiple times. The program then prints out the amount of garlic and potatoes to buy. 

| Topic	| Summary |
|------|-------|
| Reentrant Lock	|A reentrant lock in Python can be acquired multiple times before being released. This is demonstrated by nesting two calls to the pencil's acquire method.|
|Regular Lock vs Rlock	|The regular lock can be released by different threads than the one that acquired it, but the reentrant lock must be released by the same thread that acquired it. The reentrant lock must also be released as many times as it was acquired before it will be available for another thread to take.|

Key Takeaways:
• Reentrant locks in Python can be acquired multiple times before being released.
• Regular locks can be released by different threads than the one that acquired it, but the reentrant lock must be released by the same thread that acquired it.
• The reentrant lock must also be released as many times as it was acquired before it will be available for another thread to take.

From my end:
• It's important to understand the difference between regular locks and reentrant locks in Python to prevent potential issues in your program.
• Trying to split lock operations across multiple threads is generally a bad idea and can lead to problems.
• If a thread tries to release a lock that has not already been acquired, Python will raise an error and can crash your program.

Rlock: Python demo
This chapter covers the topic of Rlock: Python demo. Here's a summary of the main points:

The chapter demonstrates the use of a reentrant lock in Python using an example of two shoppers concurrently incrementing the amount of items to buy. The example uses two helper functions to increment the corresponding garlic_count or potato_count variables. These functions acquire and release the same lock object, named pencil, to enforce mutual exclusion around those operations and prevent a data race. The chapter also explains the difference between the regular lock and Rlock in Python.

| Topic	| Summary |
|------|-------|
| Reentrant lock in Python	|A reentrant lock in Python can be acquired multiple times before being released. This is demonstrated using an example where two shoppers are concurrently incrementing the amount of items to buy.|
|Regular lock vs Rlock	|The regular lock can be released by different threads than the one that acquired it, but the reentrant lock must be released by the same thread that acquired it. And of course, it must be released by that thread as many times as it was acquired before it will be available for another thread to take.|

Key Takeaways:
• Reentrant lock in Python can be acquired multiple times before being released.
• Regular lock can be released by different threads than the one that acquired it, but the reentrant lock must be released by the same thread that acquired it.
• Trying to split lock operations across multiple threads is generally a bad idea, and a surefire way to create problems.

From my end:
• The use of reentrant lock in Python is a good way to prevent data races in concurrent programming.
• It's important to understand the difference between regular lock and Rlock in Python to avoid potential issues in your program.
• Always ensure that a lock is released by the same thread that acquired it when using a reentrant lock.

</details>


<details>
	<summary>
	<b> 4.3 Try Lock </b>
	</summary>

This chapter covers the topic of Try lock. Here's a summary of the main points:

Try lock is a non-blocking version of the lock or acquire method used in multi-threading. It allows a thread to attempt to acquire a lock, and if the lock is already taken, the thread can continue with other tasks without being blocked. This method returns immediately with a boolean value indicating whether the lock was successfully acquired or not.

| Topic	| Summary |
|------|-------|
| Try Lock	|Try lock is a non-blocking version of the lock or acquire method. It allows a thread to attempt to acquire a lock, and if the lock is already taken, the thread can continue with other tasks without being blocked.|
|Use Case	|In a scenario where multiple threads have multiple tasks to perform, using try lock can be more efficient as it allows a thread to continue with other tasks if the lock is already taken.|

Key Takeaways:
• Try lock is a non-blocking version of the lock or acquire method.
• It allows a thread to attempt to acquire a lock, and if the lock is already taken, the thread can continue with other tasks without being blocked.
• The method returns immediately with a boolean value indicating whether the lock was successfully acquired or not.

From my end:
• Try lock can be particularly useful in scenarios where threads have multiple tasks and waiting for a lock to be released can lead to inefficiencies.
• It's important to handle the boolean return value of the try lock method appropriately in the code to ensure correct program execution.	
</details>

<details>
	<summary>
	<b> 4.4  Non-blocking acquire: Python demo </b>
	</summary>

This chapter covers the topic of Non-blocking acquire in Python. Here's a summary of the main points:

The chapter demonstrates how to implement the common try mock operation in Python by configuring the acquire method to be non-blocking. It uses an example of two shoppers searching for items and adding them to a shared notepad. The acquire method is used to lock and unlock the notepad, ensuring that only one shopper can add items at a time. The non-blocking acquire method allows the program to execute much faster, as one thread can continue to search for items while the other is writing to the notepad.

| Topic	| Summary |
|------|-------|
| Non-blocking acquire	|In Python, the common try mock operation can be implemented by configuring the acquire method to be non-blocking. This allows the program to execute much faster, as one thread can continue to search for items while the other is writing to the notepad.|
|Blocking acquire	|The default acquire method blocks execution, causing the two threads to take turns. This results in a slower execution time.|
|Python Threads	|Python threads are used to simulate the shoppers. The time taken from when the threads start until they finish is recorded to see how long it takes for them to find at least 20 items.|

Key Takeaways:
	• The non-blocking acquire method in Python allows for faster execution of programs by allowing one thread to continue executing while another is blocked.
	• The order of statements on each side of the 'and' operator matters in Python, as Python evaluates the statement from left to right.
	• The non-blocking acquire method immediately returns a Boolean value to indicate whether or not the lock was successfully acquired.

From my end:
	• The non-blocking acquire method can be particularly useful in multi-threaded programs where one thread may be waiting for a resource that is locked by another thread.
	• The use of sleep function in Python threads is to simulate the time spent on certain operations, such as writing to the notepad or searching for items.
	• The acquire method in Python is used to handle synchronization issues in multi-threaded programs.	
</details>

<details>
	<summary>
	<b> 4.5 Read-write lock </b>
	</summary>


This chapter covers the topic of Read-write lock. Here's a summary of the main points:

A read-write lock, also known as a shared mutex, is a type of lock that allows multiple threads to read a shared resource simultaneously but restricts write access to only one thread at a time. This type of lock is useful in scenarios where there are more threads reading from the shared data than writing to it, such as certain types of database applications. However, implementing a read-write lock is more complex than a standard mutex and typically uses more resources to keep track of the number of readers.

| Topic	| Summary |
|------|-------|
| Read-write lock	| A read-write lock or shared mutex allows multiple threads to read a shared resource simultaneously but restricts write access to only one thread at a time.|
|Advantages of Read-write lock	|Read-write locks can improve a program's performance versus using a standard mutex, especially when there are more threads reading from the shared data than writing to it.|
|Disadvantages of Read-write lock	| Read-write locks are more complex to implement than standard mutexes and typically use more resources to keep track of the number of readers.|
|Choosing the right lock	 | Deciding which type of mutex to use is a complicated decision. As a general rule of thumb, it makes sense to use a shared reader-writer lock when you have a lot more threads that will be reading from the shared data than the number of threads that will be writing to it.|

Key Takeaways:
• A read-write lock allows multiple threads to read a shared resource simultaneously but restricts write access to only one thread at a time.
• Read-write locks can improve a program's performance when there are more threads reading from the shared data than writing to it.
• Implementing a read-write lock is more complex than a standard mutex and typically uses more resources.

From my end:
• Read-write locks are particularly useful in database applications where read operations are more frequent than write operations.
• The choice between a standard mutex and a read-write lock depends on the specific requirements of your application and the nature of the threads involved.
• It's important to understand the language-dependent differences in how read-write locks are implemented as they can affect performance.	
</details>


<details>
	<summary>
	<b> 4.6 Read-write lock: Python demo </b>
	</summary>

This chapter covers the topic of Read-write lock: Python demo. Here's a summary of the main points:

The chapter explains the concept of reader-writer locks, which are a common feature in many programming languages that support concurrency. However, they're not included by default in Python. The chapter demonstrates how to install a reader-writer lock package for Python and how to use it in a Python program. The program creates 10 threads to concurrently read what day it is from a shared calendar while two other threads update it. The chapter also explains how to upgrade a program from using a basic lock to a reader-writer lock.

| Topic	| Summary |
|------|-------|
| Reader-writer locks	|Reader-writer locks are a common feature in many programming languages that support concurrency. They are not included by default in Python, but can be installed using a package from the Python package index.|
|Python program using reader-writer locks	|The chapter demonstrates a Python program that uses reader-writer locks. The program creates 10 threads to concurrently read what day it is from a shared calendar while two other threads update it.|
|Upgrading from basic lock to reader-writer lock	| The chapter explains how to upgrade a program from using a basic lock to a reader-writer lock. This involves importing the reader-writer lock package and changing the lock constructor to use the RW lock package instead of the threading module.|

Key Takeaways:
	• Reader-writer locks are a common feature in many programming languages that support concurrency, but they're not included by default in Python.
	• A Python program can use reader-writer locks to allow multiple threads to read a shared resource while only one thread can write to it at a time.
	• Upgrading a program from using a basic lock to a reader-writer lock involves importing the reader-writer lock package and changing the lock constructor to use the RW lock package instead of the threading module.
	
From my end:
	• The reader-writer lock package can be installed using the Python package manager with the console command pip install reader writer lock.
	• The RW lock object has two methods. Gen r lock generates one lock for reading which can be held by multiple threads at once and gen w lock which generates another lock object for writers which can only be held by a single thread at once.
	• The reader-writer lock doesn't make the information about the number of threads that are currently holding the counter easily accessible but it can be pulled by using read underscore marker dot c underscore rw underscore lock dot v underscore read underscore count.	
</details>


## Liveness

<details>
	<summary>
	<b> 5.1 Deadlock and Dining Philosophers Problem </b>
	</summary>


This chapter covers the topic of Deadlock and the Dining Philosophers Problem. Here's a summary of the main points:

The deadlock is a situation in concurrent programming where each member of a group is waiting for some other member to take action, and as a result, neither member is able to make progress. The Dining Philosophers Problem is a classic example used to illustrate synchronization issues when multiple threads are competing for multiple locks.

| Topic	| Summary |
|------|-------|
| Deadlock	|A situation in concurrent programming where each member of a group is waiting for some other member to take action, and as a result, neither member is able to make progress.|
|Dining Philosophers Problem	|A classic example used to illustrate synchronization issues when multiple threads are competing for multiple locks.|
|Liveness	| A set of properties that require concurrent programs to make progress. Some processes or threads may have to take turns in a critical section but a well-written program with liveness guarantees that all processes will eventually make progress.|
|Solution to Deadlock	 | Prioritizing locks so that all threads try to acquire the same first lock can help avoid deadlock.|

Key Takeaways:
• Deadlock is a common challenge in concurrent programs that use mutual exclusion mechanisms to protect critical sections of code.
• The Dining Philosophers Problem is a classic example used to illustrate synchronization issues when multiple threads are competing for multiple locks.
• Liveness is a set of properties that require concurrent programs to make progress.
• Prioritizing locks so that all threads try to acquire the same first lock can help avoid deadlock.

From my end:
• Deadlock can also occur in a banking application where each account has its own mutex to ensure that only one thread will be withdrawing from or depositing funds to that account at a time.
• To transfer funds between two accounts, a thread needs to acquire the locks for both the sender and the receiver since it would be modifying the value of both accounts. If there are multiple threads concurrently making transfers between the accounts then there's a real chance that they could end up competing for the same locks and run into a deadlock scenario.
• The solution to avoid deadlock in such a scenario would be to prioritize the locks in a certain order.	
</details>


<details>
	<summary>
	<b> 5.2 Deadlock: Python demo </b>
	</summary>

This chapter covers the topic of Deadlock: Python demo. Here's a summary of the main points:

The chapter demonstrates a deadlock with a dining philosophers problem and how to resolve it. The deadlock is created by having three philosophers, each competing for two of the three chopsticks placed around the table. A Python program is used to instantiate three lock objects and a variable named sushi count to represent the amount of sushi left between the philosophers. A function is used to represent the philosophers who think and eat sushi. The function has three input parameters: the philosopher's name and two locks, named first chopstick and second chopstick to indicate the order in which the philosopher will acquire them. The deadlock is resolved by ensuring that locks are always taken in the same order by every thread.

| Topic	| Summary |
|------|-------|
| Deadlock	|A deadlock is a situation where two or more tasks are unable to proceed because each is waiting for the other to release a resource.|
|Dining Philosophers Problem	|This is a classic problem used in concurrent algorithm design to illustrate synchronization issues and techniques for resolving them.|
|Locks	| In Python, a primitive lock is a synchronization primitive that is not owned by a particular thread when locked. In Python, it is currently the lowest level synchronization primitive available.|
|Resolving Deadlock	 |The deadlock in the given scenario is resolved by ensuring that locks are always taken in the same order by every thread.|

Key Takeaways:
	• Deadlocks are tricky to detect and debug. Just like a race condition, you might get lucky and never experience a problem with your program, even if the potential for a deadlock exists.
	• The simplest technique to prevent deadlocks is to ensure that locks are always taken in the same order by every thread.
	• Another technique for preventing deadlocks is to put a timeout on lock attempts. If a thread is not able to successfully acquire all of the locks it needs within a certain amount of time, it will back up, free all of the locks that it did take and then wait for a random amount of time before trying again to give other threads a chance to take the locks they need.
	
From my end:
	• Deadlocks can occur in a system if a process holds a resource and requests another resource held by another process, then both processes will wait indefinitely causing a deadlock.
	• Deadlocks can be prevented by avoiding the four Coffman conditions for deadlock: mutual exclusion, hold and wait, no preemption, and circular wait.
	• In Python, the threading module provides a Lock class to deal with the thread synchronization. This class provides a mechanism to the threads to change their behavior based on the status of the locks.
</details>


<details>
	<summary>
	<b> 5.3  Abandoned Lock </b>
	</summary>

This chapter covers the topic of Abandoned lock. Here's a summary of the main points:

The chapter discusses the concept of an abandoned lock in multithreading. An abandoned lock occurs when a thread acquires a lock and then terminates unexpectedly without releasing the lock. This leaves other threads waiting indefinitely for a lock that will never be released.

| Topic	| Summary |
|------|-------|
| Abandoned Lock | An abandoned lock is a situation where a thread acquires a lock and then terminates unexpectedly without releasing the lock. This can cause other threads to wait indefinitely for the lock to be released.|

Key Takeaways:
• Abandoned locks can cause deadlocks in a multithreading environment.
• It is important to ensure that locks are properly managed and released to avoid such situations.
• Unexpected termination of a thread can lead to an abandoned lock.

From my end:
• It's crucial to handle exceptions in a way that ensures locks are released even when unexpected terminations occur.
• Using constructs like 'finally' in Java or 'with' in Python can help ensure that locks are always released, even in case of unexpected terminations.
• Abandoned locks are a common source of bugs in multithreaded applications and understanding them can help in debugging such issues.	
</details>

<details>
	<summary>
	<b> 5.4 Abandoned lock: Python demo </b>
	</summary>


This chapter covers the topic of Abandoned lock: Python demo. Here's a summary of the main points:

The chapter demonstrates what happens if a lock gets abandoned in Python, using the dining philosophers example. The critical section for this program exists between the acquire methods and the release methods. If a thread acquires the locks and then something goes wrong in that critical section to cause an unexpected error, that could kill its thread before it gets a chance to release the lock. To prevent this type of situation from occurring, we should put the critical section within a try block. Python makes it easy to ensure locks will be released, if something goes wrong and unexpectedly crashes a thread, because lock objects support working with context managers. 

| Topic	| Summary |
|------|-------|
| Abandoned Lock	|An abandoned lock occurs when a thread acquires a lock and then something goes wrong in the critical section causing an unexpected error, killing the thread before it gets a chance to release the lock.|
|Try Block	|To prevent an abandoned lock, the critical section should be put within a try block. If any exception handling code is present, an except clause can be included after the try block to catch and deal with the error.|
|Finally Block	|A finally block ensures that the locks always get released before the current thread gets terminated if it crashes.|
|Context Managers	|Python lock objects support working with context managers. Using the with statement on a lock is equivalent to using the try and finally blocks. This is a more pythonic way to program.|

Key Takeaways:
• An abandoned lock can cause a program to get stuck, making no progress.
• To prevent an abandoned lock, the critical section should be put within a try block and a finally block should be used to ensure locks get released before the current thread gets terminated if it crashes.
• Python lock objects support working with context managers, providing a more pythonic way to program.

From my end:
• It's good practice to always make sure locks will be released, if something goes wrong and unexpectedly crashes a thread.
• Using a context manager is the more pythonic way to program, so it's recommended to use the with statement on a lock instead of try and finally blocks.
• In the given example, even when an exception occurs, thanks to the finally clause, the thread is able to release the lock before it terminates.	
</details>

<details>
	<summary>
	<b> 5.5 Starvation </b>
	</summary>

This chapter covers the topic of Starvation in the context of operating systems and thread execution. Here's a summary of the main points:

Starvation occurs when a thread is unable to gain access to a necessary resource and is therefore unable to make progress. This can happen due to the operating system's scheduling of thread execution, thread priorities, or having too many concurrent threads.

| Topic	| Summary |
|------|-------|
| Thread Scheduling |The operating system decides when each thread gets scheduled to execute. If a thread doesn't get a chance to acquire necessary resources before another thread takes them again, it can lead to starvation.|
|Thread Priorities |If two threads are given different priorities, the higher priority thread will be scheduled to execute more often, potentially causing the lower priority thread to starve.|
|Concurrent Threads |Having too many concurrent threads can also lead to starvation, as the competition for resources increases.|

Key Takeaways:
• Starvation occurs when a thread is unable to gain access to a necessary resource and is therefore unable to make progress.
• Thread scheduling, thread priorities, and the number of concurrent threads can all contribute to starvation.
• In general, higher priority threads will be scheduled to execute more often, potentially causing lower priority threads to starve.

From my end:
• Starvation can be a significant issue in systems with many threads and limited resources.
• Balancing thread priorities and managing the number of concurrent threads can help mitigate the risk of starvation.
• Understanding how your operating system schedules thread execution can also help in preventing starvation.	
</details>


<details>
	<summary>
	<b> 5.6 Starvation: Python demo </b>
	</summary>

This chapter covers the topic of thread starvation in Python using the dining philosophers example. Here's a summary of the main points:

Main Summary here

| Topic	| Summary |
|------|-------|
| Thread Starvation	|Thread starvation is a problem in programs containing a large number of threads. Some threads may never get a chance to execute, leading to unfair distribution of resources.|
|Dining Philosophers Example	|The dining philosophers problem is a classic example used to illustrate synchronization issues and techniques in an operating system. In this case, it is used to demonstrate thread starvation.|
|Python Code Demonstration	| The instructor modifies the dining philosophers example by adding a local variable within the philosopher function to keep track of how many pieces of sushi each philosopher thread gets to eat. The variable is incremented every time the philosopher takes a piece of sushi. The number of pieces each philosopher took is printed at the end.|
|Fairness Among Threads	| Techniques can be used to improve or even guarantee fairness among threads, but that type of workload management is very situation dependent and beyond the scope of this course.|

Key Takeaways:
• Thread starvation is a problem in programs with a large number of threads where some threads may never get a chance to execute.
• The dining philosophers problem is a classic example used to illustrate synchronization issues and techniques in an operating system.
• In Python, a local variable can be added within a function to keep track of resource distribution among threads.
• Techniques can be used to improve or even guarantee fairness among threads, but that type of workload management is very situation dependent.

From my end:
• Thread starvation can lead to some very impatient and angry users in the case of a web server that created new threads to handle a huge number of incoming requests.
• It's important to manage workload among threads to ensure fairness and efficiency.
• The dining philosophers problem is a great way to understand thread synchronization and potential issues like thread starvation.	
</details>


<details>
	<summary>
	<b> 5.7 Livelock </b>
	</summary>

This chapter covers the topic of Livelock. Here's a summary of the main points:

Livelock is a situation where two or more threads are blocking each other from making progress, but unlike deadlock, the threads in a livelock are actively trying to resolve the problem. This can occur when threads are designed to respond to each other's actions. Despite being busy, the combination of their efforts prevents them from making progress. Livelocks are often caused by algorithms intended to detect and recover from deadlock. To avoid livelocks, ensure that only one process takes action, chosen by priority or some other mechanism.

| Topic	| Summary |
|------|-------|
| Livelock	| A situation where two or more threads are blocking each other from making progress, but unlike deadlock, the threads in a livelock are actively trying to resolve the problem. |
| Cause of Livelock	| Livelocks are often caused by algorithms intended to detect and recover from deadlock. |
| Avoiding Livelock	| To avoid livelocks, ensure that only one process takes action, chosen by priority or some other mechanism. |

Key Takeaways:
• Livelock is a situation where two or more threads are blocking each other from making progress, but unlike deadlock, the threads in a livelock are actively trying to resolve the problem.
• Livelocks are often caused by algorithms intended to detect and recover from deadlock.
• To avoid livelocks, ensure that only one process takes action, chosen by priority or some other mechanism.

From my end:
• Livelock is a common issue in multi-threaded programming and understanding it can help in designing more efficient algorithms.
• The concept of livelock also applies to real-life situations where two or more entities are trying to resolve a conflict but end up in a loop of actions that prevent resolution.
• Understanding the difference between deadlock and livelock is crucial in concurrent programming.	
</details>


<details>
	<summary>
	<b> 5.8 Livelock: Python demo </b>
	</summary>

This chapter covers the topic of Livelock in Python using the dining philosopher's example. Here's a summary of the main points:

Main Summary:
The instructor demonstrates a livelock in Python by modifying the original dining philosopher's example used to demonstrate a deadlock. The deadlock occurs when the philosophers acquire their first chopstick lock and are stuck waiting for their second one to become available. To prevent this, the instructor suggests having the philosophers release the lock on their first chopstick if the second chopstick is not available when they try to take it. This gives another philosopher a chance to take the first chopstick and hopefully prevent a deadlock. However, this leads to a livelock where the philosophers are constantly picking up and putting down chopsticks without making any progress. To resolve this, the instructor introduces randomness into the locking process.

| Topic	| Summary |
|------|-------|
| Deadlock	|Occurs when the philosophers acquire their first chopstick lock and are stuck waiting for their second one to become available.|
|Livelock	|Occurs when the philosophers are constantly picking up and putting down chopsticks without making any progress.|
|Resolving Livelock	| The instructor introduces randomness into the locking process to resolve the livelock.|

Key Takeaways:
• Deadlocks and livelocks can occur in multi-threaded programs.
• Livelocks can be harder to locate and debug than deadlocks.
• Introducing randomness into the locking process can help resolve livelocks.

From my end:
• Livelocks and deadlocks are common issues in concurrent programming and understanding them is crucial for writing efficient multi-threaded programs.
• The dining philosophers problem is a classic example used to illustrate synchronization issues and deadlock and livelock situations in concurrent programming.
• The solution provided in the lecture is specific to the dining philosophers problem and may not be applicable to all livelock situations.	
</details>

