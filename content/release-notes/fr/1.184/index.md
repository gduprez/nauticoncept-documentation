---
title: "Notes de version 1.184"
description: "Release notes v1.184 du 2026-07-23"
date: "2026-07-23"
version: "1.184"
---

# Notes de version 1.184 — 2026-07-23

## ✨ Nouvelles fonctionnalités

### Affichage du statut de propriétaire et ajustement du décompte des abonnés par bateau
- **Pourquoi** : Distinguer clairement les propriétaires de navires parmi les utilisateurs associés et éviter de fausser le décompte réel du nombre d'abonnés payants rattachés à chaque bateau.
- **Ce qui a été fait** : Ajout d'un badge distinctif indiquant la qualité de propriétaire sur la liste des abonnés par bateau et mise à jour de la logique de calcul pour exclure automatiquement les propriétaires du total d'abonnés affiché.

### Ajout d'un champ de localisation des clés dans l'identité du bateau
- **Pourquoi** : Faciliter l'accès aux bateaux pour les équipes techniques et de gestion en centralisant l'information sur l'emplacement physique des clés directement sur la fiche d'identité du navire.
- **Ce qui a été fait** : Ajout d'un nouveau champ de saisie "Clé" (`accessInfos`) dans la section d'identité et de localisation du bateau sur le formulaire de gestion du bateau.

### Gestion des documents par dossiers, hashtags et double zone de glisser-déposer
- **Pourquoi** : Offrir une organisation plus flexible et rapide de la GED des bateaux, permettant de classer et filtrer efficacement les documents par mots-clés (hashtags) et d'importer facilement des fichiers ou dossiers entiers.
- **Ce qui a été fait** : Implémentation d'une interface complète de gestion de documents par dossiers, avec support d'étiquetage par hashtags, filtres de vue par tag, prévisualisation intégrée et mise en place d'une double zone d'import (dropzone) autorisant le glisser-déposer de fichiers et de dossiers.

### Option de tri chronologique et avancé de la liste des leads
- **Pourquoi** : Améliorer le suivi commercial et l'efficacité des équipes en permettant de trier les prospects selon des critères précis, tels que la date d'attribution des rendez-vous CRM.
- **Ce qui a été fait** : Intégration d'un sélecteur de tri multi-critères dans la vue liste des leads, permettant notamment un classement par ordre chronologique de la date d'attribution du rendez-vous.

### Spécification du taux de commission par bateau et calcul automatisé du MRM
- **Pourquoi** : Automatiser le calcul de la marge récurrente mensuelle (MRM) sur les abonnements pour garantir des données financières fiables, éviter les erreurs de saisie et synchroniser ces métriques directement avec le CRM HubSpot.
- **Ce qui a été fait** : Ajout de la possibilité de définir un taux de commission spécifique par navire, mise en place de la formule de calcul automatique du MRM, automatisation du passage au statut validé lors de la finalisation de l'onboarding (avec suppression du bouton manuel obsolète) et synchronisation directe via API vers HubSpot.

### Synchronisation et appariement des bateaux avec la plateforme MMK
- **Pourquoi** : Résoudre les blocages lors du rapprochement entre un bateau existant dans l'application et une unité enregistrée sur MMK, afin d'assurer une synchronisation fluide des réservations et caractéristiques.
- **Ce qui a été fait** : Création d'un composant modal dédié permettant la recherche, la liaison interactive et la déliaison des bateaux NautiConcept avec le catalogue de yachts MMK.

## 🐛 Corrections de bugs

### Affichage d'un message d'erreur clair lors de la saisie d'une adresse e-mail invalide
- **Pourquoi** : Éviter que des réservations de location soient créées avec des coordonnées clients erronées ou inexploitables sans avertissement préalable de l'utilisateur.
- **Ce qui a été fait** : Ajout d'une validation stricte de format sur le champ d'adresse e-mail lors de la création d'un nouveau client en location standard, avec affichage immédiat d'un message d'alerte explicite en cas de format invalide.

### Conservation du client créé lors de son retour sur le formulaire de réservation
- **Pourquoi** : Éviter d'avoir à rechercher et sélectionner à nouveau un client venant d'être créé lorsqu'on revient à l'écran de création d'une location standard.
- **Ce qui a été fait** : Amélioration de la gestion des paramètres de navigation permettant de transmettre et d'activer automatiquement le client fraîchement créé lors du retour vers l'interface de réservation.

### Correction d'une erreur lors de l'ajout d'une accréditation partielle avec des services complémentaires
- **Pourquoi** : Éliminer un message d'erreur intempestif apparaissant lors de l'attribution d'une accréditation partielle sur un bateau de démonstration ou de flotte.
- **Ce qui a été fait** : Ajout de vérifications de sécurité (null-checks) sur les tableaux de services complémentaires afin de sécuriser l'initialisation et d'empêcher les exceptions au chargement des formulaires d'accréditation.

### Prise en compte automatique des tags photos lors de l'ajout d'images dans une checklist
- **Pourquoi** : Garantir que les balises et annotations (photoTag) associées aux questions restent correctement attribuées et enregistrées lorsqu'une nouvelle photo est ajoutée à un élément de contrôle.
- **Ce qui a été fait** : Mise à jour du modèle de données des questions et des workflows de pièces jointes pour lier systématiquement la propriété `photoTag` aux nouvelles images capturées ou importées.

## 🔧 Améliorations

### Accès rapide au profil de l'abonné depuis l'en-tête et retour simplifié
- **Pourquoi** : Rendre la navigation plus fluide entre la vue d'abonnement et la fiche client détaillée sans perdre le contexte d'origine de la recherche.
- **Ce qui a été fait** : Rendus le nom et prénom de l'abonné cliquables dans l'en-tête pour rediriger directement vers sa fiche détaillée, et correction du comportement du bouton retour pour revenir précisément à la liste d'origine.

### Affichage direct des anomalies de caution sur les fiches de location
- **Pourquoi** : Permettre aux gestionnaires d'identifier immédiatement les anomalies ou irrégularités sur les cautions déposées sans devoir ouvrir le formulaire d'édition complet.
- **Ce qui a été fait** : Intégration d'un indicateur/badge d'anomalie visible directement sur la vue synthétique de la caution, informant l'utilisateur au premier coup d'œil.

### Bouton d'accès direct à l'accueil présent en permanence dans Charter
- **Pourquoi** : Offrir un raccourci direct vers le tableau de bord principal depuis n'importe quel écran du module Charter (checkin, checkout, timeline), évitant de multiples clics successifs sur la flèche retour.
- **Ce qui a été fait** : Ajout d'une option d'en-tête personnalisée (`titleSuffixTemplate` / raccourci Home) permettant d'insérer un bouton de retour à l'accueil permanent sur la barre de titre de la page.

### Bouton d'information boîte à clés dans l'en-tête de check-in et check-out
- **Pourquoi** : Permettre un accès instantané aux instructions de la boîte à clés pendant les opérations de départ ou de retour d'un bateau sans quitter le déroulé du contrôle.
- **Ce qui a été fait** : Intégration d'un bouton d'accès rapide dans l'en-tête des vues de checkin/checkout Charter, affichant les détails et codes de la boîte à clés du navire.

### Masquage intelligent des paramètres de réservation partielle en location standard
- **Pourquoi** : Clarifier l'interface utilisateur pour les offres de location standard en masquant les options de réservations partielles, ces dernières étant réservées exclusivement à la formule Liberty Pass.
- **Ce qui a été fait** : Ajout d'une condition d'affichage sur les panneaux d'informations commerciales pour masquer le bloc "Paramètres réservations partielles" lorsque le contrat est en mode standard, et le maintenir visible uniquement en mode Liberty Pass.

### Mise à jour automatique du statut HubSpot du lead à la validation de l'onboarding
- **Pourquoi** : Assurer la synchronisation automatique des statuts commerciaux dans le CRM HubSpot lorsqu'un prospect valide son parcours d'intégration avec un professionnel.
- **Ce qui a été fait** : Implémentation du passage automatique du statut HubSpot de "Rendez-vous à prendre" à un statut neutre/néant dès la validation complète du dossier d'onboarding.

### Persistence et affichage continu des données de télémétrie et jauges NMEA
- **Pourquoi** : Conserver et afficher la dernière valeur connue des jauges (carburant, eau, niveau de batterie, heures moteur, sondeur) sur le tableau de bord de la flotte, y compris après l'extinction de la centrale de navigation du bateau.
- **Ce qui a été fait** : Développement de la prise en charge du champ `lastKnownValues` dans la structure du dernier message du module et intégration de fonctions d'exploitation permettant de restituer visuellement les niveaux connus avec leur horodatage.

### Recherche des techniciens par nom d'équipe lors de l'affectation à une tâche
- **Pourquoi** : Faciliter le travail des planificateurs en leur permettant d'identifier rapidement le groupe de travail (atelier, staff) auquel appartient chaque intervenant lors de l'attribution d'une intervention.
- **Ce qui a été fait** : Enrichissement du composant de sélection des techniciens avec l'affichage explicite du nom de l'équipe (`workingGroup`) à côté du nom de chaque collaborateur.
