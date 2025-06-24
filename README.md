# The coding task- Dataset Generation and Validation
This repository contains  solution to the coding task, which involved generating a new dataset that is statistically similar to a given one, without directly reusing the parameters used in the original sampling process.

### Task Summary

Given: A Python script that generates a dataset with categorical and continuous variables.<br>
<b> Goal:</b><br>
1. Analyze the dataset characteristics (not the code).<br>
2. Generate new samples with similar statistical properties but without reusing the same parameters.<br>
3. Validate that the new dataset closely resembles the original one using statistical tests and visualizations.<br>

### Files

1. dataset.csv: The original dataset provided (generated using unknown parameters).<br>
2. Task2-Solution.py: Python script for generating new synthetic samples and validating them.<br>
3. new_dataset.csv: Output file containing the generated synthetic dataset.<br>
4. comparison_plots.png: Side-by-side visualizations comparing original and generated data.<br>

### Reasoning & Methodology

#### 1. Load and Clean the Original Dataset

Load the original dataset dataset.csv, which contains synthetic data with categorical and continuous features.

#### 2.Characterizing the Original Dataset

To generate synthetic samples,first analyze the statistical properties of the original dataset:

Category1: Calculate the normalized frequency of each category`. This helps to replicate the categorical balance in the new data.

Value1 and Value2: Estimate the mean and standard deviation of these continuous variables using a normal distribution fit . These parameters define how the continuous values are distributed in the original dataset.

#### 3. Synthetic Data Generation

Create a new dataset using the derived parameters

Increased to 1000 to demonstrate the ability to generalize and scale beyond the original 500

A different random seed (np.random.seed(38)) for reproducibility while still being distinct from the original code.

Category1 using a multinomial distribution.

Value1 and Value2 from fitted normal distributions with the estimated mean and standard deviation.

The resulting dataset is saved as `new_dataset.csv` for further validation and visualization.

#### 4. Validation

<b> Chi-Square Test to compare the categorical distribution (Category1) </b><br>

Calculate the observed frequency from the new dataset.The expected frequency is based on the original dataset but scaled to match the total number of new samples.A high p-value (close to 1) indicates that the synthetic and original categorical distributions are statistically similar.

<b>Kolmogorov–Smirnov (KS) Tests for continuous features (Value1, Value2)</b><br>

Evaluate whether the distributions of the continuous features `Value1` and `Value2` in the synthetic dataset are similar to the original dataset. This non-parametric test compares the cumulative distribution functions of two samples.

p-values greater than 0.05 means there is no statistically significant difference between the original and synthetic distributions 


<b>Visualizations using matplotlib and seaborn to inspect the similarity visually.</b><br>

### Results

Chi-Square p-value (Category1): 0.8013
KS-Test p-value (Value1): 0.9666
KS-Test p-value (Value2): 0.8572

These high p-values shows that the synthetic dataset is statistically similar to the original, and it does not reject the null hypothesis of the distributions being equal.

Visual plots (comparison_plots.png) further reinforce this conclusion.


### How to Run

This repository includes both an interactive Jupyter Notebook and a plain Python script version of the solution<br>

1. Task2-Solution.ipynb: Recommended version. Contains step-by-step explanations, visualizations, and results for better interpretability.
2. Task2-Solution.py: Minimal script version for direct execution

Ensure you have the required packages installed:
pip install pandas numpy scipy matplotlib seaborn

Then run:
python Task2-Solution.py
jupyter notebook Task2-Solution.ipynb

It will generate:
new_dataset.csv
comparison_plots.png
Terminal output with p-values and sample preview

