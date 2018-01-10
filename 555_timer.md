
# 555 Timer

The 555 timer is a versitile electronic componant, with uses ranging from an oscillator to make a light flash or a speaker buzz, to a smimt trigger,
to smooth noisy signals. While the chip can be unterstood as a macro level, by expirementing with different methods of interfacing passive
components with this black box, it is much better understood by looking at the internals of the chip and how they react to inputs. In order to 
understand the chip, first the underlying theory of each internal companant, and each accompaning passive element must be undertood. 

-------
## Resistors

The most simple and funtamental electronic device is the passive componant, the resistor. On the first day of any introductory electronics course, one 
will learn the relationship

![equation](/images/555_timer1.svg)

This equation relates three fundament concepts in electronics: Voltage- the potential of electrons to do work,
Current- the rate at which charge flows, and Resistance- the load that charge is pushed through. Resistors can be combined to change how they
influnce a circuit. One such combination is series resistance

![equation](/images/555_timer_pic1.svg)

when resistors are connected one after another like this, their resistances are combined by adding them together. In this case, the equivalent 
resistance of the new circuit is 

![equation](/images/555_timer2.svg)

Now, if we take that knowledge, and the relationship `V=IR`, we can construct the most simple circuit in electronics
{voltage divider pic}
Through the two resistors, a current I will flow, determined by the resistance seen by the voltage source, which we know to be `R1+R2`. Therefore,


![equation](/images/555_timer3.svg)

now we can apply the relationship again to find the voltage potential over R2, and find that 

![equation](/images/555_timer4.svg)

Now we have created a voltage divider! The voltage seen by R2 will be proportional to the two resistor values, and if they are equal, it will be 1/2 the supply voltage

-----

## Capacitors
Capacitors are the second fundamental passive circuit element. It is a device that stores and releases electric charge, depending on the voltage
difference across its terminals. The voltage difference between the plates of the capacitor (V) is proportional to the charge on the plates (Q), and the capacitace (C)

![equation](/images/555_timer5.svg)

A fundamental rule in electronics is Kirkoff's voltage law, which states that the voltages across components in a loop of a circuit must sum to 0.
Using this rule, we can breakdown what happens when a capactior charges

![capacitor chargine circuit](/images/555_timer_pic2.svg)


When the switch is closed, the circuit becomes a loop, with the supply voltage, the resistor volatage, represented by IR, and the capacitor voltage, Q/C

![equation](/images/555_timer6.svg)

Current is the rate of charge flow over time, so
`I = dQ/dT` Which can be substituted into the equation, giving

![equation](/images/555_timer7.svg)

This is first order differential equation, with the inital value of `Q = 0 at t=0`. solving this, the general solution is 

![equation](/images/555_timer8.svg)

This can now be solved for some general values, such as this time it takes the capacitor to reach 1/3 and 2/3 supply voltage by equating `Vc = 1/3 Vs`

![equation](/images/555_timer9.svg)

![equation](/images/555_timer10.svg)

![equation](/images/555_timer11.svg)

![equation](/images/555_timer12.svg)

So a capacitor charging through a resistor will charge to 1/3 of the supply voltage in .4 times the constant RC. This value, RC, is common in electronics with timing circuitry because the charging and discharging of a capacitor is a consistant an measurable process. Applying the above manipulation to 2/3 supply voltage,

>Vc = 1/3 Vs

>1/3 = (1-e^(-t/RC))

>-t/RC = ln(2/3)

>t =~ .4 RC

> similarly for Vc = 2/3Vs, 

>-t/RC = ln(1/3)

>t =~ 1.1 RC

Discharging a capacitor follows a similar pattern as charging, with this circuit being considered instead
{discharging capacitor circuit}
The diffential equation works out to be 
{R(dQ/dt)+Q/C = 0}
with boundary condition Vc = Vs at t=0, leading to 
{Vc = Vs(e^(-t/RC))}
which is a reflection across 1/2Vs from the charging equation, meaning that the derived values for charge and discharge are simply opposites,
{Vc=1/3Vs:t=~1.1RC}
{Vc=2/3Vs:t=~.4RC}

----

3.Comparator
Now that we have gone through the nessacary passive components, it is time to analyze the active section of the chip. 
The comparator is a special type of op amp, wih its charetoristics choosen to act fully in the saturation range. 
The theory and application of the op amp is too much for this post, so instead I will focus on this specific type
The comparator has 2 inputs, 2 voltage sources and one output
{comparator.img}
the output of the comparator follows a simple rule: if the negative input is greater than the positive, the negative voltage source is passed to the output
in the opposite case, The positive voltage input is passed to the output.
using this rule, compatators can be used to compare analog voltages and output a digital value. 
{comparator.graph}

3. transistors are the drivers of all computing devices, allowing logical switch operations to be done quickly, and on a small scale. 
{trans.jpeg}
When current is passed from the base lead to the emmitter lead, it allows a proportional ammount of current to flow through from collector to emmiter.
This makes a BJT essentially an amplifier of current. This opperation can be used in the "saturation region" where the current flow is all or nothing,
making the transistor act as a switch in an electronic circuit. In this opperation, transistors drive all of digital electronics.
There is one "discrete" transistor in the 555 chip, which, at the right time in the timing sequence, will open a path to ground.

5. RS-latch 
The rs latch is the most basic componant in an sequential logic circuit, that is, a circuit that not only acts on inputs, but on a previous state.
The latch has two inputs, a reset input and a set input, giving it the name Reset/set latch. The latch has a single bit of memory, which will store the state of the latch
That state is modified by the inputs. If the set input is triggered, the memory changes to high. reset trigger makes the value low. 
The whole time, the latch has two outputs, Q and ~Q which reflect the state of the memory of the cell, and are always opposite each other. 
{Rs data table}
one way to understand the rs-latch is to imagine a setup with a lightbulb and two switches. One switch turns the lightbulb one, the other turns it off.
In this setup, the lightbulb is the logical Q output, and the switches represent the R and S inputs. 

Now to assemble the Timer. Staring on one side of the block diagram, 









 












