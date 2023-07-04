Seal: Similarity Estimation from Adversarial Learning

The Seal class is used to index and query data using Adversarial Random Forests (ARF). The primary concept behind the algorithm is to ensure that data are jointly independent within each leaf of the ARF.
Key Concepts:

Adversarial Random Forests (ARF): ARF is a modification of the standard Random Forest algorithm. The ARF algorithm iteratively generates synthetic data and trains classifiers to distinguish between the original and synthetic data. The iteration continues until the classifier's out-of-bag accuracy falls below a certain threshold, indicating that the synthetic and original data are near-indistinguishable.

Leaf Coverage: Each leaf of an ARF covers a hyper-rectangular subspace in the feature space, representing a subset of adjacent vectors. The accuracy of this coverage improves as the error of coverage reduces, leading to a more refined partitioning of the feature space.

Indexing and Querying: The Seal class uses ARF for indexing and querying. In the indexing phase, it trains an ARF model on the data and maps each leaf to the indices of data points falling within it. During the query phase, it identifies the leaves that a new data point falls into and returns the most similar data point within those leaves based on cosine similarity.
Improvements with Larger Datasets:

As the dataset size increases, the indexing generally becomes more accurate due to better density estimation and reduced coverage error. A larger dataset provides a more accurate estimation of the underlying data density, leading to improved partitioning of the feature space. Additionally, the Glivenko-Cantelli theorem guarantees that the empirical distribution of data within each leaf node converges to the true underlying distribution as the dataset size increases, reducing the error of coverage. Consequently, each leaf node covers a more accurate subset of the feature space. However, while more data typically lead to better performance, there are diminishing returns beyond a certain dataset size. Also, data quality and diversity, model parameters, and the complexity of the underlying data distribution can impact the effectiveness of the indexing.
