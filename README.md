### go-interview

# Golang Interview Questions / Interviewer's Cheatsheet 

First question intended to quickly evaluate the candidate, if it is worth wasting time talking to him/her more than 20 minutes. If yes - go further and deeper.

## SECTION 1, SYSTEMS TRIVIA

- What is stack? Heap? __What is recursion?__
- How can you affect if structure will be put on stack or heap?
- What is data structure? What is variable? What is register? What is pointer?
- OS process, thread; vs. goroutine; what about memory?
- containers, VMs, containers vs VMs;
- how OS manages memory; pages;
- OS kernel, syscalls, cgroups, systemd; systemd vs docker;
- how to kill a process by name? how to find open ports? configuring sshd keys? how to see system logs? systemd logs?

  some questions can be by-passed, but at least what are processes and threads, the candidate absolutely must know.

## SECTION 2, GOLANG TRIVIA

- __slices___ (this is question #1, as 90% of weak candidates are detected at this very simple stage; so please start with it, and if it doesn't know slices, you can finish the interview)
    - what _are_ slices?
    - what are arrays?
    - two ways to create slices? make slice with zero length and N capacity?
    - are slices passed to a function via a pointer, or by copy, or something else?
    - append - please tell how you write it? how does it work? how much bigger the array gets? capacity of array of empty slice? append to very big slices?
    - remove an element at the start (left)? remove an element in the middle?
    - there's an infinite loop, new elements are appended, and first elements are removed from slice, how much memory will it consume over time?
    - you pass a slice into a function, append an element, and return it back; will the returned slice point to the same underlying array?
    - (gotcha question: you have a slice s1 with 50 elements, and take s2=[30:40], then unmarshal a JSON array into s2; can you expect that s1 will have elements 30..40 updated, or not, or what will/can happen?)
    - can you take a pointer to a slice element? why?

- Strings in Go
    - immutability
    - runes
    - overhead

- __concurrency__ (this is another question the candidate must clearly understand; a lot of them learned that concurrency!=parallelism, but make sure he/she _really_ understands what it is)
    - goroutines; threads - how many of them created by default?
    - Is there a limit for a number of goroutines?
    - what they are? how much memory they take? what if it needs more stack space?
    - how goroutines are mapped to threads of OS, and CPU of machine?
    - can you kill a goroutine from the outside? you _need_ that, how can you do that?
    - can you have goroutine's leak? well, is this possible? please describe how that might happen, and how will you find the cause?

- channels (concurrency part 2)
    - so you have a channel you need to read from, and some blocking IO function you use to read from e.g. network; please explain __how__ will you combine these two reads into a single loop, so that you won't block on a blocking function and miss the channel data?
    - now, easy, what _are_ channels? two sorts of them?
    - you write to an unbuffered channel, no one reads from, what will happen? okay, what is blocking?
    - you have a channel, multiple goroutines are reading from it; you write a message into it, which goroutine will receive it, or all of them will?
    - but what if you need to send a message to all of them?
    - what if the number of reading (listening) goroutines is variable, how can you handle this case?
    - what will happen if you read from closed channel?
    - how can this be used? is there any standard golang library, that extensively uses it?
    - what will happen if you write to closed channel?
    - okay, how to make sure that doesn't happen? any methodologies? well, you can't be sure, how can you _absolutely_ make sure there won't be panic on writing to a channel?
    - range over a channel
    - you have a channel, and wanna try to send to it, only if it can receive your data, you can't afford to block - how will you do it? will it work with unbuffered channels?
    - you can afford to wait for channel, but not too long, say 5 seconds at most; you do you implement this timeout?
    - you have IO function that blocks, and you can't afford that; how will you implement a timeout wrapper over it?
    - can you find out if channel is full?
    - if it is empty? okay, we have a channel for communicating data, and we want to drain it before exiting, what is the proper way to do it?
    - why "Uber best practices" recommends set capacity 1 to all buffered channels, or else think well about the specific digit, why is that?
    - can you resize the buffer of a channel?
    - well, you absolutely need it, how will you do it?
    - what kinds of data can you send via a channel? can you send a channel itself? an empty struct?
    - how can you implement an RPC over channels in Go? i.e. how do you communicate with N goroutines, and get synchronous replies?
    - (probably the most tricky question) How can you implement prioritization in a set of channels? (if the candidate can explain it  - you are lucky to find a star)

- synchronization (concurrency part 3)
    - what are waitgroups?
    - mutexes
    - contexts
        - types of contexts?
        - what are the use of tham?
        - suppose there are no contexts, how would you implement it yourself?
        - how would you stop net/http server?
    - semaphores vs mutexes
    - mutexes vs communication, CSP, what Go docs says about it?
    - what are deadlock?
    - can you have a deadlock in Go? provide an example
    - strategies to avoid deadlocks?
    - what are race conditions?
    - can you have race conditions in Go? example please

- GC! and MM, here we are
    - what is GC and how does it operate?
    - can you stop it? can you force it?
    - can you write a program so that GC doesn't work that much? how?
    - what algorithms are used?
    - stack vs heap
    - are variables allocated on the stack, or on the heap, how it is decided? escape analysis?
    - how to monitor the GC cycles and memory consumption?
    - so you have a memory leak - how would you debug it?

- Maps
  - vs. hash set
  - What is a hash?

- OOP

- errors

## SECTION 3, DATA FORMATS

- JSON
- gob
- XML
- yaml
- other

## SECTION 4, DATABASES

- Basics
    - Relational?
    - non-relational?
    - difference? can implement anything in one class or the another?

## SECTION 5, NETWORKING & COMMUNICATION

- IP addresses, masks, DNS
- You enter google.com in a browser and hit enter - what happens next, explain in 3 minutes
- HTTP
    - How the request looks like?
- TCP
- TLS
- UDP
- vs. vs. vs.
- Ports, sockets, difference
- What is RPC?
- What is REST?
    - How REST is different from RPC?
    - Can REST be implemented not over HTTP? example please
    - Can you cache REST? RPC?
    - Load balancing, RPC vs. REST?


## SECTION 6, MESSAGE QUEUES

## SECTION 7, INFRASTRUCTURE

