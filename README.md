# Pipeline d'analyse EEG avec MNE-Python 
 
Projet personnel réalisé en autodidacte dans le cadre de ma candidature en master de sciences cognitives. Ayant une formation en psychologie (L3), j'ai voulu m'initier aux méthodes de traitement du signal EEG utilisées en neurosciences cognitives, en apprenant à utiliser la librairie MNE-Python à partir de la documentation officielle et de l'article de Gramfort et al. (2013).
 

 
##  Objectif
 
Construire de zéro un pipeline EEG complet, du signal brut jusqu'aux potentiels évoqués pour comparer les réponses cérébrales à des stimuli **auditifs** et **visuels**, en reproduisant les étapes standards d'une analyse ERP.
 

 
##  Étapes du pipeline
 
 **Chargement des données** : Lecture du fichier `.fif` (MNE Sample Dataset) et sélection des canaux EEG, EOG et de stimulation.
 
 **Filtrage** : Filtre passe-bas à 40 Hz et passe-haut à 0.1 Hz pour isoler les fréquences d'intérêt.
 
 **Correction des artefacts oculaires (ICA)** : Algorithme FastICA pour identifier et exclure la composante liée aux clignements d'yeux.
 
 **Segmentation (Epoching)** : Découpage du signal en fenêtres de −0.3 s à +0.7 s autour des événements, avec rejet automatique des époques trop bruitées (seuil 
150 µV).
 **Potentiels évoqués (ERP)** : Moyenne des époques pour faire ressortir les composantes N100 et P200.
 
 **Comparaison auditif vs visuel** : Superposition des courbes et topographies à 100 ms et 200 ms.
 
 **Onde de différence** : Soustraction auditive − visuelle pour isoler le réseau spécifique au traitement auditif.
 

 
##  Lancer le notebook
 
### Dépendances
 
```bash
pip install mne matplotlib
```
 
### Exécution
 
```bash
jupyter notebook pipeline_mne.ipynb
```
 
> Le jeu de données MNE Sample se télécharge automatiquement à la première exécution.
 

 
##  Références
 
- **Gramfort, A. et al.** (2013). MEG and EEG data analysis with MNE-Python. *Frontiers in Neuroscience, 7*. https://doi.org/10.3389/fnins.2013.00267
- **Hyvärinen, A.** (1999). Fast and robust fixed-point algorithms for independent component analysis. *IEEE Transactions on Neural Networks, 10*(3).
