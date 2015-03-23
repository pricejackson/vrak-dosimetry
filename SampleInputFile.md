#Sample Text file used for VRAK input

# Introduction #

This is where the user will define the path to input and output files along with the image time (in hours post-injection)

VRAK input files are read into the program as lines of python code. Stylistically this is asking for a variable to be defined and assigned a string value.
Example:
```
image1='/path/to/image1.mhd'
```

Here is a list of required and optional input parameters:
  * isotope (currently 'Lu177' or 'Y90' accepted)
  * image1
  * image2
  * image3 (optional)
  * output\_pk (optional)
  * output\_activity
  * output\_dose


A sample input file:
```
isotope='Lu177'
image1='/home/data/SPECT1/result.mhd'
image2='/home/data/SPECT2/result.mhd'
image3='/home/data/SPECT3/result.mhd'
output_pk='/home/data/kinetics.npy'
output_activity='/home/data/cumulated_activity.mhd'
output_dose='/home/data/dose_estimate.mhd'
```