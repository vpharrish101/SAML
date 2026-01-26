# SAML: Adaptive sGNN - based optimization model for eliminating scanner-shift bias



**Recruiters & Hiring Managers:**
I am happy to walk through the architecture, code structure, and implementation details during an interview. Please contact me directly:


**Email:** vpharrish101@gmail.com

**LinkedIn:** https://www.linkedin.com/in/vp-harrish-249651275/


> **Status:** Research Paper pending submission. Code currently private.

> **Domain:** Computer Vision, Medical Imaging (fMRI), Graph Neural Networks, Optimization Learners.

>*Please note that results, accuracies and optimization results are intentionally redacted/not reported to preserve work data* 


## The Problem

* **TL;DR**: Hospital scanners produce different data 'noise' for same patient. This confuses DL model while training. We solve it by disrupting those 'noise'.
  
The issue is: -
  1. Different hospital scanners have different sensitivites and intensities of measuring scans.
        -> For ex, in functional MRI, the mapped blood oxygen levels for a human brain will have different values and measurements, across different scanner.
        -> We refer to this as scanner-site shift variance. Basically, values collected at different scanners have different signals and values.
  2. This causes a major hinderance for Deep Learning algorithms, as the imaging data confuses the model heavily due to radical shift in values and signals. Extraction of the underlying signals becomes highly infeasible without data-level augumentation, such as harmonizations (ComBat).
  3. But The harmonizations themselves comes with tradeoffs, such as losing precious signals, and full retraining of the model for every new scanner type added.

* **Analogy:** It's like taking a photo of the same object with a Canon and a Nikon; the colors and lighting look different even if the object is the same.



## Our Approach

* **TL;DR**: Since the 'noise' is same-y for all patients from a particular scanner, we destroy that similarity by geometrically reshaping the data, with embedded randomness.

We solve this by: -
  1. We approached this issue by using Model Agnostic Meta Learning (MAML), a Hessian matrix based training algorithm. The core idea is, exposing the model to lots of different sites at once, and modelling the loss will poteltially let the model ignore additive noise and learn the underlying signals underneath.
  2. This approach, however did not work while tested in Leave-One-Site-Out tests, as the model instead optimized for all of the trained sites. Our preliminary takeaway is that, a geometric level manipulation is needed to change the loss landscape to stop prioritizing scanner site artifacts.
  3. Since scanner noise is structured (meaning it is consistent for all patients from a particular site), we disrupt that geometry itself, by randomly projecting it. The intuition is, the scanner noise that is consistent on each patient at a site is now disrupted, forcing the model to rely less on noise.
  4.  We now sample and project the scan data in log-spaced frequencies(s=0.1,1,10), using spectral Random Fourier Features(RFF) and let a learned gate decide which of the 3 projections contain the most signal. RFF here is used as a helper for GNN, so the final weight of RFF contribution is also learnt.
  5. This approach showed success in nearly all synthetic dataset sites with varying noise level, and positive oberstations in real life data (More info on the thesis paper.)

## Tech Stack
* **Languages:** Python
* **Deep Learning:** PyTorch, PyTorch Geometric (PyG)
* **Data Processing:** Scikit-learn, NumPy, Pandas, NiBabel (Neuroimaging)
* **DevOps/Tracking:** MLflow (Experiment Tracking)



##  Code Access
*This project is part of an ongoing research thesis intended for journal publication.* To maintain the integrity of the peer-review process, the source code is currently hosted in a **private repository**.


