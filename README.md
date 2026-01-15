# Projet de Détection de Fraude Bancaire

##  Contexte et Enjeux
La fraude bancaire représente un défi majeur pour les institutions financières. Chaque année, des **milliards d’euros** sont perdus à travers différentes formes de fraude :

- Usurpation d’identité  
- Transactions non autorisées  
- Falsification de documents  

L’impact est double :

- **Financier** : pertes directes liées aux transactions frauduleuses  
- **Réputationnel** : perte de confiance des clients et partenaires  

---

## 💰 Impact Économique
Chaque fraude non détectée entraîne un coût moyen de **3,10 €** de remboursement pour l’institution financière.

| Fraudes non détectées | Coût des remboursements |
|----------------------|-------------------------|
| 1 000 | 3 100 € |
| 10 000 | 31 000 € |
| 100 000 | 310 000 € |

⚠️ Ces chiffres n’incluent pas :
- Les coûts administratifs  
- Les coûts d’enquête  
- Les pertes liées à la réputation  

---

##  Pourquoi la Détection de Fraude est Critique

### 1️⃣ Impact Financier Direct
Chaque transaction frauduleuse génère :
- Un remboursement au client
- Des frais de contestation
- Une perte de confiance

### 2️⃣ Volume Massif de Transactions
Les banques traitent **des millions de transactions par jour**.  
➡️ Un contrôle manuel est impossible, le **Machine Learning est indispensable**.

### 3️⃣ Besoin de Réactivité
Une fraude détectée **en temps réel** peut être bloquée avant validation.  
Un simple retard de quelques heures peut rendre l’argent irrécupérable.

### 4️⃣ Un Équilibre Délicat
- 🚨 Trop agressif → trop de fausses alertes, clients mécontents  
- 💤 Trop conservateur → fraudes non détectées, pertes financières  

---

## 🤖 Objectif du Projet
Développer un **système automatisé de détection de fraude** capable de :

- Maximiser le **Recall** (détecter un maximum de fraudes)
- Maintenir une **Precision** acceptable (limiter les fausses alertes)
- Permettre une **intervention rapide** (temps réel)
- Éviter le blocage injustifié des clients légitimes

 **Objectif final** : optimiser le **coût-bénéfice global** en tenant compte :
- Du coût d’une fraude non détectée
- Du coût d’une fausse alerte

---

## Approche Méthodologique

### 🔍 1. Compréhension des Données
Analyse exploratoire approfondie pour identifier :
- Les patterns de fraude
- Les caractéristiques des transactions suspectes
- Les corrélations entre variables

###  2. Feature Engineering
Création de variables discriminantes :
- Montants et fréquence des transactions
- Localisation et comportements inhabituels
- Historique client
- Signaux de risque (échecs de paiement, anomalies)

###  3. Modélisation Machine Learning
Comparaison de plusieurs algorithmes :

- **Logistic Regression** : baseline interprétable
- **Random Forest** : modèle ensembliste robuste
- **Gradient Boosting** : modèle performant par boosting

###  4. Optimisation & Validation
- Validation croisée **5-fold**
- Prévention du sur-apprentissage (overfitting)
- Comparaison via des métriques adaptées aux données déséquilibrées

---

##  Résultats

| Modèle | ROC-AUC | Recall | Precision | F1-Score |
|------|--------|--------|-----------|----------|
| Logistic Regression | 0.812 | 1.000 | 0.321 | 0.486 |
| Random Forest | 0.811 | 0.834 | 0.414 | 0.553 |
| Gradient Boosting | 0.807 | 0.623 | 0.981 | 0.762 |

### Analyse
- **Logistic Regression**  
  ✔️ Détecte 100% des fraudes  
  ❌ Trop de fausses alertes  

- **Random Forest**  
  ✅ Bon compromis entre Recall et Precision  

- **Gradient Boosting**  
  ✔️ Très peu de fausses alertes  
  ❌ Manque trop de fraudes  

 **Modèle recommandé : Random Forest**

---

## Impact Attendu

Un système de détection performant permet :

-  Réduction des pertes financières
-  Diminution des coûts opérationnels
-  Amélioration de l’expérience client
-  Détection en temps réel des fraudes

### Exemple d’Impact
Sur **10 000 transactions** dont **100 frauduleuses** :

| Approche | Fraudes détectées | Fraudes manquées | Coût des pertes |
|--------|------------------|-----------------|----------------|
| Sans système | 0 | 100 | 310 € |
| Random Forest | 83 | 17 | 52,70 € |

💰 **Économie réalisée : 257,30 €**  
(Calcul basé sur un coût moyen de 3,10 € par fraude)

---
## 🔁 Reproductibilité & Bonnes Pratiques

Ce projet a été conçu selon les **standards professionnels de la Data Science**, afin de garantir :

- 🔄 La **reproductibilité des résultats**
- 🧪 La **traçabilité des expérimentations**
- 🏗️ Une structure claire et maintenable

### Principes appliqués
- Utilisation de **seeds aléatoires fixées** pour garantir des résultats reproductibles
- Séparation stricte :
  - Données d’entraînement
  - Données de validation
  - Données de test
- Validation croisée **5-fold**
- Métriques adaptées aux **données fortement déséquilibrées**
- Pipelines clairs pour le prétraitement et la modélisation

### Évaluation orientée métier
Les métriques ne sont pas uniquement techniques :
- Le **Recall** est prioritaire (fraudes détectées)
- La **Precision** est surveillée pour limiter les coûts opérationnels
- Les résultats sont analysés sous l’angle **coût-bénéfice métier**

---

## 🛠️ Installation & Exécution du Projet

### 📋 Prérequis
- Python **>= 3.9**
- Environnement virtuel recommandé (venv / conda)

###  Dépendances principales
- `numpy`
- `pandas`
- `scikit-learn`
- `matplotlib`
- `seaborn`
- `jupyter`

---

###  Installation locale

```bash
# Cloner le dépôt
git clone https://github.com/Dave-kossi/bank-transaction-fraud-detection.git
cd bank-transaction-fraud-detection

# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate  # Linux / Mac
venv\Scripts\activate     # Windows


---

##  Conclusion
Ce projet démontre l’impact **majeur du Machine Learning** dans la lutte contre la fraude bancaire.

Grâce à :
- Des données de qualité  
-  Un feature engineering pertinent  
-  Des modèles optimisés  
-  Une évaluation rigoureuse  

Il est possible de déployer un système **efficace, rentable et scalable**, offrant un **retour sur investissement significatif** pour les institutions financières.

---

## 👤 Auteur
**Kossi Noumagno**  
Junior Data Analyst / Data Scientist  
