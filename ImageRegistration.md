# Introduction #

VRAK has currently been developed using [Elastix](http://elastix.isi.uu.nl/index.php) to perform sequential rigid and deformable registration. In my experience, the registration results are good and most importantly free from artefacts. From a workflow perspective, Elastix is convenient because it allows warping of SPECT/PET volumes based on CT registration such that the output images are all written with the same voxel dimensions and origin location; avoiding the need to resample images before importing as data arrays. Registered images are written in ITK format [mhd+raw](http://www.itk.org/Wiki/ITK/File_Formats). You may prefer to use another registration package (plastimatch or ITK itself, for example). Many support writing images as in .mhd format. Originally, VRAK was written with dicom compatibility based on [pydicom](http://code.google.com/p/pydicom/). If requested, I can add it back into the program.




# Details #

Elastix is called from the command line with arguments of fixed & moving image paths and the location of a text file containing the registration parameters (Type, optimisation, metric, resolution, output filetype, etc).

```
elastix -f fixed_image.dcm -m moving_image.dcm -out output_folder/ -p parameter_file.txt
```

Transformix, used for warping functional images, is called similarly:

```
transformix -in moving_functional_image.dcm -tp deformation_map.txt -out output_folder/
```

From the command line, this can all be scripted. The process for doing deformable registration with two CT images and resampling the corresponding functional (PET/SPECT) images is:
  1. Null Deformation of fixed CT
  1. Resample fixed SPECT to CT dimensions
  1. Rigid registration of moving CT to fixed CT
  1. Deformable registration of moving CT to fixed CT
  1. Warp moving SPECT to fixed CT

A linux shell script to do this might be:

```
#create output folder
mkdir CT1

#run elastix with 0 iterations to create a null deformation map (for resampling SPECT1 to correct dimensions)
elastix -f CT1.dcm -m CT1.dcm -out CT1/ -p null_deform.txt

#create output folder for resampled SPECT1
mkdir SPECT1

#resample SPECT with CT1 (fixed volume) dimensions
transformix -in SPECT1.dcm -tp CT1/TransformParameters.0.txt -out SPECT1/



#rigid registration CT2
mkdir CT2rigid
elastix -f CT1.dcm -m CT2.dcm -out CT2rigid/ -p rigid_param.txt

#deformable registration CT2
mkdir CT2
#call deformable registration routine with using initial rigid registration (t0). Note: rigid registration is automatically written into deformation map
elastix -f CT1.dcm -m CT2.dcm -out CT2/ -p def_param.txt -t0 CT2rigid/TransformParameters.0.txt

#Warp SPECT #2 to fixed CT (CT1)
mkdir SPECT2
transformix -in SPECT2.dcm -tp CT2/TransformParameters.0.txt -out SPECT2/

```

Or in windows:

```

mkdir CT1

elastix.exe -f CT1.dcm -m CT1.dcm -out CT1/ -p null_deform.txt

mkdir SPECT1

transformix.exe -in SPECT1.dcm -tp CT1/TransformParameters.0.txt -out SPECT1/



mkdir CT2rigid
elastix.exe -f CT1.dcm -m CT2.dcm -out CT2rigid/ -p rigid_param.txt


mkdir CT2
elastix.exe -f CT1.dcm -m CT2.dcm -out CT2/ -p def_param.txt -t0 CT2rigid/TransformParameters.0.txt

mkdir SPECT2
transformix.exe -in SPECT2.dcm -tp CT2/TransformParameters.0.txt -out SPECT2/

```



Note: sample parameter files [null\_deform.txt](http://vrak-dosimetry.googlecode.com/files/null_deform.txt), [rigid\_param.txt](http://vrak-dosimetry.googlecode.com/files/rigid_param.txt), & [def\_param.txt](http://vrak-dosimetry.googlecode.com/files/def_param.txt) are contained in the [downloads](http://code.google.com/p/vrak-dosimetry/downloads/list) section

output will be written to CT1/result.mhd, CT1/result.raw, etc.
If renaming, be sure to change the 'ElementDataFile' flag in the .mhd metafile (can be done with a text editor):
```
ElementDataFile = newname.raw
```