#Installation instructions

# Installation #


VRAK is executed as a high-level Python script with the mathematical backend NumPy. Windows users can download an _.exe_ version that includes all the Python dependencies. Linux users or anyone wanting to use the source version will need Python 2.7, NumPy, SciPy and PyQt4 (links on the homepage).
To check whether these are already installed, open the python interpreter and try the command:
```
import numpy, scipy, PyQt4
```
If there are no errors, VRAK should run without any further installation.


Everyone will need to download Elastix to perform image registration and resampling.
Once everything has been downloaded, load up VRAK and set the paths to the Elastix and Transformix executables on the 'Configure' tab.

  * Download & extract Elastix (Binaries should be fine, don't need to compile from source)
  * Download Python 2.7, NumPy, PyQt4 (if necessary)
  * Extract VRAK to a desired location
  * Run VRAK.exe, VRAK, or VRAK.py (depending on your distribution)
  * On first run, click on 'configure' tab, find the paths for Elastix and Transformix & click save

![https://vrak-dosimetry.googlecode.com/files/vrk_config.jpg](https://vrak-dosimetry.googlecode.com/files/vrk_config.jpg)

last edited 5 March 2013