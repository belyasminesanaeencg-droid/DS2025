# 🩺 CDC Diabetes Health Indicators — Rapport de Présentation Complet

---

## 📘 1. Introduction

Le jeu de données **CDC Diabetes Health Indicators** provient du [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators).  
Il est basé sur le **Behavioral Risk Factor Surveillance System (BRFSS)**, une enquête nationale conduite par le **Centers for Disease Control and Prevention (CDC)** aux **États-Unis**.  

Ce jeu de données est largement utilisé dans les projets de **machine learning appliqués à la santé publique**, notamment pour **étudier les facteurs de risque du diabète** et **modéliser les comportements de santé**.

---

## 🎯 2. Objectif du projet

L’objectif de ce projet est double :  
1. **Analyser les comportements et conditions de santé associés au diabète**, tels que le surpoids, l’activité physique, le tabagisme, ou la consommation de fruits et légumes.  
2. **Développer des modèles prédictifs** capables d’identifier les individus présentant un risque accru de diabète à partir de variables comportementales et démographiques.

Ce rapport présente la source des données, leur structure, les variables disponibles, ainsi que les pistes d’analyse et les considérations méthodologiques associées.

---

## 👩‍🔬 3. Origine et auteurs

- **Institution responsable :** Centers for Disease Control and Prevention (CDC), Division of Population Health  
- **Programme source :** Behavioral Risk Factor Surveillance System (BRFSS)  
- **Type d’étude :** Enquête téléphonique annuelle auprès d’adultes américains  
- **Financement :** CDC (fédéral)  
- **Date de mise à disposition sur UCI :** 25 septembre 2023  

### Publication scientifique de référence :
> Rios Burrows N., Hora I., Geiss L. S., Gregg E. W., & Albright A. (2017).  
> *Incidence of End-Stage Renal Disease Attributed to Diabetes Among Persons with Diagnosed Diabetes — United States and Puerto Rico, 2000–2014.*  
> Centers for Disease Control and Prevention (CDC).

---

## 🌍 4. Lieu et période

- **Lieu de collecte :** États-Unis (les 50 États, le District de Columbia, et plusieurs territoires américains).  
- **Période :** Données issues principalement des cycles d’enquête **2015 à 2020**.  
- **Méthode :** Questionnaire téléphonique administré à des échantillons aléatoires d’adultes de 18 ans et plus.  

Les données sont auto-déclarées par les participants et peuvent donc contenir des **biais de mémoire ou de perception**, mais leur échantillon national permet d’obtenir une excellente représentativité démographique.

---

## 📊 5. Description du jeu de données

### Caractéristiques générales
- **Nombre d’observations :** 253 680 individus  
- **Nombre de variables :** 35  
- **Type de variables :** numériques, catégorielles et binaires  
- **Variable cible :** `Diabetes_binary`  
  - 0 = Non diabétique  
  - 1 = Diabétique  

### Exemples de variables :
| Variable | Description | Type |
|-----------|--------------|------|
| `HighBP` | Hypertension artérielle (Oui/Non) | Binaire |
| `HighChol` | Cholestérol élevé (Oui/Non) | Binaire |
| `BMI` | Indice de masse corporelle | Numérique |
| `Smoker` | A fumé au moins 100 cigarettes dans sa vie | Binaire |
| `Stroke` | A eu un AVC | Binaire |
| `HeartDiseaseorAttack` | Antécédents de maladie cardiaque ou infarctus | Binaire |
| `PhysActivity` | Activité physique récente (Oui/Non) | Binaire |
| `Fruits` | Consommation de fruits quotidienne | Binaire |
| `Veggies` | Consommation de légumes quotidienne | Binaire |
| `HvyAlcoholConsump` | Consommation excessive d’alcool | Binaire |
| `GenHlth` | Évaluation de la santé générale (1 = excellente, 5 = mauvaise) | Ordinale |
| `MentHlth` | Nombre de jours avec mauvaise santé mentale (0–30) | Numérique |
| `PhysHlth` | Nombre de jours avec mauvaise santé physique (0–30) | Numérique |
| `DiffWalk` | Difficultés à marcher ou monter des escaliers | Binaire |
| `Age` | Tranche d’âge (13 catégories) | Catégorielle |
| `Sex` | Sexe (1 = Homme, 0 = Femme) | Binaire |
| `Income` | Niveau de revenu (1 = faible, 8 = élevé) | Ordinale |

---

## 🔬 6. Méthodologie d’analyse proposée

### 6.1. Prétraitement des données
- Vérification et nettoyage des doublons éventuels  
- Normalisation / standardisation des variables continues (`BMI`, `MentHlth`, `PhysHlth`)  
- Encodage des variables catégorielles (label encoding ou one-hot)  
- Équilibrage de la variable cible (le dataset est souvent déséquilibré)  
  - Méthodes possibles : **SMOTE**, **undersampling**, **class weights**

### 6.2. Analyse exploratoire (EDA)
- Étude de la distribution des variables de santé (`BMI`, `GenHlth`, etc.)  
- Corrélations entre variables comportementales et diabète (`PhysActivity`, `Smoker`, etc.)  
- Analyse de l’impact des variables démographiques (`Age`, `Sex`, `Income`)  
- Visualisation avec **matplotlib**, **seaborn**, ou **plotly**

### 6.3. Modélisation
Exemples de modèles prédictifs testables :
- **Régression logistique** (baseline simple et interprétable)  
- **Random Forest** (robuste et performant sur données mixtes)  
- **XGBoost / LightGBM** (optimisation avancée et importance des variables)  
- **Réseaux de neurones simples (MLP)** (approche non linéaire)  

### 6.4. Évaluation
- **Métriques** : Accuracy, Precision, Recall, F1-score, AUC  
- **Validation croisée (K-Fold)**  
- **Analyse des fausses prédictions** (importance en santé publique)  

---

## 🧭 7. Interprétation et enjeux

### 7.1. Intérêt scientifique
Le dataset permet :
- De comprendre les **facteurs comportementaux influençant le diabète**.  
- D’explorer les **disparités régionales et socio-économiques** dans les comportements de santé.  
- De servir de **base pour des études prédictives en épidémiologie**.  

### 7.2. Limites
- Données **auto-déclarées** → biais de réponse possible.  
- Données **américaines uniquement** → généralisabilité limitée.  
- Manque de certaines variables cliniques précises (glycémie, HbA1c, etc.).  

### 7.3. Considérations éthiques
- Les données sont **anonymisées et publiques** (pas d’information personnelle).  
- Toute utilisation doit respecter les conditions d’usage du CDC et du dépôt UCI.  
- Les résultats doivent être interprétés avec prudence et **ne pas être utilisés à des fins médicales directes**.  

---

## ⚙️ 8. Exemple d’utilisation en Python

```python
import pandas as pd

# Chargement du dataset
df = pd.read_csv("data/diabetes_health_indicators.csv")

# Taille et structure
print(df.shape)
print(df.info())

# Aperçu
df.head()

# Distribution de la variable cible
df["Diabetes_binary"].value_counts(normalize=True)
