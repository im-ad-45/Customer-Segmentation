# Customer Segmentation using K-Means Clustering and PCA

**Author:** Aditya Shukla

**Registration Number:** 23BAI10155

**Application Number:** IN26011099

**Batch Number:** 1(A)

**Email ID:** aditya.23bai10155@vitbhopal.ac.in

## Objective
The objective of this project is to segment mall customers into groups based on their age, gender, annual income, and spending behavior using K-Means Clustering, and to visualize those clusters in two dimensions using Principal Component Analysis (PCA).

## Dataset Link
- [Kaggle: Mall Customer Segmentation Dataset](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python)

## Libraries Used
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

## Methodology
1. **Data Understanding**: Loaded the dataset (200 customers) and identified `Age`, `Annual Income (k$)`, and `Spending Score (1-100)` as numerical features and `Gender` as the categorical feature. Inspected structure and summary statistics using `.info()` and `.describe()`.
2. **Data Preprocessing**:
   - Checked for missing values (none found).
   - Dropped the `CustomerID` column, since it's just a row identifier with no predictive signal.
   - Encoded `Gender` (Female -> 0, Male -> 1) using `LabelEncoder`.
   - Standardized all features using `StandardScaler`, since K-Means is a distance-based algorithm.
3. **Model Development**:
   - Used the Elbow Method (inertia across K = 1 to 10) to select K = 5.
   - Trained a `KMeans` model with K = 5 and assigned a cluster label to each customer.
   - Applied `PCA` to reduce the 4 standardized features to 2 principal components.
4. **Visualization and Evaluation**: Plotted the Elbow Curve, a scatter plot of clusters on Annual Income vs Spending Score, and a PCA-based 2D scatter plot colored by cluster.

## Results
- **Optimal K (Elbow Method):** 5
- **Variance captured by 2 principal components:** ~59.9%
- Clusters map onto recognizable customer segments (e.g. high-income/high-spending, high-income/low-spending, average income/average spending, low-income/high-spending, low-income/low-spending), visible in both the raw Income-vs-Spending plot and the PCA plot.

## Conclusion
This project applied K-Means clustering to segment mall customers based on their age, gender, annual income, and spending score, using the Elbow Method to justify K=5 as the number of clusters. The resulting groups map cleanly onto real marketing personas, for example high-income big spenders versus high-income conservative spenders, giving the mall's management concrete segments to target with different campaigns. Principal Component Analysis was used to compress the four standardized features into two components purely for visualization; it's worth noting these 2 components captured only about 60% of the total variance here, so the PCA plot is a useful approximation of the cluster structure rather than a complete picture. A key limitation of K-Means is that it requires the number of clusters to be chosen in advance and assumes roughly spherical, similarly sized clusters, so it can perform poorly on irregularly shaped or overlapping groups. A key advantage of PCA is that it makes high-dimensional data interpretable and visualizable in 2D without needing to arbitrarily pick just two original features and discard the rest.
