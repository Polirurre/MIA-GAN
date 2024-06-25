# RouteMIA
This repository contains the implementation of my bachelor's thesis on Membership Inference Attacks against synthetic Trajectory-generated data.

## Data preparation
The different epsilon folders store the following files each:
- Gene: Synthetic generated trajectories using e-DP MoveSim, etc.
- Real: Original data used to train e-DP MoveSim, etc.
- Test: Data used in tests in e-DP MoveSim, etc.
- Validation: Data used for validation in e-DP MoveSim, etc.

Each line in these files represents a trajectory and each index represents the coordinates of a certain location. To retrieve the coordinates from the index the mapping is done through GPS file.


## Requirements
We have used both [PyTorch](https://pytorch.org/) and [Sci-kit Learn](https://scikit-learn.org/stable/) in our implementation. To manage the needs of our attack the environment was set up with [Anaconda](https://www.anaconda.com/download/).

```
conda create -n pca
conda activate pca
%pip install torch pandas matplotlib scikit-learn numpy seaborn
```
## Code
0. Convert_file_gps
This file performs the mapping between GPS and a trajectory. It returns an HTML file that displays the trajectory in a route.

1. PCA
This file performs principal component analysis on a given dataset, allowing us to reduce the dimensionality of the dataset and thus representing a trajectory as a data point in a new feature space.

2. PCA Comparative
This file performs principal component analysis for two different datasets. For my attack, it will be gene.data against test.dat+val.data.

3. PCA Bulk
This file performs PCA Comparative for a range of epsilons, without having to manually run each.

4. PCA KNN
This file performs a K-Nearest-Neighbor after the PCA. Therefore, it will find similar trajectories between the datasets and return their distance. Moreover, the distance can be calculated according to Manhattan, Euclidean, Chebyshev algorithms.

RouteMIA
   - MIN MAX:
        Most likelyhood classifier.
   - PCA KNN SVM:
        Support Vector Machine that can use linear, polynomial or radial basis kernel classifier.
   - PCA KNN Random Forest:
        Unsupervised Random Forest classifier
        
