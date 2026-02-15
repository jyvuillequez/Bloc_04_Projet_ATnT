# Bloc 04 – Projet AT&T

Analyse de données textuelles SMS et améliorer les stratégies de détection des spams.

Projet réalisé dans le cadre de la certification **RNCP Niveau 6 – Concepteur Développeur en Science des données (Jedha Bootcamp)**.

## 1. Contexte & enjeux

- **Problématique métier :** Mettre en place un classificateur de SMS capable de détecter automatiquement les messages spam afin de réduire spam sans bloquer les messages légitimes.
- **Décideurs cibles :** Produit, sécurité SI, service relation client

## 2. Objectifs du projet

- Construire une baseline simple et interprétable pour la détection de spam (référence naïve → modèles classiques).
- Comparer plusieurs approches NLP / ML / Deep Learning (TF-IDF + LogReg, CNN/RNN, Transformer) avec un protocole commun.
- Fournir une synthèse de performance et les recommandations associées (modèle cible, compromis performance / coût / latence).

## 3. Compétences mobilisées

- Analyse exploratoire de données (EDA)
- Préparation et nettoyage de données
- Modélisation / Deep Learning
- Visualisation et restitution

## 4. Données

- **Source :** Dataset SMS "ham/spam" (messages textuels étiquetés).
- **Périmètre :** 5,5k SMS, split train/test stratifié (déséquilibre de classe = 13% spam).
- **Variables clés :**  
  - text : contenu du SMS
  - y : label (0 = ham, 1 = spam)

## 5. Méthodologie

1. **Préparation des données**
Nettoyage léger (normalisation, tokenisation selon pipeline).

Split stratifié train/test pour conserver le taux de spam.
2. **Analyse exploratoire**
- Déséquilibre de classes (ham vs spam).
- Analyse sémantique : termes/lemmes fréquents par classe.
- Sentiment analysis : comparaison ham vs spam (signal exploratoire).
3. **Modélisation / analyse avancée**
- Baseline 0 : Naïf stratified (référence minimale).
- Modèles classiques : TF-IDF + Logistic Regression.
- Deep Learning : SimpleCNN et SimpleRNN/GRU (embeddings appris).
- Transformer : DistilBERT fine-tuné.
- Évaluation commune : focus sur classe spam (1) + PR-AUC.
4. **Restitution**
- Comparaison des modèles (tableau métriques + confusion matrices).
- Sélection du meilleur compromis (performance vs complexité).
- Recommandations de mise en production (itérations futures).

## 6. Résultats

- Le modèle naïf stratified fournit une référence basse (spam très mal détecté), utile pour démontrer le gain réel des modèles.
- TF-IDF + LogReg est une baseline solide, rapide et interprétable, avec de très bonnes performances sur spam.
- DistilBERT obtient la meilleure performance globale (meilleur compromis précision/rappel spam + PR-AUC), au prix d’un coût de calcul supérieur.
- [Recommandation business principale]
- [Limites du projet + pistes d’amélioration]

## 7. Installations des librairies Python
```text
python -m pip install -r requirements.txt
```

## 8. Organisation du projet

```text
.
├─ data/
│  ├─ raw/       # données brutes
│  └─ outputs/   # exports csv
├─ notebooks/    # notebooks Jupyter (EDA et modèles)
└─ présentation/ # slides, exports captures d'images
