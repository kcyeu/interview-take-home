# Pipe and Shared Memory
Write three C++ programs that communicate using shared memory and pipes


## mainParent.cpp: 
This is the main program. It creates two child processes, WAITS for them to complete, and exits.  
Tasks:
1.	Repeatedly ask user to enter an integer n.  If user enters -1, all parent and child processes should exit. 
1.	Generate n random integers from 1 to 50, and store in an array or vector. The child processes will access this data.  
1.	When the mainParent process exits its loop, it should notify the child processes. Otherwise, the child processes will be blocked waiting for the parent.
1.	Wait for both child processes to complete; then exit.

## childA.cpp: 
This process uses pipes to communicate with mainParent.
Tasks:
1.	Repeatedly read set of integers from mainParent's pipe.
1.	Calculate the average of integers and print results.
1.	Exit when there is no more data to be processed.

## childB.cpp: 
This process uses shared memory to communicate with mainParent. Tasks:
1.	Repeatedly read set of integers from mainParent's shared memory
1.	Sort the integers in order and print results.
1.	Calculate the standard deviation of integers and print results.
1.	Exit when there is no more data to be processed.



The two child processes must be implemented as separate C++ programs. All processes run concurrently and may print their output line in an unpredictable order.
As a result, the output lines from a process may mix with output lines from other processes. Make sure that each output line does not contain output from different processes. An example is below:


---
## Example output from mainParent:
```
./mainParent

[mainParent] Main Process Started
[mainParent] childA Process Created
[mainParent] childB Process Created

[mainParent] Enter a positive integer or -1 to exit:   13
[mainParent] Generating 13 random integers: 42 8 46 35 16 7 10 19 47 3 37 5 42

[mainParent] Enter a positive integer or -1 to exit:   10
[mainParent] Generating 10 random integers: 8 36 12 9 3 46 30 14 37 31	

[mainParent] Enter a positive integer or -1 to exit:   6
[mainParent] Generating 6 random integers: 11 45 31 31 12 17	 

[mainParent] Enter a positive integer or -1 to exit:   -1
[mainParent] Process Waits
[mainParent] Process Exits
```

---
## Example output from childA:
```
[childA] Child process started

[childA] Random Numbers Received:	42 8 46 35 16 7 10 19 47 3 37 5 42
[childA] Average: 			24.38461538	

[childA] Random Numbers Received: 	8 36 12 9 3 46 30 14 37 31		
[childA] Average: 			22.60000000	

[childA] Random Numbers Received: 	11 45 31 31 12 17				
[childA] Average: 			24.50000000	

[childA] Child process exits
```

---
## Example output from childB:
```
[childB] Child process started

[childB] Random Numbers Received:	42 8 46 35 16 7 10 19 47 3 37 5 42
[childB] Sorted Sequence:   		3 5 7 8 10 16 19 35 37 42 42 46 47	
[childB] Standard Deviation: 		17.27492625

[childB] Random Numbers Received: 	8 36 12 9 3 46 30 14 37 31		
[childB] Sorted Sequence:   		3 8 9 12 14 30 31 36 37 46			
[childB] Standard Deviation: 		15.01258731

[childB] Random Numbers Received:	11 45 31 31 12 17				
[childB] Sorted Sequence:    		11 12 17 31 31 45		
[childB] Standard Deviation: 		13.41268057

[childB] Child process exits
```
