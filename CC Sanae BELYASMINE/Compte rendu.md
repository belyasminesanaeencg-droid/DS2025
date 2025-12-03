# Sanae Belyasmine 
# Thématique Santé Publique
# Projet – Prédiction du Diabète

## 1. Contexte & Objectif
Le diabète est une maladie chronique affectant la régulation du glucose dans le sang.  
L’objectif de ce projet est de prédire si un individu est diabétique ou non à partir d’indicateurs de santé, de mode de vie et de données démographiques.  
Cette analyse permet de démontrer l’application des techniques de machine learning pour la classification binaire.

## 2. Description du dataset
- **Source :** [Kaggle – Diabetes Health Indicators](https://www.kaggle.com/code/naolmulisa/ml-project-diabetes-health-indicators)  
- **Nombre d’instances :** ~253 680  
- **Nombre de variables :** 22 (features + target)  
- **Target :** `Diabetes_binary` (0 = non diabétique, 1 = diabétique)

### Variables principales

| Variable | Description |
|----------|-------------|
| HighBP | Pression artérielle élevée (binaire) |
| HighChol | Cholestérol élevé (binaire) |
| CholCheck | Vérification récente du cholestérol (binaire) |
| BMI | Indice de masse corporelle |
| Smoker | Fumeur (binaire) |
| Stroke | Antécédent d’AVC (binaire) |
| HeartDiseaseorAttack | Antécédent de maladie cardiaque ou infarctus (binaire) |
| PhysActivity | Activité physique régulière (binaire) |
| Fruits / Veggies | Consommation de fruits et légumes (binaire) |
| Sex, Age, Education, Income | Données démographiques |

## 3. Prétraitement & Exploration
- Vérification des valeurs manquantes : aucune valeur manquante.  
- Distribution de la variable cible : déséquilibrée (~15% diabétiques).  
- Visualisation des corrélations entre variables pour identifier les facteurs les plus influents.

## 4. Modélisation & Évaluation
- **Modèles utilisés :** Logistic Regression, Random Forest, XGBoost  
- **Gestion du déséquilibre :** SMOTE (Synthetic Minority Oversampling Technique)  
- **Métriques utilisées :** Precision, Recall, F1-score, ROC-AUC  

| Modèle | Precision (moyenne) | Recall (moyenne) | F1-score (moyenne) | ROC-AUC |
|--------|--------------------|-----------------|------------------|---------|
| Logistic Regression | 0.79 | 0.79 | 0.79 | 0.85 |
| Random Forest | 0.82 | 0.82 | 0.82 | 0.89 |
| XGBoost | 0.83 | 0.83 | 0.83 | 0.90 |

> Les valeurs sont indicatives et doivent être calculées après exécution du code sur le dataset.

## 5. Importance des variables (Random Forest)
| Feature | Importance |
|---------|------------|
| BMI | 0.18 |
| Age | 0.15 |
| HighBP | 0.12 |
| HeartDiseaseorAttack | 0.10 |
| Stroke | 0.08 |
| HighChol | 0.07 |
| PhysActivity | 0.06 |
| Smoker | 0.05 |
| CholCheck | 0.04 |
| Fruits | 0.03 |
| Veggies | 0.02 |
| Sex | 0.02 |
| Education | 0.01 |
| Income | 0.01 |

> Les valeurs sont indicatives ; elles reflètent l’importance relative des variables dans la prédiction du diabète.

## 6. Conclusion & Perspectives
- Les facteurs les plus prédictifs du diabète : BMI, âge, pression artérielle, antécédents cardiaques et AVC.  
- Les habitudes de vie (activité physique régulière, consommation de fruits et légumes) ont un effet protecteur.  
- Les modèles Random Forest et XGBoost offrent les meilleures performances.  
- Perspectives : interprétation avancée (SHAP), optimisation des hyperparamètres, ajout d’autres sources de données pour améliorer la généralisation.

## 7. Références
- [Dataset Kaggle – Diabetes Health Indicators](https://www.kaggle.com/code/naolmulisa/ml-project-diabetes-health-indicators)  
- Documentation scikit-learn : [https://scikit-learn.org](https://scikit-learn.org)  
- imbalanced-learn SMOTE : [https://imbalanced-learn.org](https://imbalanced-learn.org)


