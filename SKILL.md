---
name: qa-analyse-couverture-tests
description: >-
  Identifier les écarts entre les exigences, les critères d’acceptation et les tests disponibles ou exécutés. À utiliser pour rechercher les zones non testées, les couvertures partielles et les tests sans correspondance identifiée. Construire une matrice de traçabilité, distinguer conception, exécution et réussite, puis prioriser les lacunes selon les risques sans supposer une couverture non démontrée.
license: MIT
metadata:
  auteur: Vanessa ZEBAZE
  phase-stlc: Analyse de couverture et clôture des tests
  version: 1.0.0
---

# Analyse de la couverture des tests

Montre ce qui est couvert par des tests identifiés et ce qui reste sans couverture démontrée.

Distingue :

- la couverture prévue par les tests conçus ;
- la couverture effectivement exercée ;
- la conformité indiquée par les résultats.

## Quand l’utiliser ?

- Avant la clôture d’une campagne pour vérifier les exigences testées.
- Pour rechercher les critères d’acceptation ou fonctions peu couverts.
- Pour préparer une matrice de traçabilité destinée à une revue
  ou à une décision de livraison.

## Workflow

### 1. Recueille les deux ensembles

Collecte :

- les exigences et critères d’acceptation du périmètre ;
- les cas de test conçus ;
- leurs résultats d’exécution disponibles ;
- la version et l’environnement concernés.

Signale les listes incomplètes.

Pour les tests manuels, utilise les exigences, règles métier,fonctions et parcours comme éléments de couverture.

Inclure des zones de code uniquement si une cartographie ou une mesure adaptée est réellement disponible.

### 2. Construis la traçabilité

- Relie chaque exigence ou critère aux tests qui le vérifient.

- Relie chaque test à son objectif ou à son élément source.

- Justifie les correspondances à partir du contenu des tests, pas uniquement de leur titre.

- Marque les liens incertains « À confirmer ».

### 3. Identifie les lacunes

Recherche :

- les exigences ou critères sans test identifié ;
- les tests conçus mais non exécutés ;
- les exécutions bloquées ou sans résultat confirmé ;
- les couvertures partielles ;
- les tests sans correspondance identifiée.

Examine les variantes pertinentes : cas nominal, erreurs, limites, rôles, états et dépendances.

Ne déclare pas une couverture insuffisante uniquement parce qu’une catégorie de test n’est pas applicable ou n’a pas été retenue sans raison : préciser le risque ou la variante qui reste à vérifier.

Pour un test sans exigence associée, vérifie s’il couvre un risque, une régression ou une exigence non fonctionnelle avant de le considérer comme inutile.

### 4. Sépare couverture et résultat

- Un test conçu ne démontre pas qu’il a été exécuté.

- Un test exécuté ne démontre pas que toutes les variantes de l’exigence ont été vérifiées.

- Un test échoué indique un écart observé ; il peut néanmoins avoir exercé l’élément concerné.

- Si l’échec empêche d’atteindre les étapes suivantes, ne pas considérer
ces étapes comme exécutées.

- Un test réussi ne prouve pas, à lui seul, la couverture complète
d’une exigence.

### 5. Priorise les lacunes selon les risques

Classe les lacunes en tenant compte :

- de la criticité métier connue ;
- des utilisateurs ou parcours concernés ;
- des changements récents ;
- des dépendances ;
- de l’historique d’anomalies disponible.

Justifie les priorités.
N'invente pas de criticité ou de score.

### 6. Présente l’analyse pour revue

- Présente la matrice et les lacunes comme une analyse à vérifier.

- Liste les sources absentes, liens incertains et hypothèses.

- Fais confirmer les correspondances importantes par le Product Owner ou les interlocuteurs métier avant utilisation pour une décision de livraison.

## Format de sortie

# Analyse de couverture — [Fonctionnalité / campagne / livraison]

## Périmètre et sources

- Projet :
- Version et environnement :
- Exigences et critères examinés :
- Référentiel de tests :
- Résultats d’exécution :
- Limites des sources :

## Matrice de traçabilité

| Exigence / critère | Tests associés | Couverture prévue | Exécution constatée | Résultats | Lacune ou point à confirmer |
|---|---|---|---|---|---|

Pour la couverture prévue, utilise :
Complète selon le périmètre défini / Partielle / Aucun test identifié /À confirmer.

Pour l’exécution, précise les tests ou étapes réellement exécutés et ceux restant à exécuter.

## Tests sans correspondance identifiée

| Test | Objectif connu | Source ou risque à rechercher | Action proposée |
|---|---|---|---|

## Lacunes prioritaires

| Exigence ou zone | Lacune | Risque associé | Priorité justifiée | Action proposée |
|---|---|---|---|---|

## Indicateurs, si calculables

Précise ce qui est compté: exigences, critères d’acceptation ou autres éléments définis.

Affiche le numérateur, le dénominateur et la règle de calcul.

Présente séparément la couverture de conception,la couverture d’exécution et les résultats.

Ne compte pas un élément partiellement couvert comme entièrement couvert sans convention explicite.

## Points à confirmer

- Correspondances incertaines :
- Sources manquantes :
- Hypothèses :
- Validation attendue :

## Garde-fous

- Ne pas supposer une couverture sans test identifiable.
- Ne pas inventer d’identifiant de test ou d’exigence.
- Distinguer absence de lien documenté et absence certaine de test.
- Distinguer couverture, exécution et conformité.
- Ne pas déduire la couverture du code des seuls tests manuels.
- Ne pas présenter la matrice comme une preuve d’absence de défauts.
- La décision de livraison appartient au PO.
