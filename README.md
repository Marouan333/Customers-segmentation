# 🛍️ Mall Customers Segmentation using KMeans

This project applies **KMeans clustering** to segment mall customers based on their **Annual Income** and **Spending Score**.  
Customer segmentation helps businesses understand their customers better and apply targeted marketing strategies.

---

## 📂 Dataset

The dataset used is **Mall_Customers.csv**, which contains the following columns:

- **CustomerID** → Unique identifier for each customer  
- **Gender** → Male / Female  
- **Age** → Customer age  
- **Annual Income (k$)** → Income in thousands  
- **Spending Score (1–100)** → Score assigned by the mall (1 = low, 100 = high)  

Example:

| CustomerID | Gender | Age | Annual Income (k$) | Spending Score (1-100) |
|------------|--------|-----|--------------------|-------------------------|
| 1          | Male   | 19  | 15                 | 39                      |
| 2          | Male   | 21  | 15                 | 81                      |
| 3          | Female | 20  | 16                 | 6                       |
| 4          | Female | 23  | 16                 | 77                      |
| 5          | Female | 31  | 17                 | 40                      |

---

## 🧑‍💻 Steps Performed

1. **Data Exploration**  
   - Loaded dataset with pandas  
   - Checked shape, missing values, summary statistics  

2. **Feature Selection**  
   - Selected **Annual Income** and **Spending Score** as features:  
     ```python
     X = ds.iloc[:, [3, 4]].values
     ```

3. **Finding Optimal Clusters (Elbow Method)**  
   - Used **WCSS (Within-Cluster Sum of Squares)** to evaluate different `k` values  
   - Found that the optimal number of clusters is **5**

   ![Elbow Method](elbow_plot.png)

4. **Applying KMeans**  
   - Trained model with 5 clusters:  
     ```python
     kmeans = KMeans(n_clusters=5, init='k-means++', random_state=0)
     Y = kmeans.fit_predict(X)
     ```

5. **Visualization of Clusters**  
   - Plotted customer clusters with matplotlib  
   - Marked centroids for each cluster  

   ![Customer Clusters](clusters.png)

---

## 📊 Cluster Interpretation

Based on **Annual Income** and **Spending Score**, the 5 clusters represent:

1. **Low Income, Low Spending** → “Savers”  
2. **Low Income, High Spending** → “Impulsive Buyers”  
3. **High Income, Low Spending** → “Cautious Customers”  
4. **High Income, High Spending** → “Target Customers”  
5. **Average Income & Spending** → “Standard Customers”  

---

## 🚀 How to Run

1. Clone this repo:
   ```bash
   git clone https://github.com/your-username/mall-customers-kmeans.git
   cd mall-customers-kmeans
   pip install -r requirements.txt
