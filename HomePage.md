VRAK is a computer program that will iterate through serial PET or Nuclear Medicine images, calculating time activity curves in each voxel. From these estimates it is possible to deduce the number of disintigrations and radiation absorbed dose. VRAK was written for dosimetry of long half-life isotopes (Y-90, Lu-177). It uses 3mm Voxel S-Values calculated with [GATE](http://www.opengatecollaboration.org/) to convolve voxel self dose and dose to neighbours over a range of 10cm.


# Details #

Check the installation page for brief instructions on setting up the program. Performing dosimetry involves first co-registering functional images using CT volumes as a guide. Users can adjust deformable registration settings. It is also possible to estimate dosimetry for different diagnostic & therapeutic isotopes (i.e. dose for Lu-177 therapy based on In-111 imaging).




Credit goes to Bing Jian for writing _mhd\_utils_ (functions for importing and writing mhd/raw files) in [diffusion-mri](http://code.google.com/p/diffusion-mri/)