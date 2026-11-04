---
name: qa-analyse-causes-racines
description: >-
  Préparer une analyse structurée des causes d’une anomalie ou d’un incident.
  À utiliser pour comprendre pourquoi un problème est apparu, pourquoi
  il n’a pas été détecté plus tôt et comment prévenir sa réapparition.
  Utiliser les cinq pourquoi et un diagramme d’Ishikawa lorsque pertinent.
  Distinguer les faits des hypothèses et proposer des actions correctives et préventives à faire confirmer par l’équipe.
license: MIT
metadata:
  auteur: Vanessa ZEBAZE
  phase-stlc: Gestion des anomalies
  version: 1.0.0
---

# Analyse des causes racines

Recherche les causes et facteurs qui expliquent le problème au-delà de son symptôme.

Précise quels liens sont étayés par des preuves et lesquels restent des hypothèses à vérifier.

## Quand l’utiliser ?

- Une anomalie importante ou un incident nécessite une analyse des causes.
- Une rétrospective demande pourquoi le problème est apparu et pourquoi il n’a pas été détecté.
- Un problème récurrent nécessite des actions correctives et préventives.

## Workflow

### 1. Décris précisément le problème

Recueille :

- l’effet observé ;
- la date et les circonstances d’apparition ;
- le périmètre et l’impact connus ;
- la version et l’environnement ;
- la chronologie disponible ;
- les preuves : journaux, tickets, résultats de test ou comptes rendus.

Signale les éléments manquants.
N'invente pas de chronologie ni de chaîne causale.

### 2. Applique les cinq pourquoi

À partir du symptôme, recherche successivement pourquoi chaque événement ou condition s’est produit.

Pour chaque lien, précise :

- l’explication proposée ;
- la preuve disponible ;
- son statut : étayé ou hypothèse à vérifier.

N'impose pas exactement cinq niveaux.
Arrête ou ouvrre une branche lorsque les preuves sont insuffisantes.

### 3. Examine les facteurs avec Ishikawa

Recherche les facteurs pertinents dans les catégories suivantes :
 
- personnes : rôles, compétences, communication ou charge ;
- processus : règles, contrôles et organisation ;
- outils : configuration et fonctionnement ;
- données : qualité, disponibilité et états ;
- environnement : versions, interfaces et conditions d’exécution.

N'invente pas un facteur pour remplir chaque catégorie.
Plusieurs facteurs peuvent contribuer au même problème.

### 4. Distingue apparition et non-détection

Sépare :

- les causes ou facteurs ayant produit le défaut ;
- les raisons pour lesquelles les contrôles, revues ou tests ne l’ont pas détecté plus tôt.

Vérifie si le comportement concerné était prévu, testé et observable dans les conditions disponibles.

N'attribue pas automatiquement la non-détection à une erreur humaine.

### 5. Propose des actions

Distingue :

- les actions correctives : traite le problème ou ses causes identifiées ;
- les actions préventives : réduis le risque de problèmes similaires.

Pour chaque action, propose :

- un objectif ;
- un responsable ou une équipe à confirmer ;
- une échéance à convenir ;
- un moyen de vérifier son efficacité.

Ne présente pas les propositions comme des engagements déjà acceptés.

### 6. Fais confirmer l’analyse

Présente l’analyse comme un brouillon.

Liste les liens non vérifiés et les investigations nécessaires.

Fais confirmer les causes retenues et les actions par l’équipe avant de les considérer comme validées.

## Format de sortie

# Analyse des causes — [Anomalie / incident]

## Problème et impact

- Référence :
- Effet observé :
- Version et environnement :
- Date et périmètre :
- Impact connu :
- Sources :

## Analyse des pourquoi

| Niveau | Question | Explication proposée | Preuve | Statut |
|---|---|---|---|---|

## Facteurs contributifs

| Catégorie | Facteur identifié | Preuve ou vérification nécessaire |
|---|---|---|

## Causes retenues ou proposées

- Causes étayées :
- Hypothèses restantes :
- Raisons de non-détection :

## Plan d’action proposé

| Type | Action | Responsable proposé | Échéance à confirmer | Vérification d’efficacité |
|---|---|---|---|---|

## Points à confirmer

- Informations manquantes :
- Investigations nécessaires :
- Causes et actions à valider :

## Garde-fous

- Ne jamais affirmer une cause sans éléments suffisants.
- Ne pas inventer de journal/logs, d’événement ou de preuve.
- Ne pas conclure qu’une correction empêchera toute récidive.
- Privilégier l’analyse des systèmes et processus plutôt que la recherche
  d’un responsable à blâmer.
- Les causes et les actions restent proposées jusqu’à leur confirmation.
