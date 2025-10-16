# 🤖 Machine Learning Projects Portfolio

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.2+-green.svg)](https://scikit-learn.org/)
[![PyCaret](https://img.shields.io/badge/PyCaret-3.0+-red.svg)](https://pycaret.org/)

Collection de projets de Machine Learning démontrant des compétences en **analyse de données**, **clustering non supervisé** et **classification supervisée**.

---

## 📋 Table des Matières
- [Projets](#-projets)
  - [1. Spotify Clustering Analysis](#1-spotify-clustering-analysis)
  - [2. Social Media Trolls Detection](#2-social-media-trolls-detection)
- [Technologies Utilisées](#-technologies-utilisées)
- [Installation](#-installation)
- [Structure du Projet](#-structure-du-projet)
- [Méthodologie](#-méthodologie)
- [Résultats](#-résultats)
- [Contact](#-contact)

---

## 🎯 Projets

### 1. Spotify Clustering Analysis
**Objectif** : Regrouper des chansons Spotify par similarité en utilisant leurs caractéristiques audio.

#### 📊 Dataset
- **Source** : Métadonnées de chansons Spotify
- **Taille** : ~600 chansons
- **Features** : 
  - Métriques audio : `danceability`, `energy`, `valence`, `tempo`, `loudness`, `speechiness`
  - Métadonnées : `popularity`, `key`, `liveness`, `explicit`

#### 🔬 Méthodologie
1. **Exploration des données** :
   - Analyse statistique descriptive
   - Visualisation des distributions
   - Détection et traitement des valeurs manquantes

2. **Préparation des données** :
   - Sélection des features pertinentes (exclusion de `name`, `artists`)
   - Normalisation avec `StandardScaler`
   - Analyse de corrélation

3. **Modélisation** :
   - **K-Means Clustering** : Segmentation en groupes homogènes
   - **Méthode du coude** : Détermination du nombre optimal de clusters
   - **Analyse en Composantes Principales (PCA)** : Réduction dimensionnelle pour visualisation

4. **Évaluation** :
   - Score de silhouette
   - Interprétation des clusters
   - Visualisations 2D/3D des groupes

#### 💡 Résultats Clés
- Identification de groupes distincts de chansons basés sur leurs caractéristiques audio
- Les features `energy`, `danceability` et `valence` sont les plus discriminantes
- Les clusters révèlent des patterns musicaux cohérents

---

### 2. Social Media Trolls Detection
**Objectif** : Détecter automatiquement les comptes indésirables sur une plateforme de médias sociaux.

#### 📊 Dataset
- **Source** : Données de modération de profils utilisateurs
- **Taille** : 5,000+ profils
- **Features** :
  - Informations de profil : `email`, `has_picture_cover`, `has_linkedin`, etc.
  - Métriques comportementales : `nb_chars_in_bio`, `nb_tags`, `nb_goals`
  - **Target** : `is_unwanted` (binaire)

#### 🔬 Méthodologie
1. **Analyse Exploratoire** :
   - Distribution des classes (équilibre wanted/unwanted)
   - Analyse univariée de chaque feature
   - Tests statistiques (Chi-carré, boxplots)

2. **Feature Engineering** :
   - Création de `nb_tags` et `nb_goals` à partir de colonnes textuelles
   - Imputation des valeurs manquantes
   - Suppression de features non pertinentes (`node_id`)

3. **Analyse Statistique** :
   - **Test du Chi-carré** : Évaluation de l'indépendance entre variables catégorielles
   - Analyse de la longueur de bio (`nb_chars_in_bio`) : Les comptes indésirables ont significativement moins de contenu

4. **Modélisation** :
   - **Baseline** : Régression Logistique (~72% accuracy)
   - **AutoML avec PyCaret** : Comparaison de 15+ modèles
   - **Meilleur modèle** : Gradient Boosting Classifier
   - **Optimisation** : Hyperparameter tuning avec validation croisée

5. **Évaluation** :
   - Métriques : Accuracy, Precision, Recall, F1-Score
   - Matrice de confusion
   - Feature importance analysis
   - Validation croisée (K-Fold)

#### 💡 Résultats Clés
- **Accuracy** : ~75-78% sur le jeu de test
- **Feature la plus importante** : `nb_chars_in_bio` (longueur de la biographie)
- Les comptes indésirables se caractérisent par :
  - Biographies très courtes (<50 caractères)
  - Peu de tags et d'objectifs définis
  - Certains fournisseurs d'email spécifiques (iCloud plus à risque)

---

## 🛠 Technologies Utilisées

### Langages & Frameworks
- **Python 3.8+** : Langage principal
- **Jupyter Notebook** : Environnement de développement interactif

### Librairies de Data Science
- **pandas** : Manipulation de données tabulaires
- **NumPy** : Calculs numériques
- **scikit-learn** : Algorithmes de ML, preprocessing, évaluation
- **scipy** : Tests statistiques

### Visualisation
- **Matplotlib** : Graphiques statiques
- **Seaborn** : Visualisations statistiques
- **Plotly** : Graphiques interactifs

### AutoML
- **PyCaret** : Comparaison automatisée de modèles et hyperparameter tuning

---

## � Installation

### Prérequis
- Python 3.8 ou supérieur
- pip (gestionnaire de paquets Python)

### Étapes

1. **Cloner le repository** :
```bash
git clone https://github.com/paulfrettepro-collab/machine_learning_projects.git
cd machine_learning_projects
```

2. **Créer un environnement virtuel** (recommandé) :
```bash
python -m venv venv
source venv/bin/activate  # Sur Windows : venv\Scripts\activate
```

3. **Installer les dépendances** :
```bash
pip install -r requirements.txt
```

4. **Lancer Jupyter Notebook** :
```bash
jupyter notebook
```

5. **Ouvrir les notebooks** :
   - `Spotify_clustering_.ipynb`
   - `Trolls_detection_analysis.ipynb`

---

## �📁 Structure du Projet

```
machine_learning_projects/
│
├── Spotify_clustering_.ipynb          # Projet de clustering Spotify
├── Trolls_detection_analysis.ipynb    # Projet de détection de trolls
│
├── requirements.txt                    # Dépendances Python
├── .gitignore                          # Fichiers à ignorer par Git
└── README.md                           # Documentation du projet
```

---

## 🔍 Méthodologie Générale

### 1. Compréhension du Problème
- Définition claire de l'objectif
- Identification des contraintes et métriques de succès

### 2. Exploration des Données (EDA)
- Statistiques descriptives
- Visualisations
- Détection d'anomalies et valeurs aberrantes

### 3. Préparation des Données
- Nettoyage (valeurs manquantes, doublons)
- Feature engineering
- Normalisation/Standardisation
- Splitting (train/test)

### 4. Modélisation
- Sélection d'algorithmes appropriés
- Entraînement et validation
- Comparaison de modèles (si applicable)

### 5. Évaluation & Interprétation
- Métriques de performance
- Analyse des erreurs
- Feature importance
- Validation des résultats

### 6. Documentation
- Code commenté
- Explications des choix méthodologiques
- Visualisations claires

---

## 📈 Résultats

| Projet | Algorithme Principal | Métrique Clé | Performance |
|--------|---------------------|--------------|-------------|
| **Spotify Clustering** | K-Means | Silhouette Score | ~0.45 |
| **Trolls Detection** | Gradient Boosting | Accuracy | ~75-78% |

---

## 🎓 Compétences Démontrées

### Techniques de Machine Learning
- ✅ Clustering non supervisé (K-Means, PCA)
- ✅ Classification supervisée (Logistic Regression, Gradient Boosting)
- ✅ Feature engineering
- ✅ Hyperparameter tuning
- ✅ Validation croisée

### Data Science
- ✅ Analyse exploratoire de données (EDA)
- ✅ Tests statistiques (Chi-carré)
- ✅ Visualisation de données
- ✅ Preprocessing et nettoyage de données

### Outils & Technologies
- ✅ Python (pandas, scikit-learn, PyCaret)
- ✅ Jupyter Notebook
- ✅ Git & GitHub
- ✅ Visualisation (Matplotlib, Seaborn, Plotly)

---

## � Améliorations Futures

### Spotify Clustering
- [ ] Tester d'autres algorithmes (DBSCAN, Hierarchical Clustering)
- [ ] Intégrer l'API Spotify pour récupérer plus de données
- [ ] Créer un système de recommandation basé sur les clusters

### Trolls Detection
- [ ] Analyser le contenu textuel des biographies (NLP)
- [ ] Tester des modèles d'ensemble (Stacking, Voting)
- [ ] Déployer le modèle en production (Flask/FastAPI)
- [ ] Gérer le déséquilibre de classes avec SMOTE

---

## �👤 Contact

**Paul Frette**
- GitHub : [@paulfrettepro-collab](https://github.com/paulfrettepro-collab)
- Email : paul.frette.pro@gmail.com

---

## 📄 Licence

Ce projet est à usage éducatif et de portfolio. Veuillez me contacter pour toute utilisation commerciale.

---

⭐ **N'hésitez pas à mettre une étoile si vous trouvez ce projet intéressant !**
