---
layout: post
title: 02/05/2017 Quiz I Notes
description: Quiz I Notes for Computer Graphics
modified: 2017-02-05
tags: [Computer Graphics, notes]
---

## Class I: Nuisance about Computer and Human Vision

1. Human Vision
    1. Key parts in Eyes:
        1. Iris : colored annulus (ring) with radial muscles
        2. Pupil : the hole size controlled by iris (lens)
        3. Retina: Cones vs Rods -- color, less sensitive, high light vs BW, sensitive, operate at night
    2. Random Goals: Recognition, food, predator, world, etc.
    3. Limited memory, computation budget
2. Light & Color
    1. Visible light: 400 - 700nm (purple - red) （Sun radiates EM energy）
    2. Light can be described as spectrum at each wave length
    3. Y = 0.21 R + 0.72 G + 0.07 B
    4. Lack of cones led to color blindness
    5. Tetrachromatism (super color perception)

3. Electronic Eyes
    1. How to sensor
        1. sensor arrays
        2. interlace vs. progressive scan
        3. rolling shutter
    2. Bayer RGB mosaic
        1. each photosite has different filter G : R : B = 2 : 1 : 1
        2. Demosaicing: (Linear Interpolation) take the near four values to average
    3. Image Representation
        1. 3-D array (h*W*channel), starting from upper left corner
    4. Color Space:
        1. RGB
        2. Intuitive color Space
        3. L*a*b*
    4. Len vs Pinhole
        1. Pinhole
            1. all objects are in focus, small aperture size
            2. less light
            3. diffraction for small aperture
        2. lens
            1. 1/f = 1/do + 1/di
            2. Angle of View (radians)
    5. shutter speed
    6. aperture
    7. Depth of Field

## Class II: Filtering and Edge Detection
1. Simple image processing
    1. grey scale: turn 3 channels into grey scale
    2. brightness : scale the RGB value
    3. mirroring or flipping : done by change to array arrange

2. Filtering
    1. form a new image from the old pixels to extract useful information
    2. linear filtering :
        1. transformation on signals
        2. properties
            1. linearity
            2. shift invariance
        3. can be modeled by convolution
        4. weighted average (1D)
    3. cross-correlation filtering : G = H ** F;
        1. F is the original image
        2. H is the "sliding window" contains weight for each pixel in the given size of window
        3. Gaussian Filter: remove "high-frequency", smooth the image, convolution with self is another Gaussian
        4. Convolution : filter is flipped before applied
        5. property of Convolution :
            1. b = c * a
            2. multiplication like
            3. associativity !!

3. edge detector
    1. An edge is a place of rapid change in intensity
    2. gradient of a image: delta = [df/dx, df/dy] (vector-like)
    3. simple Edge Detector
        1. Blur using Gaussian Filter to eliminate noise
        2. find gradient magnitude
        3. usually combine blur and differentiation
    4. further improve to canny edge Detector
        1. eliminate local maxiama (thin edge)
        2. thresholding within two threshold + DFS

## Class III: Sparse Feature Detection

1. Motivation for sparse features
    1. Image Matching
    2. Feature refers to a region of interest in an image, like corner, edge, blob (low-level)
    3. Feature vector/descriptor is a vector describes a local image, typically want similar image share similar vector
    4. Application : stiching images together using feature-match or direct-match(costly)
    5. Procedure
        1. detect the same point independently in image
        2. correctly recognize corresponding ones
2. Corner Detector
    1. idea: looking into small window, a small shift shall give a large change in intensity (only one direction then it's edge)
    2. Gradient covariance matrix
    3. Harris Detector Algorithm
        1. Find gradient of the given image
        2. find covariance matrix for each pixels
        3. compute smaller eigenvalue e
        4. if e > T, consider a corner
        5. non-maximum suppression
3. Difference of Gaussian (blob) feature detector
    1. Gaussian Pyramids : using Gaussian Filter to blur then discard every other row and column
    2. used to improve search & pre-computation
    2. Blob Detector
        1. To find blob regions of different size
        1. Run linear Filter
        2. At different resolution level

## Class IV: Sparse Feature Detect II

1. SIFT
    1. already know how to detect, now how to match
        1. Invariant && Distinct
        2. Find local Orientation
            1. make histogram for each direction(36)
            2. then match the peak
    2. keypoint: orientation
        1. dominant gradient
        2. Rotation invariant
    3. SIFT descriptor
        1. Image gradients are sampled over 16x16 array of locations.
        2. Find gradient angles relative to keypoint orientation (in blue)
        3. Accumulate into array of orientation histograms
    4. Combined descriptor + blob detect => SIFT
