# SAML: Adaptive sGNN architecture for site-invariant analysis of fMRI

## What it does?

The issue is: -
  1. Different hospital scanners have different sensitivites and intensities of measuring scans.
        -> For ex, in functional MRI, the mapped blood oxygen levels for a human brain will have different values and measurements, across different scanner.
        -> We refer to this as scanner-site shift variance. Basically, values collected at different scanners have different signals and values.
  2. This causes a major hinderance for Deep Learning algorithms, as the imaging data confuses the model heavily due to radical shift in values and signals. Extraction of the underlying signals becomes highly infeasible without data-level augumentation, such as harmonizations (ComBat).
  3. But The harmonizations themselves comes with tradeoffs, such as losing precious signals, and full retraining of the model for every new scanner type added.

We solve this issue, by integrating methods and tricks of mmaking the model learn underlying repeating patterns, and robustly generalizing the model, without any sort of data preprocessing. 
  1. Our model allows new sites to be integrated without full retraining, reducing training time by over 90%.


TL;DR: Hospital scanners produce different data for same patient. This confuses DL model while training. We solve it by a novel methodology.

<repo under construction, full README.md along with analysis will be published after paper acceptance>
