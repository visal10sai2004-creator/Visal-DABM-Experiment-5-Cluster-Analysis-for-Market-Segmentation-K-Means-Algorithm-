# Experiment No 5: Cluster Analysis for Market Segmentation (K-Means Algorithm)

## Aim
To apply the K-Means Clustering algorithm to segment a dataset into distinct clusters and visualize how similar data points are grouped together for market segmentation.

## Dataset
The dataset consists of 16 manually entered customer data points representing two numerical features:
* **Feature 1 ($X$):** Annual Income (in Lakhs)
* **Feature 2 ($Y$):** Spending Score (`1–100`)

| Point | Annual Income ($X$) | Spending Score ($Y$) | Point | Annual Income ($X$) | Spending Score ($Y$) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | 20 | 30 | **9** | 32 | 33 |
| **2** | 22 | 35 | **10** | 24 | 31 |
| **3** | 25 | 40 | **11** | 28 | 45 |
| **4** | 70 | 80 | **12** | 75 | 70 |
| **5** | 75 | 85 | **13** | 71 | 83 |
| **6** | 80 | 90 | **14** | 83 | 89 |
| **7** | 30 | 70 | **15** | 28 | 60 |
| **8** | 35 | 75 | **16** | 27 | 67 |

## Algorithm / Steps Followed
1. Import required Python libraries (`numpy`, `matplotlib`, `scikit-learn`).
2. Input data points as separate $X$ and $Y$ feature arrays.
3. Combine both variables into a single 2D feature matrix using `np.column_stack()`.
4. Initialize the `KMeans` model with $K = 3$ clusters.
5. Fit the model and assign each data point to a cluster using `fit_predict()`.
6. Retrieve cluster centroids (`cluster_centers_`) and assigned labels.
7. Visualize the clusters and their centroids using a Matplotlib scatter plot.
8. Interpret the resulting customer segments and centroid coordinates.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Handling** | `np.array()` | Creates arrays for storing numerical feature values ($X$ and $Y$) |
| | `np.column_stack()` | Combines multiple 1D arrays into a single 2D dataset for clustering |
| **Model Initialization** | `KMeans()` | Initializes the K-Means clustering model with $K$ clusters |
| **Model Training & Prediction** | `fit_predict()` | Fits the K-Means model to the dataset and assigns cluster labels |
| **Cluster Properties** | `cluster_centers_` | Retrieves the coordinates (centroids) of the cluster centers |
| | `labels_` | Stores the cluster labels assigned to each data point |
| **Visualization (Matplotlib)** | `plt.scatter()` | Plots the data points and centroids in a 2D scatter plot |
| | `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.legend()`, `plt.grid()`, `plt.show()` | Configures labels, legend, gridlines, and displays the final graph |

## Program & Output
## Input 1
```
# 1. Import required libraries
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

# 2. Define manual data arrays
x = np.array([20, 22, 25, 70, 75, 80, 30, 35,
              32, 24, 28, 75, 71, 83, 28, 27])

y = np.array([30, 35, 40, 80, 85, 90, 70, 75,
              33, 31, 45, 70, 83, 89, 60, 67])

# 3. Combine X and Y values
X = np.column_stack((x, y))
X
```
## Output 1
```
array([[20, 30],
       [22, 35],
       [25, 40],
       [70, 80],
       [75, 85],
       [80, 90],
       [30, 70],
       [35, 75],
       [32, 33],
       [24, 31],
       [28, 45],
       [75, 70],
       [71, 83],
       [83, 89],
       [28, 60],
       [27, 67]])
```
## Input 2
```
# 4. Apply K-Means clustering
kmeans = KMeans(n_clusters=3, random_state=42, n_init='auto')
labels = kmeans.fit_predict(X)
labels
```
## Output 2
```
array([1, 1, 1, 0, 0, 0, 2, 2, 1, 1, 1, 0, 0, 0, 2, 2], dtype=int32)
```
## Input 3
```
# 5. Retrieve cluster centroids
centroids = kmeans.cluster_centers_
centroids
```
## Output 3
```
array([[75.66666667, 82.83333333],
       [25.16666667, 35.66666667],
       [30.        , 68.        ]])
```
## Input 
```
# 6. Visualize clusters
plt.figure(figsize=(8, 6))

plt.scatter(X[:, 0], X[:, 1],
            c=labels, cmap='viridis',
            s=100, alpha=0.8)

plt.scatter(centroids[:, 0], centroids[:, 1],
            c='red', marker='X',
            s=200, label='Centroids')

plt.title('K-Means Clustering for Market Segmentation')
plt.xlabel('Feature 1 (Annual Income)')
plt.ylabel('Feature 2 (Spending Score)')
plt.legend()
plt.grid(True)
plt.show()
```
## Output
<img width="686" height="547" alt="image" src="https://github.com/user-attachments/assets/7196b253-0f0b-42e8-b477-d01ec7a82d89" />

## Input
```
# 7. Display cluster details
print("Cluster Labels for Data Points:")
print(labels)

print("\nCluster Centroids (Coordinates):")
print(centroids)
```
## Output
```
Cluster Labels for Data Points:
[1 1 1 0 0 0 2 2 1 1 1 0 0 0 2 2]

Cluster Centroids (Coordinates):
[[75.66666667 82.83333333]
 [25.16666667 35.66666667]
 [30.         68.        ]]
```

## Result

Thus, the K-Means Clustering algorithm was implemented using Python to group similar data points into distinct clusters. The clusters were visualized and analysed for market segmentation, and the objective was successfully achieved.
