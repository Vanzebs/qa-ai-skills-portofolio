---
name: qa-rapport-cloture-tests
description: >-
  Préparer un rapport de clôture d’un cycle ou d’une campagne de tests. À utiliser pour synthétiser les résultats, la couverture, les anomalies ouvertes et les risques avant une revue de livraison. Calculer les indicateurs à partir des données disponibles, afficher leurs dénominateurs et proposer un avis argumenté sur la livraison.
  Ne pas inventer de chiffres ni prendre la décision finale de go/no-go.
license: MIT
metadata:
  auteur: Vanessa ZEBAZE
  phase-stlc: Clôture des tests
  version: 1.0.0
---

# Rapport de clôture des tests

Produire une synthèse factuelle permettant aux parties prenantes d’évaluer les résultats et les risques résiduels.
Présenter un avis argumenté. La décision de livraison et la clôture officielle appartiennent aux responsables désignés.

## Quand l’utiliser ?

- Une campagne, un sprint ou une phase de test se termine.
- Une partie prenante demande les résultats, anomalies, couvertures et risques dans un même document.
- Une réunion de go/no-go nécessite une synthèse étayée.

## Workflow

### 1. Recueille les informations

Identifie :

- le projet et la campagne ;
- la version et l’environnement ;
- la période ;
- le périmètre prévu et ses modifications ;
- les résultats d’exécution ;
- les anomalies ;
- l’analyse de couverture ;
- les critères de sortie définis par l’équipe.

Signale les sources absentes, partielles ou contradictoires.
Ne mélange pas les résultats de versions ou d’environnements différents.

### 2. Calcul les indicateurs

Précise les définitions utilisées et afficher les effectifs.

Utilise, sauf convention différente explicitement fournie :

- Tests terminés = Réussis + Échoués.
- Taux de tests terminés =
  (Réussis + Échoués) / Tests dans le périmètre × 100.
- Taux de réussite =Réussis / (Réussis + Échoués) × 100.

Présente séparément les tests bloqués, en cours, non exécutés et les résultats à confirmer.

Compte chaque cas une seule fois dans le bilan courant. Précise le traitement des retests et conserver leur historique.

Présente les anomalies ouvertes par sévérité selon l’échelle du projet.

Calcule une densité d’anomalies uniquement si le nombre d’anomalies, l’unité de référence et le périmètre sont connus et pertinents.
Sinon, indiquer « Non calculable » ou omettre cet indicateur.

Pour la couverture, reprendre les mesures documentées et leur définition.
N'assimile pas couverture et réussite.

Ne calcule pas un taux lorsque le dénominateur est nul ou inconnu.

### 3. Synthétise les résultats et les risques

Présente :

- les points positifs ;
- les difficultés rencontrées ;
- les anomalies critiques ou majeures encore ouvertes ;
- les zones à risque non testées ;
- les blocages ;
- les limites de couverture ;
- les éventuels contournements confirmés.

Relie les constats aux sources disponibles.

### 4. Évalue les critères de sortie

Pour chaque critère défini par l’équipe, indique :

- satisfait ;
- non satisfait ;
- non vérifiable.

Justifie l’état avec les données disponibles.

N'invente pas de seuil d’acceptation si aucun critère n’a été fourni.

### 5. Propose un avis sans décider

Propose un avis parmi :

- Favorable : les éléments disponibles soutiennent les critères convenus.
- Défavorable : des écarts ou risques empêchent de soutenir ces critères.
- Favorable sous conditions : préciser les conditions et leur validation attendue.
- Avis réservé : les informations sont insuffisantes pour conclure.

Justifie l’avis et rappele qu’il est consultatif.

### 6. Fais revoir le rapport

Présente le rapport comme un brouillon.

Mets en évidence les hypothèses, informations manquantes et critères restant ouverts.

Fais revoir le rapport par le PO et le Test Manager.

Ne déclare pas la campagne officiellement clôturée sans décision explicite.

## Format de sortie

# Rapport de clôture — [Campagne / livraison]

## Contexte

- Projet :
- Version :
- Environnement :
- Période :
- Périmètre :
- Sources et date de consolidation :

## Indicateurs

Build

Métriques :

Exécutés : X/Y (Z %)
Taux de réussite : P %
Défauts ouverts : C critiques / H majeurs / M moyens
Densité de défauts : d/fonctionnalité
Couverture des exigences : R %
Points clés :

...
Risques / éléments ouverts :

< défauts critiques ouverts, zones à haut risque non testées, critères de sortie non atteints>
Recommandation (AVIS CONSULTATIF) :

GO / NO-GO / GO CONDITIONNEL — parce que ...

## Anomalies ouvertes

| Référence | Sévérité | Impact | Contournement confirmé | Situation |
|---|---|---|---|---|

## Bilan

- Points positifs :
- Difficultés :
- Risques résiduels :
- Zones non testées ou insuffisamment couvertes :

## Critères de sortie

| Critère | État | Justification |
|---|---|---|

## VALIDATION HUMAINE OBLIGATOIRE

Hypothèses :

...
Données manquantes :

...
Éléments non confirmés :

...
Le PO; Tech lead demeure demeurent les seuls décisionnaires pour la validation finale et l'autorisation de mise en production.s :

## Garde-fous

- Ne jamais inventer de chiffre, de résultat ou de couverture.
- Afficher les dénominateurs et les limites des indicateurs.
- Ne pas masquer une anomalie ouverte derrière un taux de réussite élevé.
- Ne pas présenter un avis consultatif comme une autorisation de livraison.
- Ne pas déclarer la campagne clôturée sans validation explicite.
