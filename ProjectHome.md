![https://vrak-dosimetry.googlecode.com/files/vrk_doseInput.jpg](https://vrak-dosimetry.googlecode.com/files/vrk_doseInput.jpg)


## Update 15 Oct 2013 ##
Version 1.92 features improved kinetics fitting for 3 phase model (3 input timepoints).
Manuscript describing version 1.0 using 177-Lu is now available online [Med. Phys. 40, 112503 (2013)](http://dx.doi.org/10.1118/1.4824318)


Presented at RSNA 2012: [Automated Software Framework for Voxelized Absorbed Dose Estimation in Radionuclide Therapy](http://vrak-dosimetry.googlecode.com/files/RSNA-VRAK_Slides_compressed.pptx). _P Jackson, JM Beauregard, T Kron, MS Hofman, R Hicks_

# VRAK : Voxelized Registration and Kinetics #



### Overview ###
This program performs dosimetric calculations on sequential PET/CT or quantitative SPECT/CT images in radionuclide therapy. The basic methodology emulates organ-wise dosimetry using OLINDA/MIRD techniques, however pharmacokinetics and radiation transport are estimated at a voxel level. Input files are included to perform non-rigid alignment of image volumes with Elastix (built around ITK). Post-processing routines (kinetics and dose estimation) are written in [Python v2.7](http://www.python.org/download/releases/2.7/) with some numerical ([NumPy](http://www.scipy.org/Download)) and graphical ([PyQt4](http://www.riverbankcomputing.com/software/pyqt/download)) utilities. Output is written as ITK filetype (.mhd + .raw). I recommend [3D slicer](http://download.slicer.org/) for viewing VRAK output files.
Windows users can download the self-contained executable that includes all the dependencies. Linux users or people with python already installed may want to download the source version.

Update 3 June 2013: Version 1.91 is now available. Fixed a bug decay-correcting images that was producing inaccurate quantitation. Runs at slightly higher resolution (3mm cubic voxels). This can require 4+ GB RAM when convolving dose VSVs.


Check the [wiki](https://code.google.com/p/vrak-dosimetry/wiki/HomePage) section for more detailed documentation. It has been updated to reflect the current version. In spite of the update, the program should probably still be considered a beta release. If you are unsure of how it will handle your images and how it can be validated for your datasets just send an email and I'll try to help out.
-Price [(SITE)](https://sites.google.com/site/pjmedphys/)



### Acknowledgement: ###


The Voxelized Registration and Kinetics software  ("VRAK") has been developed with the support of the Victorian Government through the Victorian Cancer Agency Lutetium Therapy Grant for the [Molecular Imaging and Targeted Therapeutics Group](http://www.petermac.org/Research/MolecularImagingandTargetedTherapeutics) at [Peter MacCallum Cancer Centre](http://www.petermac.org/) in Melbourne, Australia.


Peter MacCallum Cancer Centre is the owner of the copyright in VRAK.


### Disclaimer: ###


The source code is distributed freely and without any warranty whatsoever.  VRAK must be installed and used at the risk of the user.


VRAK is intended for educational, research and informational purposes only and may be used only for such purposes and may not under any circumstances whatsoever be used for clinical or diagnostic purposes (ie for treatment planning, risk assessment).