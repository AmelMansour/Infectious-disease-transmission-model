;;Infectious Disease Model

breed [healthy-people healthy-person]
breed [infected-people infected-person]
breed [sick-people sick-person]
breed [immune-people immune-person]
breed [dead-people dead-person]

globals [
  total-healthy-people
  total-infected-people
  total-sick-people
  total-immune-people
  total-dead-people
]

turtles-own [  ;; Turtle variables.
  turn-check
  wall-turn-check
  incubate
  sickness
  terminal-check
  immune-check
]

to building-draw ;; Use the mouse to draw buildings.
  if mouse-down?
    [
      ask patch mouse-xcor mouse-ycor
        [ set pcolor grey ]]
end

to do-plots ;; Update graph.
  set-current-plot "Population Totals"
  set-current-plot-pen "Healthy"
  plot total-healthy-people
  set-current-plot-pen "Infected"
  plot total-infected-people
  set-current-plot-pen "Sick"
  plot total-sick-people
  set-current-plot-pen "Immune"
  plot total-immune-people
  set-current-plot-pen "Dead"
  plot total-dead-people
end

to setup  ;; Initialize the model.
  RESET-TICKS
  clear-turtles
  pop-check
  setup-agents
  update-globals
  do-plots
end

to go  ;; Run the model.
  disease-check
  ask healthy-people [repeat 5 [ fd 0.2 ] display]
  ask infected-people [repeat 5 [ fd 0.2 ] display]
  ask sick-people [repeat 5 [ fd 0.2 ] display]
  ask immune-people [repeat 5 [ fd 0.2 ] display]
  update-globals
  do-plots
  tick
end


to setup-agents  ;;  Setup the begining number of agents and their initial states.
  set-default-shape healthy-people "person"
  set-default-shape infected-people "person"
  set-default-shape sick-people "person"
  set-default-shape immune-people "person"
  set-default-shape dead-people "caterpillar"

  ask n-of initial-healthy patches with [pcolor  = black]
     [ sprout-healthy-people 1
      [ set color blue ] ]

  ask n-of initial-sick patches with [pcolor = black]
    [ sprout-sick-people 1
      [ set color yellow
        set sickness disease-period ] ]

end

to disease-check ;;  Check to see if an infected or sick turtle occupies the same patch.
  ask healthy-people[
    if any? other turtles-here with [color = yellow]
    [infect]
    if any? other turtles-here with [color = pink]
    [infect]
    wander
  ]

  ask sick-people[
    if any? other turtles-here with [color = blue]
    [infect]
    wander
    set sickness sickness - 1
    if sickness = 0
    [live-or-die]
  ]

  ask infected-people[
    if any? other turtles-here with [color = blue]
    [infect]
    wander
    set incubate incubate - 1
    if incubate = 0
    [get-sick]
  ]

  ask immune-people[wander]

end

to infect ;;  Infect a healthy turtle, test if it is immune and set the incubation timer if it isn't.
  set immune-check random 100
  ifelse immune-check < immune-chance
  [recover]
  [ask healthy-people-on patch-here[
    set breed infected-people
    set incubate incubation-period]
  ask infected-people-on patch-here [set color pink]]

end

to get-sick ;;  Change an infected turtle into an sick turtle and set the disease progression timer.
   set breed sick-people
   set color yellow
   set sickness disease-period
end

to terminate ;;  Kill a sick turtle who reaches the end of the disease progression and fails the terminal check.
  set breed dead-people
  set color white
end

to live-or-die ;; Test if the turtle dies from the disease.
  set terminal-check random 100
  ifelse terminal-check < terminal-chance
  [terminate]
  [recover]
end

to recover  ;;  Change turtle breed to immune.
  set breed immune-people
  set color sky
end


to wander ;; Random movement for agents.
    set turn-check random 20
    if turn-check > 15
    [right-turn]
    if turn-check < 5
    [left-turn]
     if [pcolor] of patch-ahead 1 != black
     [wall]

end

to wall ;;  Turn agent away from wall
    set wall-turn-check random 10
    if wall-turn-check >= 6
    [wall-right-turn]
    if wall-turn-check <= 5
    [wall-left-turn]
end

to wall-right-turn ;;Generate a random degree of turn for the wall sub-routine.
  rt 170
end

to wall-left-turn ;;Generate a random degree of turn for the wall sub-routine.
  lt 170
end

to right-turn ;;Generate a random degree of turn for the wander sub-routine.
  rt random-float 10
end

to left-turn   ;;Generate a random degree of turn for the wander sub-routine.
  lt random-float 10
end


to update-globals ;; Set globals to current values for reporters.
  set total-healthy-people (count healthy-people)
  set total-infected-people (count infected-people)
  set total-sick-people (count sick-people)
  set total-immune-people (count immune-people)
  set total-dead-people (count dead-people)
end

to pop-check  ;; Make sure total population does not exceed total number of patches.
  if initial-healthy + initial-sick > count patches
    [ user-message (word "This simulation only has room for " count patches " agents.")
      stop ]
end
