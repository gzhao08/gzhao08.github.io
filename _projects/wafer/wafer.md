---
layout: default
title: "Wafer Testing"
---

# Wafer Analysis


- **Tools:** C++, Python, Matlab
- **Concepts:** Software, Optics
- **Status:** Completed
- **Publication:** [Interferometric measurement of ultra-smooth vacuum chucks for high-precision optical manufacturing](https://www.spiedigitallibrary.org/conference-proceedings-of-spie/13720/137200E/Interferometric-measurement-of-ultra-smooth-vacuum-chucks-for-high-precision/10.1117/12.3077114.short)


## Background

Interometry is used to analyze the surfaces of objects in the field of metrology. Even objects (like silicon wafers) that look very smooth, have local deviations. Interferometers send light waves and use the reflections to determine the surface shape.

Specifically with silicon wafers, a vacuum chuck is used to secure the wafer to prevent movement and folding from occuring. However, a mask is used on the wafer which obscures vision and makes it difficult to take measurements with an interferometer. 

My goal was to figure out how to get an accurate model of the surface shape without removing the mask.

The scripts made to do the following analysis were first written in Python, then Matlab, and finally in C++ where it was integrated into the company software.

## Summary

The wafer with and without the mask looks like 

| ![img1]({{ '/assets/img/projects/wafer/wafer_photos/actual_photos/Bare/IMG_3325.jpg' | relative_url }}) | ![img2]({{ '/assets/img/projects/wafer/wafer_photos/actual_photos/Mask/IMG_3319.jpg' | relative_url }}) |

When taking sample measurements, my coworker noticed that if you set the resolution very low, the measurement could essentially "bypass" the mask allowing you to get a general view of the wafer. This looks like: 

![img3]({{ '/assets/img/projects/wafer/wafer_photos/base_data/z.png' | relative_url }})

As you can see you get a general shape but the mask still messes with the measurement so the first step is to interpolate the missing data. I used a nearest neighbours interpolation method to get

![img4]({{ '/assets/img/projects/wafer/wafer_photos/Z_Data/z_interpolated.png' | relative_url }})

Next, if we turn the resolution back up, we can get the locations of the holes in the mask, the "actual" data points. The raw measurement looks like

![img5]({{ '/assets/img/projects/wafer/wafer_photos/base_data/wafer.png' | relative_url }})

As you can see, the shapes and sizes of the holes are messed up and (if we look closely) the measurements are off too.

The task now is to merge (overlay) and use the XY data as a mask on the interpolated Z data. If we also do some fixing of the clusters of data points we can arrive at a very good model of the actual data in the mask.

![img6]({{ '/assets/img/projects/wafer/wafer_photos/XY_Data/enhanced_wafer2.png' | relative_url }})

Note that the data on the edges are commonly cropped so edge distortion can be ignored.



