# EX:10  Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
```
Step 1. Start the program

Step 2. Import the necessary python libraries

Step 3. Read the dataset of Mall_Customers csv file

Step 4. From sklearn libraary select the cluster and import KMeans Clustering

Step 5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method

Step 6. Plot the graph x and y as Number of Clusters and wcss respectively

Step 7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)

Step 8. Stop the program
```
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: APARNA RB
RegisterNumber:  212222220005
*/
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv(r"C:\Users\admin\Downloads\Mall_Customers.csv")

data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []  # Within-Cluster Sum of Square
# It is the sum of squared distance between each point & the centroid in a cluster.
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++")
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")

km = KMeans(n_clusters=5)
km.fit(data.iloc[:, 3:])

KMeans(n_clusters=5)

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data['cluster'] = y_pred
o = data[data['cluster'] == 0]
p = data[data['cluster'] == 1]
q = data[data['cluster'] == 2]
r = data[data['cluster'] == 3]
s = data[data['cluster'] == 4]

plt.scatter(o['Annual Income (k$)'], o['Spending Score (1-100)'], c="red", label="cluster0")
plt.scatter(p['Annual Income (k$)'], p['Spending Score (1-100)'], c="blue", label="cluster1")
plt.scatter(q['Annual Income (k$)'], q['Spending Score (1-100)'], c="green", label="cluster2")
plt.scatter(r['Annual Income (k$)'], r['Spending Score (1-100)'], c="orange", label="cluster3")
plt.scatter(s['Annual Income (k$)'], s['Spending Score (1-100)'], c="magenta", label="cluster4")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.legend()
plt.title("Customer Segments")

```

## Output:
## head :
![image](https://github.com/user-attachments/assets/7bf7434f-0f56-4112-9e3d-76ffbf5b4954)
## Info :
![image](https://github.com/user-attachments/assets/c045d291-5e6d-4081-b179-0bbb615a7f07)
## No.of Null-Values :
![image](https://github.com/user-attachments/assets/8aa0c0c3-e923-4431-aebc-8f68d325ede1)
## Graph:
![image](https://github.com/user-attachments/assets/c8ebd40f-a13d-4573-b73d-c198851511c0)
## No.of clusters :
![image](https://github.com/user-attachments/assets/6f5e5040-cb67-4d8e-8c65-ba09028dc93b)
## Predicted values :
![image](https://github.com/user-attachments/assets/b13ac1c0-f07f-4ea3-b82b-5bded3b0b89b)
## Customer Segments :
![image](https://github.com/user-attachments/assets/9793e7e6-9e9d-41cd-9d51-05f8ffc1e178)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
