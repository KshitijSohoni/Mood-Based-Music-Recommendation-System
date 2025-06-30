# 🎵 Mood-Based Music Recommendation System

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://www.tensorflow.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green.svg)](https://opencv.org/)
[![Spotify API](https://img.shields.io/badge/Spotify%20API-integrated-brightgreen.svg)](https://developer.spotify.com/)

An AI-powered system that bridges technology and emotions by detecting a user's facial expression and recommending songs from Spotify based on the detected mood.

---

## 📌 Overview

This project combines **computer vision**, **deep learning**, **unsupervised learning**, and the **Spotify API** to recommend music based on real-time facial emotion recognition.

### 🔧 Key Features

- 🧠 **Emotion Detection** using facial expressions (Haar Cascade, OpenCV)
- 🎧 **Music Clustering** using PCA + KMeans on Spotify audio features
- 🗣️ **Mood Classification** into predefined classes (Happy, Sad, Angry, Calm)
- 🟢 **Spotify API Integration** to play and save curated playlists

---

## 🧠 Emotion Detection Pipeline

- **Dataset**: [FER2013 Facial Expression Recognition Dataset](https://www.kaggle.com/datasets/msambare/fer2013)
- **Model**: Custom CNN built using Keras and trained on 48×48 grayscale facial images
- **Libraries**: OpenCV, Haar Cascades, TensorFlow/Keras
- **Performance**: ~50% accuracy *(can be improved with pre-trained models like MobileNet)*

---

## 🎶 Music Feature Engineering & Clustering

- **Dataset**: Spotify songs dataset with audio features and metadata
- **Features Used**: `danceability`, `energy`, `valence`, `tempo`, `loudness`, `speechiness`, `acousticness`, etc.
- **Dimensionality Reduction**: PCA (reduced to 4 components)
- **Explained Variance**: ~88%
- **Clustering**: KMeans with 4 clusters (mapped to moods)

### 🎭 Cluster to Mood Mapping

| Valence | Energy | Inferred Mood |
|--------:|-------:|:--------------|
| High    | High   | Happy         |
| Low     | High   | Angry         |
| Low     | Low    | Sad           |
| High    | Low    | Calm          |

## 📸 Visualizations

### 🎯 KMeans Clustering Result
![KMeans Clustering](/Images/Kmeans.png)

### 📊 PCA Result
![PCA Result](/Images/PCA_Result.png)

---

## 🎯 Recommendation Engine

- Filters songs based on the detected mood
- Uses **cosine similarity** on valence and energy
- Recommends the **top 3 closest songs**
- **Automatically**:
  - Plays the top track
  - Creates a new Spotify playlist
  - Adds all recommended tracks to the playlist

---

## 🟢 Spotify API Integration

- **Library**: [Spotipy](https://spotipy.readthedocs.io/)
- **Authentication**: SpotifyOAuth
- **Scopes Required**:
  - `user-read-playback-state`
  - `user-modify-playback-state`
  - `playlist-modify-public`
- **Capabilities**:
  - Real-time track playback
  - Playlist creation
  - Adding tracks to playlist based on mood

---

## 📊 Results & Metrics

| Component               | Metric                          |
|-------------------------|---------------------------------|
| Emotion Detection Acc.  | ~50%                            |
| PCA Variance Explained  | ~88%                            |
| Clusters Used           | 4 (mapped to 4 moods)           |
| Recommendation Quality  | High similarity (cosine > 0.9) |

---

## 🛠️ Tech Stack

### 💻 Language
- **Python**

### 📚 Libraries & Frameworks
- **TensorFlow / Keras** – For CNN-based emotion classification
- **OpenCV** – For real-time face detection using Haar Cascades
- **Scikit-learn** – For PCA, KMeans clustering, and cosine similarity
- **Seaborn / Matplotlib** – For data visualization
- **Pandas / NumPy** – For data preprocessing and manipulation
- **Spotipy** – For Spotify Web API integration

---

> Let me know if you’d like this in downloadable format or want to add a `Demo` or `How to Run` section!
