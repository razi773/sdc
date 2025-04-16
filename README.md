# 🐟 Détection de Filets de Pêche – Projet SDC

## 📌 Description du Projet
Ce projet vise à **détecter automatiquement les filets de pêche dans des images** à l’aide de modèles d’intelligence artificielle. Il s’inscrit dans une démarche de préservation marine et de lutte contre la pêche illégale, en permettant une **détection rapide et visuelle** des équipements utilisés.

Le modèle utilisé est hébergé sur [Roboflow](https://roboflow.com) et a été pré-entraîné à partir d’un jeu de données annoté spécifique.

---

## 🎯 Objectifs
- Détecter les filets de pêche dans des images de l’environnement marin.
- Fournir une interface simple d’utilisation pour les tests et les prédictions.
- Pouvoir intégrer ce modèle dans une future solution temps réel (drone, caméra sous-marine, etc.).

---

## 🛠️ Technologies Utilisées
- 🧠 **Roboflow** : hébergement et entraînement du modèle de vision par ordinateur.
- 🐍 **Python** : pour le scripting et l’intégration.
- 📦 **Jupyter Notebook / Google Colab** : environnement d’exécution.
- 🖼️ **OpenCV / IPython** : visualisation des images.

---

## ⚙️ Installation

Installe les dépendances nécessaires :

```bash
pip install roboflow
```

---

## 🚀 Utilisation

Voici les étapes clés pour utiliser ce notebook :

```python
# 1. Importation
from roboflow import Roboflow
from IPython.display import Image

# 2. Authentification et chargement du modèle
rf = Roboflow(api_key="NyhQ5Zvkh5tVTgczeW1C")
project = rf.workspace().project("fish-net-detection")
model = project.version(2).model

# 3. Prédiction sur une image
prediction = model.predict("/content/image.jpg")

# 4. Sauvegarde et affichage du résultat
prediction.save("/content/result.jpg")
Image("/content/result.jpg")

# 5. Extraction des objets détectés
predictions_json = prediction.json()
detected_labels = [prediction["class"] for prediction in predictions_json["predictions"]]
print("Objets détectés:", detected_labels)
```

---

## 🖼️ Exemple de Résultat

Une image test sera analysée par le modèle et le résultat affichera les filets de pêche détectés sous forme de boîtes englobantes.

---

## 📁 Organisation du Code

- `SDC.ipynb` : Notebook principal contenant le script d’inférence.
- `README.md` : Ce fichier.
- `result.jpg` : Image résultat après détection.
- `image.jpg` : Image d’entrée utilisée pour la détection.

---

## 👤 À propos

Ce projet a été développé dans le cadre d’un projet étudiant, combinant **IA et écologie** pour une meilleure gestion des ressources marines.

---

## 📄 Licence

Ce projet est sous licence MIT. Vous pouvez le réutiliser, le modifier et le partager librement avec attribution.

---
