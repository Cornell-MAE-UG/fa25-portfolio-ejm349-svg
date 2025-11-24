---
layout: project
title: Heat Exchanger Analysis
description: Control Volume Analysis
technologies: LaTeX
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
|:------------:|:--------:|
| Hot fluid starting temperature | 40 °C |
| Cold fluid starting temperature | 4 °C |
| Hot fluid ending temperature | 21.4 °C |
| Cold fluid ending temperature | 17.75 °C |
| Temperature difference at outlet | 21.4 - 17.75 = 3.65 °C |



###### Experiment 2: Counter Flow

| Description | Value |
|:------------:|:--------:|
| Hot fluid starting temperature | 40 °C |
| Cold fluid starting temperature | 7.7 °C |
| Hot fluid ending temperature | 19.8 °C |
| Cold fluid ending temperature | 25.6 °C |
| Temperature difference at outlet | 25.6 - 19.8 = 5.8 °C | 



###### Analysis
It should be noted that the starting temperature of the cold fluid in the second experiment was slightly higher than in the first, because it had already been heated once and had not fully cooled. However, this actually emphasizes the difference between the two flow configurations. Despite a smaller initial temperature difference in the counter flow experiment, the cold fluid still reached a higher outlet temperature than in the parallel flow configuration. More significantly, the temperature difference between the hot and cold fluids at the outlet was noticeably larger in counter flow.

This might seem counterintuitive at first, as one might expect similar heat transfer for identical fluids and flow rates. The key difference lies in the temperature gradients along the heat exchanger. In parallel flow, the hot and cold fluids move together, so the temperature difference decreases along the length of the exchanger, limiting the overall heat transfer. In counter flow, the cold fluid meets progressively hotter portions of the hot fluid along the exchanger. This maintains a larger temperature difference across most of the exchanger, allowing more heat to be transferred overall. As a result, counter flow achieves a higher cold fluid outlet temperature and a larger outlet temperature difference between the fluids compared to parallel flow.

Recall the energy balance equation derived above. Because both the hot and cold fluids were water and the same pump was used, it can be assumed that their mass flow rates were identical. If the regions where only the hot fluid and only the cold fluid are taken was control volumes, the same assumptions apply, except it is no longer adiabatic. The heat transfers into them would be equal and opposite, and hence why the entire system taken as a control volume would be adiabatic. Considering these individual control volumes and assuming water is an incompressible susbtance with constant specific heat, the following equations are yielded: 

$$
\dot{Q}_{C} = \dot{m}_{C}C_{W}\Delta T_{C}
$$

$$
\dot{Q}_{H} = \dot{m}_{H}C_{W}\Delta T_{H}
$$

Thus, because the heat transfers are assumed to be equal and opposite, it is valid to only consider the magnitude of one to determine the effectiveness of each. Let the effectiveness be denoted by $\varepsilon = \frac{\dot{Q}_\text{actual}}{\dot{Q}_\text{max}} = \frac{\Delta T_{\text{actual}}}{\Delta T_{\text{max}}}$ because assumed mass flow rate and specific heats are constant. First, determine for parallel flow: 

$$
\varepsilon = \frac{\dot{Q}_\text{actual}}{\dot{Q}_\text{max}} = \frac{\Delta T_{\text{actual}}}{\Delta T_{\text{max}}} = \frac{17.75°C - 4°C}{40°C - 4°C} = 0.382 = 38.2\%
$$

This was found where the actual change in temperature is the magnitidue of the change in temperature of the cold fluid, and the max is if the cold fluid reached the same temperature as the hot fluid-- of course, not possible, but a good value to act as a reference point of comparison. 

Now, repeat for counter flow:

$$
\varepsilon = \frac{\dot{Q}_\text{actual}}{\dot{Q}_\text{max}} = \frac{\Delta T_{\text{actual}}}{\Delta T_{\text{max}}} = \frac{25.6°C - 7.7°C}{40°C - 7.7°C} = 0.554 = 55.4\%
$$

Hence, a quantitative display in the rough difference in effectiveness of the parallel vs. counter flow set ups in this heat exchanger.


#### Concluding Notes
There were a series of assumptions made throughout this analysis, including: steady state operation, adiabatic, potential and kinetic energy being negligible, constant specific heats, and water being an incompressible substance. Of course, these assumptions are not perfect, but they allow for a reasonable approximation of the operation of the heat exchanger. Heat exchangers are found all over, such as in: air conditioners, radiators, car engines, refrigerators, etc. Being able to analyze them through making reasonable assumptions is incredibly important. 

Below is a video of the operation of the heat exchanger used in counter flow:

<video width="560" height="315" controls muted>
  <source src="{{ '/assets/images/IMG_6522.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>