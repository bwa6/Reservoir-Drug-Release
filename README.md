# Reservoir-Drug-Release
Simulation of drugs diffusion through a degradable carrier inside a reservoir with channels of varying length/width

This project was initially performed via MATLAB and published during my Ph.D. research:
Allen, B., et al., Modulating antibiotic release from reservoirs in 3D-printed orthopedic devices to treat periprosthetic joint infection. J Orthop Res, 2020.
This project is a faster, more efficient version using Python that was created since publication.

Brief Biomedical Background:

Periprosthetic joint infection is a costly debilitating affliction following total joint arthroplasty. Despite a relatively low incidence rate, periprosthetic joint infection is an increasing problem due to a substantial increase in arthroplasty surgeries over time. The current treatment is replacing the primary implant with a temporary bone cement spacer that releases antibiotics over time. However, the spacer is mechanically weak with an ineffective antibiotic release. Alternatively, three‐dimensional (3D)‐printed reservoirs in high‐strength devices have the potential to release antibiotics long term in a controlled manner. 3D‐printed reservoirs were loaded with calcium sulfate (carrier) embedded with gentamicin (drug). In vitro antibiotic release is tuned by varying reservoir parameters, such as channel length, diameter, and quantity. A straightforward model implemented in Python effectively fits and predicts cumulative release to rapidly design devices with a preferred release profile. Overall, this study highlights a novel approach to potentially develop high‐strength joint implants with the long‐term effective release of antibiotics to treat the periprosthetic joint infection.

Code Explanation:

In this model, I simulate reservoirs in a 3D numpy array where the values in the array determine the real-world identity, which consists of reservoir material, degradable carrier containing drug, and exits to the surroundings.  Numerous antibiotics have an initial location in this reservoir array and "diffuse" via a random walk, moving randomly to adjacent locations in the array.  The antibiotics diffuse until reaching a location in the array that is designated as an exit to the surroundings.  The exits to the surroundings are at the center of the edges of the 3D array.  At the center of these faces are channels with varying diameter and length to tune drug release.  The time of a single iteration of a random walk is based on a diffusion rate constant, which increases exponentially over time according to a bulk degradation rate constant.  The theory is that the carrier is experiencing bulk degradation, which will expedite diffusion, causing an increase in the diffusion rate constant as the carrier degrades.  In addition to bulk degradation, the carrier experiences surface erosion.  This means that the exits to the surrounding shift inward as the inteface between the carrier and the surouundings is eroded, according to a surface degradation rate constant.  Therefore, there are three rate constants that need to be determined to fit drug release data obtained during my Ph.D. research.

Data Visualization:

Using the simulation, I varied parameters of the model including channel diameter and length and the three rate constants.  Slowing the diffusion of the antibiotic shifts the curve to the right.  Antibiotics with a larger molecular weight would likely have a slower diffusion rate constant.  The inital slow release of the 'sigmoid-shaped' curve is controlled by the surface erosion rate constant.  Increasing the bulk degradation constant steepens the slope of the curve as the antibiotics are able to diffuse faster.  There are numerous biodegradable carriers with a wide range of degradation properties that enable tuning of these rate constants.  Decreasing channel diamter shifts the curve to the right as antibiotics have a harder time releasing from narrower channels.  increasing the length of the channels extends the inital slow release of the sigmoid-shaped curve.  Importantly, a large diameter and large length result in an approximately linear cumulative release curve that would be optimal for treating infections with constant, long-term release.

Conclusion:

The simulation revealed a fairly accurate prediction of antibiotic release with varying channel diameter after determining an optimal fit of the three rate constants.  This code offers an opportunity to test different the effect of channel diameter, length, quantity, and other complex reservoir features on antibiotic release.  The model makes numerous assumptions on how the rate constants should be configured that may not necessarily be accurate.  However, this code offers the framework to test other configurations of rate constants to test the ability to predict drug release from reservoirs.  See my publication for a more detailed look at the findings from this code as well as a greater understanding of the biomedical implications of this project.

Notes:

'Location_pooled_fewerframes' is a gif of antibiotic release from reservoirs with a channel diamter of 10 and length of 9.  It is a 2D representation where the third dimension is compressed so that each pixel represents the total number of antibiotics located in that x,y coordinate regardless of its z position.  The pixels are pooled such that the dimension of the reservoir goes from 90x90 to 30x30 by summing neighboring 3x3 pixels.  Each frame represents every 6 random walks (file size is too large if every random walk is recorded).  In the video, the X-shaped pattern corresponds to the surface erosion occurring at the four channels, resulting in decreased density where the biodedgradable carrier has eroded.

'Location_pooled_fewerframes_35_40' is the same as the other gif except the channel diameter is 35 and length is 40.  This is the reservoir geometry that resulted in an approximately linear cumulative release.
