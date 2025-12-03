# Projet – Prédiction du Diabète
*Basé sur le dataset “Diabetes Health Indicators” (Kaggle)*

## 1. Contexte & Objectif 🎯
Le diabète est une maladie chronique affectant la régulation du glucose dans le sang.  
L’objectif de ce projet est de prédire si un individu est diabétique ou non, à partir d’indicateurs de santé, de mode de vie et de données démographiques.  
Ce projet permet de démontrer l’application de techniques de machine learning pour la classification binaire.

## 2. Description du dataset
- **Source :** [Kaggle – Diabetes Health Indicators](https://www.kaggle.com/code/naolmulisa/ml-project-diabetes-health-indicators)  
- **Nombre d’instances :** ~253 680  
- **Nombre de variables :** 22 (features + target)  
- **Target :** `Diabetes_binary` (0 = non diabétique, 1 = diabétique)

### Variables principales

| Variable | Description |
|----------|-------------|
| `HighBP` | Pression artérielle élevée (binaire) |
| `HighChol` | Cholestérol élevé (binaire) |
| `CholCheck` | Vérification récente du cholestérol (binaire) |
| `BMI` | Indice de masse corporelle |
| `Smoker` | Fumeur (binaire) |
| `Stroke` | Antécédent d’AVC (binaire) |
| `HeartDiseaseorAttack` | Antécédent de maladie cardiaque ou infarctus (binaire) |
| `PhysActivity` | Activité physique régulière (binaire) |
| `Fruits` / `Veggies` | Consommation de fruits et légumes (binaire) |
| `Sex`, `Age`, `Education`, `Income` | Données démographiques |

## 3. Prétraitement & Exploration des données
- Vérification des valeurs manquantes : aucune donnée manquante.  
- Analyse de la distribution de la variable cible : déséquilibrée (~15% diabétiques).  
- Visualisation des features et corrélations entre elles pour identifier les variables importantes.  

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(x='Diabetes_binary', data=df)
plt.title('Distribution de la variable cible')
plt.show()

corr = df.corr()
plt.figure(figsize=(12,8))
sns.heatmap(corr, annot=True, fmt=".2f", cmap="coolwarm")
plt.title("Matrice de corrélation")
plt.show()
from imblearn.over_sampling import SMOTE
from sklearn.preprocessing import StandardScaler

X = df.drop(columns=['Diabetes_binary'])
y = df['Diabetes_binary']

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

smote = SMOTE(random_state=42)
X_res, y_res = smote.fit_resample(X_scaled, y)
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from xgboost import XGBClassifier
from sklearn.metrics import classification_report, roc_auc_score

X_train, X_test, y_train, y_test = train_test_split(X_res, y_res, test_size=0.2, random_state=42, stratify=y_res)

models = {
    "Logistic Regression": LogisticRegression(max_iter=1000),
    "Random Forest": RandomForestClassifier(n_estimators=200, random_state=42),
    "XGBoost": XGBClassifier(use_label_encoder=False, eval_metric='logloss', random_state=42)
}

for name, model in models.items():
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    y_proba = model.predict_proba(X_test)[:,1]
    print(f"=== {name} ===")
    print(classification_report(y_test, y_pred))
    print("ROC AUC:", roc_auc_score(y_test, y_proba))
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

importances = models["Random Forest"].feature_importances_
feat_names = df.drop(columns=['Diabetes_binary']).columns
feat_imp_df = pd.DataFrame({"Feature": feat_names, "Importance": importances}).sort_values(by="Importance", ascending=False)

plt.figure(figsize=(10,6))
sns.barplot(x="Importance", y="Feature", data=feat_imp_df)
plt.title("Importance des variables - Random Forest")
plt.show()

