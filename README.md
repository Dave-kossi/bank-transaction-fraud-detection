# 🛡️ Projet de Détection de Fraude Bancaire

##  Contexte et Enjeux
La fraude bancaire représente un défi majeur pour les institutions financières. Chaque année, des **milliards d’euros** sont perdus à travers différentes formes de fraude (usurpation d’identité, transactions non autorisées, falsification).

L’impact est double :
* **Financier** : pertes directes liées aux transactions.
* **Réputationnel** : perte de confiance des clients.

---

## 💰 Impact Économique
Chaque fraude non détectée entraîne un coût moyen de **3,10 €** de remboursement pour l’institution.

| Fraudes non détectées | Coût des remboursements |
| :--- | :--- |
| 1 000 | 3 100 € |
| 10 000 | 31 000 € |
| 100 000 | 310 000 € |

> ⚠️ *Ces chiffres n’incluent pas les coûts administratifs, d'enquête et les pertes de réputation.*

---

##  Pourquoi la Détection est Critique
1.  **Impact Financier Direct** : Remboursements et frais de contestation.
2.  **Volume Massif** : Le contrôle manuel est impossible sur des millions de transactions quotidiennes ; le **Machine Learning est indispensable**.
3.  **Réactivité** : Besoin de blocage **en temps réel**.
4.  **Équilibre Délicat** : Éviter d'être trop agressif (clients mécontents) ou trop conservateur (pertes financières).

---

## 🤖 Objectif du Projet
Développer un **système automatisé** capable de :
* Maximiser le **Rappel (Recall)** pour détecter un maximum de fraudes.
* Maintenir une **Précision** élevée pour limiter les fausses alertes.
* Optimiser le **coût-bénéfice global** du système.

---

## 🛠️ Approche Méthodologique
1.  **Exploration (EDA)** : Identification des patterns de fraude.
2.  **Feature Engineering** : Création de variables sur les comportements récents, la localisation et les anomalies.
3.  **Modélisation** : Comparaison de 5 algorithmes (Logistic Regression, Random Forest, GBDT, XGBoost, LightGBM).
4.  **Validation** : Cross-validation **5-fold** et métriques adaptées aux données déséquilibrées.

---

##  Résultats : Évaluation des Modèles

L'analyse repose sur le compromis Rappel/Précision :

![Performances des Modèles](Screenshot%20from%202026-01-20%2016-06-12.png)

* **Régression Logistique** : Présente le Rappel le plus élevé (**0.916**), mais sa faible précision (**0.349**) bloquerait trop de clients légitimes.
* **Modèles d'Ensemble (RF, GB, XGB, GBM)** : Offrent une **Précision exceptionnelle (proche de 1.000)**, garantissant la fiabilité des alertes.
* **Choix Final** : **LightGBM** est retenu car il offre le meilleur équilibre avec un Rappel de **0.620** (le plus élevé des modèles robustes) et une Précision de **0.997**.

---

## 🧠 Analyse de l'Interprétabilité : Pourquoi le Modèle Prédit la Fraude ?

### 1. Régression Logistique (Baseline)
![Importance LR](LR.png)
* **Signal Maître** : `Failed_Transaction_Count_7d` est le prédicteur n°1 (Score 1.0).
* **Analyse** : Le modèle est très sensible aux échecs de paiement récents mais génère trop de faux positifs.

### 2. Random Forest
![Importance RF](RF.png)
* **Précision de 100%** : Idéal pour un blocage automatique sans risque pour les clients légitimes.
* **Variables clés** : Introduit la notion de distance (`Transaction_Distance`) et d'ancienneté (`Card_Age`).

### 3. Gradient Boosting (GBM)
![Importance GB](GB.png)
* **Variables Clés** : Comme les autres modèles d'ensemble, il s'appuie massivement sur l'historique d'échecs, mais affine sa précision (0.997) via la correction séquentielle des erreurs.
* **Synthèse** : Offre une performance robuste avec un AUC de **0.810**, égalant les meilleurs modèles d'ensemble.

### 4. Gradient Boosting & XGBoost
![Importance XGB](XGB.png)
* **Rigueur** : XGBoost atteint **99.9% de précision**.
* **Focus** : Focalisation extrême sur les signaux techniques (IP, Authentification).

### 5. LightGBM (Modèle Final)
![Importance LGB](LGB.png)
* **Vision Multidimensionnelle** : Contrairement aux autres, il équilibre l'importance entre le montant, le solde et l'historique. 
* **Bénéfice** : Cette nuance lui permet de capturer plus de fraudes (**Recall 62%**) tout en restant ultra-fiable.

---

## 🔁 Reproductibilité & Bonnes Pratiques
* **Seeds fixées** pour des résultats constants.
* **Séparation stricte** des jeux de données (Train/Val/Test).
* **Pipelines clairs** pour le prétraitement et la modélisation.

---

## 📈 Impact Attendu (Exemple pour 10 000 transactions)
| Approche | Fraudes manquées | Coût des pertes | Économie réalisée |
| :--- | :---: | :---: | :---: |
| Sans système | 100 | 310 € | - |
| **Avec IA (LightGBM)** | 38 | 117.80 € | **+ 192.20 €** |

---

## 👤 Auteur
**Kossi Noumagno**
*Data Analyst / Futur Data Scientist*
