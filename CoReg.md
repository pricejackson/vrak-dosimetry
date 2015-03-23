#Tab for batch Running Elastix

# Registration Tab #

Batch image registration and warping is one of the helpful functionalities of VRAK. Elastix/Transformix is the command-line program that does all the leg work. However, it can be quite time-consuming when used to manually align and resample fused PET/CT or SPECT/CT images (particularly to an unfamiliar user). The VRAK batch registration takes care of the following steps:
  * Rigidly Register CT images
  * Deformably Register CT images
  * Warp Fused SPECT/PET images
  * Resample SPECT/PET images to 3mm cubic voxels (as mhd+raw filetype)
  * Rename images to user-selected values (mhd+raw files & edit _'ElementDataFile'_ flag in mhd header)
  * Autopopulates image paths in the _Dosimetry Input_ tab

Co-registration of 3 image volumes can require a lot of processing time. Don't be surprised if it takes an hour or more.

![https://vrak-dosimetry.googlecode.com/files/vrk_coreg.jpg](https://vrak-dosimetry.googlecode.com/files/vrk_coreg.jpg)