# Panorama Stitcher

Python-based panoramic image stitcher using OpenCV.

## How it works

The script is passed two images that contain some overlap or common region. A SIFT-based descriptor from OpenCV is used to locate keypoints in the images and creates local descriptors for these keypoints. A KNN-based matcher is then used to compare these sets of keypoints and pair the ones that show the most similarity. The similarity is calculated as the Euclidean distance between two keypoints. As recommended by the autors of the SIFT paper, these pairs go through a ratio test to discard pairs where their distance is not below a certain threshold. Now that the keypoint pairs have been finalised, a homography matrix is calculated that will provide the translation to map these pairs together. This homnography matrix is found using the RANSAC iterative algorithm. Using this translation matrix and some warp and perspective transformations, the images are stiched together, reconstructing a panoramic view from the original set of overlapping images.

## Running the script

This script is ready to run and just requires it to be executed in a jupyter notebook.

``` sh
$ git clone https://github.com/httpdaniel/PanoramaStitcher.git
$ cd PanoramaStitcher
$ jupyter notebook
```
