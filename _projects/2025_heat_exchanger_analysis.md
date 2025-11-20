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
With an understanding of how the heat exchanger operates, a computational analysis can be performed to better understand the first operation of the exchanger. First, a mass balance equation will be derived due to the steady state assumption:

$$
\sum \dot{m}_{\text{in}} = \sum \dot{m}_{\text{out}}
$$

$$
\dot{m}_{H,\text{in}} + \dot{m}_{C,\text{in}} 
= 
\dot{m}_{H,\text{out}} + \dot{m}_{C,\text{out}}
$$

Integrating this equation then yields:
$$
m_{H,\text{in}} + m_{C,\text{in}} 
= 
m_{H,\text{out}} + m_{C,\text{out}}
$$


#### Changes & Their Impact
XX