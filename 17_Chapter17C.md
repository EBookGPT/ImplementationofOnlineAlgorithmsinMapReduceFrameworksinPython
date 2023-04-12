# Chapter 17 - Clustering Algorithms: K-means and Hierarchical Clustering

Welcome to another exciting chapter on the Implementation of Online Algorithms in Map-Reduce Frameworks in Python. In this chapter, we will discuss two popular clustering algorithms - K-means and Hierarchical Clustering.

Clustering is the process of grouping similar objects together based on their features or characteristics. It is an essential task in many fields, such as machine learning, data mining, bioinformatics, and pattern recognition.

K-means and Hierarchical Clustering are popular clustering algorithms due to their simplicity, effectiveness and ease of implementation. K-means involves partitioning data into K clusters, where K is a pre-defined number of clusters, and selecting centroids for each cluster, which serves as the average of all the points in the cluster. Hierarchical clustering, on the other hand, builds a hierarchy of clusters by merging and splitting them iteratively.

In this chapter, you will learn how to implement both K-means and Hierarchical Clustering algorithms in Map-Reduce Frameworks in Python. We will also show how to evaluate the clustering results using various metrics such as inertia, silhouette score, and Calinski-Harabasz index.

So, buckle up and get ready to learn how to perform clustering using K-means and Hierarchical Clustering algorithms in Python. It is going to be a thrilling adventure!
# Chapter 17 - Clustering Algorithms: K-means and Hierarchical Clustering

## The Mysterious Disappearance of the Jewelry Store Owner

Sherlock Holmes was sitting in his apartment, lost in thought when his friend Dr. John Watson entered with a newspaper in hand.

"Good morning, Holmes," Watson greeted, "Have you heard about the disappearance of the owner of ‘Angelina’s jewelry store’?"

"No Watson, I haven't," replied Holmes, his interest piqued.

"Well, it seems that Mr. Angelina disappeared from his store yesterday, and there is no sign of forced entry or struggle," Watson explained, "The police are out of leads."

Holmes quickly put on his coat and rushed to the store. Upon arrival, he studied the surrounding area and analyzed the store's transaction records to find any patterns or potential suspects. However, with over a million transactions, it was nearly impossible to find anything significant.

That's when Holmes had an idea. He decided to implement K-means clustering on the transaction data to group the transactions into categories based on similar purchase amounts and frequency. Once grouped, he studied each category and found that the owner's transactions fell into a cluster with high transaction amounts.

Holmes was onto something. He implemented hierarchical clustering to further investigate the cluster and determined that a group of regular customers had made purchases at similar amounts and frequencies as the owner. One of these regular customers hadn't made a purchase in 2 months, which was unusual. They had also made a purchase just before the disappearance of the jewelry store owner.

Holmes quickly rushed to the customer's location, where he found the owner locked up in a trunk in the customer's basement. The customer had abducted the owner with hopes of gaining access to the store's safe.

## Resolution

Thanks to the power of K-means and hierarchical clustering algorithms, Holmes was able to uncover the kidnapper and save the missing owner. These algorithms are commonly used in many fields such as marketing, customer segmentation, and recommendation systems to group similar objects together based on their features. By applying these algorithms in Python, it is possible to find valuable insights in large datasets and make data-driven decisions.

Now that you've seen the power of clustering algorithms first hand, it is time for you to take a shot at implementing them. In the next section, we will go through some examples of how to implement K-means and hierarchical clustering algorithms in Python using the Map-Reduce Frameworks. Let's get started!
# Chapter 17 - Clustering Algorithms: K-means and Hierarchical Clustering

## The Mysterious Disappearance of the Jewelry Store Owner

To solve the case of the missing jewelry store owner, Sherlock Holmes implemented K-means and hierarchical clustering algorithms. Let's take a look at the Python code he used to do it.

### K-means Clustering

First, Holmes imported the necessary libraries, including the KMeans algorithm from the scikit-learn library, which provides implementations of many machine learning algorithms in Python.

```python
import pandas as pd
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

#Load Data from the CSV file
data = pd.read_csv("jewelry_store_transactions.csv")

#Standardize the Data
scaler = StandardScaler()
X = scaler.fit_transform(data)

#KMeans Clustering
kmeans = KMeans(n_clusters=6,random_state=0)
kmeans.fit(X)

#Get Cluster Labels
labels = kmeans.labels_

#Add Labels to the Original Dataset
data["Cluster"]=labels
```

After loading the transaction data into a Pandas DataFrame, Holmes used the StandardScaler from scikit-learn to standardize the data, which is essential for K-means clustering. Then, he created a KMeans object with n_clusters set to 6, which is the number of clusters he wanted the algorithm to group the data into. He trained the algorithm on the standardized data and obtained the cluster labels for each transaction, which he added to the original DataFrame.

### Hierarchical Clustering

Next, Holmes implemented hierarchical clustering using the AgglomerativeClustering algorithm from scikit-learn. 

```python
from sklearn.cluster import AgglomerativeClustering

#Hierarchical Clustering
hierarchical = AgglomerativeClustering(n_clusters=6)
hierarchical.fit(X)

#Get Cluster Labels
labels = hierarchical.labels_

#Add Labels to the Original Dataset
data["Cluster"]=labels
```

The code for hierarchical clustering is similar to the K-means algorithm, with the main difference being the AgglomerativeClustering algorithm. After training the algorithm on the standardized data, Holmes obtained the cluster labels and added them to the DataFrame.

Once the clustering was complete, Holmes analyzed the data and discovered that the owner's transactions fell into a cluster with high transaction amounts. He then used hierarchical clustering to further investigate the cluster and identify a group of regular customers who had made purchases at similar amounts and frequencies as the owner. By analyzing the transactions of the regular customers, Holmes was able to identify and locate the kidnapper.

In conclusion, clustering algorithms can be powerful tools for uncovering patterns and insights in large datasets. With Python and scikit-learn, it is relatively easy to implement both K-means and hierarchical clustering algorithms and put them to work on real-world problems.