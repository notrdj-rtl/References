
# Feedback

Feedback is when a portion of output gets *feed back* to the input for a *desired state*

**Negative Feedback**

When feed back, the result becomes the *opposite effect* of original output.

<u>Example with biology:</u> When you get hot, your body uses the signal that you are hot to *sweat*, and uses that signal back until you are cool again. 

**Positive Feedback**

When feed back, the result becomes the *amplified effect* of original output.

<u>Example with biology:</u>  Pushing the system further, Oxycontin signals more size for the baby, which pushes more Oxycontin.



### ~~The Operational Amplifier

![[Pasted image 20260602230722.png|500]]
	Figure 4: the Operational Amplifier, the goat tier component for feedback.

**Gold Rules:**

- *(V+ - V- = 0)*
	- due to even a small change would swing the output to over full range, so the output attempts to not let that happen.
- *Input current = 0*.
	- barely any current actually goes in, it gets removed for simplicity.


%% Testing this %%


*use later*

- Zero input offset voltage (When V+=V-, Vout=0)
- Infinite open-loop gain (A=∞)
- infinite input impedance (Rin=∞)
- zero output impedance (Rout = 0)
- Negative feedback configs have the output equal the input
- rail to rail = Vout=power in

**Open-loop config**
	gain is very high, mostly in voltage comparators
**Closed-loop config**
	gain is controlled, most used
