# voting-system-c
voting-system in c  built for my operating system project 

I made voting system for  my operating system semester project in C with 3 different modes; 
Modes:
1. manual mode
2. process mode
3. threads mode
process and threads are synchronized. 
key features: 
1. multi-candidate voting support
   - supports upto 10 candidates (MAX_CANDIDATES)
   - stores and displays candidates name
   - maintains individual vote counts for each candidate
2. unique voter tracking
   - can handle upto 1000 voters
   - uses an array voted_ids to store the ids of the already voted voters
   - prevents double voting
3. real-time vote counting
   - tracks total number of votes
   - maintains live update ofvotes per candidate
   - allows multiple processes to read vote counts concurrently
4. synchronization using semaphores
   - prevents race condition in shared memory with semaphores
   - mutex: for read-count updates
   - wrt: for writing/voting actions
   - readcount-sem: for safely increasing/decreasing readers
   - console_sem: for preventing garbled console output  during simultaneous writes
5. readers-writers problem implementation
   - multiple observers can read the number of votes but multiple voters cannot give vote at same time
6. shared memory for IPC
   - uses POSIX shared memory to allow multiple program/processes to:
     vote
     observe voting process
     synchronize access to shared data
7. session log file generation
   - unique timestamped file name
   - contains session headers, system info, and vote records
8. signal handling for cleanup
   - proper cleanup of semaphores and shared memory using sigint on ctrl+C
9. automatic resource cleanup on start    
