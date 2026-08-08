# 8-bit CPU Breadboard
Building an 8-bit breadboard computer from scratch with TTL logic gates, 555 timers, and EEPROMs.

System Architecture & Credits:
This hardware build is an implementation of **Ben Eater's 8-bit breadboard computer** reference architecture. 

System Design: Ben Eater ([eater.net/8bit](https://eater.net/8bit))
Physical Implementation & Debugging: Jack Pressey

Base: Used 2 1/4 12 x 18 MDF boards pieced together


# CLOCK MODULE

Uses 555 Timer: 555 timer uses a capacitor that charges and discharges when a transistor turns on to allows flow to ground, and recharges after an SR latch turns the transistor back off.

I will not go into detail about the wiring of the 555, but using a variable resistor which can be adjusted with a flat head screwdriver, you can adjust the frequency of the clock, this happens because the capacitor needs current to charge up and when you adjust resistance I.E make the resistance higher, the current will decrease. Using 2 0.1 microfarad capacitors I was able to take away lots of impedance, but on the clocks rising edge it still jumps to about 5 volts then goes back down to around 3.5V. This happens in a matter of hundreds of microseconds and with my parts it won't matter. The output of this clock I had connected to pin 3 was connected to a yellow LED and a resistor to ground to ensure I didn't burn out the LED.

First bug I found was that the frequency was extremely low, < 1 Hz for sure. What I found was that The capacitor I had hooked up to pin 2 and ground was 10 microfarads, which was too high to have a frequency I was satisfied with. I then switched it out to a 1 microfarad capacitor, which had a range from about just below 1Hz to a frequency that I assume either my own eyes couldn't see, or just was not oscillating. I am going to stick with this capacitance due to the middle range being the sweet spot for me.

Monostable: Using a normal push down button, I've connected it to another 555 to be able to de-bounce it so there are no issues when using it to debug.

Bistable: Using a switch, I've connected it to yet another 555 and only used the SR latch aspect of it to de-bounce the switch because if it bounces it will still already be set.

FINISHED CLOCK MODULE: Using the bistable switch that is de bounced, I was able to connect it to or, and, and inverter gates to be able to create a 2 state clock module that can either be a steady frequency that I can modulate with the variable resistor, or it can be in the monostable state of just a push button to go to the next clock pulse. There is also a hault feature to be able to stop the clock entirely which will be hooked up to my control unit for when the HLT function is used.
