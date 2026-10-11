# Vérification — harmonisation d’Amélia

## Itération et périmètre

- `.agents/tasks/amelia-review.json` était absent : première itération.
- Les six documents Markdown source présents à la racine ont été examinés : `draft.md`, `concept.md`, `concept_initial.md`, `ideation_initiale.md`, `style.md` et `README.md`.
- Les fichiers de `.agents/`, les rapports générés et les fichiers binaires ont été exclus de la recherche de contenu.

## Fichiers modifiés

- `concept.md` : remplacement de l’ancienne chevelure cuivrée et tressée dans le portrait d’Amélia; ajout de son impulsivité à ses qualités et défauts existants.
- `concept_initial.md` : ajout de sa chevelure et de son impulsivité à sa fiche au commencement de l’histoire.
- `ideation_initiale.md` : harmonisation de l’introduction descriptive d’Amélia avec sa chevelure et son impulsivité, présentée avec son obstination et son initiative.
- `.agents/tasks/amelia-verification.md` : création de la présente note de vérification.

## Fichiers examinés et laissés inchangés

- `draft.md` : le texte montre Amélia en action, mais ne contient pas de portrait physique ou personnel existant à compléter. Le récit et le chapitrage sont restés intégralement inchangés.
- `style.md` : aucune fiche ni description propre à Amélia; les règles stylistiques canoniques sont restées inchangées.
- `README.md` : contient uniquement le titre du projet et aucun portrait d’Amélia.

## Confirmation par portrait modifié

| Fichier | Blancs | Courts | Ébouriffés | Impulsive | Cohérence |
| --- | --- | --- | --- | --- | --- |
| `concept.md` | oui | oui | oui | oui | Formulation exacte « cheveux blancs, courts et ébouriffés »; impulsivité ajoutée à « brillante, généreuse, enthousiaste […] et obstinée ». |
| `concept_initial.md` | oui | oui | oui | oui | Même formulation physique; impulsivité ajoutée sans retirer sa générosité, son enthousiasme ni son obstination. |
| `ideation_initiale.md` | oui | oui | oui | oui | Même formulation physique; elle reste brillante, obstinée et pleine d’initiative, tout en étant aussi impulsive. |

## Contrôles transversaux

- La formulation « cheveux blancs, courts et ébouriffés » apparaît dans chacun des trois portraits modifiés.
- La recherche de `impulsiv` confirme le trait dans chacun de ces trois portraits.
- L’ancienne formulation « longue tresse » ne subsiste dans aucun Markdown source de la racine.
- La seule occurrence restante de « cheveux cuivrés » décrit explicitement Nina Orsoff dans `concept.md`, pas Amélia.
- Aucune graphie non accentuée `Amelia` n’a été trouvée.
- Aucun autre portrait ou passage descriptif d’Amélia n’a été trouvé dans les Markdown source de la racine.
- `concept_initial.md` reste limité à la situation initiale : seule la fiche initiale d’Amélia a été complétée et aucun événement futur n’y a été ajouté.
- Aucun élément d’intrigue, secret narratif, lieu, autre personnage, règle stylistique ou chapitre n’a été ajouté ou modifié.

## Validation disponible

Le dossier est documentaire et ne contient ni `package.json`, ni `Makefile`, ni `pyproject.toml`; aucune commande de build ou de test existante n’est applicable. La validation a donc consisté en une relecture ciblée de chaque portrait modifié et en des recherches transversales dans tous les Markdown source de la racine.
