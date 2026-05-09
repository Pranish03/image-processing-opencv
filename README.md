# Image Processing Notes

A structured collection of image processing concepts and Python implementations using OpenCV, NumPy, and Matplotlib.

---

## Requirements

```bash
pip install opencv-python numpy matplotlib
```

---

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

---

## Topics

### 1. Gray Level Transformations

Point processing techniques that operate on individual pixel intensities.

| Technique | Description |
|---|---|
| [Image Negative](#1-image-negative) | Inverts pixel intensities |
| [Log Transformation](#2-log-transformation) | Enhances dark regions |
| [Gamma Transformation](#3-power-law-gamma-transformation) | Brightness correction via power function |
| [Contrast Stretching](#4-contrast-stretching) | Expands intensity range to full scale |
| [Thresholding](#5-thresholding) | Converts grayscale to binary |
| [Gray Level Clipping](#6-gray-level-clipping) | Highlights specific intensity range |
| [Bit Plane Slicing](#7-bit-plane-slicing) | Extracts individual bit planes |

---

#### 1.1 Image Negative

Reverses intensity levels — dark pixels become bright and bright pixels become dark.

**Formula:** `s = (L - 1) - r`

where `L` = number of gray levels (256), `r` = input intensity, `s` = output intensity.

```python
negative = cv2.bitwise_not(img)
```

---

#### 1.2 Log Transformation

Maps a narrow range of dark pixel values to a wider output range, enhancing detail in darker regions.

**Formula:** `s = c * log(1 + r)`

where `c` is a scaling constant = `255 / log(1 + max_pixel_value)`.

```python
log_transformed = np.log1p(np.float32(img))
log_transformed = cv2.normalize(log_transformed, None, 0, 255, cv2.NORM_MINMAX)
log_transformed = np.uint8(log_transformed)
```

---

#### 1.3 Power-Law (Gamma) Transformation

Modifies brightness using a power function. Useful for gamma correction.

**Formula:** `s = c * r^γ`

| Gamma | Effect |
|---|---|
| `γ < 1` | Image becomes brighter |
| `γ > 1` | Image becomes darker |
| `γ = 1` | No change |

```python
gamma_corrected = np.uint8(np.power(img / 255.0, gamma) * 255)
```

---

#### 1.4 Contrast Stretching

Stretches the narrow intensity range of an image to the full display range (0–255).

**Formula:** `s = ((r - r_min) / (r_max - r_min)) * 255`

```python
stretched = np.uint8(((img - img.min()) / (img.max() - img.min())) * 255)
```

---

#### 1.5 Thresholding

Converts a grayscale image to binary by comparing each pixel to a threshold value `T`.

**Formula:**
```
s = 255  if r >= T
s = 0    if r < T
```

```python
_, threshold_img = cv2.threshold(img, threshold_value, 255, cv2.THRESH_BINARY)
```

---

#### 1.6 Gray Level Clipping

Highlights a specific intensity range `[A, B]`, suppressing everything outside it.

**Formula:**
```
s = 255  if A <= r <= B
s = 0    otherwise
```

```python
clipped = np.uint8(np.where((img >= A) & (img <= B), 255, 0))
```

---

#### 1.7 Bit Plane Slicing

Separates a grayscale image into 8 binary bit planes (bit 0 = LSB, bit 7 = MSB).

```python
for i in range(8):
    bit_plane = (img >> i) & 1
```

Higher bit planes (6, 7) carry most of the visual information. Lower planes (0–2) contain fine detail and noise.

---

### 2. Histogram Processing
> *Coming soon*
- Histogram Equalization
- Histogram Matching

### 3. Spatial Filtering
> *Coming soon*
- Mean Filter
- Gaussian Filter
- Median Filter
- Sharpening Filters (Laplacian, Sobel)

### 4. Frequency Domain
> *Coming soon*
- Fourier Transform
- Low-pass & High-pass Filters
- Ideal, Butterworth, Gaussian Filters

---

## Usage

```bash
# Clone the repo
git clone https://github.com/Pranish03/<repo-name>.git
cd <repo-name>

# Run any script
python 01_gray_level_transformations/negative.py
```

> Make sure to place your input image at `images/img-1.png` or update the path in each script.

---
