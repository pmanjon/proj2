# Project 2 README

Student 1: Pablo Manjon Gamez (919966976)
Student 2: Stephanie Hsia (920141803)

## Project Status
This the current status of the project ...
Just started
All requirements are implemented and working 8/23

For panel, we check for valid input by making sure exactly one R button and one C button are pressed. Then we set the B row buttons according patterns we noticed, so for example we only turned on B2 when R1 was on or R2-C0 were on. "CisEven" tells us if an even number C button is on. This is used to simplify our logic in our B0 implementation.

For InputBuffer, we started with a state diagram that 3 states. The beginning default state with no input or valid input, the B-state when a valid input was entered, the C-state which waits a clock cycle and then leads back to the default state.

We made a K-map out of this diagram which allowed us to implement the main circuit that sets "SetNumber" to one when we want to output the code. We used four registers for the B-buttons in order to save the first valid input from the default state to our B-state. 

For the lock circuit we started with a state diagram for the 4 main states, unlocked, locking, locked, and unlocking. We have MCS (Main change state), which changes the state to the next when is its 1. MCS would only be 1 when we we were in a locked state and the user entered the right password, or when we were in the unlocked state the user inputted two L's or an L and three digits, and when the counter finishes.

We had a counter go off when in the locking and unlocking states, which in our case is equivalent to Y0 being true. The counter then leads to a tunnel called MotorDone letting us know we finished 4 clock cycles.
Below this we have our registers. The top 4 save our last four inputs, the bottom three has the saved combination.


## Known Issues
The project fails to function properly in ...
No test cases have failed so far

## References
* [Build an XOR gate from AND/NOT](https://electronics.stackexchange.com/questions/487529/build-an-xor-gate-from-and-not)
* [Some other link](https://stackoverflow.com)

## Generative AI Use
None

### Prompt 1
How do you create an XOR from only and/or/not gates?

### Response 1
To create an XOR (exclusive OR) gate using only AND, OR, and NOT gates, you can follow these steps. The XOR gate outputs true only when the inputs are different.

The truth table for XOR is:

| A | B | A XOR B |
|---|---|---------|
| 0 | 0 |    0    |
| 0 | 1 |    1    |
| 1 | 0 |    1    |
| 1 | 1 |    0    |

The Boolean expression for XOR can be derived as:\
A &oplus; B = (A &and; &not; B) &or; (&not; A &and; B)

This can be broken down into the following steps:

1. Create \(&not; A\) and \(&not; B\) using NOT gates.
1. Create \(A &and; &not; B\) and \(&not; A &and; B\) using AND gates.
1. Combine the results of the two AND gates using an OR gate.

Here is the step-by-step logic construction:

1. **NOT gates** to get \(&not; A\) and \(&not; B\):\
   NOT(A) &rarr; &not; A\
   NOT(B) &rarr; &not; B

1. **AND gates** to get \(A &and; &not; B\) and \(&not; A &and; B\):\
   A &and; &not; B &rarr; AND(A, &not; B)\
   &not; A &and; B &rarr; AND(&not; A, B)

1. **OR gate** to get the final result:\
   (A &and; &not; B) &or; (&not; A &and; B) &rarr; OR(AND(A, &not; B), AND(&not; A, B))

Putting it all together in a circuit diagram:

1. Input \(A\) goes to a NOT gate to produce \(&not; A\).
1. Input \(B\) goes to a NOT gate to produce \(&not; B\).
1. Input \(A\) and the output of the NOT gate for \(B\) go to an AND gate to produce \(A &and; &not; B\).
1. Input \(B\) and the output of the NOT gate for \(A\) go to an AND gate to produce \(&not; A &and; B\).
1. The outputs of the two AND gates go to an OR gate to produce the final output \(A &oplus; B\).

In terms of Boolean logic:\
XOR(A, B) = \(A &and; &not; B\) &or; \(&not; A &and; B\) 

This way, you have constructed an XOR gate using only AND, OR, and NOT gates.

### Changes 1
I needed XNOR, so changed it to:\
&not;\(\(A &and; &not; B\) &or; \(&not; A &and; B\)\)

### Prompt 2
My other prompt...

### Response 2
The other response...

### Changes 2
The other changes made...