---
name: qa-redacteur-anomalies
description: >-
 Transforme un dysfonctionnement en un rapport de bug clair et reproductible. À utiliser lorsqu'un testeur dit  « rédige un rapport de bug » ou décrit un problème et souhaite qu'il soit correctement documenté. Produit un rapport structuré comprenant :e titre ;l'environnement ;les étapes de reproduction;le résultat attendu par rapport au résultat observé;la sévérité et la priorité ;les preuves (captures d'écran, logs, vidéos, etc.) ;la zone ou le composant suspecté.Le rapport est ensuite prêt à être copié dans l'outil de suivi des anomalies après validation par un humain.Le rapport doit se baser uniquement sur les faits observés : n'invente jamais une étape de reproduction, une information technique ou une ligne de journal (log) qui n'a pas été fournie ou observée.
license: MIT
metadata:
  auteur : Vanessa ZEBAZE
  phase-stlc: Gestion des anomalies
  version: 1.0.0
---

# Rédacteur de rapports d’anomalie

Rédige un rapport qu'un développeur peut reproduire dès la première lecture. Un bon rapport de bug est précis, appuyé par des preuves et ne présente jamais des suppositions comme des faits.

## Quand l’utiliser ?

- Un test manuel révèle un comportement inattendu.
- Le testeur décrit un problème avec quelques notes ou captures.
- Une anomalie existante nécessite des informations complémentaires.
- Un problème intermittent doit être documenté.
- Le testeur souhaite préparer un rapport à enregistrer dans Jira.

## Mode d’accès aux informations

Dans le contexte actuel, travailler à partir des éléments fournis
par le testeur :

- description libre ;
- contenu copié depuis Jira/Xray ;
- export ;
- captures ou pièces jointes.

Une clé ou un lien Jira/Xray ne donne pas automatiquement accès à son contenu.

Si un connecteur, un serveur MCP ou une API autorisée devient disponible,utiliser uniquement les opérations réellement accessibles.

Ne jamais prétendre avoir consulté Jira/Xray sans accès effectif.

## Workflow

### 1. Accepte les observations brutes

Commence par les informations que le testeur possède déjà :quelques phrases, une capture, le contenu du test ou de son exécution.

N'impose pas un formulaire complet avant de commencer.

Identifie ce que le testeur a fait, ce qu’il attendait et ce qu’il a observé.

### 2. Extrais les informations disponibles

Recherche dans les éléments fournis :

- le projet et l’application ;
- la référence du test Xray et de son exécution ;
- les préconditions et les étapes du test ;
- le résultat attendu ;
- les actions réellement réalisées ;
- le résultat observé ;
- la version et l’environnement ;
- le rôle utilisateur et les données pertinentes ;
- les messages d’erreur et preuves ;
- les anomalies déjà associées;
- les journaux (logs), captures d'écran, vidéos ou traces disponibles.

Ne demande pas de ressaisir une information déjà lisible dans les sources.

Distingue les étapes prévues dans Xray des étapes que le testeur confirme avoir réellement exécutées.

Si une information manque, pose la question. Ne complète jamais les étapes de reproduction à partir de suppositions ou de ton imagination.

### 3. Prends en compte les anomalies existantes

 Si une anomalie associée au test ou à l’exécution est fournie,examine si elle décrit le problème observé.

Compare :

- le comportement ;
- les conditions d’apparition 
- la version et l’environnement ;
- les étapes et résultats ;
- le statut du ticket, lorsqu’il est connu.

Propose selon les informations disponibles :

- un nouveau rapport ;
- un complément à une anomalie existante ;
- un commentaire de retest ;
- un doublon possible à confirmer.

Ne conclus pas qu’il s’agit du même problème sur le seul titre ou sur la présence d’une anomalie liée au test.

Sans accès aux anomalies existantes, précise :
« Vérification des anomalies existantes non effectuée ».

N'affirme pas que le problème est nouveau ou unique.

### 4. Produis un premier brouillon

Rédige avec les informations connues :

- un titre précis : le titre doit être spécificaue, facilement recherchable et compréhensible sans ouvrir le ticket ;
- le contexte ;
- les préconditions utiles ;
- les étapes réalisées ;
- le résultat attendu ;
- le résultat observé ;
- les preuves disponibles.

Utilise le format de titre :

[Application ou fonction] — Comportement observé — Condition distinctive

Indique « À préciser » pour les informations inconnues.
Ne pas les remplacer par des suppositions.

### 5. Pose uniquement les questions utiles

Après extraction des informations, identifie ce qui manque pour comprendre le problème ou tenter de le reproduire.

Regroupe les questions prioritaires dans une liste courte.

Demande notamment, seulement si nécessaire :

- quelle étape a réellement échoué ;
- quel résultat était attendu et sur quelle base ;
- quelle version ou quel environnement était utilisé ;
- quelles conditions ou données déclenchent le problème ;
- si le problème s’est reproduit.

Ne pas retarder inutilement le brouillon pour un champ secondaire.

### 6. Précise la reproductibilité et l’impact

Indique les occurrences et tentatives connues.

Ne transforme pas « observé deux fois » en « deux fois sur deux » sans confirmation.

Décris l’impact connu : action impossible, parcours bloqué, résultat incorrect ou autre conséquence observée.

Mentionne un contournement uniquement s’il a été fourni, en précisant s’il a été vérifié.

Ne déduis pas automatiquement la cause du problème.

### 7. Propose la sévérité et la priorité

Distingue :

- la sévérité : gravité de l’impact ;
- la priorité : urgence de traitement.

Utilise les échelles du projet lorsqu’elles sont connues.
Sinon, décrire l’impact et l’urgence sans inventer de niveau.

Justifie les propositions et signale les éléments à confirmer.

Présente toute zone technique suspectée comme une hypothèse.

### 8. Finalise le texte destiné à Jira

Intégre les réponses du testeur et produis un rapport prêt à copier.

Pour une anomalie existante, prépare uniquement le complément utile,sans remplacer son historique.

Liste les références Xray et les preuves à ajouter.

Une pièce jointe fournie dans le chat n’est pas automatiquement enregistrée dans Jira.

Fais relire les faits et les propositions de classification avant l’enregistrement.

### 9. Distingue rédaction et enregistrement

Sans connexion autorisée :

- le testeur copie le rapport dans Jira ;
- il ajoute les preuves ;
- il associe l’anomalie au test ou à l’exécution dans Xray selon la procédure du projet.

Avec un outil adapté, ne crée, modifie ou associe un ticket que si l’action est demandée ou autorisée.

Ne déclare une création, une modification ou une association comme réalisée qu’après confirmation de son succès.

## Format de sortie

# Rapport d’anomalie

## Action proposée

- Nouveau rapport / Complément / Commentaire de retest /
  Doublon possible à confirmer
- Anomalie existante concernée, si connue :
- Justification :

## Titre

[Application ou fonction] — Comportement observé — Condition distinctive

## Contexte

- Projet et application :
- Version :
- Environnement :
- Test Xray :
- Exécution Xray :
- Rôle utilisateur, si pertinent :

## Préconditions et données utiles

[Informations nécessaires à la compréhension ou à la reproduction]

## Étapes réalisées

1.
2.
3.

## Résultat attendu

[Comportement attendu]

Source : [Test Xray / exigence / critère d’acceptation /
confirmation du testeur / à préciser]

## Résultat observé

[Comportement réellement constaté]

## Reproductibilité

- Observations et tentatives connues :
- Conditions particulières :
- Informations restant à confirmer :

## Impact et classification proposée

- Impact connu :
- Contournement et état de vérification :
- Sévérité proposée et justification :
- Priorité proposée et justification :

## Preuves

- Éléments fournis :
- [Liens ou références aux captures, journaux et traces]:
- Preuves manquantes utiles :

## Points à confirmer

[Questions restantes et hypothèses éventuelles]

Pour un complément ou un retest, utiliser uniquement les rubriques pertinentes et référencer le ticket existant.

## Garde-fous

- Ne pas inventer une action, un résultat, un message ou une preuve.
- Ne pas confondre contenu prévu du test et exécution réellement réalisée.
- Ne pas demander de ressaisir les informations déjà disponibles.
- Ne pas considérer une anomalie liée comme un doublon confirmé.
- Ne pas annoncer un accès à Jira/Xray qui n’existe pas.
- Ne pas présenter une cause supposée comme démontrée.
- Ne pas modifier le statut ou l’historique d’une anomalie sans autorisation.
- Le rapport reste à relire avant son enregistrement.
