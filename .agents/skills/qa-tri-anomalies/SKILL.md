----
name: qa-tri-anomalies

description: >-

Préparer le tri d’un ensemble d’anomalies. À utiliser pour organiser un backlog, rechercher des doublons possibles, proposer une sévérité, une priorité et une orientation vers un composant ou une équipe.Signaler les rapports incomplets. Présenter toutes les classifications comme des recommandations à confirmer, sans fusionner, fermer ou réaffecter automatiquement les tickets.
license: MIT
metadata:
auteur: Vanessa ZEBAZE
phase-stlc: Gestion des anomalies
version: 1.0.0
---
# Assistant de tri des anomalies
Organise le backlog d’anomalies afin que les Product Owners puissent se concentrer sur les décisions.
Présente des recommandations que les POs peuvent accepter, modifier ou rejeter.

## Quand l’utiliser ?

- Des anomalies nouvelles ou ouvertes doivent être préparées avant un tri.
- Une personne demande de rechercher les doublons, prioriser ou orienter un ensemble de tickets.
- Le backlog contient des rapports incomplets ou difficiles à classer.

## Workflow

### 1. Recueil les anomalies

- Utilise la liste fournie ou les tickets accessibles dans l’outil de suivi.
- Identifie le projet et le périmètre concernés.
- Relève les champs disponibles :identifiant, titre, description, statut, version, environnement,impact, preuves, sévérité, priorité et composant.
- Signale les informations absentes.
- N'invente pas de statut, de classification ou de composant.

### 2. Regroupe les doublons possibles

Repére les rapports susceptibles de décrire le même problème.

Explique les éléments communs:comportement, étapes, environnement, version ou message d’erreur.

Distingue les symptômes similaires d’une cause commune confirmée.

Présente les regroupements comme des doublons possibles à vérifier.
Ne fusionne ni ne ferme pas les tickets.

### 3. Propose la sévérité et la priorité

Pour chaque anomalie, distingue :

- la sévérité : gravité de l’impact ;
- la priorité : urgence de traitement.

Utilise les échelles du projet et fournir une justification courte.

Si ces échelles sont inconnues, décrire l’impact et l’urgence
sans inventer de niveau.

Conserve les classifications existantes et présenter séparément les éventuelles modifications proposées.

### 4. Propose une orientation

Suggére un composant ou une équipe à partir des informations disponibles.

Justifie la proposition et signale les orientations incertaines.

N'attribue pa une anomalie à une personne sur la seule base d’une supposition.

### 5. Signale les rapports incomplets

Liste les anomalies pour lesquelles il manque notamment :

- les étapes de reproduction ;
- le résultat attendu ou observé ;
- la version ou l’environnement ;
- les preuves nécessaires ;
- l’impact métier.

Précise les questions à poser au PO.

### 6. Fais confirmer le tri

Présente le résultat comme une proposition.

Fais confirmer les doublons, classifications et orientations par le PO avant toute modification des tickets.

N’applique les décisions dans l’outil que si l’action est autorisée.
Ne déclare les modifications réalisées qu’après confirmation du succès.

## Format de sortie

# Proposition de tri — [Projet / lot / backlog]

- Périmètre :
- Nombre d’anomalies :
- Sources :
- Informations manquantes :

## Doublons possibles

| Tickets concernés | Éléments communs | Différences à vérifier | Confirmation attendue |
|---|---|---|---|

## Classification et orientation proposées

| Ticket | Sévérité existante / proposée | Priorité existante / proposée | Équipe ou composant proposé | Justification |
|---|---|---|---|---|

## Rapports à compléter

| Ticket | Informations manquantes | Question au rapporteur |
|---|---|---|

## Décisions attendues

- Doublons à confirmer :
- Classifications à confirmer :
- Orientations à confirmer :

## Garde-fous

- Ne pas fusionner ni fermer automatiquement une anomalie.
- Ne pas inventer de sévérité, de priorité ou de responsable.
- Distinguer recommandations et décisions déjà validées.
- Ne pas modifier silencieusement les statuts ou les affectations.
- Conserver les références des tickets et les justifications.
- Le PO conserve la décision finale.
