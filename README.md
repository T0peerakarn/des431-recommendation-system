# DES431 Project - Reccomendation System

## Overview

This in-class project for the Big Data Analytics course focuses on developing a movie recommender system that predicts user ratings for unseen movies. The dataset includes information on 610 users, 9,742 movies, and their classification across 20 genres. The goal is to create a function that leverages user preferences, movie details, and genre information to predict ratings with a lower Root Mean Square Error (RMSE) compared to the baseline model.

## Proposed Solution

The solution is based on item-based collaborative filtering

> People have different preferences for different movie genres

---

Define $P_{i, j}$ as how much $user_i$ prefers $genre_j$, and $P_{i,j}$ is calculated by

$$
P_{i, j} = \bar{r_i} + \underset{j}{avg}(r_{i, k})
$$

where

- $\bar{r}_i$ is the average rating voted by the $user_i$
- $\underset{j}{avg}(r_{i, k})$ is the rating that $user_i$ votes to the movie such that the movie contains the $genre_j$

---

Define $T_{i, j}$ as how much $movie_i$ tends to be $genre_j$, and $T_{i, j}$ is calculated by

$$
T_{i, j} =
\begin{cases}
  \frac{1}{N_i}, & \text{the } movie_i \text{ contains the } genre_j \\
  0, & \text{otherwise}
\end{cases}
$$

where

- $N_i$ is the number of genres of the $movie_i$

---

Then, the predicted rating of $user_i$ to the $movie_j$, $\hat{r}_{i, j}$, is calculated by

$$\hat{r}_{i, j} = P_i \cdot (T_j)^T$$

## Result

The proposed solution achieved an RMSE of 0.8976, outperforming the native solution's RMSE of 0.9171.
