# 🎬 Collaborative Filtering for Movie Recommendation & Valuation

This repository contains **Case 2 from Modern Analytics**, where I built a **collaborative filtering recommender system** to move beyond movie popularity and estimate **true movie value based on user engagement**.

The project combines **exploratory data analysis, matrix factorization with embeddings, model tuning, and business-oriented valuation**, similar to recommender systems used by Netflix, Amazon Prime, and Spotify.

---

## 📂 Repository Contents

```text
.
├── Case_2_CollaborativeFiltering_(Exercises).ipynb   # End-to-end collaborative filtering model
├── Modern Analytics_Case2_Team12.pdf                 # Final written report & analysis
└── README.md                                         # Project overview (this file)
```

---

## 🎯 Project Goals

* Understand **user behavior** and **movie popularity distributions**
* Build a **collaborative filtering model** using latent embeddings
* Predict user–movie ratings accurately
* Use predictions to **estimate movie value** beyond simple popularity
* Compare **popularity-based ranking vs. model-based valuation**

---

## 🔍 Exploratory Analysis

Before modeling, I analyzed structural patterns in the data:

* **Movie popularity**: number of ratings per movie

  * Long-tail distribution: most movies receive very few ratings
* **User activity**: number of ratings per user

  * A small subset of users contributes the majority of ratings
* **Highly rated vs. popular movies**:

  * Many 5-star movies have only 1–2 ratings (statistically unreliable)
  * Movies with both high ratings *and* large rating counts are more trustworthy

This step motivated the need for a **personalized, model-based approach** instead of raw averages.

---

## 🤖 Modeling Approach

### Model

* **Collaborative Filtering with Matrix Factorization**
* Learned:

  * **User embeddings** (latent preferences)
  * **Movie embeddings** (latent attributes)
  * **User bias** and **movie bias** terms

Predicted rating:

```
Rating ≈ global_mean + user_bias + movie_bias + (user_embedding · movie_embedding)
```

### Training

* Optimized using **gradient descent**
* Tuned key hyperparameters:

  * Embedding dimension
  * Learning rate
  * L2 regularization
  * Number of training epochs
* Used **validation loss** to select early stopping point

### Evaluation Metrics

* **RMSE** (Root Mean Squared Error)
* **MAE** (Mean Absolute Error)

Best model achieved:

* **Validation RMSE ≈ 0.857**
* **Test RMSE ≈ 0.888**
* **Test MAE ≈ 0.742**

---

## 🧠 What the Embeddings Learned

Using PCA to visualize learned movie embeddings revealed meaningful structure:

* Action & sci‑fi films clustered together (e.g., *The Matrix*, *T2*)
* Romantic dramas and comedies formed separate regions (*Titanic*, *When Harry Met Sally*)
* Classic films separated by era and style (*Casablanca*, *Wizard of Oz*)

This confirms the model learned **genre, style, and era signals**—not just popularity.

---

## 💡 Movie Valuation (Business Insight)

Instead of ranking movies by number of ratings, I estimated **movie value based on predicted user engagement**.

### Key Results

* Estimated **Toy Story (1995)** value: **≈ $5.2M** (engagement-driven)
* **Top-valued movies** included:

  * The Godfather
  * Shawshank Redemption
  * Schindler’s List
  * Star Wars: Episode IV
  * Pulp Fiction

### Critical Insight

* Several movies were **highly rated but not highly valued**
* Popularity ≠ long-term engagement

This demonstrates why streaming platforms prioritize **collaborative filtering** over simple popularity metrics.

---

## 📊 Popularity vs. Collaborative Filtering

| Approach                | What it Measures          | Limitations                                      |
| ----------------------- | ------------------------- | ------------------------------------------------ |
| Popularity-based        | Number of ratings         | Ignores personalization, overvalues blockbusters |
| Collaborative filtering | Predicted user engagement | Captures taste, diversity, long-tail value       |

**Conclusion:** Collaborative filtering provides a **more accurate, personalized, and monetizable valuation framework**.

---

## 🛠️ Skills Demonstrated

* Recommender systems & matrix factorization
* Embedding-based modeling
* Hyperparameter tuning & regularization
* Bias modeling (user & item effects)
* Dimensionality reduction (PCA)
* Translating ML outputs into **business value**

---

## ✨ Takeaway

This project shows how **machine learning can transform raw user behavior into strategic insights**, enabling platforms to:

* Invest in the right content
* Personalize recommendations
* Maximize user engagement and long-term value

It mirrors real-world recommender systems used in large-scale consumer platforms.
