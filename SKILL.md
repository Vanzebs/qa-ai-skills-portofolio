---
name: qa-generateur-donnees-test
description: >-
  Produit les jeux de données dont un scénario ou un cas de test a besoin pour être exécuté.
  À utiliser lorsqu’un testeur demande de « générer des données de test », de « fournir
  des valeurs limites pour ce champ » ou lorsqu’il a besoin d’enregistrements valides,
  invalides, aux limites et synthétiques pour exécuter ses cas de test. Retourne des
  jeux de données étiquetés — valides, invalides, limites et synthétiques de type faker —
  chacun associé au champ ou au scénario qu’il couvre, avec une indication précisant
  dans quel environnement ils peuvent être utilisés en toute sécurité.
license: MIT
metadata:
  auteur: Vanessa ZEBAZE
  phase-stlc: Developpement des cas de test
  version: 1.0.0
---

# Générateur de données de test

Fournit les entrées qui rendent les cas de test exécutables — des données ayant l’apparence de données réelles mais qui ne contiennent jamais de données client réelles. La couverture des cas limites et des valeurs invalides est aussi importante que celle du scénario nominal.

## Quand l'utiliser?
- Un cas de test fait référence à un jeu de données qui n’existe pas encore.
- Une personne demande des valeurs limites ou des valeurs invalides pour un champ ou un formulaire spécifique.
- Une suite de tests nécessite un grand volume d’enregistrements synthétiques afin de couvrir différents volumes, rôles ou états.
- Le Product Owner demande de crréer un jeu de données nécessaire à l'exécution des cas de test

## Workflow
1. Lire les règles du champ.
Récupère la définition du champ ou de l’entité à partir du scénario, des critères d’acceptation (AC) ou du schéma de données. Si les contraintes (type, longueur, format, valeurs autorisées) inconnues,demande des précisions ;ne suppose jamais une règle de validation qui pourrait ne pas exister.

2. Générer par catégorie.
Pour chaque champ,produit quatre catégories identifiées : valide (représentatif), invalide (violations de type, de format ou de contrainte), limite (vide, minimum, maximum, dépassement de ±1, Unicode, espaces), et synthétique (enregistrements réalistes de type faker).

3. Associer le résultat attendu.
Indique ce que chaque valeur doit produire : acceptation, rejet avec le message d’erreur attendu ou troncature, afin que les cas de test puissent vérifier le comportement attendu.

4. Signaler les précautions d’utilisation.
Identifie les données qui doivent être utilisées uniquement dans des environnements hors production (non-prod) et n’utilise jamais de données personnelles réelles (PII) ;génère à la place des noms, adresses e-mail et identifiants fictifs.

5. PORTE DE REVUE HUMAINE (obligatoire).
Présente le jeu de données comme une proposition préliminaire. Met en évidence toutes les contraintes supposées. Demande au testeur de confirmer les règles avant que ces données ne soient intégrées aux cas de test.

## Fichier de sortie
```
## Données de test — <champ / entité>  (constraintes: <type,longueur,format>)
Valides:     [ ... ]                       -> résultat attendu: accepté
Invalides:   [ ... , pourquoi invalide ]   -> résultat attendu: rejecté (<erreur>)
Limites:  [ vide, min, max, +1 ]           -> résultat attendu: <par valeur>
Synthétique: <recette faker /exemples d'enregistrements>   env: NON-PROD ONLY
--- REVUE HUMAINE ---
Conraintes supposées / "Confirmer les règles avant que ces données ne soient utilisées dans des cas de test"
```

## Garde-fous
- N’utilise jamais ni ne copie de données réelles de production ou de clients ; tous les enregistrements sont fictifs.
- N’invente jamais une règle de validation pour justifier une valeur ; lorsqu’une contrainte est inconnue, elle devient une question à clarifier.
- Etiquette tous les jeux de données réservés aux environnements hors production ; ne laisse jamais entendre qu’ils sont sûrs pour un environnement de production.
Les données constituent un brouill:aon tant que les règles du champ n’ont pas été confirmées par un humain.
