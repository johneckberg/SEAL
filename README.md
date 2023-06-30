Project: Efficient Vector Similarity Search with Adversarial Random Forests (ARF)
Overview

This project introduces an innovative method for performing efficient similarity search over high-dimensional vectors. We leverage Adversarial Random Forests (ARF), a machine learning algorithm traditionally used for classification tasks, and repurpose it as a learned hashing mechanism. This approach significantly reduces the number of pairwise similarity computations required for nearest neighbor searches in large, high-dimensional datasets.

The repository includes Python scripts for creating vector embeddings using LASER, indexing them using ARF from the arfpy package, and performing efficient similarity searches.
Theoretical Background

ARF is an iterative algorithm that partitions a dataset into distinct regions, or "leaves". The goal of ARF is to ensure that the data within each leaf is as independent as possible, meaning there should be no predictable relationship among vectors within the leaf based on the dimensions considered.

In the context of vector similarity, we aim for similar vectors to be grouped in the same leaf. When a new vector is introduced, we can quickly identify a smaller set of potential nearest neighbors by examining other vectors in the same leaf, rather than the entire dataset.

ARF achieves this by identifying splits in the data space that best separate vectors based on their target variable values. If the target variable accurately captures the similarity of the vectors (for instance, semantic similarity for text embeddings), the process should result in leaves where vectors are highly similar to each other.

The convergence property of ARF provides a mathematical guarantee that as the number of vectors increases, the ARF algorithm will increasingly accurately map similar vectors to the same leaf. This can be expressed as:

P(H(v1) ≠ H(v2)|similarity(v1, v2) > threshold) → 0 as n → ∞

This means that the probability that similar vectors v1 and v2 (based on some similarity measure and a chosen threshold) are mapped to different leaves converges to 0 as the number of vectors n goes to infinity. In other words, the ARF algorithm becomes increasingly accurate at mapping similar vectors to the same leaf as the dataset grows.
Practical Application

In this project, we utilize ARF as a learned hashing mechanism. It maps similar vectors to the same leaf (or "hash bucket"), allowing us to dramatically reduce the number of pairwise similarity computations we need to make. This accelerates the search process in large, high-dimensional datasets.

The project's scripts can be adapted for various types of high-dimensional vectors, including text embeddings, image feature vectors, and more.
