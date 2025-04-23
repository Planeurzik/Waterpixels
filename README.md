# Waterpixels Segmentation Project

## Overview

This project implements the Waterpixels segmentation method as described in the referenced article. The goal is to segment images into superpixels, which are small, homogeneous regions within an image. This implementation is done in Python and follows the steps outlined in the article.

## Methodology

The Waterpixels algorithm involves several steps:

1. **Preprocessing**: Convert the image to the Lab color space if it's not already in grayscale. Apply morphological opening and closing to smooth the image while preserving edges.
2. **Gradient Calculation**: Compute the morphological gradient of the image using dilation and erosion.
3. **Hexagonal Grid**: Overlay the gradient image with a regular hexagonal grid, applying a scaling factor $\rho$ to create space between hexagons.
4. **Marker Selection**: Identify markers within each hexagon by finding the minimum gradient and keeping the largest connected component.
5. **Distance Map**: Calculate a distance map where each pixel's value is the distance to the nearest marker.
6. **Gradient Regularization**: Create a new image where each pixel value is a combination of the gradient and the distance to the markers.
7. **Watershed Algorithm**: Apply the watershed algorithm to the regularized gradient image to achieve segmentation.

## Results

The pipeline cleaned and explained is in the `waterpixels.ipynb` notebook. The `distance_algo.ipynb` file shows how the distance is coded and how it works. See the report and the presentations for further explanations.

The implementation was tested with various parameters, including the spacing between hexagon centers, the scaling factor, and the weight of the distance map in the regularized gradient. The results show that careful selection of these parameters is crucial for achieving good segmentation (see `compute_figures.ipynb`).

## References

- Original Article: [Waterpixels Segmentation](https://hal.science/hal-01212760)
