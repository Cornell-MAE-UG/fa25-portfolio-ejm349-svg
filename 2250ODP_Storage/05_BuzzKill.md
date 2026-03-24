---
layout: project
title: ODP5 Functional Prototype
description: Open Design Project Prototyping
technologies: Fusion 360, 3D Printing
image: /assets/images/2250_sc2.png
permalink: /2250ODP_Storage/05_BuzzKill/
show_ODP: false
---

### A Mechanical Approach to Quantifiable Spotted Lanternfly Egg Mass Control

[Download Our Write-Up]({{ "/assets/05_BuzzKill.pdf" | relative_url }}) in PDF format.

**Team:** BuzzKill

### Purpose of Prototype
The purpose of this prototype was to test the mechanical operation of the various components of our design. We started by designing the entire prototype in CAD partly using components purchased on McMaster, and some sourced from the Taylor Design Studio. We then 3D printed the design in the RPL and assembled. The completed CAD as well as the assembled prototype (in operating position) are shown below.



![Shaded rendering of earlier version]({{ "/assets/images/cad_prototype.jpg" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }

<p style="text-align:center; font-style:italic; margin-top:4px;">
Figure 1: Prototype Built in Fusion 360
</p>


![Shaded rendering of earlier version]({{ "/assets/images/actual_prototype.jpg" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }

<p style="text-align:center; font-style:italic; margin-top:4px;">
Figure 2: Actual Prototype in Operating Position
</p>


Our project is a prototype jaw device designed to remove spotted lanternfly egg masses from a variety of surfaces efficiently and safely. The goal is to improve egg mass removal efficiency and collection ability while being easy to operate. The jaw will be actuated by a string connected to the trigger. When squeezed, the trigger will open the jaw, extending springs attached to the jaw that are trying to return the jaw back to closed. The handle is then released, causing the jaw to snap shut quickly, intended to remove the egg mass and collect it in the bucket. See below for a video showing a demonstration of the device with Play-Doh.



<video width="560" height="315" controls>
  <source src="{{ '/assets/images/prototype_video.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>




<video width="560" height="315" controls autoplay muted>
  <source src="/assets/images/prototype_video.mp4" type="video/mp4">
</video>



### What was Tested
We performed a test for each major identified mechanical mechanism on the prototype. The tests and results were as follows:

**Test One:** 

*Part:* Bucket and Jaw Assembly

*What it is Testing:* Scraping/Hinging Force of the Jaw When Attached to Bucket, Durability

*How to Perform Test:* 
Using spring scale, measure output force of the jaw mechanism, and using ruler measure opening gap of the jaw due to spring rest length. Then, cycle the actuating system 100 times, and measure the output force and rest length again. Observe any changes in force or rest length. 

*Test Results:* 

<u>Initial</u>

Output force of jaw mechanism when fully open: 12.5N
Opening gap of jaw due to spring rest length: 1.05 inches

<u>After 100 cycles</u>

Output force of jaw mechanism when fully open: 11.5N
Opening gap due to jaw due to spring rest length: 1.15 inches

*Conclusion for Next Iteration:* Opening gap increased by 0.1 inch and force decreased by 1N over 100 usage cycles. The springs we used for this prototype are too long and too prone to wear, so we will find shorter and more durable springs for the next prototype.
	
**Test Two:** 

*Part:* Handle/Trigger Assembly

*What it is Testing:* Ergonomics of the handle as well as the force required to squeeze the handle.

*How to Perform Test:* 
We first took images of a group member using the prototype in three different positions. One where they held the prototype upwards as if scraping egg masses from above, one straight in front, and one downwards. The RULA (Rapid Upper Limb Assessment) was completed. We used CUErgo (1) to guide us through the process of conducting this test, with our client feedback providing information we could use to estimate how long the user would be in each position.

*Test Results:* 

- Low position: scored a 3  
- Middle position: scored a 4  
- High position: scored a 4  
- Total RULA score: 3.9  
- Took over 40 pounds of force to squeeze handle when not perfectly aligned


![Shaded rendering of earlier version]({{ "/assets/images/RULA.jpg" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }

<p style="text-align:center; font-style:italic; margin-top:4px;">
Figure 3: RULA Calculations
</p>


*Conclusion for Next Iteration:* Our goal for this prototype was to get a RULA score below 5, which means that users will be at a low risk of MSD (musculoskeletal disorders) from our device (2). We calculated our prototype to have a total RULA score of 3.9, indicating low risk and achieving our goal of <5. For our next prototype, we aim to keep our score at or below 3.9. The handle and trigger will also be redesigned because the rail system often jams, causing the trigger to be stuck even for large squeezing forces.

**Test Three:** 

*Part:* Jaw-Trigger-String connection

*What it is Testing:* Effectiveness of the assembly at opening the jaw wide enough.

*How to Perform Test:* 
Using the assembled prototype, pull the trigger as far as possible and measure the opening distance of the jaw. Then, compare this height with the average size of an SLF egg mass.

*Test Results:* 

- Measured opening distance: 1.95 inches
- Measured rest length opening: 1.05 inches
- Egg masses are roughly 1.5 inches long. (3)

*Conclusion for Next Iteration:* We need to increase the amount the trigger pulls the lid upwards. The hinge and design allows the distance needed but the trigger is not currently able to pull it anywhere close to its maximum height. Due to limitations in the range of motion of a human hand, it will likely need to be redesigned to amplify the motion of a typical person's range of motion in their hand.


### Outcome

The prototype successfully proved that the core concept works, but it also made the main issues pretty clear.

The jaw system was able to generate enough force to scrape and remove material, and it held up reasonably well over repeated use. That said, performance dropped slightly after cycling, with a small loss in force and an increase in the resting gap. This points to the springs being a weak point, so they will need to be shorter and more durable in the next version.

The handle and trigger setup met the ergonomic target, with a RULA score of 3.9, so it is low risk for users. However, the force required to operate it was too high in real use, especially when the mechanism was not perfectly aligned. The jamming in the rail system is a major usability issue and needs to be fixed.

The jaw opening test showed that the mechanism can open wide enough in theory, but the trigger does not currently pull it far enough in practice. This limits its ability to reliably capture egg masses. The motion needs to be amplified so a normal hand movement can fully actuate the jaw.

Overall, the prototype validates the design direction, but key mechanical issues remain. The next iteration will focus on improving spring selection, reducing trigger force and jamming, and increasing jaw travel through a better linkage design.


### References

1. Hedge, Alan. CUergo: RULA. Cornell University, https://ergo.human.cornell.edu/ahRULA.html. Accessed 23 Mar. 2026.

2. Ergonomics Plus: A Step-by-Step Guide: Rapid Upper Limb Assessment (RULA), https://ergo-plus.com/wp-content/uploads/RULA-A-Step-by-Step-Guide1.pdf. Accessed 23 Mar. 2026.

3. University of Rhode Island Biocontrol Lab. Biocontrol of Insects: Spotted Lanternfly: Identification and Life Cycle, https://web.uri.edu/biocontrol/projects/slf-identification-and-life-cycle/. Accessed 23 Mar. 2026.
