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
	<b> 3.1  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 3.2  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 3.3  </b>
	</summary>
	
</details>

<details>
	<summary>
	<b> 3.4  </b>
	</summary>
	
</details>

## Locks
<details>
	<summary>
	<b> 4.1  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 4.2  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 4.3  </b>
	</summary>
	
</details>

<details>
	<summary>
	<b> 4.4  </b>
	</summary>
	
</details>

<details>
	<summary>
	<b> 4.5  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 4.6  </b>
	</summary>
	
</details>


## Liveness

<details>
	<summary>
	<b> 5.1  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 5.2  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 5.3  </b>
	</summary>
	
</details>

<details>
	<summary>
	<b> 5.4  </b>
	</summary>
	
</details>

<details>
	<summary>
	<b> 5.5  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 5.6  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 5.7  </b>
	</summary>
	
</details>


<details>
	<summary>
	<b> 5.8  </b>
	</summary>
	
</details>

