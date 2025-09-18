# Lightkurve Exoplanet ML Project
## OVERVIEW 
This is an ongoing project, where I am building a pipeline to analyse Kepler space telescope PDCSAP lightcurves to extract exoplanet transit features. The analysis includes signal processing, feature extraction and machine learning classification.

## DATASET
**Positive examples**: (stars with known exoplanets) KIC 6922244, KIC 11904151 <br>
**Negative examples**: KIC 12069424, KIC 8832417 

## METHOD
### 1. Signal Processing
* Search and download 4 lightcurves using lightkurve
* Remove NaN values
* Apply flattening and folding to remove long-term variability
* Period folding using Box Least Squares Periodogram
* Savitzky-Golay filtering for smoothing
### 2. Feature Extraction - *work in progress*
* **Transit Depth**: Decrease of relative flux in transit
    * Calculated as (baseline_flux - transit_min)/baseline_flux
    * Set to 0 for negative examples (no genuine transits)
* **Transit Duration**: Time span of transit
    * Calculated using approximate transit window
    * Set to 0 for negative examples (allowing for clear distinction in features of stars with exoplanets vs without exoplanets)
* **Period**: Time between transits
    * Calculated using Periodogram 
* ***Next Step***: Compiling extracted features into structured Pandas Dataframe
### 3. Machine Learning - *work in progress*
* Developing classification approach to distinguish between stars with exoplanets vs stars without exoplanet using extracted features.

## KEY RESULTS
Detailed analysis with plots available in [main analysis notebook](project-code.ipynb) <br>
| Star | Transit Depth | Transit Duration (days) | Period (days) |
|------|---------------|-------------------------|---------------|
|KIC 6922244 | 0.01197 | 0.4 | 3.51975 |
|KIC 11904151 | 0.00105 | 4 | 0.83643 |
|KIC 12069424 | 0 | 0 | 0.36809 |
|KIC 8832417 | 0 | 0 | 0.49722 |

## TECHNOLOGIES USED - *to be updated*
**Python** <br>
**Lightkurve**: Kepler data analysis <br>
**NumPy/SciPy**: Signal processing <br>
**Matplotlib**: Data visualisation 

## EVALUATION 
### Current Limitations:
* Small sample size (only 4 examples), won't result in reliable ML model training
* Not using precise transit window, can lead to overestimation 
* Few features extracted 
* Selection bias introduced when manually selecting stars and quarters
### Expansion Opportunities:
* Increase sample size and include variety of planet sizes
* Improve smoothing process, introducing de-noising methods
* Extracting more features with better precision

