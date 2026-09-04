# HR Turnover Prediction - Random Forest

Système d'aide à la décision RH basé sur le Machine Learning pour estimer le risque de turnover des collaborateurs à 12 mois.

---

### Avertissement éthique et décisionnel

Ce modèle est un outil d'aide à la décision destiné à guider les actions de fidélisation RH. Il ne doit pas être utilisé de manière autonome pour prendre des décisions d'embauche, de promotion ou de rupture de contrat.

---

## Aperçu du Projet

Le turnover imprévu entraîne des coûts de recrutement élevés, une perte de compétences clés et une perturbation des équipes.

Ce projet propose un modèle basé sur l'algorithme Random Forest permettant d'analyser le profil d'un collaborateur ou d'un candidat afin de :
* Estimer la probabilité de départ à 12 mois.
* Classer le risque en 3 niveaux (Faible, Modéré, Élevé).
* Aider les équipes RH à orienter leurs actions de rétention.

---

## Approche Machine Learning et Pipeline

Le modèle s'appuie sur l'algorithme Random Forest Classifier de la bibliothèque scikit-learn.

1. Données RH : Collecte des informations candidat/collaborateur.
2. Feature Engineering : Calcul d'écarts et d'indicateurs combinés.
3. Sélection des variables : Conservation de 18 variables explicatives.
4. Division des données : Split 80% entraînement / 20% test.
5. Modélisation : Entraînement et évaluation du Random Forest.
6. Résultat : Estimation de la probabilité et classification du niveau de risque.

---

## Variables Utilisées (18 Features)

* Risque_Rotation_Fit : Combinaison du turnover d'équipe et du fit culturel.
* Score_Fit_Culturel : Adéquation avec la culture d'entreprise.
* Taux_Rotation_Equipe_Visee : Taux de turnover historique de l'équipe cible.
* Nb_Entretiens_Paralleles : Nombre de processus de recrutement menés en parallèle.
* Delai_Acceptation_Jours : Délai de réponse du candidat.
* Anciennete_Moyenne_Precedente_Mois : Ancienneté moyenne lors des expériences passées.
* Nb_Entreprises_3_Ans : Nombre d'entreprises fréquentées sur les 3 dernières années.
* Age : Âge du candidat ou du collaborateur.
* Distance_Maison_Bureau_KM : Distance domicile-travail.
* Salaire_Propose : Rémunération proposée.
* Pretentions_Salariales : Prétentions salariales formulées.
* Ecart_Salaire : Différence entre salaire proposé et prétentions.
* Score_Test_Technique : Résultat à l'évaluation technique.
* Changement_Secteur : Reconversion ou changement de domaine.
* Score_Engagement_Entretien : Niveau d'engagement observé en entretien.
* Note_Verification_References : Évaluation issue de la prise de références.
* Ecart_Marche_Pct : Écart de rémunération par rapport au marché.
* Clarte_Projet_Pro : Clarté et alignement du projet professionnel.

---

## Configuration du Modèle et Performances

### Configuration
* Algorithme : RandomForestClassifier
* Arbres (n_estimators) : 400
* Profondeur max (max_depth) : 10
* Équilibrage des classes : balanced
* Validation croisée : 5-fold

### Performances (Jeu de données de prototype)

Note : Les résultats suivants sont obtenus sur un jeu de données synthétique utilisé pour le prototypage. Ils ne reflètent pas directement les performances du modèle dans un environnement réel.

* Accuracy (Jeu de test) : ~85.8 %
* Accuracy (Validation croisée) : ~86.7 %
* Répartition : 80% Train / 20% Test

---

## Grille de Lecture du Risque

Le modèle convertit la probabilité de départ en un score de 0 à 100% :

* Score < 40% : Risque FAIBLE (Suivi standard).
* Score 40% à 59.9% : Risque MODÉRÉ (Entretien de pointage / Analyse des attentes).
* Score >= 60% : Risque ÉLEVÉ (Revue de la rémunération, de la charge ou de l'équipe).

---

## Installation et Utilisation

### 1. Installation
```bash
git clone [https://github.com/USERNAME/REPOSITORY.git](https://github.com/USERNAME/REPOSITORY.git)
cd REPOSITORY
pip install -r requirements.txt
