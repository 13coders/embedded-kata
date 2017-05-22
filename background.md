# Background

We tend to learn and to first experience TDD on code other than our
_day job_ codebase...

- ...we see a co-worker demo TDD on typical code katas...

- ...we attend coderetreats...

- ...we watch video screencasts...

Over time, a pattern becomes apparent : that people are often
enthusiastic and sold on TDD as a generically good idea when they try
it, but when they return to work, the enthusiasm somehow
dissipates. Reality intrudes, technical specifics sap our energy,
confidence diminishes, and in a short time the transition to TDD as a
routine practice seems insurmountable.

TODO : practice vs learning

This kata is specifically for embedded systems developers. It's based
on the idea that for embedded systems, there's a gap between the
__concept of TDD__, and the __practice of TDD__ as part of our daily
workflow. Some typical problems:

- "I can't see how to work this into the build we have. It's a lot of
   work, and it's not just about writing tests. There's _other stuff
   involved._"

- "Hardware dependencies are different from the dependencies that
  developers have in, say, enterprise systems. _Hardware is hard : the
  clue's in the name._"

- "We need to keep our design really simple. We can't have virtual
  functions, RTTI, exception handling and lots of small methods. Those
  things are great for people on other platforms, _but not for
  embedded_."

Technology-agnostic code katas are an excellent way of learning and
practicing TDD and clean code. This isn't intended as a substitute -
it's intended as confidence-building __evidence__ that TDD can work on
non-trivial embedded designs.

# Evaluation boards just don't cut it

So what do embedded devs normally do when they want to experiment?
They use low-cost development boards, like the STM32 Discovery.

These are fine. They give you access to an MCU part, for about 10
bucks apiece, and they're great tools to have.

But they don't do anything.

Further up the scale we have more complete evaluation boards. Picking
the STM32 platform again, you can buy a ST-EVAL board. These are much
more expensive, typically around 200 euro for a well provisioned
board.  What you get for your money is an MCU part, but this time on a
board that's richly provisioned with integrated hardware.

But there's no functional purpose to these.

TODO : design and scale

# Stable Hardware and Functional Scope

The advantage of this design over a more open-ended development board
is that the hardware scope is fixed, and the objective is fixed on a
specific functional context.

General-purpose development boards are indispensable, but
experimentation tends to become a series of small isolated spikes of
specific features rather than an attempt at a more joined-up problem.

# Interesting ?

Read more about the [design goals for the kata](Kata-Design-Goals).
