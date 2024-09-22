# Napari Encapsulin Analyzer

## Overview

The Napari Encapsulin Analyzer is a powerful tool for analyzing encapsulins using Napari. This tool provides functionalities for detecting blob centers, selecting random images, processing image stacks, and generating masks from JSON files.

[View the Repository](https://github.com/onurburakozdemir/WLabEncapsulinNapari)

## Installation

To install the Napari Encapsulin Analyzer, follow these steps:

1. **Clone the Repository:**

   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Create the Conda Environment:**

   You can set up the environment using the provided `napari.yml` file. Run the following command:

   ```bash
   conda env create -f napari.yml
   ```

3. **Activate the Environment:**

   ```bash
   conda activate <environment-name>
   ```

4. **Launch Napari:**

   Start Napari by running:

   ```bash
   napari
   ```

## Usage

### Functions

1. **Blob Center Detection**

   This function detects the centers of blobs in a selected image layer and displays the regions.

   ```python
   @magic_factory(image_layer={'label': 'Select Image Layer'},
                  mask_layer={'label': 'Select Mask Layer'})
   def test_blob_centers(image_layer: 'napari.layers.Image', mask_layer: 'napari.layers.Image', viewer: 'napari.Viewer') -> None:
       ...
   ```

   **Parameters:**
   - `image_layer`: The layer containing the image data.
   - `mask_layer`: The layer containing the mask data.

2. **Select Random Images**

   Randomly select a specified number of images from the detected regions and display them.

   ```python
   @magic_factory(
       image_layer={'label': 'Select Image Layer'},
       n_select={'label': 'Number of Images to Select', 'min': 1, 'max': 100, 'step': 1}
   )
   def select_random_images(image_layer: 'napari.layers.Image', n_select: int, viewer: 'napari.Viewer') -> None:
       ...
   ```

   **Parameters:**
   - `image_layer`: The layer containing the stacked regions.
   - `n_select`: Number of images to randomly select.

3. **Process Image Stack**

   Process an image stack to calculate radial profiles and display plots.

   ```python
   @magic_factory(image_stack={'label': 'Select Image Stack'})
   def process_image(image_stack: 'napari.layers.Image', viewer: 'napari.Viewer') -> None:
       ...
   ```

   **Parameters:**
   - `image_stack`: The layer containing the image stack.

4. **Generate Masks from JSON Files**

   Convert JSON-defined shapes into mask images and save them as TIF files.

   ```python
   @magic_factory(
       src_folder={'label': 'Select source folder with JSON files'},
       output_folder={'label': 'Select output folder'},
   )
   def generate_masks(src_folder: str, output_folder: str) -> None:
       ...
   ```

   **Parameters:**
   - `src_folder`: Folder containing the JSON files.
   - `output_folder`: Destination folder for the generated mask images.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
