# Lab 5: Finite State Machine Design

## What We Did In The Last Lab

In our previous lab, we delved into the integration of microcontrollers, sensors, and actuators, expanding our understanding of digital circuitry. We explored components like the buzzer and ultrasonic sensor, mastering techniques to control them using Arduino microcontrollers. Through practical experiments, we learned to modulate sound intensity with the buzzer and accurately measure distances with the ultrasonic sensor. Finally, we applied this knowledge to a design challenge, creating a handheld distance detector. This lab emphasized the practical application of engineering principles in real-world scenarios. For more information regarding Lab 4's contents, please refer to this [URL](https://github.com/mlcourses/lab-4-blog-post-Giabao252/blob/main/post.md).

## Overview and Motivation

This lab introduces the details of Finite State Machine (FSM) design, a fundamental concept in computer systems. The lab's primary objective is to construct a circuit capable of determining whether a binary number is divisible by three. This task involves simulating a sequential system that processes incoming binary digits one at a time and analyzes their collective value to ascertain divisibility. Through this exercise, we will gain valuable insights into FSMs, learning how to map out state transitions into state tables and implement combinational logic to drive the system's behavior. By engaging in this hands-on exploration, we will deepen our understanding of sequential circuits and enhance our problem-solving skills in digital design.

## Lab Objectives

1. Design a Finite State Machine (DFA - Deterministic Finite Automata) using a state transition diagram that allows us to construct different binary strings which are divisible by 3.

2. Determine the number of JK Flip Flops needed for the amount of states our FSM has.

3. Design the logic for the two combinational circuits needed in our FSM design 

<img src="./assets/fsm.png" />

4. Create a Boolean Truth Table diagram and use K-Maps for each output values to determine the boolean expressions needed for our combinational circuits. 

5. Build and Test the circuit in logisim

6. Build the circuit on the PB-503 breadboard with a JK Flip Flop IC and the other logic gates that we already used.

## Materials

- PB-503 breadboard prototyping station

- 7404 NOT gate IC

- 7408 AND gate IC

- 7486 XOR gate IC

- 7476 JK Flip Flop IC

- IC data sheets

- Wires and connection tools

- Logic Probes

- Logic Switches

- Push Button

- Resistors 


## Project Steps

### Understanding the JK Flip Flop



### Designing a DFA For The Finite State Machine

- A DFA, or Deterministic Finite Automaton, is like a machine with specific states it can be in. It moves from one state to another based on inputs it receives. Each transition is determined by a clear set of rules, making its behavior predictable and precise. It's a fundamental concept used in computer science to model and solve various problems efficiently.

- For this step, we have to design a DFA that allows us to construct different binary strings which are divisible by 3. Since we are dealing with binary strings, our inputs that determines the state are only 0s and 1s. Each state must have an instruction for both inputs, otherwise it will not be deterministic. 

- Below is the DFA that we have constructed:

<img src="./assets/dfa.png" /> 

- Our DFA has three states in total, so we would need 2 JK Flip Flops to be able to represent all three states. This is because if we use 1 flip flop , we could only represent 2 states. 

## Testing

## Conclusion




