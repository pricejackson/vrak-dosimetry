#Guide to program syntax (for those interested in development)


## Introduction ##

VRAK is written as a Python script. The program itself basically steps through the code line-by-line to read the command line arguments, import the image files, and write the output files. Other than that there is a single 'for' loop to iterate voxel-by-voxel through the image processing and a few functions located in separate module (class) files. It is certainly not sophisticated code. It mainly involves manipulating image data numerical arrays. If you have spent any time scripting in Matlab, this type of programming should seem familiar.


## Details ##

# NumPy arrays #
A python class of n-dimensional matrices. Most mathematical operations are handled efficiently. Memory and casting is handled automatically. When image files are read into VRAK, data is stored as 3-dimensional `float` NumPy arrays using a version of Bing Jian's mhd\_utils function.
```
import mhd_utils_2 as mu #Import class module
data_array, meta_header = mu.load_raw_data_with_mhd(image.mhd) #read in meta header and image data
dimensions= [int(i) for i in meta_header['DimSize'}.split()] #next 3 lines correct for 3D array
dimensions.reverse()
data_array=data_array.reshape(dimensions)
```
This can all be typed line-by-line into the python interpreter. To check that your data\_array has the correct voxel dimensions use:
`data_array.shape`

would return

`(z, y, x) # the dimensions of your input image volume`