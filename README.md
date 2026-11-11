# Contrôle des vaccins du cheval

Petite application web qui vérifie si les vaccinations **grippe** et **rhinopneumonie** d'un cheval respectent le protocole obligatoire, à partir des dates d'injection.

## Fonctionnement

- Le protocole applicable est choisi d'après la date de la première injection.
- Chaque intervalle est contrôlé : conforme, trop tôt ou trop tard (avec le nombre de jours d'écart).
- En cas d'écart, l'application cherche une **reprise du protocole** : la première injection à partir de laquelle toute la suite est conforme compte comme nouvelle première injection, et les injections précédentes sont barrées.
- La prochaine échéance est indiquée.
- La dernière injection doit dater de plus de 7 jours : le cheval est en règle à partir du 8e jour qui suit.
- Les dates sont enregistrées uniquement dans le navigateur (`localStorage`) ; rien n'est envoyé sur un serveur.

## Protocoles appliqués

| Première injection | 1re → 2e injection | 2e injection → premier rappel | Entre chaque rappel |
|---|---|---|---|
| Grippe, avant le 01/01/2013 | 21 à 92 jours | 1 an maximum | 1 an maximum |
| Grippe, du 01/01/2013 au 31/12/2023 | 21 à 92 jours | 5 à 6 mois | 1 an maximum |
| Grippe, à partir du 01/01/2024 | 21 à 60 jours | 120 à 180 jours | 1 an maximum |
| Rhinopneumonie, avant le 01/01/2024 | 21 à 92 jours | 1 an maximum | 1 an maximum |
| Rhinopneumonie, à partir du 01/01/2024 | 21 à 60 jours | 120 à 180 jours | 1 an maximum |

Cet outil est une aide à la vérification : le règlement officiel et le vétérinaire font foi.

## Mise en ligne

Le site est un simple fichier `index.html`, publié avec GitHub Pages (branche `main`, dossier racine).
