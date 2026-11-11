# Contrôle des vaccins du cheval

Petite application web qui vérifie si les vaccinations **grippe** et **rhinopneumonie** d'un cheval respectent le protocole obligatoire, à partir des dates d'injection.

## Fonctionnement

- Le protocole applicable dépend de la date de primo-vaccination, c'est-à-dire de la date de la 2e injection.
- Chaque intervalle est contrôlé : conforme, trop tôt ou trop tard (avec le nombre de jours d'écart).
- En cas d'écart, l'application cherche une **reprise du protocole** : la première injection à partir de laquelle toute la suite est conforme compte comme nouvelle première injection, et les injections précédentes sont barrées.
- La prochaine échéance est indiquée.
- Le cheval peut concourir à partir du 8e jour suivant la 2e injection de la primo-vaccination ou une injection de rappel.
- Rappels : tolérance de +1 jour. 1 mois équivaut à 30 jours.
- Les dates sont enregistrées uniquement dans le navigateur (`localStorage`) ; rien n'est envoyé sur un serveur.

## Protocoles appliqués

| Date de primo-vaccination (2e injection) | 1re → 2e injection | 2e injection → premier rappel | Entre chaque rappel |
|---|---|---|---|
| Grippe, avant le 01/01/2013 | 21 à 92 jours | 1 an maximum | 1 an maximum |
| Grippe, du 01/01/2013 au 31/12/2023 | 21 à 92 jours | 5 à 6 mois (150 à 180 jours) | 1 an maximum |
| Grippe, à partir du 01/01/2024 | 21 à 60 jours | 120 à 180 jours | 1 an maximum |
| Rhinopneumonie, avant le 01/01/2024 | 21 à 92 jours | 1 an maximum | 1 an maximum |
| Rhinopneumonie, à partir du 01/01/2024 | 21 à 60 jours | 120 à 180 jours | 1 an maximum |

Source : [Règlement des compétitions FFE, dispositions générales](https://www.ffe.com/media/13278/download) (version juillet 2026), articles 1.6-3 et 1.8.B.3. Cet outil est une aide à la vérification : le règlement fait foi.

## Mise en ligne

Le site est un simple fichier `index.html`, publié avec GitHub Pages (branche `main`, dossier racine).
