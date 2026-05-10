# Image Processing Notes

A structured collection of image processing concepts and Python implementations using OpenCV, NumPy, and Matplotlib.

## Usage

```bash
# Clone the repo
git clone https://github.com/Pranish03/image-processing-opencv.git
cd image-processing-opencv

# Create virtual environment
python -m venv venv

# Activate it
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows

# Install dependencies
pip install -r requirements.txt

# Run any script
python 01_gray_level_transformations/negative.py
```

> Make sure to place your input image at `images/img-1.png` or update the path in each script.

## Structure

```
├── images/    # Input images used in programs
├── .gitignore
├── 01_gray_level_transformations.ipynb
├── 02_histogram_processing.ipynb    # coming soon
├── 03_spatial_filtering.ipynb       # coming soon
├── 04_frequency_domain.ipynb        # coming soon
├── README.md
└── requirements.txt
```

## Topics

### 1. Gray Level Transformations

Point processing techniques that operate on individual pixel intensities.

| Technique            | Description                              |
| -------------------- | ---------------------------------------- |
| Image Negative       | Inverts pixel intensities                |
| Log Transformation   | Enhances dark regions                    |
| Gamma Transformation | Brightness correction via power function |
| Contrast Stretching  | Expands intensity range to full scale    |
| Thresholding         | Converts grayscale to binary             |
| Gray Level Clipping  | Highlights specific intensity range      |
| Bit Plane Slicing    | Extracts individual bit planes           |

### 2. Histogram Processing

Intensity distribution analysis techniques that enhance images by redistributing pixel frequencies using histogram transformations.

| Technique                  | Description                                             |
| -------------------------- | ------------------------------------------------------- |
| Histogram of an Image      | Counts pixel frequency at each intensity level          |
| Histogram Equalization     | Enhances contrast by flattening the histogram using CDF |
| Histogram Specification    | Maps histogram to match a target distribution           |
| Local Histogram Processing | Applies equalization per neighborhood window (CLAHE)    |
| Histogram Statistics       | Computes mean, variance, skewness, kurtosis, entropy    |

### 3. Spatial Filtering

> _Coming soon_

- Mean Filter
- Gaussian Filter
- Median Filter
- Sharpening Filters (Laplacian, Sobel)

### 4. Frequency Domain

> _Coming soon_

- Fourier Transform
- Low-pass & High-pass Filters
- Ideal, Butterworth, Gaussian Filters
