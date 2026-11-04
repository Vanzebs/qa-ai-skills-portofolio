---
name: qa-redacteur-anomalies
description: >-
  Transformer les observations d’un testeur en rapport d’anomalie clair
  et reproductible. À utiliser lorsqu’un test échoue, qu’un dysfonctionnement
  est décrit ou qu’un problème intermittent doit être documenté.
  Produire un rapport comprenant le titre, l’environnement, les étapes,
  les résultats attendus et observés, l’impact, les preuves disponibles
  et une proposition de sévérité et de priorité.
  Rapporter uniquement les faits connus, sans inventer d’étapes ni de preuves,
  et faire confirmer le rapport avant son enregistrement.
license: MIT
metadata:
  auteur: Vanessa ZEBAZE
  phase-stlc: Gestion des anomalies
  version: 1.0.0
---

# Rédacteur de rapports d’anomalie

Rédige un rapport qu’un développeur peut comprendre et utiliser
pour tenter de reproduire le problème dès la première lecture.

Privilégie un rapport précis, étayé par les éléments disponibles,
sans présenter des suppositions comme des faits.

## Quand l’utiliser ?

- Un test échoue ou un comportement anormal nécessite un rapport.
- Une personne décrit un problème de manière informelle et souhaite
  le structurer pour l’outil de suivi.
- Un problème intermittent doit être documenté avec sa fréquence
  et ses conditions d’apparition.

## Workflow

### 1. Recueil les faits

Releve :

- les actions réalisées ;
- le résultat observé ;
- la version ou le build ;
- l’environnement ;
- le rôle utilisateur ;
- les données et préconditions utiles ;
- les journaux, captures ou traces disponibles.

Si une information manque, la demander ou la signaler comme inconnue.
Ne comble pasles informations manquantes par des suppositions.

### 2. Rédige un titre précis

Utilise le format :

[Zone concernée] — Comportement observé — Condition d’apparition

Rédige un titre spécifique et facile à retrouver dans l’outil de suivi.

### 3. Documente la reproduction

Décris les préconditions et les étapes minimales, numérotées,
à partir d’un état initial connu.

Sépare clairement :

- le résultat attendu ;
- le résultat réellement observé.

Précise la source du résultat attendu lorsqu’elle est disponible :
exigence, critère d’acceptation, règle métier ou confirmation du Product Owner.

Si le comportement attendu n’est pas clair, demande une clarification.

Si le problème ne se reproduit pas systématiquement, le préciser.
Indique le nombre d’occurrences et de tentatives lorsqu’il est connu,
par exemple : « Observé 2 fois sur 5 tentatives ».

N'affirme pas que les étapes ont été rejouées si ce n’est pas le cas.

### 4. Propose la sévérité et la priorité

Distingue :

- la sévérité : gravité de l’impact observé ;
- la priorité : urgence de traitement.

Utilise les échelles du projet et justifier chaque proposition
en une phrase.

Si les échelles sont inconnues, décrire l’impact et l’urgence
sans inventer de niveau.

Mentionne la zone ou le composant suspecté comme une hypothèse,
sans affirmer qu’il s’agit de la cause.

Laisse la classification définitive aux responsables.

### 5. Relie les preuves

Référence les éléments disponibles : captures, journaux ou traces.

Signale les observations qui ne sont pas étayées par une preuve.
Ne pas inventer de lien, de message d’erreur ou de ligne de journal.

Retire ou masque les données personnelles qui ne sont pas nécessaires au diagnostic.

### 6. Fais confirmer le rapport

Présente le rapport comme un brouillon.

Liste :

- les informations non confirmées ;
- les hypothèses ;
- la sévérité et la priorité proposées.

Fais confirmer les éléments nécessaires par le rapporteur/testeur
avant l’enregistrement dans l’outil de suivi.

## Format de sortie

# Anomalie — [Zone] — [Comportement observé] — [Condition]

## Contexte

- Projet / application :
- Version ou build :
- Environnement :
- Rôle utilisateur :
- Cas de test ou exigence associé, si connu :

## Préconditions et données de test

- État initial :
- Données nécessaires :

## Étapes de reproduction

1.
2.
3.

## Résultat attendu

[Comportement attendu]

Source : [Exigence / critère d’acceptation / règle métier / à confirmer]

## Résultat observé

[Comportement réellement constaté]

## Fréquence

- Reproduction : Systématique / Intermittente / À confirmer
- Occurrences et tentatives connues :

## Impact et classification proposée

- Impact observé :
- Sévérité proposée et justification :
- Priorité proposée et justification :
- Zone suspectée, si pertinente : [Hypothèse à confirmer]

## Preuves disponibles

- [Liens ou références aux captures, journaux et traces]

## Points à confirmer avant enregistrement

- [Informations manquantes]
- [Hypothèses]
- [Classification proposée]

## Garde-fous

- Ne jamais inventer une étape réalisée, un message d’erreur, une preuve ou un résultat.
- Distingue les faits observés des hypothèses.
- Signale les limites de reproductibilité.
- Ne présente pas une sévérité, une priorité ou une cause supposée
  comme définitivement validée.
- N'enregistre pas le rapport sans autorisation.
- Conserver les mentions d’attribution et de licence du contenu source.