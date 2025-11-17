---
layout: project
title: Linear Actuator Max Load and Height Design
description: Design Challenge with Constraints
technologies: Python Programming Language
image: /assets/images/design_cover.png
---

For ENGRD 2020 (Statics and Mechanics of Solids) we were tasked with creating a mechanism that could lift as large a weight as possible to the largest possible height. Our constraints consisted of: 150cm by 50cm workspace, three pins, a rigid bar of fixed length (our choice) and a linear actuator from a catalog. 

I first chose the ideal linear actuator for the task. From the catalog, the IMA33 Actuator seemed ideal with a max lifting force of 36KN (8,000 lbf) which is plenty considering the small dimensions. The actuator has a length ranging from 76.2mm to 457.2mm, or 7.62cm to 45.72cm. This is ideal as the actuator has a short starting length (when the stroke has not been extended) but still has a large reach to allow for the mechanism to extend the weight as high as possible within the workspace.

I chose to have the rigid bar labeled BCE to have a length of 150cm exactly, to extend the length of the workspace when horizontal to allow the weight (attached at point E) to be lifted as high as possible when the actuator (AC) is activated. With this, the general design of the actuator was complete, and this left the most critical design choice: the location of Pin C (where the actuator attaches to the rigid bar). As I will show below, the distance from Pin B to Pin C, labeled X, will affect both the max weight and the max height in opposing ways (they are in contradiction with each). I then will display the optimization process I used with Python to determine the optimum X value. 

![Shaded rendering of earlier version]({{ "/assets/images/FBD_of_rigid_arm.png" | relative_url }}){: .inline-image-r style="width: 300px"}

Considering the Free Body Diagram for the rigid bar, there are reaction forces acting at pin B, as well as the force from the actuator acting at Pin C and the weight acting downwards at Pin E (both of which cause moments about B). Considering sum of moments about B, a larger moment arm gives the force from the actuator a larger applied moment at B, and could therefore lift more weight. However, when giving the actuator a larger moment arm (larger X), the max angle between BCE and the horizontal when the actuator is fully extended decreases, and hence the weight is not lifted as high. Therefore, these goals are in contradiction with each other. Hence, a balance must be struck between the two. 

To optimize, I considered the product of the max height reached by the point E (where the weight attaches) and the max lifting moment produced about Point B from the actuator. I did this by varying X between 150 minus the minimum length of the actuator (if the design were in a straight line) and 150cm (the length of bar BCE). The code is shown below as well as the mathematical derivations of how the max height and moment about B were determined.

<div style="text-align: center;">
  <img src="{{ '/assets/images/moment_max.png' | relative_url }}" style="width: 250px; display: inline-block; margin: 0 15px;" />
  <img src="{{ '/assets/images/y_max.png' | relative_url }}" style="width: 250px; display: inline-block; margin: 0 15px;" />
</div>


```python
    # Variables

    L_min = 7.62 # Length of actuator when not extended. Units: cm
    L_max = 45.72 # Length of actuator when fully extended. Units: cm
    F_max = 36 # Units: KN
    x = 150-L_min # Initializing X value. Units: cm
    BCE = 150 # Units: cm
    best_optimize_factor=0
    ideal_x=0

    # Determine optimize factor at each x integer between 1 and 150cm
    # X value with highest is the ideal x value

    while x<=150: 
        # Determining Max Moment About B by Actuator
    
        # Determine alpha (Law of Cosines):
        alpha = math.acos((150**2+L_min**2-x**2)/(2*150*L_min))

        # Determine theta initial (Law of Sines):
        theta_i = math.asin((150*math.sin(alpha))/x)
   
        # Determine moment about B:
        M_abt_b = F_max*x*math.sin(theta_i)
    
        # Determine Max Height
    
        # Determine theta max (Law of Cosines):
        theta_max = math.acos((150**2+x**2-L_max**2)/(2*150*x))
    
        # Determine max height:
        y_max = 150*math.sin(theta_max)
    
        # Determine optimization factor:
        optimize_factor = M_abt_b*y_max
    
        # Determine if better than previous
        if optimize_factor>best_optimize_factor:
            best_optimize_factor = optimize_factor
            ideal_x = x
    
        x = x+.01
    
    print(ideal_x)
```

## Results
Following the optimization using the code above, interesting results were found. The general principle was for every X value from the minimum X value needed considering the minimum length of the actuator to the max value of X (Pin C at E) the moment about B caused by the actuator and the maximum height were found. These values were then multiplied together, and the X value that had the largest product (optimization factor) was selected to be the ideal value of X. The graph below displays the results, and it was found having Pin C at point E (X=150cm) was the most ideal value. 

![Shaded rendering of earlier version]({{ "/assets/images/optimization_results.png" | relative_url }}){: .inline-image-r style="width: 600px"}

This makes sense for a few reasons. Firstly, the magnitude of the moment caused by the actuator force was up to 5,000 KN(cm) while the maximum height value only reached rouhgly 45cm (Note: less than the 50cm requirement). It then makes sense that the ideal X value is simply the ideal value for maximizing the moment (longest moment arm-- X=150cm). Upon further investigation, the maximum height only changed by roughly 0.5 cm between the minimum and maximum X value. It then makes sense to maximize the moment, and therefore lifting force, due to such a small change in max height. A relatively small change in X compared to the length of bar BCE causes theta max to not change significantly.

Changes to the definition of the optimization factor could be valuable in exploring how to optimize the design in various ways. For example, I experimented by making the formula for the optimization factor as the moment caused by the actuator force times maximum height cubed. This resulted in a smaller ideal X value as the maximum height carried larger weight. This comes down to design choice and what matters more in your design, but I feel that setting X = 150cm is ideal for this task.