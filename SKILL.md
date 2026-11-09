---
name: qa-analyseur-exigences-jira
description: >-
  Lire un ticket JIRA et déterminer s’il est réellement prêt à être testé. À utiliser lorsque le Product Owner dit « analyse ce ticket », « cette user story est-elle prête à être testée ? », « identifie des lacunes dans JIRA-X », ou lorsqu'il fournit une liste de tickets jira, user story / des critères d’acceptation et souhaite qu’ils soient examinés de manière critique. Récupère le ticket, évalue à l’aide d’une liste de vérification et renvoie un rapport des lacunes / ambiguïtés / risques ainsi que des questions de clarification au Product Owner.
license: MIT
metadata:
  auteur: Vanessa ZEBAZE
  phase-stlc: Analyse des exigences
  version: 1.0.0
---

# Analyseur des exigences JIRA

## Quand l'utiliser?

- Le Product Owner te fournit une clé JIRA ou le texte d’une user story et demande : « est-ce prêt à être testé ? »
- Une session de refinement nécessite que les ambiguïtés soient identifiées avant l’estimation.
- Les critères d’acceptation semblent insuffisants et vous souhaitez que les lacunes soient identifiées avant le début de la conception des tests.

## Workflow

1. **Récupère les tickets à analyser.**

- Utilise en priorité l’export local :[Tickets Jira](references/tickets-jira.csv.csv). Le chemin est relatif au dossier contenant ce fichier SKILL.md.

- Lis le CSV avec l’encodage UTF-8, le séparateur point-virgule (`;`) et la première ligne comme en-têtes.
  Respecte les champs entre guillemets contenant des retours à la ligne : une ligne de texte ne correspond pas forcément
  à un ticket distinct.

- Si l’utilisateur fournit des clés Jira, sélectionne uniquement les tickets correspondants dans la colonne « Clé de ticket ».Si le périmètre n’est pas précisé, demande quels tickets analyser.

- Avant l’analyse, indique le fichier réellement lu, les clés des tickets sélectionnés et les champs disponibles.

- Utilise uniquement les informations présentes dans l’export. Conserve la clé Jira dans chaque résultat. Cet export est un instantané ; ne le présente pas comme l’état actuel de Jira.

- Une référence à une pièce jointe ne donne pas accès à son contenu. Signale les pièces jointes et informations manquantes.

- Si le fichier est inaccessible ou illisible, signale-le et
  demande au Product Owner de le joindre ou d’en fournir le contenu. N’invente jamais le contenu d’un ticket.

- Si l’utilisateur demande une récupération directe dans Jira, utilise un connecteur MCP ou une API uniquement si cet accès est effectivement disponible.


Avant de commencer, vérifie les tickets et les champs réellement lisibles. Signale les informations absentes ou inaccessibles sans les inventer.

Une fois le ticket récupéré, extrais les informations suivantes pour l’analyse :

      - le résumé,
      - la description,
      - les critères d'acceptation,
      - les composants,
      - les tickets liés,
      - les pièces jointes,
      - la version de correction.

2. **Évalue l’état de préparation.**

   Parcoure chaque exigence et indique :

   ✅ claire / ⚠️ ambiguë / ❌ manquante.

   Vérifie :
   - les critères d’acceptation testables,
   - les états d’erreur / vide / limite définis,
   - les rôles et permissions,
   - les besoins non fonctionnels (perf, sécurité),
   - les données et dépendances.

3. **Classe les constats** en trois catégories :

   - Lacunes (informations manquantes),
   - Ambiguïtés (deux interprétations valides),
   - Risques (ce qui pourrait être livré de manière défaillante).

   Évalue chacun en fonction de son impact.

4. **Rédige des questions de clarification** destinées au PO :

   - spécifiques,
   - une seule thématique par question.

   **POINT DE REVUE HUMAINE (obligatoire).**

   Présente le rapport sous forme de brouillon.

   Indique ce que tu as supposé et ce que tu n'as pas pu confirmer.

   Demande au Product Owner de confirmer ou modifier le contenu et s'il a un doute sur la réponse demande lui de clarifier directement avec le métier ; ne passe pas à la conception des scénarios tant que cela n’a pas été validé.

## Format de sortie

```text
## Analyse des exigences — <JIRA-KEY>

Verdict de préparation :
PRÊT / NON PRÊT (n blocages)

Lacunes
[ ❌ ... ]

Ambiguïtés
[ ⚠️ ... deux interprétations pour chacune ]

Risques
[ évalués selon leur impact ]

Questions pour le Product Owner
(numérotées, une seule thématique par question)

--- POINT DE REVUE HUMAINE ---

Hypothèses / Éléments que je n’ai pas pu confirmer /
« Confirmer ou envoyer ces questions au métier »

Créer une page HTML légère dans le répertoire /tmp,
nommée analyse-jira <JIRA-KEY>.html contenant tous les constats comme résultat.
```

## Sécurité et garde-fous

- Ne jamais inventer un critère d’acceptation, un champ ou une exigence. Un élément manquant constitue un constat, pas un vide à compléter.
- Ne réécris pas le ticket à la place du Product Owner ; mets en évidence la lacune et pose la question.
- Un verdict « PRÊT » est indicatif ; la décision appartient au PO.
- Chaque constat doit être traçable à une ligne spécifique du ticket ou à l’absence d’une information dans celui-ci.

## RÈGLES STRICTES ANTI-HALLUCINATION (OBLIGATOIRES)

- N’invente pas de fonctionnalités, API, codes d’erreur, éléments d’interface utilisateur ou comportements.

- Ne suppose pas un comportement par défaut ou « typique » du système.

- Si une information est manquante ou peu claire, réponds :

« Informations insuffisantes pour déterminer. »

- Chaque affirmation doit être traçable aux informations fournies en entrée.

- Si un détail est déduit, indique-le explicitement comme :

« faible niveau de confiance ».

Le résultat doit être déterministe et reproductible.