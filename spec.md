---
layout: default
title: The Kata
---

## The Kata

## High-level operation

## Handling the door

The door is simulated by a slide switch. In the upper position, the
door is open, in the lower position it's closed.

When the program is being selected by the operator, the "Open"
indicator has to be updated promptly to show the current state of the
door switch.

## Selecting a wash program

A straightforward function - the operator can press the up and down
buttons to cycle between selected programs. The current program is
always shown on the left-hand two digits as "Px". The "P" never
changes.

- The available programs are clamped to the range 1-3. Pressing UP
  when the display shows P3 has no effect. Pressing the DOWN button
  when the program is on P1 has no effect.

- On startup, the currently selected program is P1.

- They're cheap momentary switches, so some degree of button bounce is
  inevitable. How will you debounce? And when will you do this?

## Running the wash program

The wash program is initiated by pressing "START". If the door switch
is currrently open, this has no effect. Otherwise, if the door is
closed, the wash program is commenced.

Check the high-level operation FSM again : there are many actions
initiated when the program is started and ended.

- The program is locked in until it's ended.

- Pressing "START" has no effect when the wash program is already
  running.

- If the door slide switch is moved to open, it's disregarded and the
  "OPEN" indicator stays off. The door cannot be opened while the wash
  program is running.

### Timer countdown and ticker

### Filling

### Operating valves

#### The powder valve

#### The softener valve

### Draining

### Heating

### Running the motor

## Unloading the washing machine

## Wash program variations

There are three different programs the operator can select. There are
variations in:

- what phases (wash, condition, rinse, spin) are in the program
- the timing of the phases
- the water fill level that's
- the target temperature of each phase (if heated)

### Program 1 : hot wash, soften, rinse and spin

### Program 2 : warm wash, rinse and gently spin

### Program 3 : rinse and spin only
