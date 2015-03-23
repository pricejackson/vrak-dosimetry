#Allows users to adjust deformable registration parameters

VRAK will auto-generate Elastix input text files when doing batch registration. Deformable registration is set up for 2 resolutions. Users can adjust some of the settings on the _Registration Parameters_ tab. Elastix is slower many other deformable registration programs, however it's alignment is usually free from artefacts. If it is taking too long or consuming too much memory, it may be useful to either lower the number of **iterations** or increase the **Voxel Binning** values. Adjusting the weight of the **bending energy penalty** (between 0.0 and 1.0) may fix unnatural deformation artefacts.

The default settings on this tab should give a good balance of efficiency & accuracy.

![https://vrak-dosimetry.googlecode.com/files/vrk_reg_params.jpg](https://vrak-dosimetry.googlecode.com/files/vrk_reg_params.jpg)