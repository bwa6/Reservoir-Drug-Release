# Reservoir-Drug-Release
Simulation of drugs diffusion through a degradable carrier inside a reservoir with channels of varying length/width

This project was initially performed via MATLAB and published during my Ph.D. research:
Allen, B., et al., Modulating antibiotic release from reservoirs in 3D-printed orthopedic devices to treat periprosthetic joint infection. J Orthop Res, 2020.
Since publication, this project represents a more efficient simulation using Python.

Brief Biomedical Background
Periprosthetic joint infection is a costly debilitating affliction following total joint arthroplasty. Despite a relatively low incidence rate, periprosthetic joint infection is an increasing problem due to a substantial increase in arthroplasty surgeries over time. The current treatment is replacing the primary implant with a temporary bone cement spacer that releases antibiotics over time. However, the spacer is mechanically weak with an ineffective antibiotic release. Alternatively, three‐dimensional (3D)‐printed reservoirs in high‐strength devices have the potential to release antibiotics long term in a controlled manner. 3D‐printed reservoirs were loaded with calcium sulfate (carrier) embedded with gentamicin (drug). In vitro antibiotic release is tuned by varying reservoir parameters, such as channel length, diameter, and quantity. A straightforward model implemented in Python effectively fits and predicts cumulative release to rapidly design devices with a preferred release profile. Overall, this study highlights a novel approach to potentially develop high‐strength joint implants with the long‐term effective release of antibiotics to treat the periprosthetic joint infection.

Code Explanation
In this model, I simulate reservoirs in a 3D numpy array where the values in the array determine the real-world identity, which consists of reservoir material, degradable carrier containing drug, and exits to the surroundings.  Numerous antibiotics have an initial location in this reservoir array and "diffuse" via a random walk, moving randomly to adjacent locations in the array.  The antibiotics diffuse until reaching a location in the array that is designated as an exit to the surroundings.  The exits to the surroundings are at the center of the edges of the 3D array.  At the center of these faces are channels with varying diameter and length to tune drug release.  The time of a single iteration of a random walk is based on a diffusion rate constant, which increases exponentially over time according to a bulk degradation rate constant.  The theory is that the carrier is experiencing bulk degradation, which will expedite diffusion, causing an increase in the diffusion rate constant as the carrier degrades.  In addition to bulk degradation, the carrier experiences surface erosion.  This means that the exits to the surrounding shift inward as the inteface between the carrier and the surouundings is eroded, according to a surface degradation rate constant.  Therefore, there are three rate constants that need to be determined to fit drug release data obtained during my Ph.D. research.

Conclusion
The simulation revealed a fairly accurate prediction of antibiotic release with varying channel diameter after determining an optimal fit of the three rate constants.  This code offers an opportunity to test different the effect of channel diameter, length, quantity, and other complex reservoir features on antibiotic release.  The model makes numerous assumptions on how the rate constants should be configured that may not necessarily be accurate.  However, this code offers the framework to test other configurations of rate constants to test the ability to predict drug release from reservoirs.  See my publication for a more detailed look at the findings from this code as well as a greater understanding of the biomedical implications of this project.

