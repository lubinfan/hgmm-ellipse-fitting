# Robust Ellipse Fitting Using Hierarchical Gaussian Mixture Models
## 1. Motivation
Traditional methods mainly rely on the least-squares principle for ellipse fitting, however, as the Gauss-Markov theorem pointed, they are sensitive or susceptible to outliers. To solve this problem, we propose a novel method for robust ellipse fitting using hierarchical Gaussian mixture models. The method consists of two layers, where the first layer aims to locating ellipses through a distance-density-based region growing, and the second one further improves the fitting accuracy. Since we combine distance and density to decide correct ellipses, the method is quite robust against noise and outliers. Moreover, due to the hierarchical structure, out proposed method greatly narrows down the iterative scope of the kernel bandwidth, thereby accelerating the fitting process.

![outlier](https://github.com/zikai1/HGMMEllFit/blob/main/outlier.png)
![eye](https://github.com/zikai1/HGMMEllFit/blob/main/eye.png)
![eyefit](https://github.com/zikai1/HGMMEllFit/blob/main/eyefit.png)

## 2. How to use
For easy use, the code is implemented by MATLAB R2019a. 
- Download the code by 
"git clone https://github.com/zikai1/HGMMEllFit"

- Complie the cpp files in the HGMM_make directory in MATLAB to generate mex files. 

- Add the mex files by "addpath(genpath('.\HGMMEllFit\HGMM_make'))" .

- Run the demo file "demo.m" to generate ellipse fitting results in outlier-contained cases.

## 3. Suggestions
There are mainly three parameters in our algorithm, to get better performance, we provide some suggestions for them.
- The bandwidth h, which acts as a smoothing parameter. We suggest $h\in [4, 1]$ for the outer fitting, and $h\in [0.9, 0.6]$ for the inner fitting.
- The point number N in the growing region. When the ellipse is quite large, we suggest slightly tuning N higher.
- The neighborhood number $\epsilon$ in the growing region. If there are a large part of outliers, we suggest using a larger $\epsilon$ to improve the fitting accuracy.

