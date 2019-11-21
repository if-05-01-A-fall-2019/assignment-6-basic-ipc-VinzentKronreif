# Vinzent Kronreif 
# Assignment 6: Basics of Interprocess Communication

## 1. Race Conditions
The race conditions are when the process wich comes first gets overwritten by the second process because the first process writes something in a variable and the second process also writes something in it, so the last wins.

## 2. Disabling Interrupts
### i. Why is it impossible to achieve Mutual Exclusion via disabling interrupts on a multi-core machine?
Because if one core is blocked, the other one still can go on with all processes, so it doesn't work.
### ii. Why is it dangerous to give user processes the power to disable interrupts?
Because if you have bugs or any mistakes in your programm, it could happen that the interrupts are already blocked so you cant stop or restart program, without shutting down the whole system.

## 3. Peterson's Solution
### i. Play through the two scenarios of the handout of Peterson's solution. Document how it works.
#### Scenario1: 
It works, because when process0 is in the CR and process1 calls enter_region(), process 1 has to wait until process0 is not interested any more.
#### Scenario2: 
The slower process wins and is able to run the code in the cr. Scenario works.
### ii. Play through the scenario which makes the strict alternation approach fail. Document how it fails.
The scenario wich makes it fail, is when one of the processes has another priority as the other. Then one of the processes trys a few times to go in the while() but doesnt get in and that is useless computing time.
### iii. What is the meaning of the variable loser in Peterson's solution? When does it have any effect?
This variable is used, if the two processes are nearly simultaneously. Because the variable can only have one state. So the process that gets last to write in the variable is the looser and has to wait in the while().
### iv. Extend the given functions such they can handle three processes.
