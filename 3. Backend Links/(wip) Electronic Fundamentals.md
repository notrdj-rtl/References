**Table Of Contents**

Labs:
[[#DC Circuits]]
[[#Capacitors]]
[[#Diodes]]

Additional Tools:
[[#4-Way Resistance Test]]
[[#Switch]]
[[#Buzzer]]

---

### <u>DC Circuits</u>


**Ohms Law**

*V=IR*

Voltage - Work done to move a unit of positive charge to a negative point (between two points)
Current - rate of flow of electric charge past a point (goes through)

*Power equation: P=VI*

**Series vs parallel**

*Series* 
r(total) = r1+r2
I(total) = I1=I2
V(total) = V1+V2

*Parallel* 

r(total) = = 1/(1/r1 + 1/r2)
I(total) = I1+I2
V(total) = V1=V2

**Kirchoff's laws**

1. V(sum of loop) = 0
2. I(sum of in) + I(sum of out) = 0

<u>How do you visualize this loop?</u>

**Voltage Divider**

Main Equation:
*Vout/Vin = R2/R1+R2*
If current is needed:
*I = V/(r1_r2)*

<u>Doesn't voltage take the path of least resistance?</u>

potentiometer = Tool used for voltage division (variable resistance)

<u>**Voltage source and Current source**
</u>

<u>what</u>

**Thevenin Model**

*V(Th) = V(in)R2/(R1+R2)* *= open circuit voltage*
*R(Th) = R1R2/(R1+R2)*



---
### Capacitors

**RC circuit**

**Differentiator**

**Low-pass filter**

**Filter example 1**

**Filter example 2**

**Blocking Capacitor**

**LC Filter**

---
### Diodes



---
### Multimeter

	**What is it?**
		measuring voltage, current, resistance, capasitance, transistors, temps, batteries, etc. 
		Analog vs digital -> way of measuring (digital is superior), manual vs auto (manual is you are tuning but cheap, auto is self tuning). 
	**How to measure**
		Black goes to negative (source), red goes to positive (load). Start at highest value, go lower until accurate. Do not go beyond limits. You find individual components only. Resistance changes with temp.
	**DC Voltage**
		represented by V line. measures analog single directions. 
	**AC Voltage**
		represented by V squiggle. Measures digital back and forth direction. More dangerous. 
	**Continuity**
		Tests if two parts are connected on a circuit. Could be false if alt route exists. does not work with high resistances.

---

Common tools:


potentiometer = Tool used for voltage division (variable resistance)

### Switch

Opens (stops) or closes (allows) electrical signals. Usually momentary.

**Pull-Down Requirement**

In order to prevent **floating** (No GND connection, will pickup any noise), you put a resistor to GND. The resistor helps the open switch to have a GND, and high enough, will not interfere with the closed circuit. 
### Buzzer

DC Powered with an IC. Used everywhere. Volume controlled by resistors.

**Passive vs Active**

Active has a **oscillating source** (Can convert DC->AC), passive does not. For passive, you need square waves between 2k and 5k for drive it. Active, because it does the work for you, is more expensive. It is also less configurable and sounds worse.

**Programming**

Active can use digital write no issue. 
Passive requires the "Tone" command. analogWrite will *not* work because the frequency will always be 500hz (what changes is the current).

### 4-Way Wire Testing for Resistance

**Concepts:**

	You give a current from a source (comes from circuit) with a constant voltage, and using V=IR, you can accurately estimate resistance. 
	Use when below 1 Ohm, maybe use for 1-100 range.
	The model is the Keithley 2400 series.

### ~~Semiconductor Basics~~