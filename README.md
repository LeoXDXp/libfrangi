libfrangi
=========

C++/OpenCV implementation of the Frangi multiscale vesselness filter in 2D (reference:
A. F. Frangi, W. J. Niessen, K. L. Vincken, and M. A. Viergever, “Multiscale vessel enhancement filtering,”
in Proc. Med. Image. Comput. Assist. Interv. 1496, pp. 130–137 (1998)).

This code is based on a MATLAB implementation found at [MATLAB Central](http://www.mathworks.com/matlabcentral/fileexchange/24409-hessian-based-frangi-vesselness-filter). 

Basic usage
-----------

Include `frangi.h`. Create a variable `frangi2d_opts_t opts`. Set each field
to desired values or use `frangi2d_createopts(&opts)` for default values. 

Load the image into a `cv::Mat` instance. Create `cv::Mat` instances
for Frangi filter outputs: `J`, `scale` and `directions`. The 2D Frangi
filter can then be applied as `frangi2d(img, J, scale, directions, opts)`.

Building and installing with Cmake
-----------------------

1. `mkdir build`
2. `cd build`
3. `cmake ..`
4. `make`
5. `make install`

Manual Building and installing
----------------------------

1. `cd src`
2. `g++ -c -Wall -pedantic -fpic `pkg-config --cflags --libs opencv4` frangi.cpp`
3. `gcc -shared -o libfrangi.so frangi.o`
4. `cp libfrangi.so /usr/local/lib/`  (Remember to add /usr/local/lib/ to the LD_LIBRARY_PATH if neccesary)
5. `g++ main.cpp -o main -Wall -pedantic -L/usr/local/lib/ -lfrangi  -I../src/ `pkg-config --cflags --libs opencv4` ` (if LD_LIBRARY_PATH includes /usr/local/lib/, you can delete the -L parameter)

Requirements
------------

* OpenCV >= 2.3
