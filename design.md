---
layout: default
title: Design Goals
---
# Design goals

## Technical Characteristics

We wanted to have a design which included a broad range of typical
hardware and firmware scenarios. After all, if the point is to bridge
the realism gap, then it needs to be at least _somewhat_ realistic.

We also needed to come up with a problem which is almost universally
understood. The technical characteristics are important, but to base
the design on something niche would have been a problem - the lack of
familiarity would have meant that participants would need to spend
time understanding problem domain concepts, rather than concentrating
on the practice of TDD and incremental design.

Because of this, we narrowed down the scope to domestic/consumer
applications and picked a number of candidate designs. Only the
washing machine had the right mix, and was common enough to be almost
universally recognisable.

Here's what we decided on for a realistic design challenge:

- __Multiple analog "sensor" inputs__ : we live in an analog world,
  and ADC is a very common feature of embedded systems
  development. The STM32 MCU has multiple modes for carrying out
  conversion (blocking, interrupt-on-completion and DMA transfer). We
  leave the choice of implementation to the developer. Using actual
  sensors for this would be fragile, so we substitute simple rotary
  potentiometers.

- __Multiple discrete digital outputs__ : we use discrete LEDs as
  proxies for what would be interaction with electromechanical
  elements of the washing machine : solenoids, valves, actuators, etc
  
- __Multiple discrete digital inputs__ : the design had to have a mix
  of digital inputs, with both momentary and latching switches. It's
  also necessary to be able to deal with these using polling, or using
  interrupts - and leaving that choice to the developers.

- __Timers__ : many embedded control systems have to operate based on
  stimulation from sensory input events, but also from timers. Working
  effectively with timer hardware, and with code that needs to
  understand the passage of time, poses some unique design challenges.

- __Pulse-Width Modulation output__ : microcontrollers often drive
  "the big stuff" using PWM signals, like the electric motor that
  turns the drum, or the pump that drains the water. PWM creates a
  square wave output with a duty cycles (the ratio of one-ness to
  zero-ness). This is often treated as an approximation of analog
  output signals, or converted to a cleaner analog signal using
  low-pass filters.

- __Non-trivial state machines__ : the problem has to be one where
  there will be some design decisions to be made for the classic
  problem of managing and modelling system state, and dealing with
  state transitions. This challenge is so common in embedded systems
  development as to be almost universal. How these things are dealt
  with are left open to the developer.

- __Serial protocol integration__ with other hardware components
  protocol. In the current era of modularised electronics components,
  it's often necessary to integrate with non-trivial "active"
  components using serial protocols like I2C, SPI and UART. We
  integrate with the 7-segment driver using SPI, and send it short
  2-byte messages to update the 7-segment displays.

- __Bi-directional communication__ to control and monitor the system :
  the design supports UART to allow for simple commands to be executed
  over a USB->UART adapter. This technology is simple to configure,
  adapters are cheap to buy, and it's reliable. It was an explicit
  goal to not have a specific wireless communications technology
  (WiFi, LoRa, BLE etc) - these interactions can be fragile and
  time-consuming in a Dojo-style setting.

- __Multiple programming models__ : it's commonplace for embedded
  developers to have to make tough choices between interrupt-driven,
  polling in ```while(1) {}``` loops, timer-and-interrupts and in some
  cases also background DMA data transfer. This has all of these
  options, and it's left entirely as an option to the developer to
  figure out which combination works best, and how best to design for
  it.

- __Realistic tradeoffs__ : much though this author would love to code
  using the full expressive power of both the core C++ language and
  its standard library, this isn't possible (or indeed desirable) in
  an embedded context. Coding for a real hardware target forces us to
  address those tradeoffs in our design.

## Secondary Goals

There were some other goals that contribute to the success of the
design:

- __Agnostic about C or C++__ : Hardware Abstraction Layer APIs are
  provided in C and (modern) C++. If participants want to implement a
  solution entirely in test-driven C, this is possible, and the same
  for C++.

- __Logistically simple__ : to make the logistics of using this
  hardware in a Dojo or workshop learning session, it needs to be
  self-contained. Using a modular, plug-in approach where the ST
  Nucleo is inserted into the board also means that different MCUs can
  be used. The Nucleo includes an ST-Link debugger that works with
  open soorce tools, and this was a significant factor.

- __Bare Metal or RTOS__ : it should be a problem that can be solved
  using a lightweight RTOS (FreeRTOS particularly, but not ruling out
  other), as an alternative to a bare metal build.

- __Many Usage Scenarios__ : it should be something that can be used
  to learn about embedded systems development for people
  transitioninng to that technical domain from other technologies, as
  well as for experienced embedded developers learning new practices
  like TDD.  [More on these here](Usage Scenarios)

Finally, we also wanted the hardware design to be _fun, and
playable!_. The design is supposed to motivate participants by giving
visual feedback when functions work. Everyone :heart: LEDs, after all.

The combination of different switch types, rotary potentiometers, and
discrete, bar and 7-segment LEDs make the design a fun experience to
work with, with lots of visual feedback.
