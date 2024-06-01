
# Removing Seasonal Variations from the Performance Ratio (PR) Dataset Using FFT

Performance Ratio (PR) is a critical metric for evaluating the performance of Photovoltaic (PV) power plants. PR values are influenced by various factors, with some being weather-dependent, which introduces seasonal fluctuations in the PR.


To address this, we utilise the Fourier Transform to remove the periodic seasonal variations from the PR dataset. Specifically, we implement the Fast Fourier Transform (FFT) using the Scipy Python package. We can effectively eliminate the seasonal variations by identifying and filtering out the dominant peak in the power spectral density corresponding to the period of seasonal variation of PR. Finally, we use the Inverse FFT (IFFT) to reconstruct the PR time series without the seasonal components.

[The code for performing the FFT on PR dataset](FFT.ipynb)
## Prerequisites 
### PR dataset 
A time series PR dataset with daily resolution is used in the program. Points to be noted while selecting the PR dataset-
* The dataset must be a time series with daily resolution.
* The dataset must cover complete years (e.g., 1 year, 2 years, 3 years, etc.).
* The dataset should have minimal NAN values.
* If NAN values are present in the dataset, interpolation methods are utilised to compute the missing values in the PR dataset.

The details of the PR dataset used in the program is given in the methodology section.

### Python Prerequisites
* pandas
* scipy
* numpy
* bokeh

(Note: The choice of plotting software is flexible; bokeh is used here for all graph plotting.)


## Methodology
### 1. The PR dataset
The [PR dataset used in the code](pr_dataset.csv) comprises:
* Date column
* PR column

The dataset spans from 20-10-2010 to 20-10-2013 (3 years).

### 2. The FFT on PR dataset
FFT is applied to the PR dataset using the Scipy Python package. The Power Spectral Density (PSD) is computed using FFT. Refer to the code for details.

### 3. Filtration of seasonal component from PR dataset
The dominant peak in the PSD of PR is isolated, assuming that the seasonal variation is represented by a single sinusoidal component. The dominant peak frequency corresponds to a period of 365 days, representing the seasonal variations.

The data is filtered into two components:
* Seasonal component: representing the seasonal variation of PR dataset.
* Residue component: the dataset remaining after removing the seasonal component.

### 4. The IFFT on PR dataset
IFFT is applied to the filtered data to reconstruct the PR dataset after eliminating the seasonal variations.

## Result
The [result](pr_fft_dataset.csv) of the code for the PR dataset is:
### 1. The seasonal component of PR
![PR seasonal!](image/pr%20seasonal%20component.png)

Fig-1, The red dots represent the PR from the dataset and the black line represents the seasonal variations in the PR.
### 2. The residue component of PR
![PR residue!](image/pr%20residue%20component.png)
Fig-2, The blue dots represent the PR after elimination of seasonal variations. 



