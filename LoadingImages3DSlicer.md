#Slicer is my preferred image viewer.

# Introduction #

[3D Slicer](http://www.slicer.org/) is a robust medical image viewing program. It's not always the most intuitive, but its open-source, handles most any medical image format, and comes with a number of built-in plugins that may be helpful depending on your application. Just as an aside, large image sets may load and scroll slowly on computers without a dedicated graphics card.

Here is a brief guide to loading up the .mhd/.raw output images produced by VRAK:


# Details #

  * Click 'Add Data': Either in file menu or on toolbar
![http://vrak-dosimetry.googlecode.com/files/add_data.png](http://vrak-dosimetry.googlecode.com/files/add_data.png)




  * Select 'Choose File(s) to Add' and select the appropriate .mhd file in the dialog that appears.
![http://vrak-dosimetry.googlecode.com/files/open_dialog.png](http://vrak-dosimetry.googlecode.com/files/open_dialog.png)




  * Images are loaded in grayscale by default. To use a colour look-up table for functional (PET/SPECT) images, select 'Volumes' in the Module dropdown list. Then in the volume Panel, select the appropriate active volume and choose a colour LUT from the dropdown.
![http://vrak-dosimetry.googlecode.com/files/Colour_LUT.png](http://vrak-dosimetry.googlecode.com/files/Colour_LUT.png)




  * Load up both PET and CT volumes in the viewing window. To see the full viewing options you may have to click first on the small arrow (just left of the R shown below), and then on the double arrow just below that. From there you can choose the desired foreground & background volumes. Volume opacity (mix) is also adjusted here.
![http://vrak-dosimetry.googlecode.com/files/Overlay_fg_bg.png](http://vrak-dosimetry.googlecode.com/files/Overlay_fg_bg.png)




There you have it, your images should be ready to view.
More detailed Slicer tutorials are available [here](http://www.slicer.org/slicerWiki/index.php/Documentation/4.0/Training#Introduction:_Slicer_4.0_Tutorials) and [here](http://www.slicer.org/slicerWiki/index.php/Slicer_3.6:Training).

Ultimately, most users will probably just want to segment their images to get measures of absorbed dose to lesions and sensitive organs. Have a look through this guide to using the [Slicer Interactive Editor](http://www.slicer.org/slicerWiki/images/6/69/InteractiveEditorTutorial_Slicer3.6-SoniaPujol.pdf).