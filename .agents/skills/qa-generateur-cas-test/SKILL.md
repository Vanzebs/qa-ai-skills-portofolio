---
name: qa-generateur-cas-test
description: >-
  Rédige des cas de tests détaillés et exécutables à partir d'exigences, de Users stories ou du contenu des tikcets Jira. À utiliser lorsqu'un Product Owner demande "rédige les cas de test pour TS-1", "détaille ce scénario" ou lorsqu'il fournit une liste de scénarios revue et prête à être transformée en étapes détaillées. Pour chaque cas de test, précise les préconditions,les étapes ordonnées à suivre, les données nécessaires et les résultats attendus. Assure la traçabilité avec l'exigence source et les critères d'acceptation. Si les informations sur les critères d'acceptations sont manquantes, demande au Product Owner de t'en fournir. 
license: MIT
metadata:
  Auteur: Vanessa ZEBAZE
  phase-stlc: Développement des cas de test
  version: 1.0.0
---

# Rédacteur des cas de test

Transforme des **scénarios approuvés** ou des **exigences fonctionnelles**  en cas de test qu'un testeur peut exécuter sans avoir à deviner. La précision est l'objectif principal : aucune étape ambiguë

## Quand l'utiliser?

- Les scénarios ont été conçus et revus, et nécessitent désormais un niveau de détail exécutable.
- Le Product Owner fournit un identifiant Jira ou une liste d'identifiant et demande les cas de tests complets étape par étape.
- Une campagne de tests de régression nécessite des cas de test rédigés à partir d'un ensemble de couverture validé.


## Workflow
1. *Confirme que la source est approuvée*. Travaille à partir de scénarios revus et validés, et/ou d'exigences brutes. Si un scénario est ambigu ou non approuvé, demande des clarifications avant de le développer. N'improvise pas la couverture de test.

2. *Rédige chaque cas*. Pour chaque scénario, produit :

- un identifiant unique ;
- un titre ;
- les préconditions ;
- les références aux données de test ;
- des étapes numérotées (une action par étape) ;
- un résultat attendu spécifique pour chaque étape.
- Conservez des étapes atomiques et observables.

3. *Couvrir les variantes*. Les parcours positifs, négatifs et les cas limites doivent chacun disposer de leur propre cas de test. Ne les regroupe pas dans un seul cas comportant plusieurs branches.

4. *Assurer la traçabilité*. Chaque cas doit référencer l'identifiant du scénario ainsi que le critère d'acceptation (AC) qu'il vérifie. Signale tout scénario sans cas associé et tout cas ne correspondant à aucun élément.

5. *POINT DE REVUE HUMAINE* (obligatoire). Présente les cas de test sous forme de brouillon. Liste les hypothèses concernant les données, l'environnement et les résultats attendus que tu n'as pas pu confirmer. Demandez à un relecteur ou au Product Owner d'approuver ou de modifier les cas avant qu'ils ne soient intégrés à la suite de tests ou utilisés pour l'automatisation.

## Format de sortie
```
## Cas de test — <fonctionnalité / CLE-JIRA>
TC-1  <titre>            (issu de TS-1, AC-1)   Priorité: P0
  Preconditions: ...
  Données de test: <référence vers le jeu de données>
  Etapes:
    1. <action>            -> Résultat attendu: <résultat observable>
    2. <action>            -> Résultat attendu: <Résultat observable>
  Postconditions / nettoyage: ...

--- POINT DE REVUE HUMAINE ---
Hypothèses / Résultats attendus non confirmés / "Approuver ou modifier avant la mise en production"
```

## Gardes-fou
- N'invente jamais un résultat attendu que tu ne peux pas justifier à partir d'un critère d'acceptation (AC) ou d'un scénario. - - Indique plutôt *résultat attendu à confirmer* au lieu de faire une supposition.
- Ne crée pas de valeurs de données concrètes directement dans les cas de test. Fais référence au jeu de données fourni par le Product Owner ou par ceux obtenusà l'aide du générateur de données de test.
- Conserve les étapes déterministes et observables. Evite les formulations vagues telles que "vérifier que cela fonctionne".
- Les cas de test produit restent à l'état de brouillon jusu'à leur validation par un humain. Ne valide jamais toi-même tes propres cas de test.
