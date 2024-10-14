---
mediawiki: Biomat
name: "Biomat"
title: Biomat
categories: [Filtering]
release-date: "10/14/2024"
initial-release-date: "03/26/2019"
team-founder: 'Jiří Janáček'
team-maintainer: 'Jiří Janáček | mailto:jiri.janacek_at_fgu.cas.cz'
source-url: https://github.com/jiri-janacek/biomat
---



## Plugins for 3D image preprocessing

**Stack Linear Contrast** - multiplies images in stack by coefficient obtained by linear interpolation of the "first" and "last" coefficient. A simple tool for compensation of contrast decreasing with depth within thick sample.

**Lipschitz 3D** Filter - top hat - subtracts slowly varying background calculated as lower Lipschitz envelope from the image.

Preprocessing example: [Stack of confocal images of capillaries in rat brain](/media/plugins/capillaries-brain.zip)

-   {% include bc path='Plugins | Biomat | Stack Linear Contrast'%} with parameters "first" = 1.0 and "last" = 3.0
-   {% include bc path='Process | Filters | Gaussian blur 3D'%} with "sigma" = 1 pixel
-   {% include bc path='Plugins | Biomat | Lipschitz 3D Filter'%} with parameter "slope" = 2 "top hat" on

## Plugins for detection of fibres in 3D image

**Tensor Line 3D Filter** - enhances white fibers of uniform width sparsely distributed on dark background.

Example: [Stack of confocal images of capillaries in rat adipose tissue](/media/plugins/capillaries-adipose.zip).

-   {% include bc path='Plugins | Biomat | Tensor Line 3D Filter'%} with "sigma" = 3 pixels
-   {% include bc path='Image | Adjust | Brightness/Contrast'%}
-   {% include bc path='Process | Filters | Gaussian blur 3D'%} with "sigma" = 1 pixel

**Vector Line 3D Filter** - enhances white fibers of varying width. Crossection of the fibers need not be circular. Parameter "sigma" in pixels corresponds to the largest diameter.

Example: [Stack of micro CT images of capillaries in mouse embryonic heart](/media/plugins/capillaries-heart.zip).

-   {% include bc path='Plugins | Biomat | Vector Line 3D Filter'%} with parameters "sigma" = 4 pixels, "scale number" = 2

## Plugins for evaluation of directionality in 2D images using heat equation

**2D Heat Kernel Tensor** - second order moments of heat kernel calculated from 8 bit binary image.

**2D Tensor Statistics** - summary of tensor image (in ROI). "Value" is average trace of the tensor, "shape" is the ratio of its eigenvalues and "angle" of the first eigenvector is measured counterclockwise from the horizontal axis.

**2D Tensor Color Coding** - standard color coding of 2D tensor image. Symmetric tensor is coded as channels of 32 bit image stacks.

Example: [Projection of segmented capillaries in brain](/media/plugins/biomat/MAX_2_4cortexa1.tif).

-   {% include bc path='Plugins | Biomat | 2D Heat Kernel Tensor'%} with "sigma" = 10 pixels
-   {% include bc path='Plugins | Biomat | 2D Tensor Statistics'%}
-   {% include bc path='Plugins | Biomat | 2D Tensor Color Coding'%}

