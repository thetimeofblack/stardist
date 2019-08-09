# *StarDist* - Object Detection with Star-convex Shapes 

<!-- ![](https://github.com/mpicbg-csbd/stardist/raw/master/images/stardist_overview.png) -->
![](images/stardist_overview.png)

This repository contains the implementation of star-convex object detection for 2D and 3D images, as described in the papers: 

<img src="images/stardist_logo.jpg" title="siân is the king of the universe" width="25%" align="right">

- Uwe Schmidt, Martin Weigert, Coleman Broaddus, and Gene Myers.  
[*Cell Detection with Star-convex Polygons*](https://arxiv.org/abs/1806.03535).  
International Conference on Medical Image Computing and Computer-Assisted Intervention (MICCAI), Granada, Spain, September 2018.

- Martin Weigert, Uwe Schmidt, Robert Haase, Ko Sugawara, and Gene Myers.  
[*Star-convex Polyhedra for 3D Object Detection and Segmentation in Microscopy*](TBD).  
arXiv, 2019

Please [cite the paper(s)](#how-to-cite) if you are using this code in your research.


### 2D
![](images/overview_2d.png)

### 3D
![](images/overview_3d.png)


## Installation

This package requires Python 3.5 (or newer) and can be installed with `pip`:

    pip install stardist

### Notes

- Depending on your Python installation, you may need to use `pip3` instead of `pip`.
- Since this package relies on a C++ extension, you could run into compilation problems (see [Troubleshooting](#troubleshooting) below). We currently do not provide pre-compiled binaries.
- StarDist uses the deep learning library [Keras](https://keras.io), which requires a suitable [backend](https://keras.io/backend/#keras-backends) (we currently only support [TensorFlow](http://www.tensorflow.org/)).
- (Optional) You need to install [gputools](https://github.com/maweigert/gputools) if you want to use OpenCL-based computations on the GPU to speed up training.
- (Optional) You might experience improved performance during training if you additionally install the [Multi-Label Anisotropic 3D Euclidean Distance Transform (MLAEDT-3D)](https://github.com/seung-lab/euclidean-distance-transform-3d).


## Usage

We provide several Jupyter [notebooks](https://github.com/mpicbg-csbd/stardist/tree/master/examples) that illustrate how this package can be used.

![](https://github.com/mpicbg-csbd/stardist/raw/master/images/example_steps.png)


## Troubleshooting

Installation requires Python 3.5 (or newer) and a working C++ compiler. We have only tested [GCC](http://gcc.gnu.org) (macOS, Linux), [Clang](https://clang.llvm.org) (macOS), and [Visual Studio](https://visualstudio.microsoft.com) (Windows 10). Please [open an issue](https://github.com/mpicbg-csbd/stardist/issues) if you have problems that are not resolved by the information below.

If available, the C++ code will make use of [OpenMP](https://en.wikipedia.org/wiki/OpenMP) to exploit multiple CPU cores for substantially reduced runtime on modern CPUs. This can be important to prevent slow model training.


### macOS
Although Apple provides the Clang C/C++ compiler via [Xcode](https://developer.apple.com/xcode/), it does not come with OpenMP support.
Hence, we suggest to install the OpenMP-enabled GCC compiler, e.g. via [Homebrew](https://brew.sh) with `brew install gcc`. After that, you can install the package like this (adjust names/paths as necessary):

    CC=/usr/local/bin/gcc-8 CXX=/usr/local/bin/g++-8 pip install stardist


### Windows
Please install the [Build Tools for Visual Studio 2019](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2019) from Microsoft to compile extensions for Python 3.5 and newer (see [this](https://wiki.python.org/moin/WindowsCompilers) for further information). During installation, make sure to select the *C++ build tools*. Note that the compiler comes with OpenMP support.

## How to cite 

``` 
@inproceedings{schmidt2018,
  author    = {Uwe Schmidt and Martin Weigert and Coleman Broaddus and Gene Myers},
  title     = {Cell Detection with Star-Convex Polygons},
  booktitle = {Medical Image Computing and Computer Assisted Intervention - {MICCAI} 
  2018 - 21st International Conference, Granada, Spain, September 16-20, 2018, Proceedings, Part {II}},
  pages     = {265--273},
  year      = {2018},
  doi       = {10.1007/978-3-030-00934-2_30},
}
```
