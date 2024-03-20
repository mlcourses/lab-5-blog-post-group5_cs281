# Lab 5: Finite State Machine Design

## What We Did In The Last Lab

In our previous lab, we delved into the integration of microcontrollers, sensors, and actuators, expanding our understanding of digital circuitry. We explored components like the buzzer and ultrasonic sensor, mastering techniques to control them using Arduino microcontrollers. Through practical experiments, we learned to modulate sound intensity with the buzzer and accurately measure distances with the ultrasonic sensor. Finally, we applied this knowledge to a design challenge, creating a handheld distance detector. This lab emphasized the practical application of engineering principles in real-world scenarios. For more information regarding Lab 4's contents, please refer to this [URL](https://github.com/mlcourses/lab-4-blog-post-Giabao252/blob/main/post.md).

## Overview and Motivation

This lab introduces the details of Finite State Machine (FSM) design, a fundamental concept in computer systems. The lab's primary objective is to construct a circuit capable of determining whether a binary number is divisible by three. This task involves simulating a sequential system that processes incoming binary digits one at a time and analyzes their collective value to ascertain divisibility. Through this exercise, we will gain valuable insights into FSMs, learning how to map out state transitions into state tables and implement combinational logic to drive the system's behavior. By engaging in this hands-on exploration, we will deepen our understanding of sequential circuits and enhance our problem-solving skills in digital design.

<img src="./assets/fsm.png" />

## Lab Objectives

1. Design a Finite State Machine (DFA - Deterministic Finite Automata) using a state transition diagram that allows us to construct different binary strings which are divisible by 3.

2. Determine the number of JK Flip Flops needed for the amount of states our FSM has.

3. Design the logic for the two combinational circuits needed in our FSM design above.

4. Create a Function Table and use K-Maps for each output values to determine the boolean expressions needed for our combinational circuits. 

5. Build and Test the circuit in logisim.

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

- Firstly, we have to know that JK Flip Flop is a sequential circuit. Sequential circuits, unlike combinational circuits, incorporate memory elements to store information temporarily. Imagine a road with traffic lights: while combinational circuits act like traffic signals, instantly responding to inputs and changing lights accordingly (green to red, for instance), sequential circuits behave more like a traffic signal with memory. They retain their current state until new input triggers a change, similar to how a traffic light remains red until a timer expires or a sensor detects a vehicle. In essence, sequential circuits can remember past states and produce outputs based not only on current inputs but also on their internal state or history

- JK Flip Flops can be implemented with the following logics:

    + If we want the device to store 0, we set J to 0, and K to 1.
    + If we want the device to store 1, we set J to 1, and K to 0.
    + f we want the device to maintain the previously stored value acress a clock transition, we set both J and K to 0. 

<img src="./assets/jkff.png" /> 

- In this lab, we are using the 7476 JKFF chip, featuring a **negative-edge-triggered**. This means the point in time when a flip-flop may take on a new value occurs on the falling edge of the clock. 

### Designing a DFA For The Finite State Machine

- A DFA, or Deterministic Finite Automaton, is like a machine with specific states it can be in. It moves from one state to another based on inputs it receives. Each transition is determined by a clear set of rules, making its behavior predictable and precise. It's a fundamental concept used in computer science to model and solve various problems efficiently.

- For this step, we have to design a DFA that allows us to construct different binary strings which are divisible by 3. Since we are dealing with binary strings, our inputs that determines the state are only 0s and 1s. Each state must have an instruction for both inputs, otherwise it will not be deterministic. 

- Below is the DFA that we have constructed:

<img src="./assets/dfa.png" /> 

- Our DFA has three states in total, so we would need 2 JK Flip Flops to be able to represent all three states. This is because if we use 1 flip flop , we could only represent 2 states. 

### Constructing the Function Table

- This step is to specify the actual before and after values for all the combination of signals in the circuit, especially the JK flip flops. This includes the detail of what signals to send to each JK flip flop as the J and K inputs so that the flip-flop output value on the next clock cycle represents the correct next-state value. 

- The table is divided into three main sections: 
    + Left side: information regarding the current state and current input combination for x. 
    + Middle: information regarding the next state and the control inputs for the JK flip-flops that cause this next state to happen correctly. 
    + Right side: desired output F based on the current state.

- Our Function Table will look like this:

<img src="./assets/function_table.png" /> 

- Our first column indicates our states which matches up with our DFA. We have the states S0, S1, S2 and a "don't care" state (because our DFA only needs 3 states). Next, we look at the current states of the two JK flip flops (denoted as Q0 and Q1) to determine the outputs. State S0 will be reached when Q0 and Q1 are both 0, S1 is when Q0 is 1 and Q1 is 0, S2 is when Q0 is 0 and Q1 is 1 and our don't care state is when both Q0 and Q1 is 1. These will then be evaluted with the input being put into the flip flop, which can be either 0 or 1 (represented by x) and future states as well as the result of the flipflop is determined in "Next State" and "F" columns.

### Drawing Kmaps

- After writing out our function table, we will draw out Kmaps for each J0, J1, K0 and K1 to see when each J and K will be true. This will help us design a wiring diagram later because we will be able to see when J0, K0, J1 and K1 will be true. We have the following Kmaps:

 <img width="702" alt="kmap" src="https://github.com/mlcourses/lab-5-blog-post-group5_cs281/assets/67582698/b6c1a9a1-6fb8-461c-968f-b4c7619061ab">

- We then use this to construct our wiring diagram. Our wiring diagram looked like this:

<img width="723" alt="wiring diagram" src="https://github.com/mlcourses/lab-5-blog-post-group5_cs281/assets/67582698/38706e61-f5ab-4d8c-b7cb-d257fe0b63c6">

- The wiring diagram takes the inputs into each state (J0, K0, J1 and K1) shown in the Kmaps above and then wires them before putting them into the JK flipflop. For example, if we look at the gate 2J on the JK flipflop (which is J0), we can trace it back to the 7432 XOR chip, of which it is the output of Q1 (1A is connected to 1Q of the JK flipflop which is Q1) and x. We get the wiring diagram by filling out this connection process.

## Testing

- After we have our wiring diagram, we assembled the circuit. This is what our final circuit board looks like:
  
![IMG_8032](https://github.com/mlcourses/lab-5-blog-post-group5_cs281/assets/67582698/cdd9aafe-1c90-471f-a26a-904cc7aa012a)

- This matches our wiring diagram drawn above, though the wiring for the clock is a little different. For the clock, we used the button on our breadboard and connected it according to this diagram:

#### Clock diagram

We had to connect the clock to a resistor and the resistor to a +5V source, which provided it power. We then connected the clock to the JK-flip flop itself to tell it when to update. The green wire on the breadboard is connecting the clock to the JK flipflop, while the purple wire connects it to the high-low indicators to make it easier to check our clock.

- Below is a video that demonstrates how our circuit works. There is audio in the video that describes how the circuit function and the different intermdiary state changes that culminates in the final result.

#### Testing Video

## Conclusion

In conclusion, this lab helped us understand the process of using sequential circuits in our larger circuit. We used the JK flip flop and becaue the output of the flip flop depended on what state the flip flop was in before, we had to draw out DFA diagrams and then Kmap the different JK inputs. The main takeaway for this lab is the use of the JK flip flop and how to plan out the correct wiring for a sequential circuit to ensure that the states carry over correctly and the circuit works as intended. Another takeaway would be the wiring of a clock to our circuit and to the JK flipflop so we could update it whenevr we wanted to and see its effects on each state and final result.




