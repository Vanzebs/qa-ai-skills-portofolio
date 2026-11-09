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
1. **Vérifie le périmètre et la préparation des exigences.**

### Recense tous les tickets demandés
- Lire tous les tickets du périmètre demandé, y compris le exigences brutes, non analysées ou non validées.
- Ne limite pas silencieusement la rédaction aux seuls tickets déjà analysés ou considérés comme prêts.
- Si le périmètre est imprécis, demander quels tickets traiter.

## Établir un bilan avant la rédaction

- Consulte les analyses des exigences disponibles. En l’absence d’analyse, examine les informations du ticket et produit une évaluation préliminaire de sa testabilité. Ne présente pas cette évaluation comme une validation du PO.

- Distingue deux informations indépendantes :

  **Préparation pour la rédaction :**
  - Prêt : informations suffisamment précises pour rédiger des cas et des résultats attendus vérifiables.
  - Partiellement prêt : certaines parties sont exploitables,mais des ambiguïtés ou informations manquantes subsistent.
  - Non prêt : des informations essentielles empêchent de définir des cas vérifiables.
  - Non évaluable : contenu absent, inaccessible ou illisible.

  **Validation du Product Owner :**
  - Validée : confirmation explicite disponible.
  - Non validée : absence de validation explicitement indiquée.
  - Non renseignée : aucune preuve de validation disponible.

- Ne pas confondre le statut Jira avec la préparation du ticket ou sa validation par le Product Owner.

### Présente le bilan complet

Indique le nombre total de tickets, puis les nombres et les références des tickets prêts, partiellement prêts, non prêts et non évaluables. Les totaux doivent correspondre au périmètre.

Présente également la validation PO dans le tableau suivant :

| Clé Jira | Résumé | Préparation | Validation PO | Source de l’évaluation | Informations manquantes / ambiguïtés | Conséquence sur la rédaction |
|---|---|---|---|---|---|---|
| <clé> | <résumé> | <état> | <état> | <analyse existante ou évaluation préliminaire> | <éléments précis> | <impact concret> |

### Demande comment poursuivre

Si des tickets ne sont pas prêts ou si leur validation PO n’est pas confirmée, présente les conséquences applicables :

- couverture potentiellement incomplète ;
- résultats attendus restant à confirmer ;
- risque de mauvaise interprétation des règles métier ;
- cas à reprendre après clarification ou validation du PO ;
- impossibilité de finaliser certaines étapes ou certains cas.

Relie ces conséquences aux tickets concernés, sans présenter des risques génériques comme des problèmes déjà constatés.

Demande ensuite explicitement au PO ou PPO :« Sur les <total> tickets demandés, <nombre> sont prêts,
<nombre> partiellement prêts, <nombre> non prêts et <nombre>
non évaluables. La validation PO n’est pas confirmée pour <nombre> tickets : <références>.

Souhaitez-vous :
A. Rédiger uniquement les cas des tickets prêts dont la validation PO est confirmée ;
B. Rédiger également des brouillons pour tous les autres tickets exploitables, malgré les limites indiquées ;
C. Clarifier d’abord les tickets concernés ? »

Attendre la réponse avant de rédiger les cas concernés.Si le PO a déjà explicitement autorisé la rédaction sur des exigences brutes ou non validées, appliquer ce choix sans demander une nouvelle confirmation.

## En cas d’autorisation de poursuite

- Rédige les cas à partir des informations réellement disponibles.
- Marque les cas concernés :« Brouillon — exigence incomplète et/ou validation PO à confirmer ».
- Identifie précisément les hypothèses et questions ouvertes.
- N'invente pas une règle métier, une limite, une donnée ou un résultat attendu pour compléter le cas.
- Inscrit « À confirmer » pour les éléments indéterminables.
- Distingue les cas suffisamment détaillés pour être exécutés des propositions restant à compléter.
- Pour un ticket inexploitable, fournit les questions nécessaires et explique pourquoi aucun cas détaillé ne peut être rédigé.
- Conserve tous les tickets dans le bilan final, y compris ceux pour lesquels aucun cas n’a pu être produit.

L’autorisation de rédiger un brouillon ne constitue ni une validation des exigences par le PO, ni une approbation des tests.

2. *Rédige chaque cas*. Pour chaque scénario, produit :

- un identifiant unique ;
- un titre ;
- les préconditions ;
- les références aux données de test ;
- des étapes numérotées (une action par étape) ;
- un résultat attendu spécifique pour chaque étape.
- Conservez des étapes atomiques et observables.

3. **Couvrir et identifier les variantes.**

- Créer un cas distinct pour chaque comportement à vérifier. Ne regroupe pas plusieurs branches dans un même cas.

- Identifie chaque cas selon deux axes :

  **Nature :**
  - Positif : vérifier un comportement autorisé avec des données et des conditions valides.
  - Négatif : vérifier le traitement d’une donnée invalide d’une action interdite ou d’une condition d’erreur.
    Le rejet attendu constitue un résultat conforme.

  **Variante :**
  - Nominal : parcours standard avec des conditions usuelles.
  - Alternatif : autre parcours valide prévu par les exigences.
  - Limite : valeur ou condition située à une frontière définie.
  - Autre : précise la variante, par exemple champ obligatoire absent, droits insuffisants ou transition de statut interdite.

  - Pour un cas nominal ou alternatif, utilise la nature Positif.
  - Pour un cas limite, préciser Positif ou Négatif selon que la valeur est autorisée ou doit être rejetée.
  - Justifie brièvement la classification de chaque cas.
  - Ajouter si utile des étiquettes complémentaires :droits, intégration, changement de statut, reprise, etc.

  - Génère uniquement les variantes pertinentes au regard des exigences et des risques identifiés.
  - N'invente pas de seuil, de règle ou de résultat attendu pour remplir toutes les catégories.

  - Signale les variantes impossibles à préciser faute d’informations et les questions à faire confirmer.

4. *POINT DE REVUE HUMAINE* (obligatoire). Présente les cas de test sous forme de brouillon. Liste les hypothèses concernant les données, l'environnement et les résultats attendus que tu n'as pas pu confirmer. Demande à un relecteur ou au Product Owner d'approuver ou de modifier les cas avant qu'ils ne soient intégrés à la suite de tests.

## Format de sortie

Présente les cas de test en tableaux Markdown.Le résultat reste un brouillon à faire valider par le Product Owner avant d'être utilisé pour l'exécution des tests.

# Tableau de synthèse

Produis une ligne par cas de test.

| ID du cas | Clé Jira / scénario / AC | Titre | Nature | Variante | Justification de la classification | Priorité |
|---|---|---|---|---|---|---|
| <ID local> | <références disponibles> | <titre précis> | <Positif ou Négatif> | <Nominal, Alternatif, Limite ou Autre à préciser> | <raison courte> | <priorité justifiée ou À confirmer> |

- Utilise des identifiants locaux pour les nouveaux cas.
  Ne les présente pas comme des identifiants Xray existants.
- N'invente pas de référence de scénario ou d’AC.
  Indique « Non fourni » si nécessaire.
- Regroupe les cas par nature puis par variante,sans dupliquer un cas appartenant à plusieurs catégories.

# Détail de chaque cas de test

Répète les deux tableaux suivants pour chaque cas.

| Élément | Contenu |
|---|---|
| ID et titre | <ID local — titre> |
| Traçabilité | <clé Jira, scénario et AC disponibles> |
| Objectif | <comportement vérifié> |
| Nature | <Positif ou Négatif> |
| Variante | <Nominal, Alternatif, Limite ou Autre à préciser> |
| Étiquettes complémentaires | <si pertinent> |
| Priorité | <priorité et justification, ou À confirmer> |
| Préconditions | <état initial, rôle, environnement et dépendances utiles> |
| Données de test | <référence du jeu de données et caractéristiques requises> |
| Postconditions / nettoyage | <état final et remise en état nécessaire> |

| Étape | Action du testeur | Données ou référence utilisée | Résultat attendu observable |
|---|---|---|---|
| 1 | <une action> | <référence ou Sans objet> | <résultat spécifique à cette étape> |
| 2 | <une action> | <référence ou Sans objet> | <résultat spécifique à cette étape> |

Conserve une action par étape et un résultat attendu correspondant. Ne remplace pas les étapes détaillées par le seul tableau de synthèse.

## Bilan des variantes

Indique le nombre de cas par nature et par variante. Signale les catégories pertinentes non couvertes,avec leur justification ou l’information manquante.Ne compte pas plusieurs fois un même cas.

--- POINT DE REVUE HUMAINE ---
Hypothèses / Résultats attendus non confirmés / Approuver ou modifier avant le debut des tests /Question à confirmer
```

## Gardes-fou

- N'invente jamais un résultat attendu que tu ne peux pas justifier à partir d'un critère d'acceptation (AC) ou d'un scénario. - - Indique plutôt *résultat attendu à confirmer* au lieu de faire une supposition.
- Ne crée pas de valeurs de données concrètes directement dans les cas de test. Fais référence au jeu de données fourni par le Product Owner ou par ceux obtenus à l'aide du générateur de données de test.
- Conserve les étapes déterministes et observables. Evite les formulations vagues telles que "vérifier que cela fonctionne".
- Les cas de test produit restent à l'état de brouillon jusqu'à leur validation par le PO. Ne valide jamais toi-même tes propres cas de test.
