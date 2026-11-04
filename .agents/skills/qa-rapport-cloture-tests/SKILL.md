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

1. **Recueil les données d'entrée.** Récupére les résultats d'exécution des tests, les données relatives aux défauts et l'analyse de couverture. Si une source est manquante ou incomplète, indique-le explicitement ; ne crée jamais de métriques pour compléter le rapport.

2. **Calcule les métriques.** 
Calcule :
   - le taux de réussite sur les tests exécutés ;
   - le pourcentage d'avancement de l'exécution des tests ;
   - la densité de défauts ;
   - le nombre de défauts ouverts par niveau de sévérité (en mettant en évidence les défauts critiques ouverts) ;
   - la couverture des exigences.

   Affichez les valeurs utilisées dans les calculs (numérateurs et dénominateurs) afin que les résultats puissent être vérifiés et audités.

3. **Synthétise les résultats.** 
Présente :
   - les points forts (ce qui s'est bien passé) ;
   - les points faibles ;
   - les risques non résolus.

   MetS particulièrement en évidence tout défaut critique ou majeur encore ouvert ainsi que toute zone à haut risque qui n'a pas été testée.

4. **Formule une recommandation, sans prendre la décision.** 
Fournis une recommandation de type **GO / NO-GO / GO CONDITIONNEL**, accompagnée des raisons qui la justifient. Cette recommandation doit être explicitement présentée comme un **avis consultatif** destiné à aider à la décision.

5. **VALIDATION HUMAINE OBLIGATOIRE.** 
Présente le document sous forme de **brouillon de rapport**. 
Liste :
   - les hypothèses ;
   - les données manquantes ;
   - les critères de sortie (exit criteria) encore non satisfaits.

   Demandez au **Product Owner** et au **Test Manager** de relire le rapport et de prendre la décision finale de validation et d'autorisation de mise en production.

## Format de sortie

## Rapport de clôture des tests — <cycle / version> build <ver>

**Métriques :**
- Tests exécutés : X/Y (Z %)
- Taux de réussite : P %
- Défauts ouverts : C critiques / H majeurs / M moyens
- Densité de défauts : d/fonctionnalité
- Couverture des exigences : R %

**Points clés :**
- ...

**Risques / éléments ouverts :**
- <défauts critiques ouverts>
- <zones à haut risque non testées>
- <critères de sortie non satisfaits>

**Recommandation (AVIS CONSULTATIF) :**
- GO / NO-GO / GO CONDITIONNEL, car ...

---

## VALIDATION HUMAINE OBLIGATOIRE

**Hypothèses :**
- ...

**Données manquantes :**
- ...

**Critères de sortie encore ouverts :**
- ...

**Ce rapport est un brouillon destiné à la prise de décision. Le responsable QA et le responsable de la mise en production doivent le relire, val
## Garde-fous

- Ne jamais inventer de chiffre, de résultat ou de couverture.
- Afficher les dénominateurs et les limites des indicateurs.
- Ne pas masquer une anomalie ouverte derrière un taux de réussite élevé.
- Ne pas présenter un avis consultatif comme une autorisation de livraison.
- Ne pas déclarer la campagne clôturée sans validation explicite.
