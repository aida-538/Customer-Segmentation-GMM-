# Customer Segmentation Using RFM, PCA, and Gaussian Mixture Models

##  Project Overview
This project performs customer segmentation on a large Online Retail dataset to identify distinct customer groups based on purchasing behavior. Unlike traditional clustering methods (like K-Means), this project utilizes **Gaussian Mixture Models (GMM)** to allow for soft clustering, accounting for the uncertainty in customer behavior.

The goal is to enable the marketing team to target specific clusters with tailored campaigns, such as re-engaging dormant users or rewarding VIPs.

##  Dataset
The analysis uses the **Online Retail** dataset containing over **500,000 transactions**.
* **Source:** [Include Link to Source if known, e.g., UCI Machine Learning Repo]
* **Key Features:** `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, `Country`.

##  Tech Stack
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-learn (PCA, GaussianMixture, StandardScaler)

##  Methodology
1.  **Data Cleaning:**
    * Removed cancelled transactions (InvoiceNo starting with 'C').
    * Filtered out rows with missing `CustomerID` or invalid prices/quantities.
2.  **Feature Engineering (RFM):**
    * **Recency (R):** Days since last purchase.
    * **Frequency (F):** Total number of transactions.
    * **Monetary (M):** Total money spent.
3.  **Dimensionality Reduction:**
    * Applied **StandardScaler** to normalize the skewed RFM data.
    * Used **PCA (Principal Component Analysis)** to reduce dimensions to 2 components, capturing **85% of the variance**.
4.  **Modeling (GMM):**
    * Tested cluster counts (k=1 to 10) using **BIC (Bayesian Information Criterion)**.
    * Selected **k=6** as the optimal number of clusters based on the BIC elbow point.

##  Results & Customer Segments
The model identified **6 distinct customer segments**:

| Cluster | Segment Name | Characteristics | Strategy |
| :--- | :--- | :--- | :--- |
| **0** | **Low-Spend Occasional** | Active recently, but spend little and buy rarely. | Use low-cost promotions to increase basket size. |
| **1** | **Loyal High-Spenders** | Frequent buyers with high spending. | Reward loyalty with VIP perks. |
| **2** | **Inactive / Lost** | Very low spend, haven't bought in a long time. | Don't invest heavy marketing budget. |
| **3** | **Elite Super VIPs** | Extreme high value and frequency (Outliers). | Assign dedicated account managers; exclusive offers. |
| **4** | **Dormant** | Historically low spenders who stopped buying. | Automated low-cost reactivation emails. |
| **5** | **Active Mid-Spenders** | Decent spending and frequency. | Target with personalized recommendations to upsell. |

##  Key Insights
* **Soft Clustering:** GMM allowed us to calculate the *probability* of a customer belonging to a cluster. We found that **~90% of customers** were assigned to a cluster with >60% confidence, while 10% were "borderline" cases requiring nuanced marketing.
* **PCA Interpretation:**
    * **PC1:** Represents "Customer Value" (High Frequency/Monetary).
    * **PC2:** Represents "Inactivity" (High Recency).


   ```bash
   git clone [https://github.com/yourusername/Customer-Segmentation-GMM.git](https://github.com/yourusername/Customer-Segmentation-GMM.git)
