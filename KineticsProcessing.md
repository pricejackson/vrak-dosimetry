# Introduction #

VRAK imports serial functional images as matrices and iterates through image volumes voxel-by-voxel with a 2- or 3-phase exponential pharmacokinetic curve fitting routine. In this initial build, output is given as a cumulated activity image where voxel intensity represents the quantity of disintigrations per unit volume (as Bq\*hours/mL; assuming input images are correctly quantified in units Bq/mL)

Prerequisites:
[python 2.7](http://www.python.org/download/releases/2.7/)
[numpy](http://www.scipy.org/Download)

# Details #

Software will process either 2- or 3-timepoint serial PET or quantitative SPECT images. Co-registered images (see [Elastix Image Registration](ImageRegistration.md) section should be written in .mhd/.raw filetype. VRAK is called from the command line requiriing only the path to input images, isotope half-life (in hours), and output path (for image volume and optionally NumPy array of fit parameters).

```
usage: VRAK.py [-h] -halflife HALFLIFE -t1 T1 -t2 T2 [-t3 T3] -im1 IM1 -im2
                 IM2 [-im3 IM3] [-k_out K_OUT] -act ACT_OUT

VRAK nuclear medicine kinetics and dosimetry software

optional arguments:
  -h, --help          show this help message and exit
  -halflife HALFLIFE  Physical halflife of radionuclide in hours (ie
                      Lu-177=161.04)
  -t1 T1              image #1 time post-injection (in hours)
  -t2 T2              image #2 time post-injection (in hours)
  -t3 T3              [optional] image #3 time post-injection (in hours)
  -im1 IM1            path to registered PET/SPECT image #1 .mhd
  -im2 IM2            path to registered PET/SPECT image #2 .mhd
  -im3 IM3            [optional] path to registered PET/SPECT image #3 .mhd
  -k_out K_OUT        [optional]path for output (.npy) NumPy kinetics array [z,y,x,p]
                      p=4/6 (depending on 2 or 3 image input)
  -act ACT_OUT        output cumulated activity image volume (.mhd)
```


For example:

```
VRAK.py -halflife 161.04 -t1 4 -t2 48 -im1 image1.mhd -im2 image2.mhd -k_out kinetics.npy -act im_out.mhd
```

would run VRAK using two coregistered images (image1.mhd & image2.mhd) acquired at 4 and 48 hours for an isotope with 161 hour half-life (Lu-177). The output image (im\_out.mhd + im\_out.raw) contains an estimate of the number of disintigrations in each voxel using the interpolated 2-phase biexponential (1 uptake + 1 clearance) pharmacokinetics. Optionally, the fit parameters for each voxel are saved in a numpy array (kinetics.npy). That array can be loaded into the Python IDLE for manual data analysis or used to make a video slide show of interpolated activity (though not yet available in the general release). Be warned, kinetics files can be quite large (1-2 Gb).

If 3 images and timepoints are supplied at runtime, VRAK will use a 3-phase tri-exponential fitting routine (1 uptake + 2 clearance).

This software was originally written for serial timepoints in the range of 4-72 hours and isotopes with half-lives of several days. It may be necessary to adjust the conditioning or bounds of the PK routine to suit other research scenarios.