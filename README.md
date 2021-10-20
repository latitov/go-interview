### go-interview

# Golang Interview Questions / Interviewer's Cheatsheet 

Section 1 & 2 are intended to quickly evaluate the candidate, if it is worth wasting time talking to him/her more than 20 minutes. If yes - go to sections 3+.

## SECTION 1, SYSTEMS TRIVIA

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

- __concurrency__ (this is another question the candidate must clearly understand; a lot of them learned that concurrency!=parallelism, but make sure he/she _really_ understands what it is)
    - goroutines  - how many of them created by default?
    - what they are? how much memory they take? what if it needs more stack space?
    - how goroutines are mapped to threads of OS, and CPU of machine?
    - can you kill a goroutine from the outside? you _need_ that, how can you do that?
    - 
- errors
- 

## SECTION 3, GOLANG COMPLETE

- escape analysis

## SECTION 4, DATABASES

## SECTION 5, NETWORKING & COMMUNICATION

## SECTION 6, MESSAGE QUEUES

## SECTION 7, INFRASTRUCTURE

