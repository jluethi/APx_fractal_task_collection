# APx Fractal Task Collection

The APx Fractal Task Collection is mainainted by [Apricot Therapeutics AG](https://apricotx.com/), Switzerland. This is a collection of tasks intended to be used in combination with the [Fractal Analytics Platform](https://github.com/fractal-analytics-platform) maintained by the [BioVisionCenter Zurich](https://www.biovisioncenter.uzh.ch/en.html) (co-founded by the Friedrich Miescher Institute and the University of Zurich). The tasks in this collection are focused on extending Fractal's capabilities of processing 2D image data, with a special focus on multiplexed 2D image data. Most tasks work with 3D image data, but they have not specifically been developed for this scenario.


## Installation

You can install the package locally with:
```console
pip install git+https://github.com/Apricot-Therapeutics/APx_fractal_task_collection.git
```

## Running tasks

For instructions on how to run tasks, please refer to the official [Fractal Tasks Core Documentation](https://fractal-analytics-platform.github.io/fractal-tasks-core/) 

## Available Tasks

Please note that all tasks pass basic tests based on 2D and 3D OME-ZARR files. However, in the 3D case, the resulting output has not been extensively checked and might not make sense (as most tasks have been developed for the 2D use-case). If you are using the tasks for 3D data and encounter any weird behaviour, please open an issue.

| Task | Description | 2D Tests Passing | 2D Output validated | 3D Tests Passing | 3D Output validated |
| --- | --- | :---: | :---: | :---: | :---: |
| Create OME-Zarr Multiplex IC6000 | Generates a OME-Zarr file based on the output of a IN Cell Analyzer 6000 (GE Healthcare). |☑️|☑️|☑️|✖️|
| IC6000 to OME-Zarr |Converts output images from IC6000 microscopy to OME-Zarr. Use after "Create OME-Zarr Multiplex IC6000". |☑️|☑️|☑️|✖️|
| Calculate Illumination Profiles | Calculates illumination correction model based on [BaSiCPy](https://github.com/peng-lab/BaSiCPy) for each available channel. |☑️|☑️|☑️|✖️|
| Apply BaSiCPy Illumination Model | Applies BaSiCPy illumination models to a OME-Zarr file. Use after "Calculate Illumination Profiles" |☑️|☑️|☑️|✖️|
| Chromatic Shift Correction | Corrects chromatic shift in OME-Zarr file per wavelength id. Requires reference images (for example fluorescent beads) |☑️|☑️|☑️|✖️|
| Stitch FOVs with Overlap | Stitches FOVs that were imaged with overlap, using [ASHLAR](https://github.com/labsyspharm/ashlar). |☑️|☑️|☑️|✖️|
| Calculate Registration (image-based) [chi-squared shift] | Calculates shift between acquisitions based on chi-squared shift algorithm from the python package [image registration](https://image-registration.readthedocs.io/en/latest/api/image_registration.chi2_shifts.chi2_shift.html) |☑️|☑️|☑️|✖️|
| Segment Secondary Object | Segments secondary objects in images. Requires a label image that provides seeds and an intensity image. |☑️|☑️|☑️|✖️|
| Clip Label Image | Clips a label image with a secondary label image. For example, this can be used to clip cell segmentations with nuclear segmentations to receive the cytoplasm. |☑️|☑️|☑️|✖️|
| Convert Channel to Label | Utility task to convert a channel from a OME-Zarr file to a label image. Can be used to import an external label image into Fractal without creating a new task. |☑️|☑️|☑️|✖️|
| Filter Label by Size | Filters a label image by size and removes objects larger/smaller than a given threshold. |☑️|☑️|☑️|✖️|
| Measure Features | Measures features for a given label image. Currently, four feature sets are available: intensity featues, morphology features, population context features and texture features (Haralick and Law's Texture Energy). |☑️|☑️|☑️|✖️|
| Label Assignment by Overlap | Assigns child labels to parent labels by their overlap. Relationship is saved in the observations of the feature table. |☑️|☑️|☑️|✖️|
| Aggregate Tables to Well Level | Aggregates/Concatenates feature tables from all acquisitions. Can be saved either on the well level or in the first aqcuisition. |☑️|☑️|☑️|✖️|
| Multiplexed Pixel Clustering | Applies multiplexed pixel clustering to selected images. |☑️|☑️|☑️|✖️|

