# Introduction #

Running this software requires two command-line calls:
  * Elastix Registration
  * VRAK command

Elastix takes care of registering images and essentially converting to aligned numerical arrays. VRAK processes the image arrays and integrates the number of disintigrations for each voxel:
  * Open image data as numpy matrices
  * zero 'low-activity' voxels
  * decay-correct based on time post-injection and physical halflife
  * iterate through volume with curve fitting routine
  * integrate # of decays based on physical half-life
  * write output cumulated activity image volume (& optionally kinetics array)
At the moment, dose convolution would only be available for very specific isotopes and voxel dimensions. If radionuclide decay yields long-range particles, it may be necessary to create a new dose convolution kernel (via Monte Carlo). Otherwise, direct voxel S-values may suffice. A reasonable approach to this functionality will be adressed with future releases.
  * Dose convolution (voxelized dose kernel)
  * Write Output absorbed dose image volume
Optional:
  * Call VRAK\_VID: visual output of interpolated kinetics for given tomographic slice (activity & cumulated activity)


![http://vrak-dosimetry.googlecode.com/files/flowchart_image.png](http://vrak-dosimetry.googlecode.com/files/flowchart_image.png)
Note: Dose convolution is now functional (I just haven't updated the flow chart)