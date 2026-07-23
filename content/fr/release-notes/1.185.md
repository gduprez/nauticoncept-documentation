---
title: "Notes de version 1.185"
description: "Notes de version v1.185 du 2026-07-23"
date: "2026-07-23"
version: "1.185"
---

# Notes de version 1.185 — 2026-07-23

## 🔧 Améliorations

### Affichage direct des alertes d'anomalie de caution
- **Pourquoi** : Permettre aux gestionnaires de repérer immédiatement les incohérences de caution (telles qu'une ventilation incomplète) sans devoir ouvrir le formulaire d'édition complet.
- **Ce qui a été fait** : Restitution directe des messages d'avertissement et des anomalies de caution ("Ventilation de caution incomplète") dans l'interface principale de suivi.

### Affichage du badge propriétaire et ajustement du décompte des abonnés
- **Pourquoi** : Distinguer clairement les abonnés propriétaires des abonnés réguliers sur un navire afin de ne pas fausser le décompte réel des abonnés actifs.
- **Ce qui a été fait** : Ajout d'un badge explicite "Propriétaire" sur la fiche abonné et exclusion automatique des propriétaires dans le calcul du total d'abonnés par bateau.

### Amélioration de la navigation de retour et personnalisation de l'en-tête de page
- **Pourquoi** : Rendre la navigation plus directe entre la fiche d'abonnement et la vue d'ensemble, en évitant des clics multiples et en permettant l'accès direct aux détails de l'abonné.
- **Ce qui a été fait** : Évolution du composant de titre de page (`PageTitle`) pour prendre en charge des liens de retour personnalisés (`backLink`), des paramètres de requête et un template de titre interactif (`titleSuffixTemplate`).

### Champ d'informations d'accès et localisation des clés sur la fiche bateau
- **Pourquoi** : Permettre aux équipes techniques et d'exploitation de connaître l'emplacement et la procédure d'accès aux clés du bateau directement depuis sa fiche descriptive.
- **Ce qui a été fait** : Intégration d'un nouveau champ d'accès aux clés (`boat access info field`) dans la section d'identité et de localisation du bateau avec les clés de traduction associées.

### Gestion des documents de bateau par dossiers, hashtags et prévisualisation
- **Pourquoi** : Structurer la documentation des navires pour faciliter le classement, le filtrage rapide par mots-clés et la consultation en ligne des fichiers.
- **Ce qui a été fait** : Ajout du système de gestion des dossiers, du filtrage par hashtags, de la prévisualisation et de l'ouverture des documents dans un nouvel onglet, ainsi que de l'amélioration de l'affichage des documents non tagués.

### Masquage des paramètres de réservation partielle en mode de location standard
- **Pourquoi** : Éviter d'afficher des options inutiles ou déroutantes dans les informations commerciales lors des locations standard, ces paramètres ne concernant que la formule Liberty Pass.
- **Ce qui a été fait** : Conditionnement de l'affichage du bloc "Paramètres réservations partielles" pour qu'il soit automatiquement masqué en location standard et conservé uniquement pour le mode Liberty Pass.

### Prise en compte des tags photo lors de l'ajout d'images dans une checklist
- **Pourquoi** : S'assurer que les balises ou annotations d'images configurées dans les modèles de questions s'appliquent correctement lorsque de nouvelles photos sont ajoutées à une checklist.
- **Ce qui a été fait** : Intégration de la propriété `photoTag` dans le modèle de données des questions et synchronisation automatique des tags photo dans les flux d'attachements et pièces jointes.

### Recherche des techniciens par nom d'équipe lors de l'affectation à une tâche
- **Pourquoi** : Faciliter le choix d'un intervenant lors de l'attribution d'une tâche en identifiant immédiatement son groupe de travail (atelier, staff, etc.).
- **Ce qui a été fait** : Inclusion du nom du groupe de travail (`workingGroup`) dans le libellé des sélecteurs de techniciens et dans les critères de recherche.

### Sécurisation des services complémentaires lors de l'attribution d'accréditations partielles
- **Pourquoi** : Prévenir l'apparition d'erreurs ou de dysfonctionnements lors de l'ajout d'une accréditation partielle sur un navire disposant de services complémentaires.
- **Ce qui a été fait** : Ajout de vérifications de sécurité (`null-checks`) sur les tableaux de services complémentaires et report de l'initialisation des paramètres dans `ngOnInit`.

### Synchronisation et appariement des bateaux avec le catalogue MMK
- **Pourquoi** : Permettre l'association fluide d'un navire enregistré dans l'application avec un yacht disponible sur le système de réservation externe MMK.
- **Ce qui a été fait** : Implémentation du composant modal d'appariement MMK avec sélection interactive, gestion de la liaison/déliaison (`isLinked`), suppression de l'association et synchronisation API.

### Tri multi-critères et chronologique de la liste des prospects (leads)
- **Pourquoi** : Offrir aux professionnels une meilleure visibilité sur le suivi de leurs prospects en permettant leur classement par ordre chronologique ou par date d'attribution CRM.
- **Ce qui a été fait** : Ajout de fonctionnalités de tri avancées dans l'interface de gestion des leads pour ordonner facilement la liste selon plusieurs critères métier.

### Validation et alerte en cas d'adresse e-mail invalide lors de la création d'un client
- **Pourquoi** : Éviter la création de comptes ou de réservations avec une adresse e-mail mal renseignée en informant immédiatement l'utilisateur.
- **Ce qui a été fait** : Renforcement du contrôle de validation du formulaire de création client avec ajout de messages d'erreur ciblés et explicites en cas d'e-mail invalide.
