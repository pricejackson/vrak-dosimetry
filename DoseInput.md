#Dose Input Tab

This tab selects all of the input data for processing kinetics and dosimetry. Here users can select either 2 or 3 input images. Depending on the number of images, VRAK will fit 2- or 3-phase exponential uptake & clearance curves to each voxel. If you have used the registration function in the previous tabs, all of the voxels will be resampled as aligned 5mm cubes. This is **very important**. At this point, the images are read in as 3D matrices of intensity values. It is assumed that they are already correctly aligned.

You must input the time post-injection of each image. The **imaging isotope** box is used for decay-correcting the images prior to kinetics fitting. The **Dosimetry Isotope** box is used for integrating cumulated activity and then convolving dose with VSVs.

The software was calibrated for long half-life therapeutic isotopes. There are some assumptions given to the curve-fitting routine that prevent overestimation of dose by limiting the rate constant of the uptake phase. It may not be appropriate to apply these assumptions to short half-life isotopes.

![https://vrak-dosimetry.googlecode.com/files/vrk_doseInput.jpg](https://vrak-dosimetry.googlecode.com/files/vrk_doseInput.jpg)