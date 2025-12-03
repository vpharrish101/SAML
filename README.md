# SAML: Cross-Site Generalization for Medical AI

> **Status:** Research Paper pending submission. Code currently private.

> **Domain:** Computer Vision, Medical Imaging (fMRI), Graph Neural Networks, Optimization Learners


## The Problem

The issue is: -
  1. Different hospital scanners have different sensitivites and intensities of measuring scans.
        -> For ex, in functional MRI, the mapped blood oxygen levels for a human brain will have different values and measurements, across different scanner.
        -> We refer to this as scanner-site shift variance. Basically, values collected at different scanners have different signals and values.
  2. This causes a major hinderance for Deep Learning algorithms, as the imaging data confuses the model heavily due to radical shift in values and signals. Extraction of the underlying signals becomes highly infeasible without data-level augumentation, such as harmonizations (ComBat).
  3. But The harmonizations themselves comes with tradeoffs, such as losing precious signals, and full retraining of the model for every new scanner type added.

* **Analogy:** It's like taking a photo of the same object with a Canon and a Nikon; the colors and lighting look different even if the object is the same.


## The Solution
We solve this issue, by integrating methods and tricks of mmaking the model learn underlying repeating patterns, and robustly generalizing the model, without any sort of data preprocessing. 
  1. Our model allows new sites to be integrated without full retraining, reducing training time by over 90%.
  2. The system is designed to be "plug-and-play" for new hospitals without requiring a machine learning engineer to retrain the model from scratch.

## Tech Stack
* **Languages:** Python
* **Deep Learning:** PyTorch, PyTorch Geometric (PyG)
* **Data Processing:** Scikit-learn, NumPy, Pandas, NiBabel (Neuroimaging)
* **DevOps/Tracking:** MLflow (Experiment Tracking)


##  Code Access
*This project is part of an ongoing research thesis intended for journal publication.* To maintain the integrity of the peer-review process, the source code is currently hosted in a **private repository**.

**Recruiters & Hiring Managers:**
I am happy to walk through the architecture, code structure, and implementation details during an interview. Please contact me directly:

📧 **Email:** vpharrish101@gmail.com
🔗 **LinkedIn:** https://www.linkedin.com/in/vp-harrish-249651275/
