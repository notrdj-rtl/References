%% Version 1.0 %%

**Table of Contents:**

[[#Embedded Variables]]
[[#Boolean Logic]]
[[#Loop]]

---
### Embedded Variables

**List a variable**

you use the *"int 'variable';"* command. You can equal it to any value you want when needed using "="

**Set a variable to a  Connection**

you can use the *"#define 'number'"* command. 

**Setting the pin mode** 

*"pinMode('variable', OUTPUT)"* will make the variable a output connection. This is put in void setup to run once.

**to activate a connection digitally**

you use *"digitalWrite('variable', 'condition')"*. 
Alternatively, you can **activate a connection using analog** with the command "analogWrite('variable', 'current value')"

**Read the connection signal by digital input** 

to change a variable value, with the command *"digitalread('variable')"*. 
Alternatively, you can **read the connection signal by analog input** using the command "analogWrite('variable, 1-256')"



---

### Boolean/Arithmitic Logic

Boolean is the digital reading ground for electronics. 1 means on, 0 means off. "true" or "HIGH" sets the variable to 1, and "false" or "LOW" sets it to 0. 

**reverse a variables boolean**
"'variable' = !'variable'". 
If its 0, its now 1, and vise versa.

**Common Combos**

and = &&
or = ||

**Random Values**
*random(value)*
much easier here, but can't help to think maybe... too easy?

---
### Loop

The loop is used to run over repeatedly nonstop. Useful for continuous operation.

**Delay the loop**

delay(number) for however milliseconds. 

**Count the loop**

you use the command "int i = 0; i++". 
Everytime the loop restarts, the i value increases. Used for changing statements over time.



---

### Common Statements

**IF ELSE Statement**

"If () {}, else () {}" is used to tell the program what happens when the condition in the () happens, to do {}, otherwise, do the else program.

**void statements**
*needs more info on how it actually works*

Only does what's its told, does not report anything back. 

void setup runs once.
void loop runs indefinably.

**Tone statement**

usually used for passive buzzers. generates a frequency square wave. To stop the tone statement, you use noTone().

"tone(pin, frequency, duration)" is the command.

*Passive Buzzer Common Hz* 

Alto Do (523Hz), Re (587Hz), Mi (659Hz), Fa (698Hz), So(784Hz), La (880Hz), Si (988Hz) to Treble Do (1047Hz).


**Arduino Print()**
*needs more info (why does serial work, and why use begin 9600)*

in arduino, you first use "Serial.begin(9600);" yo open the serial port at 9600 bps in void setup.

Then, you can use "Serial.print(val, format);"
