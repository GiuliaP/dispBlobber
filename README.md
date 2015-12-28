dispBlobber
====================

Module to detect the closest proto-object in the robot's visual field using stereo-vision.

## Description

This module takes as input a disparity map (grayscale image) and provides as output the closest (brightest) blob, which is generally an object or proto-object in the scene. The output is provided in the following forms:

- binary image with the segmented blob
- cropped rectangular region enclosing the segmented blob on the input disparity map
- 2D top-left (TL) and bottom-right (BR) pixel coordinates of the cropped rectangular region on the input disparity map
- 2D pixel coordinates of the centroid of the segmented blob, eventually averaged over a buffer of arbitrary size, on the input disparity map

If the input disparity map comes from the [SFM](https://github.com/robotology/stereo-vision) module and this module is connected to the RPC port of the [SFM](https://github.com/robotology/stereo-vision), then  the stereo pairs (correspondent 2D points on the other camera) and the 3D re-projections in the world reference frame of the above points (blob's TL and BR ROI vertices and centroid) are also provided as output.

The centroid's coordinates of the closest blob in the scene provided by this module can be fed to the [ARE](http://wiki.icub.org/iCub_documentation/group__actionsRenderingEngine.html) or directly to the [iKinGazeCtrl](http://wiki.icub.org/iCub_documentation/group__iKinGazeCtrl.html) module in order to focus the robot's gaze on the object of interest. If the data connection is streamlined then the robot keeps on focusing on the closest proto-object in its visual field.

Example applications of the usage of this module can be found here:
- [onthefly-recognition](https://github.com/robotology/onthefly-recognition) Demo to teach the iCub to recognize to new objects on-the-fly.
- [icubworld](https://github.com/GiuliaP/icubworld) Application to acquire a dataset of images from the iCub's cameras while the robot is observing a set of objects shown by a human operator. The dataset can be used, e.g., to train/benchmark offline a visual recognition system.

## Installation

##### Dependencies
- [YARP](https://github.com/robotology/yarp)
- [iCub](https://github.com/robotology/icub-main)
- [icub-contrib-common](https://github.com/robotology/icub-contrib-common)
- [OpenCV](http://opencv.org/downloads.html)

## License

Material included here is Copyright of _iCub Facility - Istituto Italiano di Tecnologia_ and is released under the terms of the GPL v2.0 or later. See the file LICENSE for details.
