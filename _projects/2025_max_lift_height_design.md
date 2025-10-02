---
layout: project
title: Linear Actuator Max Load and Height Design
description: Design Challenge with Constraints
technologies: Python Programming Language
image: /assets/images/radio-machine-cad.jpg
---

For ENGRD 2020 (Statics and Mechanics of Solids) we were tasked with creating a mechanism that could lift as large a weight as possible to the largest possible height. Our constraints consisted of: 150cm by 50cm workspace, three pins, a rigid bar of fixed length (our choice) and a linear actuator from a selected catalog. 

I first chose the ideal linear actuator for the task. From the catalog, the IMA33 Actuator seemed ideal with a max lifting force of 36KN (8,000 lbf) which is plenty considering the small dimensions. The actuator has a length ranging from 76.2mm to 457.2mm, or 7.62cm to 45.72cm. This is ideal as the actuator has a short starting length (when the stroke has not been extended) but still has a large reach to allow for the mechanism to extend the weight as high as possible within the workspace.

I chose to have the rigid bar labeled BCE to have a length of 150cm exactly, to extend the length of the workspace when horizontal to allow the weight (attached at point E) to be lifted as high as possible when the actuator (AC) is activated. With this, the general design of the actuator was complete, and this left the most critical design choice: the location of Pin C (where the actuator attaches to the rigid bar). As I will show below, the distance from Pin B to Pin C, labeled X, will affect both the max weight and the max height in opposing ways (they are in contradiction with each). I then will display the optimization process I used with Python to determine the optimum X value. 

Considering the Free Body Diagram for the rigid bar, there are reaction forces acting at pin B, as well as the force from the actuator acting at Pin C and the weight acting downwards at Pin E (both of which cause moments about B). Considering sum of moments about B, a larger moment arm gives the force from the actuator a larger applied moment at B, and could therefore lift more weight. However, when giving the actuator a larger moment arm (larger X), the max angle between BCE and the horizontal when the actuator is fully extended decreases, and hence the weight is not lifted as high. Therefore, these goals are in contradiction with each other. Hence, a balance must be struck between the two. 

To optimize, I considered the product of the max height reached by the point E (where the weight attaches) and the max lifting moment produced about Point B from the actuator. I did this by varying X between 150 minus the minimum length of the actuator (if the design were in a straight line) and 150cm (the length of bar BCE). The code is shown below as well as the mathematical derivations of how the max height and moment about B were determined.



```python
    some code = 10;
    plot();
```




![Shaded rendering of earlier version]({{ "/assets/images/radio-machine.jpg" | relative_url }}){: .inline-image-r style="width: 200px"}






![Photo of old radio]({{ "/assets/images/old-radio.jpg" | relative_url }}){: .inline-image-l}
