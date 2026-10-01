# econ3916-lab04-anomaly-detection
# Robust Statistics -- Automated Anomaly Detection

## Objective
I tested how different summary statistics and outlier detection methods
behave on real housing data, and how much each one moves when the data
is deliberately corrupted.

## Methodology
- Loaded the California Housing dataset (20,640 observations) and
  computed two groups of summary statistics: the mean and standard
  deviation, which are sensitive to extreme values, and the median,
  trimmed mean, IQR, and MAD, which are not.
- Built Tukey Fences by hand, using the quartiles and IQR to set upper
  and lower bounds, and flagged home prices that fell outside them.
- Ran an Isolation Forest to detect anomalies across several features
  at once, rather than looking at price alone.
- Compared the observations flagged by each method to see where they
  agreed and where they differed.
- Replaced 5% of the data with corrupted values and recomputed every
  statistic to measure how far each one shifted.

## Key Findings
- Tukey Fences and Isolation Forest flagged different observations.
  Tukey looks at one variable at a time, so it catches extreme prices.
  Isolation Forest looks at combinations of features, so it catches
  homes that are unusual overall even when their price looks normal.
  Neither method is a full replacement for the other.
- After 5% contamination, the mean shifted by [YOUR VALUE]%, while the
  median shifted by only [YOUR VALUE]%. A small amount of bad data was
  enough to distort the mean, but the median, trimmed mean, IQR, and
  MAD stayed close to their original values.
- The practical takeaway: when data may contain errors or extreme
  values, I should report outlier-resistant measures alongside the mean
  and standard deviation, not instead of checking the data visually.
