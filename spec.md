---
layout: default
title: The Kata
---

## The Kata

## High-level operation

## Handling the door

## Selecting a wash program

A straightforward function - the operator can press the up and down
buttons to cycle between selected programs. The current program is
always shown on the left-hand two digits as "Px". The "P" never
changes.

- The available programs are clamped to the range 1-3. Pressing UP
  when the display shows P3 has no effect. Pressing the DOWN button
  when the program is on P1 has no effect.

- On startup, the currently selected program is P1.

- They're cheap momentary switches, so button bounce is
  inevitable. How will you debounce? And when will you do this?

## Running the wash program

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
