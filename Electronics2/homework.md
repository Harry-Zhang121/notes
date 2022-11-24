# Electronics 2 homework
Design a break point circuit given by following parameters.



| Reference voltage| Break points | Slope |
|---|---|---|
| $U_{ref1} = 6.4V$ | $U_{inBrk1} = -5V$ | $Slope_1 = 1 $
| $U_{ref2} = -6.4V$ | $U_{inBrk2} = 5V$ | $Slope_2 = 1 $
| $U_{ref3} = 1V$ | $U_{outBrk1} = -9V$ | 
| | $U_{outBrk2} = 11V$ | 

## Graph
With there parameter we are able to plot a graph of input and output voltage.
![graph](./graph.jpg)

## My approch

### Analyize the graph
We can notice that if we shift the graph by 1 unit down. $U_{outBrk1}$ becomes 10V and $U_{outBrk2}$ becomes -10V. We can then obtain a perface symmetrical graph.

There are two break points with the same slop beforw the fiest breakpoint and after the second breakpoint. We can also calculate the slope between breakpoints as:
$$
Slope_3 = \frac{11-(-9)}{5-(-5)} = 2
$$

This happens to be double of slope 1 and 2.

### Analyize the circuit
We can seperate the circuit to three parts:
![circuit](./circuit.jpg)

#### Part1(Purple)
This is a inverting amplifier which invert the voltage output. Graphically the graph will be "fliped" along the horizontal axis.

#### Part2(Orange)
This is a breakpoint circuit it self. The voltage $U_B$ depends on current $I_B$
$$ U_B = - 10k\Omega * I_B \tag{1}$$ 

#### Part3(Green)
The two 3-pole circuit we need to generate two break points.

#### Part4(Blue)
This is not a three pole. But we can shift the graph by supplying a current $I_s$ here.


### Circuit design
First we assume E9 is open circuit. In which case part1 invert the voltage. 

$$U_{out} = - U_B$$

Because of equation 1 and inverting amplifier we need to shift the voltage graph at $U_B$ **up** by 1V. This is done by $I_s$

$$ I_s = \frac{1V}{-10k\Omega} = 0.1 mA \tag{2} $$

Now we have a 
