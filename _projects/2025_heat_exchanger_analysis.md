---
layout: project
title: Heat Exchanger Analysis
description: Control Volume Analysis
technologies: XX
image: /assets/images/HE_final.jpg
---

For ENGRD 2210 (Thermodynamics) we ran a series of experiments on a given heat exchanger setup. Below contains a description of the device and how it works, various computations exploring the physics of its operation, and analysis on potential changes to the device.

#### Photos and Schematic
The heat exchanger used has four labeled ports. Using these ports and specific arrangements of the tubing carrying the fluids, the heat exchanger can be set up in parallel flow or counter flow. Below is an image of the heat exchanger set up. Note: in this image, the exchanger is in parallel flow.

![Shaded rendering of earlier version]({{ "/assets/images/general_exchanger.jpeg" | relative_url }}){:  style="width: 500px"}

Then, the heat exchanger was changed to counter-flow in which the fluids are now flowing in opposite directions through the heat exchanger as pictured below:

![Shaded rendering of earlier version]({{ "/assets/images/counter_flow.jpeg" | relative_url }}){:  style="width: 500px"}

It can be observed that on the left hand side is a red cooler with blue liquid, representing our cold fluid, while the red fluid on the right is our hot fluid. The cold was achieved through ice and an insulated bag, while the hot fluid was heated with an electic heater. The two setups can be summarized in the two schematics below:

![Shaded rendering of earlier version]({{ "/assets/images/parallel_flow_schematic.jpg" | relative_url }}){: style="display:block; margin:0 auto; width:400px;"}

![Shaded rendering of earlier version]({{ "/assets/images/counter_flow_schematic.jpg" | relative_url }}){: style="display:block; margin:0 auto; width:400px;"}



#### Qualitative Description
Essentially, the heat exchanger operates in an adiabatic steady state (will assume these conditions when completing computational analysis). The cross section of the heat exchanger (as pictured) forces the fluids to disperse amongst many different pathways. 

<div style="text-align: center;">
  <img src="{{ '/assets/images/HE_cross_section.jpg' | relative_url }}" style="width: 200px; display: inline-block; margin: 0 15px;" />
  <img src="{{ '/assets/images/HE_cross_section2.jpg' | relative_url }}" style="width: 200px; display: inline-block; margin: 0 15px;" />
</div>

This increases the surface area of interaction between the hot and cold fluid, facilitating heat transfer between the two. As can be seen, the metal borders between the two fluids are very thin, again helping to facilitate this heat transfer. The rib design and thin ribs contribute to effective conduction, thereby heating the cold fluid by the hot fluid.

In summary, the heat exchanger operates by increasing the surface area of both the hot and cold fluid, forcing them to flow near each other (separated by very thin ribs) which facilitates effective conduction from the hot fluid to the cold fluid through these ribs. As a result, the hot fluid becomes colder, while the cold fluid becomes hotter.



#### Control Volume System Diagram
The control volume for the system is shown below. Note: the control volume system will look identical whether in parallel or counter flow as still in steady state and still the same amount of mass flow, just entering the heat exchanger in different locations. Then, theoretically, the results of the heat transfer should be identical for both flows, but it will be explained that this was not the case. 

![Shaded rendering of earlier version]({{ "/assets/images/control_volume_system.jpg" | relative_url }}){:  style="display:block; margin:0 auto; width: 500px;"}


#### Quantitative Analysis
With an understanding of how the heat exchanger operates, a computational analysis can be performed to better understand the operation of the exchanger. First, a mass balance equation will be derived due to the steady state assumption:

$$
\sum \dot{m}_{\text{in}} = \sum \dot{m}_{\text{out}}
$$

Thus,

$$
\boxed{ \dot{m}_{H,\text{in}} + \dot{m}_{C,\text{in}} 
= 
\dot{m}_{H,\text{out}} + \dot{m}_{C,\text{out}}}
$$

Now, will complete an energy balance within the control volume assuming the fluids do not mix: 

$$
\dot{E}_{CV} = \dot{Q} - \dot{W} + \sum \dot{m}_{\text{in}} \left(h_{\text{in}} + PE_{\text{in}} + KE_{\text{in}} \right) - \sum \dot{m}_{\text{out}} \left(h_{\text{out}} + PE_{\text{out}} + KE_{\text{out}} \right)
$$

Then, with the steady state and adiabatic assumption (no external heat transfer), as well as assuming $\dot{W} = 0$ and kinetic and potential energy are negligible-- a typical assumption for heat exchangers-- this equation simplifies to: 

$$
\boxed{ \dot{m}_H \left( h_{H,in} - h_{H,out} \right)
+ \dot{m}_C \left( h_{C,in} - h_{C,out} \right)
= 0}
$$

Finally, an entropy balance can be performed as shown: 

$$
\dot{S}_{cv}
=
\frac{\dot{Q}}{T_b}
+
\sum \dot{m}\,(s_{in} - s_{out})
+
\dot{\sigma}_{gen}
$$

Again, applying the assumptions made, this equation simplifies to: 

$$
\boxed{
\dot{m}_H ( s_{H,in} - s_{H,out} )
+
\dot{m}_C ( s_{C,in} - s_{C,out} )
+
\dot{\sigma}_{gen} = 0
}
$$

The equation could be further simplified by assuming the heat exchanger is reversible and setting $\dot{\sigma}_{gen} = 0$, however, considering there is a heat transfer over a finite temperature difference within the heat exchanger, this would likely be an invalid assumption.



#### Change & Its Impact: Parallel vs. Counter Flow
Although equations shown above have been created a simplfieid to model the operation of the heat exchanger, observing the role they play in a concrete example is of value. During the lab, we chose to observe the effect on the operation of the heat exchanger when we switched from parallel flow to counter flow as has been alluded to above.

When looking at the equations above, it appears that it would not matter which flow you choose, the values will be the same, however, this was not the case. We ran two experiments: 



###### Experiment 1: Parallel Flow

| Description | Value |
|------------|--------|
| Hot fluid starting temperature | 40 °C |
| Cold fluid starting temperature | 4 °C |
| Hot fluid ending temperature | 21.4 °C |
| Cold fluid ending temperature | 17.75 °C |
| Temperature difference at outlet | 21.4 - 17.75 = 3.65 °C |

<br><br>

###### Experiment 2: Counter Flow

| Description | Value |
|------------|--------|
| Hot fluid starting temperature | 40 °C |
| Cold fluid starting temperature | 7.7 °C |
| Hot fluid ending temperature | 19.8 °C |
| Cold fluid ending temperature | 25.6 °C |
| Temperature difference at outlet | 25.6 - 19.8 = 5.8 °C | 

<br><br>

###### Analysis
It should be acknowledged that the starting temperature for the cold fluid for the second experiment was slightly higher than the first due to it already having been heated once and taking an extended period of time to cool back down. However, I argue that this highlights to difference between the two flows even further. Despite the hot and cold fluid being at a smaller initial temperature difference in the counter flow example, the cold fluid still heated up slightly more in counter flow than in parallel flow, and what is perhaps more signficiant is the temperature difference at the outlet. In counter flow, the difference between the fluids at the end was noticably larger than in parallel flow. 

This is counterintuitive when first observing the equations found above-- the data should be identical. The underlying cause of this discrpancy is the time the fluids spend in close proximity, and therefore the time conduction is taking place between the fluids themselves. In parallel flow, the fluids are moving together through the heat exchanger, having a large amount of time to transfer heat from the hot to cold fluid, and therefore have more time to tend towards their equilibrium temperature. In counter flow, when the fluids first begin flowing through the exchanger, they do not have significant heat transfer until they meet in the middle of the exchanger. This causes a larger temperature difference and therefore more heat transfer. This pattern continues as the fluid continues to encounter fluid 