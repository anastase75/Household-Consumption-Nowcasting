# Household-Consumption-Nowcasting

📊 Résumé du Projet
Prédiction de la croissance de la consommation des ménages françaises en utilisant des données alternatives (Google Trends) comme indicateurs avancés, combinées avec les données officielles INSEE.
Objectif : Démontrer la valeur ajoutée des données haute fréquence pour le nowcasting économique.

🎯 Résultats Clés
ModèleRMSER²AméliorationSARIMA (Baseline)4.32-0.20-Ridge Regression2.850.48+34%SARIMAX + Trends4.28-0.17+0.9%Random Forest4.11-0.08+4.8%
Meilleur modèle : Ridge Regression avec une amélioration de 34% par rapport au baseline.

📁 Structure du Projet
├── nowcasting_project.py          # Script principal
├── data_final.csv                 # Dataset fusionné INSEE + Google Trends
├── model_results.csv              # Résultats comparatifs des modèles
├── predictions_comparison.png     # Visualisation des prédictions
├── correlation_matrix.png         # Matrice de corrélation
├── eda_time_series.png           # Analyse exploratoire temporelle
└── README.md                      # Ce fichier

🔧 Méthodologie
Données

INSEE : Croissance annuelle de la consommation des ménages (1950-2024)
Google Trends : 6 indicateurs mensuels agrégés annuellement (2004-2024)

Soldes
Crédit à la consommation
Électroménager
Crédit immobilier
Chômage
Inflation



Dataset final : 21 années (2004-2024), 9 variables
Modèles Implémentés

SARIMA : Baseline sans variables exogènes
SARIMAX : Avec Google Trends comme variables exogènes
Ridge Regression : Régression linéaire L2 régularisée
Random Forest : Ensemble learning avec contraintes anti-overfitting

Validation

Split temporel : 80% train (2004-2019) / 20% test (2020-2024)
Métriques : RMSE, MAE, R²
Pas de cross-validation (taille limitée du dataset)


💡 Insights Économiques
Feature Importance (Ridge Regression)
VariableCoefficientInterprétationCrédit consommation+0.79Leading indicator #1 - Les recherches de crédit précèdent les achatsChômage-0.47Impact négatif logique - ↑ chômage → ↓ consommationSoldes-0.23Corrélation négative - possiblement lié aux périodes de criseInflation+0.01Impact marginal dans ce modèle
Corrélations avec la Consommation

PIB : +0.93 (forte corrélation attendue)
Chômage : -0.61 (relation inverse forte)
Inflation : +0.28 (impact modéré)


🚧 Limites et Améliorations Possibles
Limites Actuelles

Fréquence des données : Annuelle alors que le nowcasting vise du temps réel
Taille du dataset : 21 observations limitent la puissance statistique
Historique Google Trends : Seulement depuis 2004

Pistes d'Amélioration

✅ Utiliser des données mensuelles INSEE (disponibles pour certains indicateurs)
✅ Ajouter d'autres sources alternatives :

Données de transactions bancaires
Données de mobilité (Google Mobility, Apple Maps)
Données satellites (luminosité nocturne)
Données de cartes de crédit


✅ Implémenter des modèles avancés :

Dynamic Factor Models (DFM)
LSTM pour capturer les dépendances temporelles
Modèles bayésiens pour quantification de l'incertitude




🛠️ Technologies Utilisées

Python 3.12
Pandas : Manipulation de données
Statsmodels : Modèles SARIMA/SARIMAX
Scikit-learn : Ridge, Random Forest, métriques
Matplotlib/Seaborn : Visualisations


🚀 Comment Exécuter
bash# Installation des dépendances
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn openpyxl

# Exécution du projet
python nowcasting_project.py
Prérequis :

Fichier INSEE : econ-gen-pib-composante.xlsx
Fichier Google Trends : time_series_FR_20040101-0000_20260515-2211.csv


📚 Références

INSEE - Comptes Nationaux
Google Trends
Giannone, D., Reichlin, L., & Small, D. (2008). Nowcasting: The real-time informational content of macroeconomic data
Choi, H., & Varian, H. (2012). Predicting the Present with Google Trends


👤 Auteur
Anas Fenniche
Master IASD - Dauphine
