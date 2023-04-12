# Chapter 18: Dimension Reduction Algorithms- Principal Component Analysis (PCA) and Singular Value Decomposition (SVD) 

*"When you have eliminated the impossible, whatever remains, however improbable, must be the truth” - Sherlock Holmes*

Welcome fellow detectives to another exciting chapter of our adventure in the world of Big Data and Machine Learning. In the previous chapter, we examined the puzzle of clustering algorithms and the fascinating world of K-means and hierarchical clustering. Our special guest, Geoffrey Hinton, imparted his invaluable insights into these algorithms and their practical applications.
 
As we progress further, it's time to unravel another mystery of Machine Learning. In this chapter, we will uncover the secrets of two significant dimension reduction algorithms, Principal Component Analysis (PCA) and Singular Value Decomposition (SVD). PCA and SVD play a crucial role in the world of big data and machine learning.
 
Dimension reduction algorithms are indispensable because they help us deal with data that is excessively large and complex by reducing its dimensions while preserving its information. These algorithms find the underlying structure and patterns of the data and efficiently represent the data in its lower dimensional form. 

Now, let us follow the script and accompany our dear friend, Sherlock Holmes, as he explores the world of PCA and SVD. Who knows what complex and perplexing situations await us? Let's join hands and get started on this exciting journey of exploration and discovery.
# Chapter 18: Dimension Reduction Algorithms- Principal Component Analysis (PCA) and Singular Value Decomposition (SVD) 

*"When you have eliminated the impossible, whatever remains, however improbable, must be the truth” - Sherlock Holmes*

The famous physicist, Enrico Fermi, was once asked if he believed in extraterrestrial life, to which he replied, "They are among us, but we don't recognize them." It is this line of thinking that has directed us on our newest adventure. 

Sherlock Holmes had been summoned by Scotland Yard to investigate a data breach at the Greenwich Observatory. They reported that their telescope data had been tampered with, and the stars' coordinates seemed to have changed. The Observatory was a data hub, and its data sets were critical for navigation for ships and planes.

Accompanied by Dr. John Watson, Holmes arrived at the observatory and began investigating the breach. However, they couldn't make sense of the data. There were far too many dimensions, and it was impossible to glean any information from it.

This is where our esteemed guest, Geoffrey Hinton, came into the picture. He suggested that they use PCA and SVD to reduce the dimensions of the data, thereby making it easier to understand. PCA creates new dimensions that capture the maximum variability in the data, while SVD decomposes the data into its fundamental components, making it easier to understand.

Using Python, they implemented PCA and SVD and discovered that the data was not tampered with. Instead, the new coordinates were due to the movement of the Earth's crust. They had uncovered a geological discovery!

It was revealed that the telescopes' data needed to be treated carefully and needed to be regularly processed into smaller sets to study the Earth's movement. If not handled properly, it could lead to miscalculated navigational data.

In conclusion, PCA and SVD allowed the detectives to uncover a critical geological discovery by reducing the dimensions of the data. It opened doors to entirely different interpretations and insights into the data that they would have never discovered without deploying these algorithms.
To solve the mystery of the data breach at the Greenwich Observatory, Sherlock Holmes and Dr. Watson turned to dimension reduction algorithms, PCA, and SVD, to help make sense of the vast amount of data they had received.

Python provides several libraries that can carry out PCA and SVD on large datasets. Let us take a look at the code that helped the detectives solve the case:

First, they imported the necessary libraries such as Numpy, Pandas, and Scikit-learn. 

```python
import pandas as pd
import numpy as np
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
from scipy.linalg import svd
```

Next, they cleaned the data, removed missing values, and scaled it using the Standard Scaler. This standardization helps the PCA algorithm to operate more efficiently.

```python
# Clean and preprocess the data
df = pd.read_csv('observatory_data.csv')
df = df.dropna()
X = df.iloc[:, 1:].values
X = StandardScaler().fit_transform(X)
```

Then, they implemented the PCA algorithm to reduce the number of dimensions and visualize the data in a two-dimensional plane.

```python
# Implement PCA algorithm
pca = PCA(n_components=2)
principal_components = pca.fit_transform(X)
principal_df = pd.DataFrame(data=principal_components, columns=['PC1', 'PC2'])

# Visualize PCA results
fig = plt.figure(figsize=(8, 8))
ax = fig.add_subplot(1, 1, 1)
ax.set_xlabel('Principal Component 1', fontsize=15)
ax.set_ylabel('Principal Component 2', fontsize=15)
ax.set_title('2 Component PCA', fontsize=20)
ax.scatter(principal_df['PC1'], principal_df['PC2'], c='b', s=50)
```

Finally, they implemented Singular Value Decomposition and recovered the original data matrix with a reduced number of dimensions.

```python
# Implement the SVD algorithm
U, s, VT = svd(X)

# Select top k singular vectors to represent matrix X
k = 5
sigma = np.zeros((X.shape[0], X.shape[1]))
sigma[:k, :k] = np.diag(s[:k])
B = U @ sigma @ VT
```

By using PCA and SVD on the vast data sets, Sherlock and Watson were able to detect the subtle changes in the stars' coordinates caused by the Earth's movement, ultimately solving the data breach of the Greenwich Observatory.

Dimension reduction algorithms play a crucial role in big data analytics and help drive unimaginable discoveries.