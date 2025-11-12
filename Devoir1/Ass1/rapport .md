# 🩺 CDC Diabetes Health Indicators — Rapport de Présentation

## 📘 1. Contexte général
Le jeu de données **CDC Diabetes Health Indicators** provient du [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators).  
Il contient des données issues du **Behavioral Risk Factor Surveillance System (BRFSS)**, un programme de surveillance de la santé publique géré par le **Centers for Disease Control and Prevention (CDC)** aux **États-Unis**.

Le BRFSS est une enquête téléphonique nationale réalisée chaque année auprès d’adultes américains.  
Son objectif est de recueillir des informations sur les **comportements à risque**, les **maladies chroniques** et l’**accès aux soins**.

---

## 🧪 2. Objectif de la recherche
Cette base de données vise à **identifier les indicateurs de santé associés au diabète** et à **modéliser le risque de développer la maladie** à partir de variables comportementales et médicales.

Elle est couramment utilisée pour des projets de :
- Classification supervisée (diabétique / non-diabétique)
- Analyse exploratoire des comportements de santé
- Détection des facteurs prédictifs de maladies chroniques

---

## 👩‍🔬 3. Auteurs et origine
- **Institution :** Centers for Disease Control and Prevention (CDC), États-Unis  
- **Programme :** Behavioral Risk Factor Surveillance System (BRFSS)  
- **Date d’ajout sur UCI :** 25 septembre 2023  
- **Financement :** CDC  
- **Référence scientifique :**  
  > Rios Burrows N., Hora I., Geiss L. S., Gregg E. W., & Albright A. (2017).  
  > *Incidence of End-Stage Renal Disease Attributed to Diabetes Among Persons with Diagnosed Diabetes — United States and Puerto Rico, 2000–2014.*  
  > Centers for Disease Control and Prevention (CDC).

---

## 🌎 4. Lieu et période
- **Lieu de collecte :** États-Unis  
- **Période :** Données issues du programme BRFSS couvrant principalement les années **2015 à 2020**  

L’enquête est menée chaque année par téléphone dans les 50 États, le District de Columbia et les territoires américains.

---

## 📊 5. Description du jeu de données
- **Nombre d’observations :** 253 680 individus  
- **Nombre de variables :** 35  
- **Type de données :** numériques et catégorielles  
- **Variable cible :** `Diabetes_binary`  
  - 0 = non diabétique  
  - 1 = diabétique  

### Exemple de variables :
| Variable | Description | Type |
|-----------|--------------|------|
| `HighBP` | Hypertension artérielle (oui/non) | Binaire |
| `HighChol` | Cholestérol élevé (oui/non) | Binaire |
| `BMI` | Indice de masse corporelle | Numérique |
| `Smoker` | Fumeur actuel | Binaire |
| `PhysActivity` | Activité physique récente | Binaire |
| `Fruits` | Consommation de fruits | Binaire |
| `Veggies` | Consommation de légumes | Binaire |
| `GenHlth` | État de santé général (1 = excellent, 5 = mauvais) | Ordinal |
| `Age` | Tranche d’âge | Catégoriel |

---

## 🎯 6. Objectifs analytiques possibles
Ce jeu de données peut être utilisé pour :
- L’**analyse exploratoire** des relations entre comportement et santé ;  
- La **modélisation prédictive** du risque de diabète ;  
- La **visualisation des tendances** en santé publique ;  
- Des **projets éducatifs** en apprentissage automatique (machine learning).  

---

## ⚙️ 7. Exemple d’utilisation (Python)
```python
import pandas as pd

# Charger le jeu de données
df = pd.read_csv("data/diabetes_health_indicators.csv")

# Aperçu des premières lignes
df.head()

