---
layout: project
title: ODP6 Client Report
description: Open Design Project Final
technologies: Fusion 360, 3D Printing
image: /assets/images/2250_sc2.png
permalink: /2250ODP_Storage/06_BuzzKill/
show_ODP: false
---

### Context and Problem Statement
We took on the challenge of controlling the egg masses of spotted lanternflies (SLF) as it was more efficient than targeting SLF in its adult stage. Individual egg masses contain 30-50 eggs, which can be laid on organic or inorganic surfaces, and can still hatch if scraped off the surface (1, 6). Current egg mass control strategies fail to ensure destruction or provide a reliable way to quantify egg mass management. Our challenge was to develop a mechanical system that ensures destruction of egg masses across various surfaces and enables growers to numerically analyze the system’s success. Our main constraints were making the device user-friendly, lightweight, easy to manufacture, and effective against large numbers of egg masses, which we analyzed by creating numerical testing protocols for each design driver. By combating the SLF invasion via egg masses, we are addressing the issue at its source rather than killing individual adult SLFs.

### Final Prototype and Application
Our final prototype consists of a device designed to easily remove SLF egg masses. The prototype weighs 3.6 kilograms, and is 1.5 metres long. All of the materials came from McMaster-Carr or were 3D printed/machined in the RPL/Taylor Design Studio. The features of the prototype include: 

- A scraping edge (jaw) optimized to match the adhesion of egg masses, allowing for more complete removal in a single pass.
- An ergonomic and adjustable handle system that gives users better control over force and angle, reducing fatigue and improving consistency.	
- A 25 cubic inch (410 cubic cm) bucket that captures the eggs as they are removed – estimated to hold 100 egg masses at once.
- A divider within the bucket that prevents already collected egg masses from falling out when collecting more egg masses and removable bucket to dispose of them.
- A pivoting head, to allow for removal from a variety of heights keeping the bucket-jaw assembly level.


![Shaded rendering of earlier version]({{ "/assets/images/componenets.png" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }

<p style="text-align:center; font-style:italic; margin-top:4px;">
Figure 1: Final Prototype and Components
</p>

![Shaded rendering of earlier version]({{ "/assets/images/bucket_jaw.png" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }

<p style="text-align:center; font-style:italic; margin-top:4px;">
Figure 2: Alternate View of Bucket
</p>

The user operates the prototype typically with a cross body orientation. First, the head angle is set to the correct position based on the height of the egg mass. The shoulder stock is then placed at their shoulder, and the handle is adjusted to the correct position for them to grab with their opposite hand. Then, the ‘pull handle’ is drawn back and set on the ‘pull handle lock’ to keep the jaw open. Then, the bucket is held up to position, and the ‘pull handle’ is pushed off the ‘pull handle lock’ to allow the jaw to snap closed. This effectively scrapes the egg mass off. Then, the divider is opened to allow the egg mass to fall into the basket, then the divider is closed again. This process is repeated for each egg mass collected. When the bucket has been filled, the basket can be pulled out to dispose of the collected egg masses. This offers effective, versatile, and quantifiable egg mass collection.

### Conclusion and Recommendation
The intended goal of the prototype was to efficiently collect egg masses while being comfortable for the user when reaching at a variety of heights. We achieved an average of 2.65 seconds per egg mass when collecting which is incredibly efficient considering current solutions that involve scraping with a credit card. The design performed favorably on the Rapid Upper Limb Assessment (RULA) scoring a 3.9 when a score of below 4 is desired to indicate an ergonomic design (2). Lastly, the generated force of the scraping jaw was 12.5N, which decreased by 8% to 11.5N after 100 cycles. 

The culmination of these tests indicated to us that the design is efficient and comfortable for a user, meeting our main two objectives; however, there are areas for improvement. For starters, we recommend that electronic components be implemented to open and close the jaw, pivot the head, and open and close the divider. These adjustments work to eliminate the issue of a loss in force as the springs wear out, and allow the design to be entirely adjusted from operating position– more user friendly. 

The amount spent was \$211.27 throughout the entire process, which came out to 39.6% under budget. Of that, only \$104.62 was spent on the final prototype, coming out to 29.9% of the budget. That cost further breaks down to be only \$29.30 on the 3D printed components, which can be drastically reduced if mass-produced with injection molding (3). 

We conclude that the prototype is worth pursuing further, as we think it has performed successfully as a proof of concept. We recommend the following changes for an industry-grade product: implement electronic motors to allow users to adjust bucket angle, open/close the jaw and divider from the operating position, and use a malleable material for the tooth to allow it to contour to the scraping surface.

### Testing and Results
- Took 53s to remove 20 simulated Play-Doh egg masses, averaging 2.65s per egg mass.
    - Egg mass removal efficiency is one of our success criteria and is vital to foster effective integration within farms. Conclude the device is efficient in egg mass removal.
- Jaw can open up to 87 mm at maximum extension.
    - Again, tested to ensure high removal efficiency. Conclude the device is sufficiently large to remove average SLF egg mass (50mm) in one scrape.
- Jaw clamping force of 12.5 N. After 100 cycles, an 8% decrease in force to 11.5 N was observed.
    - Clamping force is our second success criterion. We need sufficient scraping force to remove the egg mass. We have enough force, but greater than 5% force reduction – electric motor recommended.
- RULA (Rapid Upper Limb Assessment) score of 3.9 and weight less than 8lbs.
    - Comfortability is our third success criterion. Because the process is already somewhat manual, the device needs to be ergonomic for the user. A score below 4 is desirable – design is ergonomic.

### Prototype and Testing Details
To construct our final prototype, we cut the PVC pipe to size and drilled ¼ in holes at the desired locations to bolt the 3D printed components to the pipe and then thread the string through the pipe to connect the pull handle and jaw scraper. We created seven 3D printed components: latches, jaw, pivoting head attachment, handle, pull handle lock, shoulder stock, and bucket. These attachments were all created out of PLA. The components are attached by sliding onto the pipe and fastening with M6 and AN4 bolts. The divider, basket, and string catch were constructed out of cut balsa wood, sanded, and glued together. The latches, which hold the basket and divider shut when desired, were attached using M6 bolts. To construct the jaw assembly, we used M6 bolts to attach the hinge and then attached the springs with zip ties to the tabs inside the jaw.

When determining how much to cut the PVC pipe we performed a simple torque balance. In a study of 20 normal right handed males, the average peak torque they could produce in the full flexion shoulder movement (the relevant one of operations of the device) was 19.92 ft-lb (4). Estimating the weight of the bucket and 100 collected egg masses to weigh around 2.5 pounds gives us a maximum length of roughly 8 feet. Due to flex in the PVC pipe, we elected for a length of 3.5ft for the pipe, and 5ft for the entire design.


![Shaded rendering of earlier version]({{ "/assets/images/exploded.png" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }

<p style="text-align:center; font-style:italic; margin-top:4px;">
Figure 3: Exploded View of Prototype
</p>

The testing methods were developed based on prototype use and our success criteria. Play-Doh was used to simulate egg masses, about 1 in × 1 in × 0.5 in. To test the average time to remove an egg mass, we placed 20 egg masses at varying heights and timed how long it took to remove all of them. The 50 mm jaw opening requirement was based on the need to fit around and scrape an average egg mass in one motion. We tested this using a dial caliper to accurately measure the maximum opening distance.

The clamp force test came from observations that egg masses can be removed with a plastic card, meaning that the device did not need an extremely high force to work. We tested the clamp force using a spring scale at the teeth of the jaw. Our goal from the iterations was that after 100 cycles the force did not change by more than 5%, which our design failed, prompting our recommendations above. 

Lastly, CuErgo’s RULA XL testing was chosen because the device is used at different heights and body positions, so comfort is vital if growers were to implement the device in their vineyards. The score is derived from standardized calculations in many categories such as the weight and length of the device, percentage of time in different operating positions, and more (5). Other ergonomic considerations included average grip strength across demographics and force required to operate common garden tools (7, 8).

### References
1. J Keller, J Rost, K Hoover, J Urban, H Leach, M Porras, B Walsh, M Bosold, D Calvin. “Dispersion Patterns and Sample Size Estimates for Egg Masses of Spotted Lanternfly (Hemiptera: Fulgoridae),” Environmental Entomology, Volume 49, Issue 6, December 2020, Pages 1462–1472.https://doi.org/10.1093/ee/nvaa107

2. Ergonomics Plus: A Step-by-Step Guide: Rapid Upper Limb Assessment (RULA), https://ergo-plus.com/wp-content/uploads/RULA-A-Step-by-Step-Guide1.pdf. Accessed 23 Mar. 2026.


3. Naoum, Kat de and Rebecca Piccoli. 2025. “Injection Molding vs. 3D Printing: Differences and Comparison.” Xometrys RSS. Retrieved May 5, 2026 (https://www.xometry.com/resources/injection-molding/injection-molding-vs-3d-printing/).  
    
4. Soderberg, Gregory J., and M. J. Blaschak. “Shoulder Internal and External Rotation Peak Torque Production Through a Velocity Spectrum in Differing Positions.” Journal of Orthopaedic \& Sports Physical Therapy, vol. 8, no. 11, May 1987, pp. 518–24. DOI.org (Crossref),https://doi.org/10.2519/jospt.1987.8.11.518.


5. Hedge, Alan. CUergo: RULA. Cornell University, https://ergo.human.cornell.edu/ahRULA.html. Accessed 23 Mar. 2026.

6. Houping Liu, Oviposition Substrate Selection, Egg Mass Characteristics, Host Preference, and Life History of the Spotted Lanternfly (Hemiptera: Fulgoridae) in North America, Environmental Entomology, Volume 48, Issue 6, December 2019, Pages 1452–1468, https://doi.org/10.1093/ee/nvz123

7. Perna FM, Coa K, Troiano RP, Lawman HG, Wang CY, Li Y, Moser RP, Ciccolo JT, Comstock BA, Kraemer WJ. Muscular Grip Strength Estimates of the U.S. Population from the National Health and Nutrition Examination Survey 2011-2012. J Strength Cond Res. 2016 Mar;30(3):867-74. doi: 10.1519/JSC.0000000000001104. PMID: 26196662; PMCID: PMC7197498.

8. SELVİ Kemal Çağatay, KABAŞ Önder, KARATAŞ Mehmet. “FORCE REQUIREMENTS OF DIFFERENT MANUAL PRUNING SHEARS WHEN CUTTING ABELIA (ABELIA GRANDIFLORA) BRANCHES” 7th TAE 17-20 September 2019, Prague, Czech Republic, https://2019.tae-conference.cz/proceeding/TAE2019-085-Kemal-Ca\%C4\%9Fatay-Selvi.pdf

### Appendix
#### Handling Team Member Absences
During Allen’s absence, the team made sure to understand his progress in his role. Before his absence, the team used office hours to work on assembling our final prototype to get ahead before the lab section to ensure we would not fall behind schedule. This strategy let us ensure that no components of our prototype were missing and that we could focus on individual aspects of the prototype without Allen being present.

During Trevor’s absence, our team made sure to meet during the week before our presentation to rewrite and rehearse the elevator pitch with the adjustments made to fill in for his planned part. This let us make sure that our presentation was still able to go smoothly despite his absence. Furthermore, we informed him of the progress we made on the project so that he was up to speed upon his return. This provided a smooth transition.


#### Bill of Materials

![Shaded rendering of earlier version]({{ "/assets/images/BOM1.png" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }


![Shaded rendering of earlier version]({{ "/assets/images/BOM2.png" | relative_url }}){: style="display:block; margin-left:auto; margin-right:auto; max-width:400px; height:auto;" }