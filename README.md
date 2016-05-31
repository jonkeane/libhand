LibHand v0.9
Copyright (c) 2011, Marin Saric <marin.saric@gmail.com>
All rights reserved.

http://www.libhand.org/  -- the most up-to-date information on LibHand.

About LibHand
----------------------------------------

LibHand is an open-source permissively licensed portable library for
rendering and recognizing articulations of human hand. The goal of LibHand
is to provide as simple programming interface as possible to manipulate
human hand pose information, render a human hand and analyze the resulting
image. Potential scientific applications include Computer Graphics, Computer
Vision and Robotics.

LibHand is available at <http://www.libhand.org/>
Feel free to contact LibHand's author Marin Saric at: marin.saric@gmail.com

LibHand is implemented in C++ and offers a MATLAB interface to facilitate
experimentation. LibHand is currently actively supported for MacOS X and
Ubuntu Linux on 64-bit x86 processors.

By leveraging OGRE, a modern 3D engine, LibHand can render, deform and
analyze a realistic 70k+ triangle hand model at high framerates on mid-range
computer hardware.

LibHand provides OpenCV-friendly interfaces to make it very easy for the
Computer Vision and Robotics community to use it in their research. LibHand
is designed to make it easier to reproduce and extend.the research in areas
such as hand grasping, hand pose recognition, hand gesture recognition,
visual servoing, etc.

Additionaly LibHand provides a realistic Human Hand 3D model available in
Blender and OGRE formats under a very permissive license (see (6)).

The LibHand was inspired by concepts from recent research in human hand to
robot grasping, for example:

Installing
----------------------------------------

### Software dependencies
LibHand 0.9 was developed against following dependencies
- [OpenCV](https://en.wikipedia.org/wiki/OpenCV) (Open Source Computer Vision) v2.3.y
- [OGRE](https://en.wikipedia.org/wiki/OGRE) (Object Orientated Graphics Rendering Engine) v1.7.4
	- OpenGL headers (GL/glu.h)
- [Tcl/Tk](https://en.wikipedia.org/wiki/Tcl) (likely v8.5.y)
- [CMake](https://en.wikipedia.org/wiki/CMake) v2.8.6

Please see the (deprecated) INSTALL.txt file for the old, out-of-date static
compilaton instructions for Ubuntu 11.10, MacOS X Mavericks (via MacPorts
and Homebrew) and Matlab bindings.

#### Satisfying software dependencies under Debian/Ubuntu
The following instructions allow compilation of libhand without too much trouble on all supported versions on Debian/Ubuntu, and has been tested on 32-bit versions of Ubuntu 12.04 (Precise), Ubuntu 14.04 (Trusty), Ubuntu 16.04 (Xenial), Debian 7 (Wheezy) and 32-bit, 64-bit and armhf versions of Debian 8 (Jessie).

```bash
sudo apt-get install build-essential cmake git libogre-dev libglu1-mesa-dev libxt-dev libopencv-dev tcl tk
```
On Ubuntu 16.04, substitute libogre-dev with libogre-1.9-dev.

### Compiling libhand and pose_designer
```bash
git clone https://github.com/jonkeane/libhand
mkdir build
cd build
cmake ..
make
# Collate libhand build artifacts into local "dist" directory (for external applications to link against)
make install
```
### Usage
Unfortunately, the OGRE package in the Debian and Ubuntu repositories does not appear to configure its own runtime linking paths correctly, so we have to supply the path manually. On a 64-bit Ubuntu 16.04 system linux system for example, before running libhand you may need to run:
```bash
# Ensure path exists first: on 32-bit, x86_64 is replaced with i386. Replace OGRE version with whatever was installed (likely OGRE-1.9.0, OGRE-1.8.0, or OGRE-1.7.4).
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu/OGRE-1.9.0
sudo ldconfig
```
Once the OGRE library path is configured, you can launch the graphical pose designer from the build directory:
```
./hand_cpp/source/pose_designer
```
...and then use the file dialog box to open hand_model/scene_spec.yml to design hand poses! From the Pose Designer you can use press 'r' to open another dialog box to load some pre-defined hand pose (located in poses/*.yml). Toggle the help popup by pressing 'h'.

What's contained in this distribution?
----------------------------------------

The file INSTALL.txt contains instructions on how to compile and set up
LibHand. Here is a general overview of the LibHand directory structure.

- hand_cpp - compile this first.
 The hand_cpp directory provides the LibHand C++ library and the
 pose_designer utility. 

The pose_designer utility can be used to "test drive" LibHand and experiment
with different hand poses.

- hand_model - this is the main hand 3D data directory. There is a
  "scene_spec.yml" file that is used by the LibHand software to load in the
  hand 3d scene, the hand 3D mesh, textures, skeletons, etc. 

- examples - this directory contains the tutorial code with detailed
  comments. The examples directory requires the hand_cpp directory to be
  compiled and setup first

- hand_matlab - contains the interface code for MATLAB, along with MATLAB
  examples. To compile hand_matlab, you need a recent version of MATLAB that
  is setup to compile with mex. Make sure you can compile C the example code
  that comes with your installation of MATLAB before trying to compile
  the LibHand MATLAB interface. Alternatively, you can download a
  pre-compiled MATLAB binary from <http://www.libhand.org/>

- poses - contains some example hand poses as YAML files, to be used with
  the pose_designer and the example code for both C++ and MATLAB.

- install_help - contains some utilities to make installing the LibHand
  dependecies easier.

Citation
----------------------------------------

  * If this software or its derivative is used to produce an academic
publication, you are required to cite this work by using the following
citation or an alternate form provided on "http://www.libhand.org/" :
```
    @misc{libhand,
      author = "Marin \v{S}ari\'{c}",
      title = "LibHand: A Library for Hand Articulation",
      year = "2011",
      url = "http://www.libhand.org/",
      note = "Version 0.9"
    }
```

License
----------------------------------------

LibHand is available under a derivative of a BSD-license that requires the
academic community to provide attribution to LibHand by means of
citations. Essentially, you can use, modify and sell LibHand or the derived
software in academic and non-academic, commercial and non-commercial,
open-source and closed-source settings, but you have to give proper
credit. Please see the license.txt file for the exact licensing information.

The Hand 3D Model License
----------------------------------------

LibHand comes with a textured, rigged and skinned realistic model of a human
hand. The LibHand 3D Hand Model is located in the hand_model directory and
it's available under the Creative Commons Attribution 3.0 Unported License.

Please see the hand_model_license.txt file in the hand_model directory for
the exact licensing information.


Copyright (c) 2011, Marin Saric <marin.saric@gmail.com>
All rights reserved.

This file is a part of LibHand. LibHand is open-source software. You can
redistribute it and/or modify it under the terms of the LibHand license. The
LibHand license is the BSD license with an added clause that requires
academic citation. You should have received a copy of the LibHand license
(the license.txt file) along with LibHand. If not, see
<http://www.libhand.org/>
