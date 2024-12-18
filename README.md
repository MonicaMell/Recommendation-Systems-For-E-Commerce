# E-Commerce Product Recommendation System

## Tasks Completed So Far

Here is the [link to the GitHub repository](https://github.com/MonicaMell/Recommender-System-for-E-commerce).

### Dataset Acquisition

We have used an Amazon dataset on user ratings for beauty products. This dataset doesn't have any headers. To avoid biases, each product and user is assigned a unique identifier instead of using their name or any other potentially biased information.

You can find the dataset here: [Beauty Products Recommendation](https://www.kaggle.com/datasets).

You can find many other similar datasets here: [Amazon Datasets](https://www.amazon.com).

---

### Exploratory Data Analysis (EDA) Phase

The primary goal of this phase was to understand the dataset's structure, identify patterns, detect anomalies, and prepare the data for further modeling. 

**Implementation:**
- **Data Inspection:** The dataset was loaded and basic statistics such as data types, missing values, and summary statistics were reviewed.
- **Visualization:** Various plots were created to explore the distribution of features, item frequencies, and user behaviors. These visualizations include histograms, box plots, and bar charts to understand the spread of data and identify any potential outliers.

**Key Insights:**
- A deep dive into the most popular products revealed that certain categories of beauty products had much higher user ratings and interactions than others.
- The distribution is skewed to the right. Over 50% of the ratings are 5 stars, followed by just under 20% with 4-star ratings. The percentages of ratings continue to decrease, with fewer than 10% of the ratings being 2 stars.

---

### Pre-Processing

The goal of this task was to prepare the Amazon beauty products dataset for use in the recommendation system.

**Implementation:**
- **Filtering:** Users who had provided fewer than 30 ratings were excluded to ensure the model had enough interaction data for each user. This was done to improve recommendation quality by focusing on active users, reducing sparsity in the dataset, and making it easier to work with.
- **Density Check:** The matrix density was checked to determine how sparse or dense the dataset was, helping decide on the best data preparation strategy.

**Key Insights:**
- After filtering, the dataset was significantly reduced but had a much higher interaction density, leading to more reliable recommendation performance.

---

### Rank-Based Recommendation System

**Objective:**  
Recommend products with the highest number of ratings. Target new customers with the most popular products and solve the Cold Start Problem.

**Outputs:**  
Recommend top 5 products with a minimum number of ratings.

**Approach:**  
- Calculate the average rating for each product.
- Calculate the total number of ratings for each product.
- Create a DataFrame using these values and sort it by average.
- Write a function to get the top 'n' products with specified minimum number of interactions.

---

### User-Based Collaborative Filtering

**Objective:**  
Provide personalized and relevant recommendations to users.

**Outputs:**  
Recommend top 5 products based on interactions of similar users.

**Approach:**  
- Convert the `user_id` from an object type to integer type for convenience.
- Write a function to find similar users based on cosine similarity.
- Extract the similar users and their similarity scores, remove the original user, and return the rest.
- Write a function to recommend users based on their similarity with other users, returning products that the similar users have interacted with but the actual user has not.

---

### Model-Based Collaborative Filtering

**Objective:**  
Provide personalized recommendations to users based on their past behavior and preferences, while addressing the challenges of sparsity and scalability.

**Outputs:**  
Recommend top n products for a particular user.

**Approach:**  
- Convert the matrix of product ratings to a CSR (Compressed Sparse Row) matrix to save memory and computational time, focusing only on non-zero values.
- Perform Singular Value Decomposition (SVD) on the sparse matrix to reduce its dimensionality to 50 latent features.
- Calculate predicted ratings for all users by multiplying the U matrix, the sigma matrix, and the Vt matrix.
- Store predicted ratings in a DataFrame with the same columns as the original matrix.
- Write a function to recommend products based on predicted ratings, filtering out products the user has already rated.

---

### Recommending System Using KNN

**Objective:**  
Implement a K-Nearest Neighbors (KNN) algorithm to provide recommendations by identifying similar users or items based on existing ratings data.

**Approach:**  
- **Algorithm Type:** KNN identifies similarities between users and items.
- **Distance Metric:** Use cosine similarity to compute the similarity between items, which measures the cosine of the angle between two non-zero vectors.
- **KNN Application:** Apply KNN to identify the top 50 similar items for each product based on cosine similarity scores.
- **Recommendation Generation:** Suggest items most similar to those the user has already interacted with.

---

### Evaluating the Model

To evaluate the effectiveness of our recommendation systems:

- Calculate the average rating for all items by dividing the sum of all the ratings by the number of ratings.
- Calculate the average rating for all the predicted ratings.
- Create a DataFrame (`rmse_df`) containing the average actual ratings and the average predicted ratings.
- Calculate the RMSE (Root Mean Square Error) by taking the square root of the mean squared errors between the actual ratings and the predicted ratings.

---

## Prerequisites

- Install Python 3.7 or higher.
- Jupyter Notebook or similar environment.
- Ensure the following Python libraries are installed:
  - `numpy`
  - `pandas`
  - `matplotlib`
  - `warnings`
  - `scikit-learn`
  - `scipy`

---

## Running the Code

To clone the repository to your local machine, use the following command:

```bash
git clone https://github.com/MonicaMell/Recommendation-Systems-For-E-Commerce
