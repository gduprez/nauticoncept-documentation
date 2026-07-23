---
title: "Notes de version 1.186"
description: "Notes de version v1.186 du 2026-07-23"
date: "2026-07-23"
version: "1.186"
---

# Notes de version 1.186 — 2026-07-23

## ✨ Nouvelles fonctionnalités

### Gestion des documents par dossier et classement par hashtags
- **Pourquoi** : La gestion d'un volume important de documents de bateaux devenait complexe et peu structurée, rendant la recherche et l'organisation des fichiers fastidieuses pour les utilisateurs.
- **Ce qui a été fait** : Implémentation d'une nouvelle vue par dossiers et par hashtags pour les documents de bateaux, création d'un composant de saisie de hashtags (`FormInputHashtagComponent`), ajout d'un bouton de prévisualisation et d'ouverture de documents dans un nouvel onglet, et ajustement de l'interface d'affichage pour les fichiers non étiquetés.

## 🐛 Corrections de bugs

### Ajustement de l'affichage des alertes et maintien des relevés NMEA de carburant
- **Pourquoi** : Lors de l'extinction de la centrale de navigation du bateau, l'absence de mise à jour des données NMEA entraînait la perte de lecture de l'état des jauges d'essence pour les professionnels sans rallumer l'équipement.
- **Ce qui a été fait** : Correction du calcul de la vitesse moteur et affinage de la détection des modes moteurs dans les cartes de messages afin de conserver et d'afficher le dernier état connu des jauges de carburant même lorsque le système de navigation principal est éteint.

### Correction de la synchronisation et du matching des bateaux avec MMK
- **Pourquoi** : Il était impossible d'associer ou de faire correspondre un bateau existant dans l'application avec sa fiche correspondante dans le système de réservation MMK, bloquant la synchronisation des réservations.
- **Ce qui a été fait** : Implémentation complète d'un composant modal de correspondance (`match-boat-mmk`), de l'intégration des API MMK pour l'association et la dissociation de bateaux, et ajout d'options conditionnelles de suppression d'association.

### Correction du marquage automatique des photos dans les checklists
- **Pourquoi** : Lors de la création d'une checklist configurée avec des tags sur les photos, l'ajout d'une nouvelle prise de vue n'appliquait pas automatiquement le tag prédéfini.
- **Ce qui a été fait** : Prise en charge de la propriété `photoTag` dans le modèle des questions de checklist et intégration du flux de données pour associer automatiquement les tags aux pièces jointes ajoutées.

### Gestion des erreurs sur les réservations de démonstration sans services complémentaires
- **Pourquoi** : L'ajout d'une accréditation partielle sur des bateaux de démonstration déclenchait un message d'erreur système bloquant, dû à l'absence de services complémentaires configurés.
- **Ce qui a été fait** : Ajout de vérifications de valeurs nulles (`null-checks`) sur les tableaux de services complémentaires et report de l'initialisation des paramètres globaux lors du chargement du composant.

### Notification d'erreur pour les adresses email invalides lors de la création d'un client
- **Pourquoi** : Dans le module de location standard, la saisie d'une adresse email invalide lors de la création d'un nouveau client ne renvoyait aucun message explicatif, induisant l'utilisateur en erreur.
- **Ce qui a été fait** : Ajout des clés de localisation et amélioration de la validation du formulaire de saisie client pour afficher un message clair indiquant que l'adresse email est invalide.

## 🔧 Améliorations

### Affichage direct des anomalies de caution
- **Pourquoi** : Les utilisateurs devaient impérativement ouvrir la fenêtre d'édition d'une caution pour consulter les éventuelles anomalies, ce qui ralentissait le suivi financier des locations.
- **Ce qui a été fait** : Ajustement du filtrage des données de souscription de location et mise à jour des traductions de notification pour rendre les anomalies de caution visibles directement depuis la vue globale.

### Affichage du statut propriétaire et exclusion du décompte des abonnés
- **Pourquoi** : Les propriétaires de bateaux étaient comptabilisés à tort parmi les abonnés standards, ce qui faussait les statistiques et le nombre réel d'abonnés par navire.
- **Ce qui a été fait** : Ajout d'un badge distinctif indiquant si l'abonné est propriétaire du bateau et modification de la logique de calcul pour exclure automatiquement les propriétaires du décompte des abonnés.

### Ajout d'un champ d'information pour la localisation des clés du bateau
- **Pourquoi** : L'emplacement physique ou les modalités d'accès aux clés du navire n'étaient pas clairement indiqués dans l'identité du bateau.
- **Ce qui a été fait** : Ajout du champ d'information d'accès aux clés (`accessInfos`) dans la section d'identification/localisation de la fiche bateau, accompagné des traductions en français et anglais.

### Masquage conditionnel des paramètres de réservation partielle en location standard
- **Pourquoi** : Le panneau "Paramètres réservations partielles" s'affichait inutilement dans les informations commerciales lors des locations de type Standard, alors qu'il ne concerne que les offres Liberty Pass.
- **Ce qui a été fait** : Modification du comportement d'affichage de la fiche bateau pour masquer la vue des réservations partielles lorsque le mode de location est défini en location Standard.

### Navigation retour et accès rapide à la fiche abonné
- **Pourquoi** : La navigation dans les détails de réservation nécessitait de multiples clics pour revenir en arrière ou accéder aux détails du profil client.
- **Ce qui a été fait** : Prise en charge du comportement de retour arrière direct via l'en-tête de page (`PageTitle`) et intégration de liens cliquables sur les nom et prénom de l'abonné pour accéder directement à sa fiche.

### Recherche de techniciens par nom d'équipe lors de l'affectation des tâches
- **Pourquoi** : Lors de l'attribution d'une tâche, il n'était pas possible de filtrer ou de rechercher les membres de l'équipe selon leur groupe de travail (Atelier ou Staff).
- **Ce qui a été fait** : Intégration des informations de groupe de travail (`workingGroup`) dans les options de sélection et les libellés d'affichage des techniciens pour faciliter la recherche par équipe.

### Tri personnalisé dans la liste des prospects (leads)
- **Pourquoi** : L'absence d'options de tri dans la liste des prospects empêchait les professionnels d'organiser leur suivi commercial par ordre chronologique ou par date d'attribution des rendez-vous.
- **Ce qui a été fait** : Implémentation d'une fonctionnalité de tri multi-critères dans la vue des leads, permettant d'ordonner la liste selon différents critères pour un meilleur suivi commercial.
