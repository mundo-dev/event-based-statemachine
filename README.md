# event-based-statemachine
Event based state machine for nodejs.
# Objectives
There are already a lot state machine implementations available, however most of them do not meet all the requirements I have. The provided solution has to fulfill especially the following requirements (not a complete list):

- (R1) The event transport is based on events from a nodejs EventEmitter.
- (R2) Timeout events are supported.
- (R3) Customizable logging is required.
- (R4) Defining and using the statemachine is oriented more on a practical than theoretical approach.
- (R5) Support of composed state machines.
- (R6) Easy to read/maintain the definition of the state machine 
- (R7) Keep it simple

## R1 - EventEmitter based events
If you using nodejs one of the first thing you're getting in touch with are events submitted by a nodejs EventEmitter. An EventEmitter provides a nice build-in feature of nodejs for submitted events an register listener to events.

## R2 - Timeout events
In practice you expect an event to happen within a certain time frame. If the event doesn't happen within the time frame you would like to trigger a different action.

## R3 - Logging
Having a couple of statemachines active in your implementation the behaviour of the statemachines should be easily comprehensible related to occured events an taken state transitions.

## R4 - Practical orientation
There are formal definitions of a finite-state machine/automaton (FSM/FSA) available https://en.wikipedia.org/wiki/Finite-state_machine. However the usage of this statemachine should oriented on a practical approach. E.g., formally you have to define the set of states/events
and the transition mapping desctiption is based on elements out of these sets. So using this formal approach you have to define the set of states, set of events, transition mapping [state, event] -> [state] and the initial state. In practice you can provide the transition mapping and inital state to derive the set of states and events implicitly. Another example is the usage of a so called DEFAULT transition (depending on the current state), which makes it possible to keep the transition mapping definition shorter.

## R6 - Easy to Read and maitain
The statemachine definition should provide easy readabilty and maintainability.

## R7 - Keep it simple
The implementation should not provide solutions for every possible use case. For example it could provide callback interfaces for (pre-/post-) state change and event occurence. Because this may interfere with simplicity, readability and maintainability and may produce side effects such interfaces will not be offered.
