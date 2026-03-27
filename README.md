# 🎵 Smart Music Recommendation System

> An end-to-end ML pipeline that recommends songs based on mood, audio features, and lyrics.

Built by **Mohamed Mazen** — Computer Engineering student at Arab Academy for Science, Technology & Maritime Transport (AASTMT).

---

## 🎬 Demo

<img width="1754" height="846" alt="image" src="https://github.com/user-attachments/assets/7d6f73fa-4df3-47bf-8d5e-62c03a09cfce" />

---

## ✨ Features

- 💬 **Mood-based recommendations** — type how you feel, get matching songs via NLP sentiment analysis
- 🔍 **Audio similarity search** — find songs similar to any track using cosine similarity on audio features
- 🎸 **Genre browser** — explore top songs across 114 genres
- 🔎 **Song search** — search by song name or artist across 960k songs
- 🎯 **Song clustering** — unsupervised grouping into 5 natural vibes (Party, Chill, Intense, Sad/Acoustic, Instrumental)
- 🤖 **Popularity prediction** — classify whether a song will be popular using Random Forest, XGBoost, and Logistic Regression
- 🖥️ **Interactive notebook UI** — tabbed ipywidgets interface built directly into the notebook

---

## 🧠 How It Works

```
User Input (text / song name / genre)
        ↓
NLP Mood Detection (VADER Sentiment Analysis)
        ↓
Audio Feature Matching (Cosine Similarity)
        ↓
Recommendation Engine
        ↓
Top Songs Ranked by Popularity
```

1. **Data Pipeline** — two Spotify datasets (114k + 960k songs) are merged on artist and song name, combining genre, popularity, and lyrics into a single unified dataset
2. **Feature Engineering** — audio features normalized to 0–1 using MinMaxScaler, mood labels assigned based on valence/energy model from music psychology
3. **Clustering** — KMeans groups songs into 5 vibes using 9 audio features; optimal k found via Elbow Method; clusters visualized in 2D using PCA (99.9% variance explained)
4. **Classification** — three models trained to predict popularity; Random Forest achieved best results at 85% accuracy
5. **NLP** — VADER sentiment analysis converts free-text mood descriptions into one of four mood categories (happy, calm, sad, angry)
6. **Recommendations** — cosine similarity on normalized audio features returns the most acoustically similar songs

---

## 📊 Model Performance

| Model | Accuracy | F1 (Popular) |
|---|---|---|
| Logistic Regression | 56% | 0.42 |
| **Random Forest** | **85%** | **0.62** |
| XGBoost | 65% | 0.51 |

**Random Forest** won with 85% accuracy. Key findings:
- **Loudness, acousticness, and valence** are the strongest predictors of popularity
- Class imbalance (74% non-popular) handled using `class_weight='balanced'`

Note: The trained model file is not included due to its large size.
To generate it, run the notebook which will preprocess the data and train the model.
---

## 🗃️ Dataset

| Dataset | Songs | Source |
|---|---|---|
| Spotify Tracks Dataset | 114k | Kaggle — maharshipandya |
| Songs with Attributes & Lyrics | 960k | Kaggle — BwandoWando |

Both datasets are merged on artist + song name to combine:
- Audio features (danceability, energy, valence, tempo, etc.)
- Genre and popularity metadata
- Song lyrics for NLP analysis

> ⚠️ Some recent songs may not appear due to dataset coverage. Spotify API integration is ready to be enabled once developer credentials are approved.

---

## 🛠️ Libraries used

- **Python** — pandas, numpy, scikit-learn, XGBoost
- **NLP** — vaderSentiment
- **Visualization** — matplotlib, seaborn
- **UI** — ipywidgets
- **ML** — KMeans, PCA, Random Forest, XGBoost, Logistic Regression
- **Similarity** — cosine similarity on normalized audio features

---

<p align="center">Built with 🎵 by <a href="https://github.com/mohamedelagamy-tech">Mohamed Mazen</a></p>
