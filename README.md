# Infectious-disease-transmission-model
#Introduction

Infectious disease modeling is an approach used in health sciences and epidemiology to study the spread and control of diseases within a population. These models are often employed to gain insights into the underlying mechanisms of disease spread, to evaluate the effectiveness of control and prevention strategies, and to forecast future epidemic trends.

Infectious disease models can vary in complexity, ranging from simple mathematical models to detailed computer simulations. In these models, individuals in a population are often represented as autonomous agents, such as turtles in NetLogo, or as mathematical variables, as seen in compartmental models like the SIR model (Susceptible-Infectious-Recovered).

#Model 

This code is a simulation of an infectious disease model in the NetLogo modeling environment. Here is a detailed explanation of each part of the code: 

#Turtle Breeds:
*healthy-people
*infected-people
*sick-people
*immune-people
*dead-people 
are the different breeds of turtles representing the various conditions of individuals in the simulation:
*Healthy
*Infected
*Sick
*Immune
*Deceased

A key characteristic of infectious disease models is how the disease spreads from one individual to another. This can include parameters such as the transmission rate, incubation period, duration of illness, and probability of recovery or mortality. By adjusting these parameters, researchers can explore different scenarios and assess the potential impact of public health interventions such as vaccination, quarantine, or hygiene measures.

![image](https://github.com/AmelMansour/Infectious-disease-transmission-model/assets/141269604/d32a68a4-b574-43db-8e6e-3a7be4d18f89)


#Main Procedures:

#*setup: 
Initializes the simulation by resetting ticks, clearing existing turtles, checking if the initial population exceeds the grid size, and initializing agents.
#*go: 
Manages the simulation's progression at each tick by checking interactions between agents, updating agents' states and global variables, and refreshing the plots.
#setup-agents:
Initializes different turtle species (agents) with appropriate shapes and initial states.
#*disease-check:
Checks interactions between agents, such as disease transmission, progression, recovery, or death.
#*infect:
Infects a healthy turtle, determines if it becomes immune or develops the disease, and initializes the incubation timer if necessary.
#*get-sick:
Changes an infected turtle into a sick turtle and initializes the disease timer.
#*live-or-die:
Determines if a sick turtle dies or recovers.
#*recover:
Changes the turtle's species to immune.
#*wander:
Manages agents' random movement, with sub-routines to handle wall collisions.
#*wall:
Handles agents' behavior when encountering a wall by adjusting their movement direction.
#*right-turn and left-turn:
Perform random right or left turns for agents' random movement.


#Utility Procedures:

#*building-draw:
Allows drawing buildings by clicking with the mouse on the grid.
#*do-plots:
Updates plots displaying population totals in each state.

In the NetLogo interface, buttons would control the simulation flow, such as:

#*setup:
initializing the simulation.
#*go:
running the simulation step by step.

** When you click the "setup" button in the NetLogo interface, several actions occur:

![image](https://github.com/AmelMansour/Infectious-disease-transmission-model/assets/141269604/ca2225df-5520-4026-9fff-a0299582846a)

~ The simulation is initialized by calling the setup procedure.
~ Tick counts are reset to zero with RESET-TICKS.
~ All existing turtles are cleared with clear-turtles.
~ A check is performed to ensure that the initial population of the simulation does not exceed the total number of patches (cells) on the grid with pop-check.
~ Agents are initialized on the grid by calling the setup-agents procedure.
~ Plots are updated by calling the do-plots procedure.

** When you click the "go" button in the NetLogo interface, the simulation advances by one time step:

![image](https://github.com/AmelMansour/Infectious-disease-transmission-model/assets/141269604/3bc20a6b-4e77-4dd5-ac7d-68ee08943358)

~ The disease-check procedure is called to check interactions between agents, such as disease transmission, progression, recovery, or death.
~ Each agent moves randomly according to the wander procedure.
~ Global variables are updated by calling the update-globals procedure.
~ Plots are updated again by calling the do-plots procedure.
~ The simulation tick is incremented by one unit with tick.
==> These actions repeat each time you click the "go" button, allowing the simulation to simulate disease progression and population evolution over time.

#Conclusion

In summary, infectious disease models provide a powerful framework for studying epidemic dynamics and informing public health decisions. By better understanding how diseases spread within a population, researchers can develop more effective strategies to prevent, control, and mitigate the effects of epidemics.
