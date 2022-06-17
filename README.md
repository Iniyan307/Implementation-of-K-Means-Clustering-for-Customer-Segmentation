# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Import the standard Libraries.
2. Import KMeans from sklearn.cluster.
3. Inside for loop define kmeans and append it in wcss.
4. Define km and use it predict y_pred.
5. Cluster the predicted data and print it.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Iniyan S
RegisterNumber:  212220040053
*/

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/sample_data/Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow method")

km =KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="yellow",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="#00b3ff",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="#00ff22",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="#f7861b",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:
### head():
![OP](/OP1.png)
### info():
![OP](/OP2.png)
### Elbow Method :
![OP](/OP3.png)
### y_pred:
![OP](/OP4.png)
### Customer Segments :
![OP](/OP5.png)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
