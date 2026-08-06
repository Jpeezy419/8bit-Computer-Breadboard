# 8-bit CPU Breadboard
Building an 8-bit breadboard computer from scratch with TTL logic gates, 555 timers, and EEPROMs.

System Architecture & Credits:
This hardware build is an implementation of **Ben Eater's 8-bit breadboard computer** reference architecture. 

System Design: Ben Eater ([eater.net/8bit](https://eater.net/8bit))
Physical Implementation & Debugging: Jack Pressey

Base: Used 2 1/4 12 x 18 MDF boards pieced together


# CLOCK MODULE

Uses 555 Timer: 555 timer uses a capacitor that charges and discharges when a transistor turns on to allows flow to ground, and recharges after an SR latch turns the transistor back off.
