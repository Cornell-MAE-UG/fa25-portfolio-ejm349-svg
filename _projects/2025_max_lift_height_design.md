---
layout: project
title: Linear Actuator Max Load and Height Design
description: Design Challenge with Constraints
technologies: Python Programming Language, LaTex
image: /assets/images/ACT_final.jpg
---

##### Defining the Problem
For ENGRD 2020 (Statics and Mechanics of Solids) we were tasked with creating a mechanism that could lift as large a weight as possible to the largest possible height. Thus, the problem consists of an optimization task between the two objectives, within the given constraints.

##### Constraints & Objectives
Our constraints consisted of: 150cm by 50cm workspace, three pins, a rigid bar of fixed length (our choice), the weight acts as a concentrated load at specified location, and a linear actuator from a given catalog.

The objective of the problem is, again, to design a mechanism that can lift as large of a weight as possible to the largest possible height.

##### Design Degrees of Freedom
Given the constraints, characteristics of the design that can be altered include: the bar orientation, ground pin locations, third pin location, actuator mounting location, actuator base location, length of bars, payload attachment point, and the actuator stroke selection.

##### Rigid Static Analysis

###### Design Choices
I first chose the ideal linear actuator for the task. From the catalog, the IMA33 Actuator seemed ideal with a max lifting force of 36kN (8,000 lbf) which is plenty considering the small dimensions. The actuator has a length ranging from 76.2mm to 457.2mm, or 7.62cm to 45.72cm. This is ideal as the actuator has a short starting length (when the stroke has not been extended) but still has a large reach to allow for the mechanism to extend the weight as high as possible within the workspace.

I chose to have the rigid bar labeled BCE to have a length of 150cm exactly, to extend the length of the workspace when horizontal to allow the weight (attached at point E) to be lifted as high as possible when the actuator (AC) is activated. With this, the general design of the actuator was complete, and this left the most critical design choice: the location of Pin C (where the actuator attaches to the rigid bar). As I will show below, the distance from Pin B to Pin C, labeled X, will affect both the max weight and the max height in opposing ways (they are in contradiction with each). I then will display the optimization process I used with Python to determine the optimum X value. 

![Shaded rendering of earlier version]({{ "/assets/images/FBD_of_rigid_arm.png" | relative_url }}){:  style="display:block; margin:0 auto; width: 300px;"}

###### Computational Analysis
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
    F_max = 36 # Units: kN
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


###### Results
Following the optimization using the code above, interesting results were found. The general principle was for every X value from the minimum X value needed considering the minimum length of the actuator to the max value of X (Pin C at E) the moment about B caused by the actuator and the maximum height were found. These values were then multiplied together, and the X value that had the largest product (optimization factor) was selected to be the ideal value of X. The graph below displays the results, and it was found having Pin C at point E (X=150cm) was the most ideal value. 

![Shaded rendering of earlier version]({{ "/assets/images/optimization_results.png" | relative_url }}){:  style="display:block; margin:0 auto; width: 500px;"}

This makes sense for a few reasons. Firstly, the magnitude of the moment caused by the actuator force was up to 5,000 kN(cm) while the maximum height value only reached roughly 45cm (Note: less than the 50cm requirement). It then makes sense that the ideal X value is simply the ideal value for maximizing the moment (longest moment arm-- X=150cm). Upon further investigation, the maximum height only changed by roughly 0.5 cm between the minimum and maximum X value. It then makes sense to maximize the moment, and therefore lifting force, due to such a small change in max height. A relatively small change in X compared to the length of bar BCE causes theta max to not change significantly.

Changes to the definition of the optimization factor could be valuable in exploring how to optimize the design in various ways. For example, I experimented by making the formula for the optimization factor as the moment caused by the actuator force times maximum height cubed. This resulted in a smaller ideal X value as the maximum height carried larger weight. This comes down to design choice and what matters more in your design, but I feel that setting X = 150cm is ideal for this task.

###### Final Design v1
With this in mind, the final design will have the actuator attach to BCE at its end point (the location where the load is concentrated). The design is shown below:

![Shaded rendering of earlier version]({{ "/assets/images/final_design_v1.jpg" | relative_url }}){:  style="display:block; margin:0 auto; width: 400px;"}


##### Non-Rigid Static Analysis
Now, analysis will be completed to better understand the limitations of the design. The bar is no longer rigid and is susceptible to bending from the combined action of the weight and the actuator force. 

###### Assumptions
Bar is non-rigid, weight is a constant distributed load over a length L starting from point E, considering only components of the force transverse to the beam, beam is slender, plane sections remain plane, maximum (total) weight is equal to the maximum force output of the actuator, and small deformations.

###### Finding Maximum Deflection
To find the maximum deflection, notice that the force from the actuator passes through one of the pins, and thus does not cause bending-- only need to consider weight for bending. Because only the transverse components of these forces are being considered, the maximum net load will occur when the actuator is not extended (largest transverse component). First, will calculate the relevant angles as defined in the previous sections and create a free body diagram: 

$$
\alpha = \theta_i = \arccos(\frac{(150cm)^2 + (7.62cm)^2 - (150cm)^2}{2(150cm)(7.62cm)}) = 88.54^\circ
$$

$$
\beta = 2\alpha - 90^\circ = 2(88.54^\circ) - 90^\circ = 87.09^\circ
$$

![Shaded rendering of earlier version]({{ "/assets/images/fbd_bending_fix.jpg" | relative_url }}){:  style="display:block; margin:0 auto; width: 400px;"}

Note: These are valid because the design creates an isosceles triangle as two sides are equal to 150 cm. The total weight is drawn as a single force acting through the centroid of its surface of application (half of L because stated it is a constant distributed load).

Now, find the transverse force on the bar (component of weight that is transverse): 

$$
W_{\max,t} = W_{\max}\sin\beta = 36\,\text{kN}\,\sin(87.09^\circ) = 35.95\,\text{kN}
$$

This beam behaves as a pinned-pinned beam experiencing a transverse force at a point along its length. This precise scenario is solved in the course textbook appendix, from which it can be found that (after substituting specific values from this problem):

$$
y_{\text{d, max}} = -\frac{W_{\max,t}\left(\frac{L}{2}\right)\left[\left(150\,\text{cm}\right)^2 - \left(\frac{L}{2}\right)^2\right]^{3/2}}{9\sqrt{3}\, E I \left(150\,\text{cm}\right)}
$$

Thus, the maximum bending of the beam is related to the length L over which the distributed load is applied, or more practically, how large the box or container this system is designed to lift is-- this conceptually makes sense that there is this dependence. This equation holds as long as $\frac{L}{2} < 75cm$.

Notice that the equation also depends on two other unknowns: the Young's Modulus (E) and moment of inertia (I). These are simply material properties, and thus depend on the cross section and material of the beam chosen. For the sake of calculation, I will first assume that the bar is made of Structural (ASTM-A36) steel and has a square cross sectional area with side length 2cm. From this, the E value can be found in the textbook, and the moment of inertia can be found through the equation $I_{\text{square}} = \frac{1}{12}wh^3$, where w is the width and h is the height. Thus,

$$
I_{\text{square}} = \frac{1}{12}(2cm)(2cm)^3 = \frac{4}{3}cm^4
$$

$$
E_{\text{steel}} = 200GPa
$$

Now, for the last assumption, will assume that $L = 20cm$, a realistic value for the width of a container carrying some weight. Then, substituting these values, the max deflection gives: 

$$
y_{\text{d, max}} = -\frac{35.95\times{10^3}N\left(\frac{0.20m}{2}\right)\left[\left(1.50\,\text{m}\right)^2 - \left(\frac{0.20m}{2}\right)^2\right]^{3/2}}{9\sqrt{3}\, (200\times{10^9}Pa) (\frac{4}{3}cm^4\times{(\frac{0.01m}{1cm})^4}) \left(1.50\,\text{m}\right)} = -0.193m
$$

To summarize, I assumed a square cross-sectional with side length of 2cm, that the bar is made of structural steel, that the weight is equivalent to the maximum actuator force behaving as a constant distributed load, and that said load acted over a length of 20cm and only the transverse component would be considered. From this, and the given equation in the textbook for maximum deflection in this case, it was found that the bar bends at most 0.193m downwards.

###### Choosing Beam Design (Cross Section, Material)
Oftentimes when designing beams such as this, parameters will be given for how far the beam should be allowed to bend. From the problem statement, the bar must bend no more than 2% of its length. Or equivalently,

$$
y_{\text{d, allowable}} = 0.02(1.5m) = 0.03m
$$

This is clearly smaller than the previously calculated max deflection, thus the bar must be strengthened. Decreasing the L value could decrease the maximum deflection; however, assuming constant L, want to find a mass-efficient material and cross sectional shape that could meet this criteria. 

There are two possible approaches that come to mind when trying to solve this problem. First, choose a material (E) value and find a suitable cross sectional shape that could support that load. Second, choose a cross sectional shape and find a suitable E value, and thereby material. Upon looking at material properties in the textbook appendix, aluminum had a much smaller weight per unit length than any of the metals typically used to support loads of this caliber; thus, I will choose option 1, in which I choose a material ($E_{\text{al}} = 70GPa$) and then find a suitable I value, and thus cross-sectional shape from assuming the cross-sectional shape is still a square.

$$
y_{\text{d, max}} = -\frac{W_{\max,t}\left(\frac{L}{2}\right)\left[\left(150\,\text{cm}\right)^2 - \left(\frac{L}{2}\right)^2\right]^{3/2}}{9\sqrt{3}\, E I \left(150\,\text{cm}\right)}
$$

$$
\implies I_{\text{required}} = -\frac{W_{\max,t}\left(\frac{L}{2}\right)\left[\left(150\,\text{cm}\right)^2 - \left(\frac{L}{2}\right)^2\right]^{3/2}}{9\sqrt{3}\, E (y_{\text{d, max}}) \left(150\,\text{cm}\right)}
$$

Substituting the correct values,

$$
I_{\text{required}} = -\frac{35.95\times{10^3}N\left(\frac{0.20m}{2}\right)\left[\left(1.50\,\text{m}\right)^2 - \left(\frac{0.20m}{2}\right)^2\right]^{3/2}}{9\sqrt{3}\, (70\times{10^9}Pa) (-0.03m) \left(1.50\,\text{m}\right)} = 2.45\times10^{-7}m^4 = 24.54\,\text{cm}^4
$$

Using the assumption of a square cross-sectional shape still, it is known that,

$$
I_{\text{square}} = \frac{1}{12}wh^3 = \frac{1}{12}h^4   \because w = h
$$

$$
\implies h = \sqrt[4]{12I_{\text{required}}} = \sqrt[4]{12(24.54\,\text{cm}^4)} = 4.14\,\text{cm}
$$

Therefore, the final (v2) design of the bar is made of aluminum with a square cross-sectional area with side length 4.14cm. 

###### Final Design v2
From the analysis above, the final design of the mechanism that can lift a maximum amount of weight to a maximum height without bending more than 2% of its total length and being mass-efficient is as follows:

![Shaded rendering of earlier version]({{ "/assets/images/final_design_v2.jpg" | relative_url }}){:  style="display:block; margin:0 auto; width: 500px;"}

###### Sources of Error & Other Approaches
Possible sources of error mainly lie in the assumptions made. Firstly, it was assumed the maximum weight is equal to the maximum force of the actuator. This is likely not entirely accurate as only a component of the weight is along the line of action of the actuator force. Secondly, it was assumed the weight is evenly distributed over its length-- this is not necessarily the case and could decrease or increase bending depending on the location of the centroid.

It was also assumed that the cross-section will be square. I mainly chose this to have a better comparison with the initial design now that there was a new material (aluminum) and a constraint on max bending. Considering the weight per unit length of aluminum being roughly one third of steel's, and that the cross-sectional side length doubled but the max bending decreased by roughly 84%, this seems to be a very mass-efficient solution. Instead, I could have continued to assume steel and calculate the needed I value, however, when I did this, the needed I value was far smaller than the given I values for various steel beam cross-sectional shapes in the textbook appendix. This would imply more material and weight is being used, so I pivoted to the lighter aluminum material as shown.