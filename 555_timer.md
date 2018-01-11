
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

![equation](/images/555_timer_pic5.svg)

Through the two resistors, a current I will flow, determined by the resistance seen by the voltage source, which we know to be `R1+R2`. Therefore,


![equation](/images/555_timer3.svg)

now we can apply the relationship again to find the voltage potential over one of the resistors, R2, and find that 

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


When the switch is closed, the circuit becomes a loop, with the supply voltage, the resistor voltage, represented by  IR, and the capacitor voltage, Q/C. These values must sum to 0, so they can be expressed in the following equation

![equation](/images/555_timer6.svg)

Current is the rate of charge flow over time, so
`I = dQ/dT` Which can be substituted into the equation, giving

![equation](/images/555_timer7.svg)

This is first order differential equation, with the inital value of `Q = 0 at t = 0`. solving this, the general solution is 

![equation](/images/555_timer8.svg)

This can now be solved for some general values, such as this time it takes the capacitor to reach a third of supply voltage by equating `Vc = 1/3 Vs`

![equation](/images/555_timer9.svg)

![equation](/images/555_timer10.svg)

![equation](/images/555_timer11.svg)

![equation](/images/555_timer12.svg)

So a capacitor charging through a resistor will charge to one third of the supply voltage in .4 times the constant RC. This value, RC, is common in electronics with timing circuitry because the charging and discharging of a capacitor is a consistant and measurable process. Applying the above manipulation to two thirds supply voltage,



 












