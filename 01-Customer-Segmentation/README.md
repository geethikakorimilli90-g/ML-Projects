# Customer Segmentation using K-Means Clustering

## 📌 Project Overview

This project uses the K-Means clustering algorithm to segment mall customers based on their Annual Income and Spending Score. The goal is to identify different groups of customers and understand their spending behavior.

## 🎯 Objective

To divide customers into meaningful groups based on:

- Annual Income
- Spending Score

## 📊 Dataset

The dataset contains information about 200 mall customers with the following features:

- CustomerID
- Gender
- Age
- Annual Income (k$)
- Spending Score (1-100)

## 🛠️ Technologies Used

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Scikit-learn

## 🤖 Machine Learning Algorithm

K-Means Clustering is used to group customers into different clusters. The Elbow Method was used to determine the optimal number of clusters.

**Optimal Number of Clusters: 5**

## 📈 Customer Segments

The customers were divided into five segments:

- Standard Customers
- Premium Customers
- High-Spending Customers
- Potential Customers
- Low-Value Customers

## 💡 Key Insights

- Premium customers have high income and high spending scores.
- Potential customers have high income but low spending scores.
- Low-income customers can still have high spending behavior.
- Customer segmentation can help businesses create targeted marketing strategies.

## 🚀 Project Workflow

Dataset  
↓  
Data Exploration  
↓  
Data Cleaning  
↓  
Feature Selection  
↓  
Elbow Method  
↓  
K-Means Clustering  
↓  
Customer Segmentation  
↓  
Business Insights

## 📁 Project Structure

```text
01-Customer-Segmentation/
│
├── Customer_Segmentation_KMeans.ipynb
└── README.md
