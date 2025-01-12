# Description
Dual logic gates. Select between AND, OR, XOR, NAND, NOR, and XNOR gates.  
Each input can be inverted as well.  
Press the encoder on a number to invert that input. This is denoted with a -.  
Press the encoder on a gate to enter the submenu and change the gate.  
Note that the ctrl knobs have an effect, if you want to control the inputs purely with CV, turn the knobs all the way down!  
Of course, you can also use the knobs to set the inputs high or low without CV.  

# Controls
| Control | Description | Comment |
| --- | --- | --- |
| Ctrl 1 - 4 | Gate Inputs | 1 and 2 to gate 1. 3 and 4 to gate 2. |
| Encoder | Menu Navigation | Turn to navigate, press to invert or enter submenus. |
| CV Out 1 - 2 | Logic Outs | Output of logic gates 1 and 2 respectively |

# Diagram
<img src="https://raw.githubusercontent.com/electro-smith/DaisyExamples/master/patch/logic/resources/logic.png" alt="logic.png" style="width: 100%;"/>

# Code Snippet
```cpp
switch(gateType)
{
    case 0:
        return a && b;  //AND
    case 1:
        return a || b;  //OR
    case 2:
        return (a && !b) || (!a && b);  //XOR
    case 3:
        return !(a && b);  //NAND
    case 4:
        return !(a || b);  //NOR
    case 5:
        return (a && b) || (!a && !b);  //XNOR
}
```